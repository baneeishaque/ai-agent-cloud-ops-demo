# Webinar playbook — from an open registration to the follow-up email

Everything needed to run "Your laptop is a bad home for an AI agent" as a live technical
session: timeline, deck plan, demo script, Q&A design, runbook, and follow-up.

Assumptions from the organizer: the community has already been told about the webinar, a
registration form is live, and registration is handled through that form.

## 1. Positioning

- **Title:** "Close your laptop: running an AI agent 24/7 from a chat window"
- **One-line promise:** by the end, every attendee knows how to move an agent off their laptop,
  schedule an overnight job, and verify its work in the morning — and knows the trade-offs.
- **Audience:** software developers with roughly two years of experience. No cloud or AI-agent
  experience assumed; no React, Next.js, or Tencent Cloud account required.
- **Length:** ~2 hours 15 minutes including a 30-minute Q&A at the end. Length is not a
  constraint, so the flow errs toward "finish the story" rather than "fit the slot".
- **Format:** screen-shared slides with a live deploy demo, recorded.

## 2. Timeline (assumes ~2 weeks of runway)

| When    | Action                                                                                              |
| ------- | --------------------------------------------------------------------------------------------------- |
| T-14    | Advertised (done). Confirm the registration form captures the fields in section 3                   |
| T-10    | Confirmation email to registrants: date, time in UTC+8 and their local time, what to prepare       |
| T-7     | Agenda email + calendar invite with the join link; open a "questions" field for the Q&A             |
| T-3     | Slides frozen; demo environment built and rehearsed once                                            |
| T-2     | Reminder email: "bring a laptop if you want to follow along; the first step is free-tier eligible"  |
| T-1     | Final reminder with the join link; publish the exact prompt and repo link as a teaser               |
| T-1h    | Host opens the room; check audio, screen share, recording                                            |
| T-0     | Run the day-of runbook (section 7)                                                                  |
| T+1     | Recording + slides + prompt cookbook sent to registrants and the community                          |
| T+3     | Feedback form (3 questions); collect "what should we automate next" ideas                            |
| T+7     | Publish a short recap post linking the recording; announce the next session                         |

## 3. Registration form — fields that pay off later

Keep the form short; these fields make the Q&A and the follow-up better:

- Name and email (already covered by the existing form).
- **Timezone** — so the calendar invite and reminders land at sane local times.
- **Experience level** — "new to cloud", "2–4 years", "5+ years"; use it to pick the depth of
  act 4.
- **"What would you want an always-on agent to do for you?"** — the seed bank for the Q&A and
  for real-life examples.
- **"Any question you want answered live?"** — the Q&A queue starts non-empty.
- Consent checkbox for recording and for the follow-up email.

## 4. Slide deck plan — simple slides, maximum content

Design rules:

- One idea per slide; a dark gradient background with a single accent bar (the same visual
  language as the project's video pipeline).
- Maximum density comes from **slide count and an appendix**, not from cramming: body text stays
  at three lines or fewer; the "code" chip carries the detail.
- Every concept slide has a **real-life anchor** (an airport, a missed price cut, a morning
  commute) before it has a definition.
- Flow is strictly simple → advanced: story, then timezone math, then architecture, then the
  demo, then the prompt, then trade-offs.
- Export a PDF backup of the deck; assume the live demo can fail.

| Act | Minutes | Slides | Content                                                                 | Real-life anchor                          |
| --- | ------- | ------ | ----------------------------------------------------------------------- | ----------------------------------------- |
| 0   | 5       | 3      | Welcome, promise, agenda; who this is for                               | —                                         |
| 1   | 10      | 6      | The half-open laptop story; sleep, network, pause                       | Laptops at airports and coffee shops      |
| 2   | 10      | 6      | The UTC+8 timezone gap; when EU/US peak hours fall; cost of a missed night | Missed competitor price cut; late stockout |
| 3   | 12      | 8      | Three planes: control, compute, evidence; the hosting comparison table  | Phone as the control point                |
| 4   | 20      | 8      | Live demo: deploy, connect the model, link WhatsApp, send "hi"          | "It answers on WhatsApp" moment           |
| 5   | 20      | 10     | The prompt is the program: annotated clauses; dedupe; zero-report; guardrails | The 08:00 report arriving on the commute |
| 6   | 10      | 5      | Verify: chat report vs saved file vs execution records                  | Auditing one night's work                 |
| 7   | 12      | 8      | Trade-offs and failure modes; what monitor-only really means            | "The night the source went down"          |
| 8   | 30      | —      | Q&A session (see section 6)                                             | —                                         |
| A   | —       | 12     | Appendix: prompt variations, cost math, snapshot restore, glossary      | —                                         |

## 5. Live demo script

**Pre-flight (T-15 minutes):**

- Instance state: Lighthouse instance *Running*, OpenClaw application reachable.
- Model key saved; WhatsApp linked and replying; test message sent and answered.
- Sample data source verified with one record shown on screen.
- The monitoring prompt pre-typed in a notes app (never type it live).
- The morning report and the saved file open in background tabs.
- Recording started; fallback screenshots open in a second window.

**Beats:**

1. Show the console, create the instance from the OpenClaw template (2 vCPU / 2 GB / 40 GB),
   region outside the mainland. Talk through *why* the region matters.
2. Connect the model: *Pre-installed application* → *Models* → API key → save.
3. Link WhatsApp: *Channels* → *Authorization Access* → QR → phone → *Linked Devices*. Send
   "hi" and let the room see the reply.
4. Paste the overnight prompt; show the start-of-run confirmation.
5. Close the laptop lid **on camera**; let that sit for a beat — this is the thesis.
6. Switch to the morning artifacts: the report in WhatsApp, the log file path, the execution
   records. Walk one alert from source change → chat message → file line.

**Fallback:** if the QR link or the model call fails, play the recorded 4-minute demo video and
continue with the screenshots; do not debug live for more than two minutes.

## 6. Q&A session design (at the end, as a session)

- **Queue:** start from registration questions; add live questions via chat; upvote the room's
  favourites.
- **Format:** 30 minutes, moderated. The moderator groups questions into "architecture",
  "safety", "cost", and "next steps".
- **Seed questions** (use if the room is quiet):
  1. What stops the agent from changing prices on its own?
  2. What happens if WhatsApp unlinks the device overnight?
  3. How do you keep the agent's data access read-only?
  4. Is a $5 VPS enough, or does this need Lighthouse specifically?
  5. How do you test a prompt like this before trusting it?
  6. What would you automate next with the same pattern?
- **Parking lot:** anything needing more than two minutes gets written down and answered in the
  follow-up post.
- **Safety:** never promise unattended write actions; repeat the least-privilege posture.

## 7. Day-of runbook

| Time     | Action                                                                  |
| -------- | ----------------------------------------------------------------------- |
| T-60 min | Open room; start recording; check audio and screen share                |
| T-15 min | Demo pre-flight complete; fallback window open                          |
| T-5 min  | Welcome slide up; moderator ready with the question queue               |
| Start    | Act 0; state the promise and the Q&A-at-the-end format                  |
| Mid      | Act 4 demo; watch the clock only to protect the Q&A                     |
| Q&A      | 30 minutes; moderator drives; park the long answers                     |
| End      | Share the repo, the prompt cookbook, and the feedback form link         |
| T+0      | Stop recording; export the chat transcript for the follow-up            |

## 8. Rehearsal

- One full dry run with a timer: acts 0–3 should land under 40 minutes.
- One demo-only run where the QR link deliberately fails, to practise the fallback.
- One slide pass for the "simple" rule: if a slide has more than three lines of body text, move
  detail to the appendix or the code chip.
- Confirm the deck reads top-to-bottom as one story with no forward references.

## 9. Follow-up sequence

1. **T+1:** email registrants the recording, the deck PDF, the
   [prompt cookbook](../docs/prompt-cookbook.md), and the repository link; thank the Q&A
   participants by name.
2. **T+1:** post a recap in the community with the same links, plus the top three questions
   with written answers.
3. **T+3:** feedback form — one rating, one "what was unclear", one "what next".
4. **T+7:** publish the "parking lot" answers as a short post; announce the next session.

## 10. Metrics to watch

| Metric                        | Source                     | Target            |
| ----------------------------- | -------------------------- | ----------------- |
| Registration → attendance     | Form count vs. room count  | > 40%             |
| Q&A participation             | Chat + live questions      | > 10 questions    |
| Completion (stayed to Q&A end) | Room count at minute 90   | > 60% of attendees |
| Follow-up link clicks         | UTM-tagged links in email  | > 25%             |
| "What next" ideas collected   | Feedback form              | > 5               |
