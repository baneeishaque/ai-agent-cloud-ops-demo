# Content kit

Everything needed to present the always-on agent pattern: one canonical long-form article,
platform-specific adaptations, and a multilingual video pipeline.

## Asset map

| File                                            | Platform                    | Format                          | Length        |
| ----------------------------------------------- | --------------------------- | ------------------------------- | ------------- |
| [`funnel-medium/`](funnel-medium/README.md)     | Medium + social             | Funnel to the Medium deep dive  | 9 assets      |
| [`youtube/`](youtube/)                          | YouTube                     | Full video pipeline (37 locales) | ~3 minutes    |

## Publishing order

1. **Publish the Medium article first** — every funnel asset links to it.
2. **Community blog post** the same day; it hands readers to the article.
3. **LinkedIn announcement** the next morning; the engineering story 2–3 days later.
4. **X thread** the same day as the LinkedIn announcement, a few hours later.
5. **Instagram carousel + Reels** midweek; Snapchat Spotlight the same day as Reels.
6. **Facebook** the day after the short-form push.
7. **WhatsApp developer groups** last — they reach people who already know you; give them the
   polished artifact, not the announcement.
8. **YouTube video** whenever the multilingual cut is ready; it is the only asset that shows
   all 37 locales in one artifact.

## Conventions

- **Repo URL** used throughout:
  `https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo`. If the published URL
  differs, find-and-replace before posting.
- **UTM tags**: append
  `?utm_source=<platform>&utm_medium=social&utm_campaign=ai-agent-cloud-ops-medium` to Medium
  links (the community blog post uses `utm_source=community-blog&utm_medium=referral`).
- **Numbers** quoted in the kit (3 setup steps, 4 comparison factors, the 50-unit stock
  threshold, 08:00 UTC+8 report time, 2 vCPU / 2 GB / 40 GB plan, 37 video locales) are
  verified against [`youtube/scenes.json`](youtube/scenes.json) and the source article.
  Re-check before posting if the project changes.
- **Promo figures** (up to 80% off new OpenClaw instances, 40% off renewals) come from the
  Lighthouse 6th Anniversary Promotion as documented in September 2026; promotions expire, so
  verify before quoting.
- **Screenshots** for carousel/X posts: the Lighthouse instance list, the OpenClaw application
  panel, the WhatsApp thread with the 08:00 report, and the saved log file path. Suggested
  filenames: `shot-console.png`, `shot-openclaw.png`, `shot-whatsapp.png`, `shot-logfile.png`.

## Video pipeline (YouTube)

`youtube/` contains a scripted pipeline rather than a finished upload:

- `translations/<locale>.json` — per-locale slide titles and narrations (37 files; the
  community-reviewable layer).
- `build-scenes.py` — owns scene order, on-screen code, the locale roster, and voices;
  assembles `scenes.json`.
- `scenes.json` — generated single source of truth consumed by the renderer and builder.
- `render-slides.mjs` — renders slide images with headless Chromium (per-script fonts, RTL,
  Nastaliq line boxes).
- `build-video.py` — generates narration with macOS `say`, assembles per-locale videos, muxes
  the master multi-audio MKV (20 audio + 37 subtitle tracks), and exports subtitles.
- `subtitles/` — generated SRT/VTT files for all 37 locales, committed as deliverables.
- `metadata.md` — titles, descriptions, tags, and chapters per locale.

See [`youtube/README.md`](youtube/README.md) for the full pipeline, the locale roster, and the
17 subtitle-only locales.
