# System design — an always-on agent, driven from chat

This document explains the system documented in the source article, then adds the engineering
analysis the article leaves implicit: why each piece exists, which failures it prevents, and
where the design still depends on trust.

## 1. The problem

A laptop is a personal computer with a sleep policy. Closing the lid can suspend the machine,
drop the network connection, and pause whatever was running — including a long-lived AI agent
process. The article opens with the viral consequence: people carrying half-open laptops
through airports and coffee shops to keep their agents alive.

For cross-border e-commerce teams, the timing is exactly wrong. Peak shopping hours in Europe
and the US fall overnight for a team on Beijing time (UTC+8), so the window when price checks,
inventory alerts, and unpaid-order monitoring matter most is the same window when the operator
is asleep and the laptop is closed.

## 2. Architecture — three planes, one instance

```text
+---------------------------+        +-----------------------------+        +----------------------+
| Control plane             |        | Compute plane               |        | Evidence plane       |
| WhatsApp on your phone    |  --->  | OpenClaw on Lighthouse      |  --->  | /workspace files     |
| (instructions, alerts,    |        | (agent runtime, scheduler,  |        | (durable log the     |
|  morning report)          |        |  tool access, model calls)  |        |  chat can reference) |
+---------------------------+        +-----------------------------+        +----------------------+
```

- **Control plane: the chat app.** The operator sends instructions from WhatsApp; the agent
  replies in the same thread. There is no dashboard to build and no VPN to keep open — the
  phone is the control point.
- **Compute plane: the cloud instance.** A Lighthouse instance runs the OpenClaw application
  image. It has a dedicated public IPv4 address, so the chat channel can reach it, and it runs
  independently of any laptop. Closing the laptop does not stop the cloud process.
- **Evidence plane: files on the instance disk.** Every monitoring run writes a log to the
  workspace (the article's example:
  `/workspace/cross-border-ops/overnight-summary-2026-09-19.txt`). The chat message is the
  notification; the file is the record. Verifying one against the other is the operator's
  audit step.

## 3. Why a cloud instance — the comparison

The article compares three hosting options across four factors. Reproduced as-is:

| Factor                | Laptop                                                                | Home/office host (Mac mini, PC)                                       | Tencent Cloud Lighthouse                                        |
| --------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------- |
| Power and scheduling  | Lid close can sleep, disconnect the network, pause background tasks   | Needs continuous power; outages and restarts interrupt tasks          | Runs independently, 24/7; backed by the Tencent Cloud SLA       |
| Network               | Changing locations or losing Wi-Fi interrupts persistent connections  | Relies on home/office network; cross-border webhooks may be unstable  | Dedicated public IPv4 for chat apps to reach the instance       |
| Isolation and recovery | Runs alongside personal files, limited isolation                     | Stays on the home network; compromise recovery may need a reinstall   | OS-level isolation; restore from a snapshot in the console      |
| Cost and operations   | Occupies the main computer, adds hardware wear                        | $500+ upfront, plus DIY dynamic DNS                                   | Subscription pricing, no hardware or home network to maintain   |

Analysis, not vendor copy: the decisive column is the first two factors. Sleep policy and
residential network reliability are the two properties a personal machine cannot promise, and
they are precisely the properties an overnight job depends on. Isolation is the sleeper
benefit — an agent that reads competitor pages and holds API keys is exactly the workload you
do not want running beside your personal files.

## 4. Setup, condensed

The full walkthrough lives in the article; the three steps in one screen:

1. **Deploy and connect.** Lighthouse console → create a Linux instance → *Application
   templates* → OpenClaw. The walkthrough plan is 2 vCPU / 2 GB / 40 GB. Choose a region
   outside the Chinese mainland when the chat app is WhatsApp, Telegram, or Discord. When the
   instance is *Running*, open *Pre-installed application* → *Models* → enter the API key.
   Then *Channels* → WhatsApp → *Authorization Access*, and scan the QR from
   WhatsApp → *Settings* → *Linked Devices* → *Link a Device*. Test with "hi" and wait for the
   reply.
2. **Schedule the overnight job.** Share the data sources (competitor product URLs, warehouse
   inventory), grant read access, and verify one sample record per source. Then send the
   monitoring prompt — see [`prompt-cookbook.md`](prompt-cookbook.md).
3. **Verify in the morning.** Read the report in WhatsApp at the scheduled time, compare it
   with the saved file on the instance, and review the job's execution records.

## 5. The reliability design (why the prompt looks over-specified)

Six clauses in the monitoring prompt carry the reliability story:

| Clause                                        | Failure it prevents                                      |
| --------------------------------------------- | -------------------------------------------------------- |
| Alert on price drop or stock below 50 units   | Alerting on every poll; noise that trains you to ignore  |
| Alert again only if the status changes        | Duplicate storms when a condition stays true             |
| Send a summary even if there are no issues    | Silent success looking identical to silent failure       |
| Save the log and return its file path         | Chat-only history that cannot be audited or diffed       |
| Tell me if a data source becomes unavailable  | A job that quietly degrades to "nothing to report"       |
| Verify access and confirm the frequency first | Discovering at 08:00 that the job never started          |

The through-line: **a scheduled agent must make its absence observable.** The article's prompt
does this twice — once with "send a report even if there are no issues" and once with "if
monitoring stops, tell me promptly".

## 6. Guardrails — and their honest limit

The prompt ends with an explicit authority boundary:

> Monitor and recommend only: do not change prices, place purchase orders, or contact
> customers.

This is a **prompt-level guardrail**, and it is the right first move: the agent's job is to
observe and report, so it is granted no write authority over business systems. But analysis
must be honest about the boundary:

- A prompt instructs the model; it does not sandbox it. The real control is the credentials the
  agent holds. Grant read-only keys, scoped to the exact data sources, and revoke them when the
  job ends.
- "Do not contact customers" is only as strong as the tools the agent has. If the WhatsApp
  channel can message arbitrary contacts, the boundary is policy, not capability.
- Keep the human in the loop for every consequential action: the agent recommends, the operator
  decides, and the decision happens in systems the agent cannot reach.

Used this way, monitor-only is a least-privilege posture, not a promise.

## 7. Failure modes

| Failure                          | Symptom                                        | Mitigation in the design                                            |
| -------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------- |
| Laptop lid closed                | Local agent pauses                             | Agent runs on the instance, not the laptop                          |
| Home power/network outage        | Overnight job missed                           | Instance has its own power and public IPv4                          |
| Chat session drops (linked device) | Alerts arrive nowhere                        | Re-link QR; keep the summary in the file as the durable record      |
| Model API outage                 | Agent stops mid-run                            | Prompt requires "tell me promptly" on stop; execution records show it |
| Data source blocks or changes    | Empty or stale readings                        | Sample-record check at setup; unavailable-source clause in the prompt |
| Alert fatigue                    | Operator stops reading                         | Dedupe by status change; one morning summary                        |
| Instance drift or compromise     | Unknown state                                  | OS-level isolation; restore from a console snapshot                 |

## 8. Cost and operations

The article frames pricing as subscription-based, with no dedicated hardware and no home
network to maintain — the honest comparison is not instance price versus zero, it is instance
price versus the alternatives: a Mac mini ($500+ upfront, per the article), a laptop that must
stay awake, or an employee watching a screen overnight.

At the time of writing, the Tencent Cloud Lighthouse 6th Anniversary Promotion lists new
OpenClaw instances at up to 80% off and existing instances at 40% off renewals. Promotions
expire; verify pricing before quoting it in any published asset.

## 9. What this is not

- **Not a sandbox.** Isolation is OS-level on the instance; the agent's authority inside that
  OS is whatever you grant it.
- **Not an execution system.** The documented posture is monitor-and-recommend; there is no
  automated price change, purchase, or customer contact.
- **Not unattended forever.** The design assumes a daily operator loop: read the report, verify
  the file, adjust thresholds.
- **Not vendor-neutral in its tooling.** The walkthrough uses Lighthouse's OpenClaw application
  image; the pattern (always-on box + chat control + scheduled job + file evidence) ports to
  any VPS, but the steps in this kit describe the documented path only.
