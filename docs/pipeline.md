# Pipeline: phone → notes → summary

Built in phases. Each phase works on its own before the next one starts.

## Phase 1: manual (from the first shift)

- **Capture:** one Google Doc on the phone, "M32 Notes". Newest date heading at the top, with bullets
  under it. Notes go in on breaks and lunch only, unless the Store Manager OKs phone use during training.
- **Voice:** Recorder app transcripts (text) for training talks, **only with the speaker's consent and
  the Store Manager's OK.** The company bans recording "proprietary operational activity." For anything
  else, record a voice memo of **my own** recap after the shift.
- **After the shift:** copy the day's bullets into `daily/`, fill in `templates/end-of-day.md`, commit.

## Phase 2: nightly script (after week 1)

Runs once at the end of the day. Not hourly: phone notes only happen on breaks, so hourly runs would
mostly find nothing.

1. `rclone` (already set up on the homelab) pulls the "M32 Notes" Doc and any new transcripts from a
   Drive folder.
2. A local model (via LiteLLM on the homelab) fills `templates/end-of-day.md` **from the notes only.** It
   is told to quote the bullet behind each point and to leave a section empty rather than guess.
3. A name and number scrub runs before anything is committed.
4. Commit to **local Gitea** (hourly is fine there). **Push to GitHub once a day** at most, by hand or
   with one evening job. A steady drip of automated GitHub commits is what got an account flagged before.

## Phase 3: Hermes (after phase 2 is stable)

- Point Hermes at `summaries/` and `learning/` so it can spot patterns across weeks. It should
  answer things like "what do I keep getting stuck on?" or "what did I learn about de-escalation?"
- Friday: generate `summaries/weekly/` from `templates/weekly-review.md`.

## Phone shortcut for Recorder

- **Volume-key sequence:** Android has no built-in setting for this. The free, open-source **Key Mapper**
  app (Play Store or F-Droid) can map a triple volume-up press to "launch app → Recorder." It needs the
  accessibility permission.
- **Simpler:** a home-screen shortcut, or a launcher swipe gesture set to open Recorder.
- Google Recorder is a Pixel app. On other phones, use the built-in recorder with transcription, or
  Live Transcribe.
