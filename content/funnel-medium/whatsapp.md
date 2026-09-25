# WhatsApp — developer community groups

Messages for React / web developer community groups. Share **once per group**, ideally after
asking an admin. The goal is a useful artifact, not a broadcast; the etiquette notes below are
part of the deliverable.

## Short version (default)

> Hi all 👋 I wrote up how I moved my overnight AI agent off my laptop and onto a cloud
> instance I control from WhatsApp — the part that isn't in tutorials: the prompt clause that
> makes silent failures impossible, alert dedupe, and why "monitor and recommend only" is
> policy, not a sandbox.
>
> Full article: <https://medium.com/@baneeishaque/close-your-laptop-agent-cloud-ops?utm_source=whatsapp&utm_medium=social&utm_campaign=ai-agent-cloud-ops-medium>
>
> Code and prompt cookbook are MIT on GitHub if you want to steal the pattern. Happy to
> answer questions here.

## Longer version (groups that welcome detail)

> Sharing something I wish I'd found a year ago.
>
> I run an overnight price-and-inventory monitor for a small cross-border store. It kept dying
> because my laptop sleeps — so I moved it to a small cloud instance (OpenClaw on Tencent Cloud
> Lighthouse) and made WhatsApp the control plane. The interesting part isn't the hosting:
>
> • three planes: chat = control, instance = compute, files on disk = evidence
> • the prompt is the program: fixed scope, defined events (price drop, stock < 50), payload
> contract (product, change, time)
> • dedupe: alert again only if the status changes — no alert storms
> • zero-report: "send a report even if there are no issues" — silence stops meaning success
> • absolute time: 08:00 Beijing time (UTC+8), not "in the morning"
> • guardrails: "monitor and recommend only" — and read-only credentials behind the policy
>
> I wrote the full system design, including the trade-offs I accepted, here:
> <https://medium.com/@baneeishaque/close-your-laptop-agent-cloud-ops?utm_source=whatsapp&utm_medium=social&utm_campaign=ai-agent-cloud-ops-medium>
>
> Repo (MIT): github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

## Etiquette

- Ask an admin before posting in moderated groups; "sharing a write-up I made" gets a warmer
  reception than a silent drop.
- Share once per group. Do not repost in the same group when engagement is low; the article is
  evergreen.
- Answer questions in the group instead of DMing links.
- If the group has a "share your projects" day or thread, use it — and drop the longer version
  there.
