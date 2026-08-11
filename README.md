<div align="center">

# Club Manager

### A fan tracker for Umamusume clubs.

It reads your club's numbers from [uma.moe](https://uma.moe) and posts a clean daily
fan leaderboard to Discord — automatically, every day, with no spreadsheets and
nothing to keep open.

Part of the **Icarus Suite**

[![Download](https://img.shields.io/badge/⬇_Download-latest%20release-4ade80?style=for-the-badge)](https://github.com/Remezzo/Umamusume-Fan-Tracker/releases/latest)
[![Version](https://img.shields.io/badge/version-1.0.0-ededed?style=for-the-badge)](https://github.com/Remezzo/Umamusume-Fan-Tracker/releases/latest)
[![License](https://img.shields.io/badge/license-proprietary-9a9a9a?style=for-the-badge)](LICENSE)
[![Discord](https://img.shields.io/badge/Discord-join-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/wpbd3hTBDc)

<br>

<img src="docs/promo/sample-board.png" alt="A Club Manager daily leaderboard posted to Discord" width="840">

</div>

---

## What it does

Club Manager is a desktop app for people who run Umamusume clubs. You add your
club, set the daily fan quota you expect from each member, and it takes over:
every day it pulls the real figures from uma.moe, works out who is ahead and who
is behind, renders the leaderboard above, and posts it to your Discord.

You manage everything from a small dashboard that opens in your browser. It runs
on your own PC — your uma.moe key and your webhooks never leave it — and once
it's set up you don't have to touch it again.

The rest of this page walks through everything it can do.

---

## Reading the board

The daily image is the heart of it. Each row is one member, and every column
answers a specific question at a glance:

- **Today's total** — their all-time career fan count.
- **Today's gain** — how many fans they added on the latest completed day.
- **Carry over** — the one that matters, and the only coloured column: how far
  ahead of (or behind) their quota they are for the month. **Green** means a
  full day's cushion, **amber** means positive but thin, **red** means behind.
  One look down this column tells you exactly who to nudge.
- **Monthly average** and **Monthly total** — their pace and their running
  total for the month.
- **Projected** — where they finish the month *if nothing changes*.

Members are ranked by carry-over, so the people pulling their weight sit at the
top and anyone slipping sinks to the bottom where you'll notice. Names in
Japanese, Korean and Chinese render correctly. The header carries the club's
rank and tier; the footer flags how many members are below target.

> **Want a different bar than quota?** Highlight thresholds let you colour any
> column against a number *you* choose — say, turn "today's gain" green for
> anyone over 5M — on top of the quota colouring.

---

## Catch what's happening in your club

**Month-end projection.** Carry-over tells you where a member stands *today*.
The projection tells you where they'll *end up* at their current pace — so you
can catch a member who'll miss quota on day 6, with three weeks left to turn it
around, instead of discovering it on the 31st. Members who joined mid-month are
measured only over the days they can still be counted for, so joining late never
looks like failing.

**Roster alerts.** Every run tells you who **joined**, who **left**, and who
**changed their name** since last time — right on the board and in the log. No
more scrolling the member list wondering who vanished. (A departure is only
announced once two runs agree, so a member who simply missed a sync is never
wrongly reported gone.)

**Milestones.** When a member — or the whole club combined — crosses a round
lifetime number like 10M, 100M or 1B, Club Manager calls it out. A little
recognition for the people carrying your rank.

---

## The long view

**Weekly summaries.** A separate post covering the last seven days: each
member's week total, their best single day, and how the week sat against quota.

**Month in review.** When a month closes, Club Manager posts the final
standings — who made quota, the club total, every day charted — and files it in
a local archive that keeps growing long after uma.moe stops serving it. Your
club's history becomes *yours*.

**Look back at any day.** The Leaderboard page can rebuild the board for any
past day of this month or the three months before it, exactly as it stood.
Great for settling "what were we on last Tuesday?" It's read-only and saved
nowhere, so browsing history never disturbs today's board.

---

## Size up the competition

**Trends — your club vs any other.** Put your club next to a rival and see
where the real difference is: monthly rank, tier, daily pace, pace *per member*,
and projected month-end, over two charts — daily gains side by side, and the
running month-total so you can see whether a gap is opening or closing. Both
rosters list underneath, and you can open any member in place.

**The tier ladder.** See exactly what every tier — SS, S+, S, all the way down —
is costing *this month*, straight from uma.moe's own thresholds: the fans-per-day
you'd need to hold it, and how much harder it's being contested than last month.
Click any tier to list the clubs sitting in it right now, then click one to
instantly line it up against yours. Aiming for promotion has never been this
concrete.

---

## Dig into individual trainers

**Look anyone up** by name or UID — lifetime totals, month-by-month history,
rolling 3/7/30-day gains and rank, all in one place.

**Head to head.** Compare two trainers side by side, as a table and as a
shareable image. Figures uma.moe hasn't filled in read "not reported" rather
than being counted as a zero, so nobody looks worse than they are.

**Track the ones you care about** to keep their report a click away, and post
any trainer's report straight to Discord.

---

## Run it your way

**Networks.** Group several clubs into one network and get a single combined
board — every member from every club in one ranking — while each is still judged
against their *own* club's quota. Post it to the network's own channel.

**Post anywhere, to anyone.** Give a club, network or trainer more than one
webhook and the same board goes to every server at once. Add a role **ping** and
Club Manager wraps the ID for you so it actually notifies (a plain role name
never does — it handles that gotcha).

**Post on a schedule — three ways:**
- **Built in** — pick times for the daily, weekly and monthly posts.
- **Start with Windows** — one toggle and it launches at sign-in, minimised,
  surviving reboots.
- **Task Scheduler** — point a task at `ClubManager.exe run` if you prefer.

Or hit **Run now** any time, **Refresh** to re-pull the latest without posting,
and **Today** to jump the board back to the newest day.

---

## Yours, and easy to keep

- **Private by design.** Everything runs locally. The dashboard listens on
  `localhost` only; nothing is sent anywhere except the data requests to uma.moe
  and the boards you post to your own Discord. No account, no cloud, no
  telemetry.
- **Backup & restore.** Save your whole setup — clubs, networks, trainers,
  settings — to one file, with an option that strips the secrets so the copy is
  safe to share.
- **A readable activity log** you can export to `.txt`, `.csv` or `.json`.
- **Search everything** from one box in the header (`Ctrl`+`K`) — jump to any
  page, club, trainer, setting or help topic.
- **A full in-app Help page** explaining every feature and the handful of things
  that look like bugs but aren't.
- **Self-updating.** It tells you when a new version is out and points you
  straight to it; your config and data carry across untouched.

---

## Up and running in three minutes

1. **[Download the latest release](https://github.com/Remezzo/Umamusume-Fan-Tracker/releases/latest)**, unzip the folder anywhere, and run **`ClubManager.exe`**. The dashboard opens in your browser.
2. **Paste a uma.moe API key** — sign in at [uma.moe/settings](https://uma.moe/settings) and generate one. That's the only credential it needs.
3. **Add your club** (paste its uma.moe link), set the daily quota, drop in a Discord webhook, and hit **Post now**.

No Python, no installer, no dependencies. Set a schedule and walk away.

> **Keep the unzipped files together** — `ClubManager.exe` needs the libraries
> beside it. Run it from its folder; don't pull the exe out on its own.

---

## Verify your download

Every release ships SHA-256 checksums. From the unzipped folder in PowerShell:

```powershell
(Get-FileHash ClubManager.exe -Algorithm SHA256).Hash.ToLower()
```

Match it against `SHA256SUMS.txt`. If they agree, the file is exactly what was
published.

> **First run:** the app isn't code-signed (certificates cost money a free tool
> skips), so Windows SmartScreen shows *"Windows protected your PC"* — click
> **More info → Run anyway**. If your antivirus quarantines it, that's a known
> false positive with compiled-Python programs, not a real detection; the
> checksum above proves the file is genuine. Restore it from quarantine or add a
> folder exclusion.

---

## Requirements

Windows 10 or 11. A free uma.moe account for the API key, and a Discord webhook.
That's the whole list — everything else is bundled into the download.

## The Icarus Suite

Club Manager is one of a family of local, privacy-respecting Umamusume tools —
career automation, headless rerolling, live translation and more. The **Suite**
page inside the app links them all.

## License

Club Manager is proprietary software — © 2026 Remezzo, all rights reserved. You
may download and use the official release and read the source for reference, but
you may not reuse, modify or redistribute it. See [LICENSE](LICENSE) for the
full terms.
