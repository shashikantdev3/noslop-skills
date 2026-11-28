# enterprise-ui example: an admin users page

The request: "build an admin page to manage users, make it look professional, not like AI made it. Here is what we have now: before.html"

[before.html](before.html) was written by hand to show common AI-slop patterns. [after.html](after.html) was produced by Claude Opus 5.5 following [skills/enterprise-ui/SKILL.md](../../skills/enterprise-ui/SKILL.md) in Build mode, and is shown unedited. Its delivery notes, with assumptions and what was and was not checked, are in [after-notes.md](after-notes.md).

| Before | After |
| --- | --- |
| ![The vibecoded page: a purple-to-pink gradient hero saying "Welcome back, Admin!", four glowing KPI tiles with made-up numbers, and emoji avatar cards with lorem ipsum](before.png) | ![The rebuilt page: a plain app shell with a users table of name, email, role, status badges, last active and date added, with search and role and status filters](after.png) |

Both screenshots are 1440 by 900 px.

## Try it

Download both files and open them in a browser. after.html loads nothing from the network. Add one of these to the address to see each state: `?state=empty`, `?state=loading`, `?state=error`, `?state=noaccess`. Search for something that does not exist to see the no-results state.
