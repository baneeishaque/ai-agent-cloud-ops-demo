# LinkedIn — two posts

Post 1 is the announcement (day 1); post 2 is the engineering story (2–3 days later). Both
funnel to the Medium article.

## Post 1 — the hook (day 1)

> Developers are carrying half-open laptops through airports just to keep their AI agents
> awake. The lid sensor has become a job scheduler.
>
> I did it too — until I moved my overnight price-and-inventory monitor off my laptop and onto
> a small cloud instance controlled entirely from WhatsApp.
>
> The result: closing the lid no longer pauses the agent. Instructions, alerts, and the 08:00
> report all live in one chat thread; the evidence lives in a log file on the instance disk.
>
> Three steps, one prompt, and a set of guardrails I would not run this without.
>
> I wrote up the whole system — the hosting comparison, the prompt line by line, and the
> trade-offs nobody puts in the announcement post:
>
> <https://medium.com/@baneeishaque/close-your-laptop-agent-cloud-ops?utm_source=linkedin&utm_medium=social&utm_campaign=ai-agent-cloud-ops-medium>
>
> #AI #CloudComputing #DevOps #SoftwareEngineering

## Post 2 — the engineering story (day 2–3)

> The most important line in my overnight agent is the one that reports nothing.
>
> "Send a report even if there are no issues."
>
> Scheduled agents fail silently by default. Without that clause, a quiet night and a job that
> died at 23:40 look exactly the same — and you find out when a competitor's price cut has
> already done its damage.
>
> The rest of the prompt is a spec: fixed scope, defined events (price drop, stock below 50
> units), dedupe by status change, an absolute UTC+8 report time, a saved log file, a
> degradation alarm, and a hard authority boundary — "monitor and recommend only: do not change
> prices, place purchase orders, or contact customers."
>
> One more thing engineers should hear: that last clause is policy, not sandbox. Read-only
> credentials are the control.
>
> Full annotated prompt and the three-plane architecture:
>
> <https://medium.com/@baneeishaque/close-your-laptop-agent-cloud-ops?utm_source=linkedin&utm_medium=social&utm_campaign=ai-agent-cloud-ops-medium>
>
> #AI #DevOps #CloudArchitecture #Automation
