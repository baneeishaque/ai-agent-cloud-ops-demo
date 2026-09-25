# Medium funnel kit

Traffic funnel for the **standalone Medium deep dive** —
[`medium-article.md`](medium-article.md) — which lives separately from the
repository-announcement kit in the parent [`content/`](../README.md) folder.

Everything here points readers at one destination: the Medium article. The
article then funnels readers to the repository.

## Asset map

| File                                          | Platform             | Format                              | Length          |
| --------------------------------------------- | -------------------- | ----------------------------------- | --------------- |
| [`medium-article.md`](medium-article.md)      | Medium               | Deep dive: design, trade-offs, prompt | ~2,000 words  |
| [`community-blog-post.md`](community-blog-post.md) | Community blog  | Companion post, warmer voice        | ~1,200 words    |
| [`linkedin.md`](linkedin.md)                  | LinkedIn             | Two posts: hook + engineering story | 120–200 words   |
| [`x-thread.md`](x-thread.md)                  | X / Twitter          | 10-post thread                      | 280 chars/post  |
| [`facebook.md`](facebook.md)                  | Facebook             | Group/Page post                     | ~170 words      |
| [`whatsapp.md`](whatsapp.md)                  | WhatsApp             | Developer-group messages + etiquette | 60–120 words   |
| [`instagram.md`](instagram.md)                | Instagram            | 8-slide carousel + Reel caption     | Slides + caption |
| [`snapchat.md`](snapchat.md)                  | Snapchat             | Spotlight script                    | ~35 seconds     |
| [`reels.md`](reels.md)                        | Reels / Shorts / TikTok | Three short-form scripts         | 30–45 s each    |

## Publishing order

1. **Publish the Medium article first** — every asset below links to it, so it
   must resolve before anything else goes out.
2. **Community blog post** the same day (it is the soft-launch companion; it
   links to the Medium piece as "the full write-up").
3. **LinkedIn post 1** the next morning; post 2 two to three days later.
4. **X thread** the same day as LinkedIn post 1, a few hours later.
5. **Reels + Instagram carousel + Snapchat** midweek, all in one push — the
   short-form video drives the most cold traffic.
6. **Facebook** the day after the short-form push.
7. **WhatsApp developer groups** last and least often — treat it as a favour to
   communities, not a broadcast channel.

## Conventions

- **Medium URL placeholder** used throughout:
  `https://medium.com/@baneeishaque/close-your-laptop-agent-cloud-ops`.
  If the published URL differs, find-and-replace it in every file here
  **before** posting anything.
- **UTM tags**: append
  `?utm_source=<platform>&utm_medium=social&utm_campaign=ai-agent-cloud-ops-medium`
  to Medium links. The community blog post uses
  `utm_source=community-blog&utm_medium=referral`.
- **Repo URL** (used inside the Medium article and the community post):
  `https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo`.
- **Verified numbers** quoted here: 3 setup steps, 4 hosting comparison factors,
  the 50-unit stock threshold, the 08:00 Beijing time (UTC+8) report time, the
  2 vCPU / 2 GB / 40 GB walkthrough plan, 37 subtitle languages, and 20 narration
  tracks. Re-check against [`../youtube/scenes.json`](../youtube/scenes.json)
  and the source article before posting if the project changes.
- **Promo figures** (up to 80% off new OpenClaw instances, 40% off renewals)
  come from the Lighthouse 6th Anniversary Promotion as documented in September
  2026. Promotions expire — verify before quoting.
- **Screenshots** for carousel/short-form assets: the Lighthouse instance list,
  the OpenClaw application panel, the WhatsApp thread with the 08:00 report, and
  the saved log file path. Suggested filenames: `shot-console.png`,
  `shot-openclaw.png`, `shot-whatsapp.png`, `shot-logfile.png`.
