# M32 Self-Learning Notes

My learning log as a new **Customer Service Manager** in a grocery store. I write quick notes during the
day. At the end of each shift they get rolled into a summary: what I did, what I learned, what worked,
what didn't, and what to focus on tomorrow.

## The rules this repo lives by

These notes are about **my own growth as a manager**, not about the company. The employer's handbook
treats personal websites and "any other form of electronic communication" as social media, and bars
sharing proprietary information. So:

| Goes in | Never goes in |
|---|---|
| What I learned and how I handled it | Coworker or customer names. Use roles ("cashier A", "a guest") |
| Leadership and communication lessons | Sales, shrink, labour or any store numbers |
| Questions I need to ask | Internal procedures, schedules, security or cash-handling details |
| My own reflections and goals | Company documents, photos or audio |
| Text transcripts **with consent noted** | Raw audio (stays on my phone, only to check a transcript) |

Company documents and anything derived from them live in `private/`, which git ignores.

## Layout

```
templates/           copy these, don't edit them
schedule/            my shifts, so the hourly blocks line up
daily/YYYY/MM/       one file per shift: raw quick notes (YYYY-MM-DD.md)
transcripts/YYYY/MM/ text-only transcripts, consent line at the top
summaries/daily/     end-of-shift summary per day
summaries/weekly/    Friday review
learning/            running topic notes (leadership, communication, questions)
docs/pipeline.md     how notes get from my phone to here
private/             LOCAL ONLY: policy summary, source documents
```

## Daily flow (phase 1: manual, starting the first shift)

1. **On breaks:** add bullets to the day's notes (phone, Google Doc).
2. **After a training talk:** Recorder transcript, once the trainer and the Store Manager say yes.
3. **After the shift:** paste into `daily/`, write or generate the end-of-day summary from
   `templates/end-of-day.md`, then commit.

See `docs/pipeline.md` for the automated version that comes later.
