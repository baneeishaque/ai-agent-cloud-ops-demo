# ai-agent-cloud-ops-demo

An always-on AI agent pattern, documented end to end: run **OpenClaw on Tencent Cloud
Lighthouse**, drive it from **WhatsApp**, and let it monitor competitor prices and warehouse
inventory overnight — while your laptop stays closed.

This repository is a content and operations kit, not an application. It contains the system
design, the exact overnight prompt, the guardrails, and a complete publishing suite (article,
social assets, and a 37-locale video pipeline) that presents the pattern.

The pattern is documented from the Tencent Cloud International Developer article
[Does Closing Your Laptop Stop Your AI Agent? Keep It Running on Lighthouse](https://x.com/tenctcloud_Intl/status/2101938368179577243)
(September 21, 2026). This kit explains the system as-is and adds the engineering analysis
around it.

## The problem in one line

Closing a laptop lid can put it to sleep, drop the network, and pause the agent — exactly when
overnight shopping hours in Europe and the US peak for teams on Beijing time (UTC+8).

## The pattern

Three planes, one instance:

```text
WhatsApp (control plane)  →  OpenClaw on Lighthouse (data plane)  →  /workspace files (evidence)
```

1. **Deploy and connect.** Create a Lighthouse Linux instance from the OpenClaw application
   template (2 vCPU / 2 GB / 40 GB is the walkthrough plan), connect a model API key, and link
   WhatsApp by QR code from *Settings → Linked Devices*.
2. **Schedule the overnight job.** Send the monitoring prompt in WhatsApp: watch competitor
   prices and warehouse stock, alert on changes, dedupe repeated alerts, send an 08:00 UTC+8
   summary even when nothing happened, and stay read-only.
3. **Verify in the morning.** Read the report in WhatsApp, then compare it with the saved log
   on the instance disk (`/workspace/cross-border-ops/overnight-summary-<date>.txt`).

## Repository map

| Path                                                | Contents                                                       |
| --------------------------------------------------- | -------------------------------------------------------------- |
| [`docs/`](docs/README.md)                           | System design, the annotated prompt cookbook, webinar playbook |
| [`content/funnel-medium/`](content/funnel-medium/README.md) | Article + social funnel (9 assets)                     |
| [`content/youtube/`](content/youtube/README.md)     | 37-locale video pipeline (scenes, translations, subtitles)     |
| [`content/README.md`](content/README.md)            | Asset map, publishing order, and conventions                   |

## Quickstart

```bash
npm install                                        # Playwright Chromium (slide rendering)
python3 content/youtube/build-scenes.py --check    # validate the 37 translations
python3 content/youtube/build-scenes.py            # write scenes.json
python3 content/youtube/build-video.py --subtitles --docs
node content/youtube/render-slides.mjs --locale en # slide smoke test
```

Requirements: macOS for the `say` narration stage, `ffmpeg`/`ffprobe` on PATH, Node.js 20+,
and Python 3.9+ (stdlib only). See [`content/youtube/README.md`](content/youtube/README.md)
for the full pipeline.

## Trade-offs, honestly

The pattern is not free: a cloud instance is a recurring cost, the agent holds read access to
business data, chat apps are a consumer control plane with their own limits, and
"monitor-only" is a prompt-level guardrail — not a sandbox. The comparison table, the
guardrail analysis, and the failure modes are in
[`docs/system-design.md`](docs/system-design.md).

## License

MIT — see [LICENSE](LICENSE).
