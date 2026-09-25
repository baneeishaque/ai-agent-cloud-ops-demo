# Prompt cookbook — the overnight monitoring job

The monitoring prompt is the program. This document quotes the documented prompt verbatim,
annotates every clause, and collects the variations and guardrail clauses worth reusing.

## 1. The prompt, verbatim

From the source article, sent in WhatsApp after the data sources are connected and one sample
record per source has been verified:

> Tonight, monitor competitor prices for the configured products and inventory levels at the
> US East Coast warehouse.
>
> If a competitor lowers its price or inventory falls below 50 units, alert me in this WhatsApp
> chat. Include the product, the change in price or stock level, and the time. Send another
> alert for the same issue only if its status changes again.
>
> At 08:00 Beijing time (UTC+8) tomorrow, end the monitoring session and send a summary of
> anything that needs attention. Send a report even if there are no issues. Save the monitoring
> log to the workspace and return its file path.
>
> If a data source becomes unavailable or monitoring stops, tell me promptly. Monitor and
> recommend only: do not change prices, place purchase orders, or contact customers.
>
> Before starting, verify access to the data sources and confirm the monitoring frequency.
> Send a status confirmation once monitoring begins.

## 2. Line-by-line annotation

| Clause                                             | Intent                                    | Failure it prevents                                  |
| -------------------------------------------------- | ----------------------------------------- | ---------------------------------------------------- |
| "the configured products" and "the US East Coast warehouse" | Fix the scope to what was set up  | The agent inventing a broader or different scope     |
| "Tonight"                                          | Bounded session                           | A job that runs forever without a defined end        |
| "If a competitor lowers its price"                 | Event definition: price drop              | Polling noise; alerts on unchanged prices            |
| "or inventory falls below 50 units"                | Event definition: threshold               | Undefined "low stock" meaning something different nightly |
| "alert me in this WhatsApp chat"                   | Channel is explicit                       | Alerts going to email or a dashboard nobody watches  |
| "Include the product, the change … and the time"   | Alert payload contract                    | "Price changed" alerts you cannot act on             |
| "another alert … only if its status changes again" | Dedupe by state transition                | Alert storms while a condition stays true            |
| "At 08:00 Beijing time (UTC+8)"                    | Absolute time, explicit zone              | UTC/DST ambiguity; a report that drifts an hour      |
| "Send a report even if there are no issues"        | Zero-report clause                        | Silent success indistinguishable from silent failure |
| "Save the monitoring log … return its file path"   | Durable evidence, addressable             | Chat-only history that cannot be audited or diffed   |
| "If a data source becomes unavailable … tell me"   | Degradation alarm                         | A job that quietly reports "all clear" on stale data |
| "Monitor and recommend only"                       | Authority boundary                        | An agent taking irreversible business actions        |
| "verify access … confirm the monitoring frequency" | Pre-flight check                          | Discovering at 08:00 that the job never started      |
| "Send a status confirmation once monitoring begins" | Start-of-run handshake                   | Uncertainty about whether the schedule is armed      |

## 3. Variations

Swap clauses, keep the structure (scope → events → channel → time → zero-report → evidence →
failure alarm → authority → pre-flight).

### Tighter polling window

> Check every 30 minutes between 20:00 and 08:00 Beijing time (UTC+8), then stop.

### Multiple warehouses

> Monitor inventory at the US East Coast and US West Coast warehouses. Alert per warehouse,
> and name the warehouse in every alert.

### Weekly digest instead of nightly

> Run Monday through Friday. On Saturday at 09:00 Beijing time (UTC+8), send one weekly summary
> that groups alerts by product and counts how many times each threshold was crossed.

### Escalation path

> If the same product crosses the threshold on two consecutive nights, mark it as escalating in
> the morning summary.

### Holiday pause

> Do not run on October 1–7. Send a single message on September 30 confirming the pause.

## 4. Guardrail clause library

- "Monitor and recommend only."
- "Do not change prices, place purchase orders, or contact customers."
- "Use read-only access to the configured sources; never request write credentials."
- "If you cannot verify a source, report the failure instead of estimating."
- "Never fabricate a reading; mark missing data as missing."
- "Keep all output inside the workspace; message no one except this chat."
- "If an instruction is ambiguous, ask before acting."

## 5. Before you shut the laptop

1. Confirm monitoring is active (the start-of-run confirmation arrived).
2. Confirm the 08:00 summary is scheduled.
3. Confirm the Lighthouse instance stays running.

## 6. Anti-patterns

| Anti-pattern                          | What breaks                                             |
| ------------------------------------- | ------------------------------------------------------- |
| "Watch prices and tell me if anything changes" | No scope, no threshold, no channel contract    |
| No dedupe clause                      | Repeated alerts for one unchanged condition             |
| No zero-report clause                 | A silent failure looks like a quiet night               |
| No timezone                           | The report arrives at the wrong local hour, or drifts   |
| No file path requested                | No evidence to audit in the morning                     |
| No pre-flight clause                  | The job may never have started                          |
| Write authority left open             | The agent can act, not just observe                     |
| "Approximately 50" or "low stock"     | The threshold moves with the model's mood               |

## 7. Iterating safely

- Change **one clause per night** and compare the saved logs — the file is a diffable record.
- Keep the prompt in version control next to the job's expectations; treat it like code.
- When alert quality drops, fix the event definition before raising the model.
