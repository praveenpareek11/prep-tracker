# Prep Tracker

A single-file interview prep tracker: a 16-week schedule ribbon, eight prep tracks, and 176 DSA problems with per-topic progress.

Everything is one `index.html` — no build step, no dependencies, no backend. Open the file directly in a browser.

## Using it

- **Prep Tracks** — the eight non-DSA tracks, each with its window on the calendar and a progress bar showing actual vs. expected-by-today.
- **DSA Problems** — 176 problems grouped by topic, filterable by topic / difficulty / status.
- **Focus now** — the current week's active tracks and your next few unchecked tasks.
- **Search** (`/`) — filters tasks and problems together, with match highlighting.
- Keyboard: `/` search, `1` tracks, `2` DSA, `Esc` clear.

A DSA checkbox means *re-implemented cold from a blank file* — not "read and understood."

## Plan dates

The plan start lives in synced state, not in the source. **Plan dates** (footer) shifts the whole schedule — every week boundary, the apply-ready date and the focus card move together — so a break gets absorbed instead of pretending the missing weeks were worked. Same sheet sets the DSA runway end and toggles the review ladder between `3d · 14d · 45d` and `3d · 14d`.

Current plan: starts **Aug 31 2026**, application-ready **Dec 14 2026**.

## Two separate bars

**Application readiness** is T0–T6 only. **DSA** is scored separately on its own runway, because conflating them is what produced a misleading "40% behind" when the real picture was a calendar that had drifted.

On the DSA bar the marker is the *target* pace from the runway end — the line that can be missed. Beneath it, a projection computed from observed throughput: hours/week actually logged, priced at ~50 min for a cold solve and ~18 for a re-solve, against the hours still owed. If the projection disagrees with the target, that gap is the point; move the rate or move the date, but don't hide it.

Pattern coverage (`N/22`) is reported as information. It is deliberately **not** a readiness gate — block-level breadth-first can't touch all 22 patterns by December, and a gate you can't meet is just noise.

## Spaced review

Ticking a problem puts it on a review ladder: **3 days → 14 days → 45 days**. Intervals chain from your last completed rep, so being late stretches the schedule rather than collapsing it.

Anything due appears in a **Due for review** panel at the top of the DSA tab, worst-overdue first, with a count in the header stats. Re-solve from a blank file, then:

- **Solved cold** — advance to the next interval. After the third rep the problem retires as *mastered*.
- **Struggled** — back in 3 days, staying on the same rung. It only advances once you clear it cleanly.

Each row also carries a small badge (`R2 · in 5d`, `R1 · 3d overdue`, `✓ mastered`), and the status filter has a **Due for review** option.

Problems ticked before this existed have no recorded solve date, so they stay off the ladder until you use the one-time **Start review schedule** button, which dates them today.

After a long gap the 3/14/45 spacing stops meaning anything — everything is a cold re-solve. When the queue is badly overdue the due panel offers **Rebase overdue reviews**: each drops to rung 1 and is spread 2/day, hardest first (flagged struggles, then misidentified patterns, then the rest). Solve dates and struggle counts are kept.

## Choosing what to solve next

**Group: Coverage — breadth-first** orders pattern blocks by what's least covered, but stays inside a block until ~3 problems are done before opening the next — fluency needs consecutive reps, so it never rotates per problem.

Concept units have no calendar window. Each one is surfaced just-in-time, immediately before the first problem of the block it unlocks, and the focus card leads with it when the next block is gated shut.

## Notes

Every track task and every problem takes a note — click the ☰ icon on the row. Notes accept light Markdown: `**bold**`, `` `code` ``, `- bullets`, and bare or `[titled](https://…)` links, which become clickable. They save as you type and sync with everything else.

Once written, a note stays visible under its row, so scanning the list *is* the revision pass. Notes are also searchable — typing in `/` matches note text, which is what makes 176 rows navigable months later.

**Export notes (.md)** dumps every note grouped by pattern into a single Markdown file you can read outside the tracker.

The highest-value note on a problem isn't the resource link — it's the signal you missed: *"thought two pointers, was actually binary search on the answer; the tell was 'minimise the maximum'."* Links you can re-find. That sentence you can't.

## Syncing across devices

Progress is kept in the browser's `localStorage`, so by default each device tracks separately.

To sync, click **☁** in the top right. You paste a GitHub token once per device, and progress is stored in a **private Gist** on your own account:

1. [Generate a fine-grained token](https://github.com/settings/tokens?type=beta)
2. Under **Account permissions**, set **Gists** to **Read and write**. Nothing else is needed.
3. Paste it into the sync panel and hit **Connect**.

The first device to connect creates the gist. Any device that connects afterwards merges its progress in, then keeps in sync — newest change wins. Two devices edited offline at the same time will resolve to whichever synced last.

**No token is ever stored in this repo.** It lives only in the local storage of the browser you pasted it into. Hit **Disconnect this device** to remove it.

## Backups

**Export progress** writes a JSON file; **Import progress** restores one. Worth doing occasionally — clearing site data wipes local progress, and the gist is a single point of failure if you delete it.
