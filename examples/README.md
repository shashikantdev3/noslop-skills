# Examples

Real runs, not mockups. Each "after" was produced by Claude Opus 5.5 following one skill, run as a subagent in Claude Code on 28 November 2026, and is shown unedited. The "before" admin page was written by hand to pack in common AI-slop patterns. All data is invented.

| Skill | Before | After |
| --- | --- | --- |
| [enterprise-ui](enterprise-ui/) | A vibecoded admin users page: purple gradients, glass cards, emoji, made-up KPIs, lorem ipsum ([before.html](enterprise-ui/before.html)) | A dense, accessible users table with filters in the URL, every state, safe bulk actions and 60 seeded users ([after.html](enterprise-ui/after.html), [notes](enterprise-ui/after-notes.md)) |
| [wellasked](wellasked/) | "i need a prompt for codex ... export to csv ... fast and secure and handle big data ... make it production ready" | 2 questions with recommended defaults, then a gated, testable Codex prompt with numbers in its "Done when" |
| [prompt-review](prompt-review/) | A support-bot system prompt that says "NEVER say you don't know" and refunds any unhappy customer | Not ready: 4 blockers, 4 majors, 2 minors, then a revised prompt with every change marked |

To try the pages, download them and open them in a browser. On after.html, add `?state=empty`, `?state=loading`, `?state=error` or `?state=noaccess` to the address to see each state.
