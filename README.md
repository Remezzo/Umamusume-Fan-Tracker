Club Manager
============
Part of the Icarus Suite.

Tracks Umamusume clubs and trainers from uma.moe and posts matte-black
leaderboard images to Discord. Managed from a web UI in your browser.


GETTING STARTED
---------------
  1. Double-click  setup.bat        (installs Python packages; once only)
  2. Double-click  start.bat        (opens Club Manager in your browser)
  3. Sign in at https://uma.moe, open https://uma.moe/settings, generate an
     API key, and paste it into the box on the Dashboard.
  4. Go to "Clubs" and add a club:
       Club ID   the number in the club's uma.moe URL
                 https://uma.moe/circles/717148109  ->  717148109
       Webhook   Discord: Server Settings > Integrations > Webhooks >
                 New Webhook > Copy Webhook URL
       Quota     daily fan target per member
  5. Click "Preview" to check it, then "Post now" to send it.

uma.moe issues API keys for integrations like this, so nothing has to be
clicked and it runs unattended. Treat the key like a password: it lives in
config.json alongside your webhooks.


WHAT IT DOES
------------
  Daily board      One image per club: every member ranked by Carry Over,
                   with their lifetime total, today's gain, monthly average
                   and monthly total. Members counted for only part of the
                   month are marked (e.g. "· 3d") because their target is
                   smaller.

  Projection       Where each member ends the month at the rate they are
                   going, coloured against the whole month's quota — so it
                   warns while there is still time to do something. Someone
                   who joined mid-month is measured over the days they will
                   actually have, not the whole month. Settings > Discord &
                   image turns the column off.

  Roster alerts    Who joined, who left, and who changed their name since the
                   last run, on the board and in the log. A departure is only
                   announced once two runs agree, so a member who simply
                   missed a day's sync is never reported as having left.

  Milestones       A one-off note when a trainer passes a round lifetime
                   figure (10M, 100M, 1B…) or the club passes one between
                   everyone. Marks already passed the first time a club is
                   seen are recorded quietly rather than announced.

  Weekly summary   The last seven days: each member's week total, their best
                   single day, and how the week sat against quota, over a
                   chart of the club's gain per day.

  Month in review  When a month closes, its final standings — who made quota,
                   the club total, and every day charted. Filed in a local
                   archive that keeps growing after uma.moe has moved on, and
                   readable again from the Leaderboard page.

  Networks         Group clubs together. A network gets a combined board —
                   every member from every club in one ranking, each still
                   measured against their own club's quota — and can post it
                   to its own webhook.

  Trainers         Look anyone up by UID, profile link or name, for lifetime
                   totals, month-by-month history, rolling 3/7/30-day gains
                   and rank. Track the ones you care about to keep a report a
                   click away, and post reports to Discord.

  Head to head     Two trainers side by side, as a table and as an image.
                   Figures uma.moe has not filled in read "not reported"
                   rather than counting as a loss.

  Trends           Your club against any other: rank, tier, daily pace, pace
                   per member, and where each ends the month. Charts for the
                   daily figures and the running total, both rosters side by
                   side, and any member openable in place.

  Tier ladder      What each tier costs this month, from uma.moe's published
                   thresholds — fans per day, the same divided by your club
                   size, and how much harder the tier is being contested than
                   it was last month. Cutoffs climb all month, so the per-day
                   rate is the figure to steer by.

  Help &amp; search   A Help page covering every feature, what each column
                   means, and the things that look like bugs but are not.
                   The search box in the header reaches pages, clubs,
                   trainers, settings and help topics — Ctrl+K or /.

  History          The Leaderboard page can rebuild any past day of this
                   month or the three before it. Looking back is read straight
                   from uma.moe and saved nowhere, so it never disturbs what
                   today's board says.

  Several channels A club, network or trainer can hold more than one webhook.
                   "Add another webhook" in its editor adds a second (up to
                   eight) and the same post goes to all of them, so one club
                   can report into two servers at once. One dead webhook does
                   not stop the others.


POSTING ON A SCHEDULE
---------------------
Three ways; pick one.

  Built in     Settings > "Post automatically", set a time. Weekly summaries
               and the month in review have their own days and times.
               start.bat must be left running.

  With Windows Settings > This app > "Start with Windows". Club Manager then
               starts at sign-in, minimised and without opening a browser, so
               the built-in schedule survives a reboot. It writes one entry
               under HKEY_CURRENT_USER and nothing else; turning it off
               removes it again.

  Task         Task Scheduler > Create Basic Task > Daily > Start a program >
  Scheduler    point it at run.bat. Nothing needs to stay open.
               (run.bat exits with code 2 if the API key is missing.)

A day is published once it is complete, so the newest data is normally
yesterday's. If it is not up yet, the run waits and tries again — see
Settings > Retries.


KEEPING A COPY
--------------
Settings > "Back up your setup" writes one JSON file holding every club,
network, tracked trainer and setting. An update never touches config.json,
but nothing else protects it from a lost drive.

  Download a backup    everything, including the API key and webhook URLs.
                       Treat that file like a password.
  Without secrets      the same, with the key and webhooks removed. Safe to
                       share or keep in a repository; restoring it leaves the
                       key and webhooks you already have in place.

Restoring copies your current config.json into data\backups\config first, so
restoring the wrong file is undoable.


UPDATING
--------
Settings > Updates checks https://github.com/Remezzo/Umamusume-Fan-Tracker for
a newer release. Installing replaces the program files and leaves config.json,
catalogue.json, data\ and credentials\ alone; the files being replaced are
copied into data\backups first. Club Manager can restart itself afterwards —
the page reconnects on its own.


WHAT IS IN THIS FOLDER
----------------------
  start.bat              opens the web UI            <- the usual way in
  setup.bat              installs dependencies       <- run once
  run.bat                one-shot run, for Task Scheduler
  uma2_fan_tracker.py    command-line entry point
  fantracker\            the program
  webui\                 the web interface (help.js holds the Help content)
  config.json            your clubs, networks, trainers and settings
  config.example.json    reference copy
  catalogue.json         optional: overrides the Suite page's entries
  data\                  run state, snapshots, rendered images, activity log
                         (created on first run; safe to delete to start over)
  data\months\           finished months, one file per club per month
  data\backups\          the program files an update replaced, and copies of
                         config.json taken before a restore


REQUIREMENTS
------------
  - Python 3.10 or newer
  - Browser


NOTES
-----
  - Keep config.json private: it holds your Discord webhooks and API key.
  - The web UI listens on 127.0.0.1 only. Nothing on your network reaches it.
  - The whole folder can be moved or copied anywhere; paths are relative.
  - Japanese and Korean member names render correctly in the images.
  - The activity log exports as .txt, .csv or .json — never an archive.
