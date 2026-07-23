# The Cookie Jar — Event Calendar

A single-file website with two clearly separated sides — **CookieRun Braverse (Official)** and **Michelin Star Cookies (Us)** — each with its own Discord link and its own calendar of events. People pick a side at the top, and only that side's Discord banner, "next up" event, and calendar show.

Events display on an actual visual month calendar, not a scrolling list: colored dots mark event days, and tapping a date opens the details below.

## How to add or change an event

1. Open `index.html` in any text editor.
2. Find `ADD YOUR EVENTS HERE` near the bottom, inside the `<script>` tag.
3. There are two sections: `official` and `ours`. Each has two lists:
   - `recurring` — things that repeat on the same weekday every week forever (e.g. Casual is always Wednesday, Competitive is always Saturday). List a pattern once and it fills in automatically on every matching date, no re-entry needed.
   - `events` — one-time things with a specific date (season launches, special community days).

**Recurring event example** (repeats every Wednesday):
```
{ weekday: 3, title: "Casual Day", type: "casual", time: "All day", desc: "Casual mode day. Happens every Wednesday." },
```
`weekday` is 0=Sun, 1=Mon, 2=Tue, 3=Wed, 4=Thu, 5=Fri, 6=Sat.

**One-time event example:**
```
{ title: "Competitive Weekend", date: "2026-08-08", time: "All day", type: "competitive", desc: "Competitive-mode weekend.", link: "" },
```

- `date` must be `"YYYY-MM-DD"` (one-time events only)
- `type` must be one of: `"competitive"`, `"casual"`, `"community"`, `"milestone"`, `"tournament"`, `"party"`, `"signup"`, `"reminder"`
- `link` can be `""`. Paste a Discord invite and the button auto-labels itself "Join Discord →"
- `status` is optional — set it to `"predicted"` for a date you're estimating. Leave it out once it's confirmed.

**To add a one-off note to a single occurrence of a recurring event** (e.g. "Casual Day, but double rewards" on one specific Wednesday): add a one-time event to `events` with the same date and the same `type` as the recurring rule — it automatically replaces the generic recurring entry for that date only, everywhere else keeps the normal pattern.

4. Save the file.

## Updating each side's Discord link

Near the top of the script, each side has a `discord` block:

```
discord: {
  url: "https://discord.gg/yourcode",
  updated: "2026-07-23",
  expiresInDays: 30
}
```

When you regenerate an invite link, just update `url` and change `updated` to today's date — the countdown badge recalculates itself.

## Seeing your changes before publishing

Just double-click `index.html` (or drag it into a browser tab). It works fully offline, exactly like the live version. Edit, save, refresh the tab — no upload needed until you're happy with it.

## Publishing / updating the live site

1. Push `index.html` to your GitHub repository (Settings → Pages turns it into a live URL — see prior setup notes, or ask again if you need the walkthrough repeated).
2. For future edits: open the repo on github.com, click `index.html`, click the pencil (✎) icon to edit right in the browser, then scroll down and click "Commit changes." The live site updates automatically within about a minute.
3. For bigger edits, press `.` on the repo page to open a full code editor (github.dev) in your browser instead of the small inline box.

## Sign-up notice

The Official side has `signupHeadsUp: 7` set near the top of its config. This shows one small dashed notice card (not repeated on every date — that got cluttered fast with a weekly pattern) reminding visitors that sign-ups tend to open a set number of days ahead and to keep checking Discord. Change the number, edit the wording in `renderSignupNotice()`, or delete the `signupHeadsUp` line to turn it off for a side.

## Look and feel

The two sides now have genuinely different visual identities, not just a different accent color:

- **CookieRun Braverse (Official)** — a scrapbook / schedule-board look: kraft paper texture, a small original cookie mascot doodle (not any official artwork), and calendar days that show colored marker-style labels (Casual, Competitive, etc.) right in the cell, similar to how the official schedule graphics look.
- **Michelin Star Cookies (Us)** — a dark, elegant "boutique award" look with gold star accents, playing on the name. Calendar days with something happening just get a small gold star.

Switching sides at the top swaps the whole background, fonts, and card styling automatically — nothing to configure.

## Note on the schedule

Casual (Wednesdays) and Competitive (Saturdays) now repeat automatically forever via the `recurring` list — you don't need to add them week by week. Themed events have been removed since they're not continuing. Season 3's start and the Free Learn to Play day remain as one-time entries since those are specific dates, not weekly patterns.
