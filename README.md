# The Cookie Jar — Event Calendar

A single-file website that lists upcoming Cookie Run community events (tournaments, parties, sign-up windows, reminders). No database, no login — you edit one list of events directly in the file.

## How to add or change an event

1. Open `index.html` in any text editor (Notepad, TextEdit, VS Code, etc).
2. Find the section that says `ADD YOUR EVENTS HERE` — it's near the bottom, inside the `<script>` tag.
3. Copy one existing event block, like this:

```
{
  title: "Webcam Tournament — Round 1",
  date: "2026-08-15",
  time: "3:00 PM EST",
  type: "tournament",
  desc: "First round matches stream live. Bring your best build.",
  link: ""
},
```

4. Paste it anywhere inside the `EVENTS` list and change the details:
   - `date` must be `"YYYY-MM-DD"` (e.g. August 15, 2026 → `"2026-08-15"`)
   - `type` must be exactly one of: `"tournament"`, `"party"`, `"signup"`, `"reminder"`
   - `link` can be left as `""` if you don't have a URL to share
5. Save the file. That's it — the page automatically sorts events by date, highlights the soonest one at the top, and shows a "days away" countdown.

To remove an event, delete its whole `{ ... },` block.

## How to put this on the internet

You don't need to buy hosting for a site this simple. Two free, beginner-friendly options:

**Netlify Drop (easiest, no account needed to start)**
1. Go to https://app.netlify.com/drop
2. Drag the `index.html` file onto the page.
3. You'll get a live link instantly. Create a free account to keep the link permanent and to re-upload updates later.

**GitHub Pages (best if you want a stable, permanent free URL)**
1. Create a free GitHub account and a new repository.
2. Upload `index.html` to it.
3. In the repository's Settings → Pages, set the source to your main branch.
4. GitHub will give you a URL like `yourname.github.io/repo-name`.

Either way, updating the site later just means editing the events list and re-uploading the same `index.html` file.
