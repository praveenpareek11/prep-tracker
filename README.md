# Prep Tracker

A single-file interview prep tracker: a 16-week schedule ribbon, eight prep tracks, and 176 DSA problems with per-topic progress.

**Live:** https://praveenpareek11.github.io/prep-tracker/

Everything is one `index.html` — no build step, no dependencies, no backend. Open the file locally or use the live URL.

## Using it

- **Prep Tracks** — the eight non-DSA tracks, each with its window on the calendar and a progress bar showing actual vs. expected-by-today.
- **DSA Problems** — 176 problems grouped by topic, filterable by topic / difficulty / status.
- **Focus now** — the current week's active tracks and your next few unchecked tasks.
- **Search** (`/`) — filters tasks and problems together, with match highlighting.
- Keyboard: `/` search, `1` tracks, `2` DSA, `Esc` clear.

A DSA checkbox means *re-implemented cold from a blank file* — not "read and understood."

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
