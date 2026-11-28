# after.html: delivery notes

Built in Build mode with the enterprise-ui skill. The screen is a users table with a detail drawer. Its tasks are to find a user, see their role and status, add a user, and deactivate users.

## Assumptions

- Only admins can open this page. Everyone else sees the no-permission state (`?state=noaccess`).
- There is no design system in the project, so the page uses its own small set of tokens: a grey ramp, one blue accent, four status colors, the system UI font, and one inline icon set drawn in a single stroke style.
- Deactivation can be undone. Users keep their data and can be reactivated, so a confirmation dialog plus an Undo toast is enough. Deactivating 10 or more users at once also asks for the count to be typed.
- Users who were invited but never signed in have the status "Invited" and show "Never signed in".
- Desktop only, light theme only. Changing a role and the other nav pages (Dashboard, Analytics, Settings) are out of scope.

## What I checked

- Screenshots at 1280 px and 1440 px wide. Nothing scrolls sideways, and long names and emails are cut off with an ellipsis and a tooltip.
- A keyboard-only pass. Tab order goes skip link, nav, Add user, search, filters, density, then the header checkbox, sort buttons and rows. Every stop has a visible focus ring. Space selects a row, Enter opens the drawer, and Escape closes dialogs and returns focus to where it was.
- Every state through the URL: `?state=empty`, `?state=loading`, `?state=error` (Retry works) and `?state=noaccess`. The no-results state shows up when a search such as `?q=zzqx` matches nothing.
- Search, role filter, status filter, sort direction, page, density and the open user all live in the URL and come back on reload.
- Bulk flow: the page checkbox selects the page, then "Select all 60 results" selects every result. The confirmation names the count and lists the first names. Users who are already deactivated are skipped and named as skipped. The dialog warns when every active admin would be deactivated, and Undo restores the previous status.
- Add user: errors appear inline on blur and on submit, focus moves to the first error, duplicate emails are caught, and the submit button shows a spinner and cannot be pressed twice.
- Contrast for every token pair, computed with the WCAG formula. Text pairs are 5.5:1 or higher and control borders are 3.8:1.
- The console shows no errors, and the page makes no network requests besides loading itself.
- The review checklist found no blockers.

## What I could not check

- Screen readers (NVDA, VoiceOver). I only checked roles and names in the accessibility tree.
- Browsers other than Chromium. The page uses the native `dialog` element.
- 10,000 rows. The table shows 25 rows a page and filters on the client, which is fine for 60 users but has not been measured at that size.
- Minor items left open: tooltips on cut-off cells show only on hover, but the full values are in the drawer. A toast that appears while the drawer is open sits behind the drawer's backdrop. There is no stale-data state because the demo data never refreshes.

## Main changes from before.html

- Removed the hero banner, the made-up KPI tiles, the gradients, the glass effects, the glows, the pulsing badge, the hover lift and every emoji.
- Replaced the centered card grid with a full-width table: name, email, role, status, last active and date added. It has sortable columns, a sticky header and pagination.
- Status is a badge with an icon and a word, so it never relies on color alone.
- Added search plus role and status filters, all kept in the URL.
- Replaced the instant "Delete" behind `confirm('Are you sure?')` with "Deactivate N users". It works on selected rows, opens a dialog that names the count, and offers Undo.
- Added a working Add user form with validation.
- Added a detail drawer that the first column links to.
- Designed the empty, no results, loading, error, no permission and success states.
- Replaced the six "John Doe" style users and the lorem ipsum with 60 generated users from a fixed seed. The data includes long names, users who never signed in, and a deactivated admin, and the page labels it as sample data.
- Removed the "UserHub AI" branding and the "Growth" nav item. The product is now just "Admin", with a collapsible left nav.
