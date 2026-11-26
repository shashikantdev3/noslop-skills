---
name: enterprise-ui
description: "Build, brief or review enterprise-grade UI: admin consoles, data tables, forms, dashboards, record pages, settings and internal tools that people use all day. Use when asked to build or improve a business app screen, to write a UI prompt or spec for a coding agent or design tool, or to check a UI for AI slop. Produces consistent, dense, accessible screens with every state covered, reuses the design system already in the project, and follows a never-list for generic AI looks (gradients, glass effects, emoji icons, hero banners, fake data). Not for marketing or landing pages."
---

# enterprise-ui

People use enterprise software for hours a day to get work done. Good enterprise UI is quiet, predictable and fast. The data and the task are the main thing on the screen; the interface steps back.

This is not a landing page. Do not try to make it memorable. Make it consistent, legible, accessible and complete. For a branded marketing page, use a design-led skill instead.

## Modes
Pick the mode from the request:
- **Build:** you write the UI code. Follow the workflow, then run the review before you deliver.
- **Brief:** someone wants a prompt or spec for another agent or design tool. Fill the brief template at the end.
- **Review:** someone shares existing UI (code, a screenshot or a URL). Run the review checklist and report findings by severity, each with a specific fix. Do not rewrite unless asked.

## Principles
1. **The task leads.** Every screen serves 1 to 3 named tasks. Layout follows those tasks, not decoration.
2. **Use what exists.** The project's design system, tokens and components win over anything new. Never add a second component library or icon set.
3. **Consistency over novelty.** The same thing looks and behaves the same everywhere.
4. **Density with control.** Show useful data above the fold. Offer a compact density for data-heavy screens.
5. **Every state is designed:** empty, no results, loading, partial, error, no permission, stale data, success. This is the one list of states; the checklist and the brief template refer to it.
6. **Accessible by default:** WCAG 2.2 AA, full keyboard use, visible focus, real labels, never color alone.
7. **Real data shapes.** Long names, big numbers, zero, null, 10,000 rows. Never lorem ipsum, and never invented numbers presented as real.
8. **Safe actions.** Destructive and bulk actions name what they affect and wait for confirmation. Offer undo where you can.
9. **Plain words.** Labels users already know; errors that say what happened and how to fix it.
10. **Check the docs.** Take component names and props from the library's current docs, not from memory.

## Workflow

### Step 1: Understand
- Who uses it, in which role, and how often.
- The 1 to 3 tasks this screen must make easy, written as verbs ("find an invoice", "approve a refund").
- The screen type: list or table, record detail, form or wizard, dashboard, settings, queue or inbox.
- Data volume: how many rows, fields and updates.
- Platforms: desktop only (design for 1280 px wide and up) or responsive down to 360 px.

### Step 2: Find what exists
- Look before you choose: the package manifest, theme or token files, the Tailwind config, the existing screens and components.
- Match what you find: its components, spacing, colors, icons and patterns.
- Only if nothing exists, recommend one option with a one-line reason:
  - React with Tailwind: shadcn/ui, with TanStack Table for data-heavy tables.
  - Data-heavy admin apps: Ant Design, or MUI with its data grid.
  - Apps that sit beside Microsoft 365: Fluent UI.
  - Large, dense, regulated products: IBM Carbon.
  - Angular: Angular Material. Vue: Vuetify or PrimeVue.
- Read the chosen library's current docs for component names and props. Versions change; do not guess.

### Step 3: Ask only what matters
Ask at most 3 questions, in one message, each with 2 to 4 options and the recommended default first. Say that "go" accepts every default. Ask only when the answer changes the result, has no safe default, and is not in the project. Typical ones:
- No design system in the project, and the stack allows several.
- Desktop only, or mobile too.
- Dark mode required, or not now.

Otherwise proceed and list your assumptions at the end.

### Step 4: Specify the screen
Before writing code, write a short spec. In Brief mode, the spec feeds the brief template, and the filled template is the output.
- The layout pattern and regions.
- The components, from the chosen library.
- The data: fields, formats, sample data.
- The actions, with which one is primary.
- Every state.
- Accessibility and responsive behavior.

Use the patterns below.

### Step 5: Build or brief
- **Build:** follow the spec, the foundations and the never-list. Use realistic sample data generated with a fixed seed. Label it as sample data on screen, and never ship it to production.
- **Brief:** fill the template at the end.

### Step 6: Review
Run the review checklist. If you can, look at the result:
- take screenshots at 1280 and 1440 px wide, and at 375 px if it is responsive;
- do one pass with only the keyboard.

Fix the blockers before you deliver.

### Step 7: Deliver
1. The code or the brief.
2. The assumptions you made, at most 5 bullets.
3. What you checked, and what you could not check.

## Foundations
Use these when the project has no design system. When it has one, its values win.

- **Layout.**
  - An app shell: a top bar, a collapsible left nav and a content area.
  - Tables use the full width. Forms stay within about 720 px.
  - Align content to the left.
- **Spacing.** A 4 px base, using 4, 8, 12, 16, 24, 32 and 48.
- **Borders and shadows.** 1 px neutral borders separate regions. Shadows appear only on overlays: menus, popovers, dialogs.
- **Corner radius.** 4 to 6 px on controls, at most 8 px on panels.
- **Type.**
  - One sans-serif family: the system UI stack, or a proven UI face such as Inter, IBM Plex Sans or Segoe UI.
  - 14 px body for dense apps, 16 px for public forms. Line height 1.4 to 1.5.
  - Tabular figures for numbers in tables.
  - Sentence case for labels, buttons and headings.
- **Color.**
  - A neutral grey ramp, plus one accent for primary actions, selection and focus.
  - Four status colors (success, warning, danger, info), each with a shade that is safe for text.
  - Contrast of at least 4.5:1 for text and 3:1 for controls and focus rings.
  - Status always pairs color with an icon or text.
  - Dark mode only through tokens.
- **Icons.** One set (Lucide, Material Symbols, Fluent or Carbon) at 16 or 20 px. Icon-only buttons need an accessible name and a tooltip.
- **Targets.** At least 24 by 24 px for anything clickable.
- **Motion.** 100 to 200 ms, and only to show a change of state. Respect reduced-motion settings. Nothing decorative.

## Screen patterns

### Data tables
- **Alignment.** Text aligns left. Numbers align right, with tabular figures and the unit in the header.
- **Structure.** A sticky header. The first column identifies the row and links to its detail.
- **Finding rows.** Search, filters and sort. Keep filter state in the URL so a view can be shared. Offer column show and hide past 6 columns.
- **Volume.** Paginate or virtualize past about 200 rows.
- **Selection and bulk actions.** A bulk action bar shows the count. Make "all on this page" and "all results" two explicit choices.
- **Long values.** Truncate with a tooltip. Never wrap IDs.
- **Times.** Show times in the user's time zone, with the full date and time on hover.
- **States.** Each is different:
  - no data yet: explain it and offer the primary action;
  - no results: offer to clear the filters;
  - error: offer a retry;
  - loading: skeleton rows in the real layout.

### Forms
- **Layout.** One column, with labels above the fields and help text under them.
- **Required fields.** Mark either required or optional fields, consistently.
- **Validation.** Validate on blur and on submit.
  - Show errors inline.
  - On a long form, also show a summary at the top and move focus to the first error.
  - Keep what the user typed after an error.
- **Long forms.** Use sections with headings. Very long forms become steps, with progress and save as draft.
- **Buttons.** One primary button per form, named with a verb ("Create invoice", not "Submit").
- **Disabled submit.** Never disable submit without saying why.

### Dashboards
- **Purpose.** Each panel answers a named question for a named role.
- **KPIs.** 3 to 6 at most. Each has a time range and a comparison (against the last period or a target).
- **Charts.**
  - Label the axes and units.
  - No 3D.
  - No pie chart with more than 5 slices.
  - Every chart drills down to a table.
- **Freshness.** Show when the data was last updated.

### Record detail
- **Header.** The name, the status and the main actions.
- **Body.** Sections or tabs for the rest.
- **History.** An activity log that shows who did what, and when.

### Settings and admin
- **Layout.** Group settings into sections.
- **Saving.** Use an explicit save, or autosave with a visible confirmation, never a mix.
- **Dangerous actions.** Put them at the bottom, separated from the rest.
- **Permissions.** Show what a user cannot do as disabled, with the reason, unless hiding it is safer.

## Actions and feedback
- **Button hierarchy.** One primary action per view. Everything else is secondary or tertiary.
- **Confirmations.**
  - The dialog names the object and the count.
  - The confirm button uses the verb: "Delete 3 invoices", never "OK".
  - For high-impact actions, the user types the name to confirm.
- **Feedback.** Each kind goes in one place:
  - field problems inline;
  - page problems in a banner;
  - background success in a toast, with undo where possible.
- **Errors** stay on screen until the user dismisses them.
- **Loading.**
  - First load uses skeletons.
  - A submit button shows a spinner and blocks a double submit.
  - Jobs longer than about 10 seconds show progress.

## Writing in the UI
- **Style.** Sentence case. Buttons start with verbs. Use the same word for the same thing everywhere.
- **Errors** say what happened, why if it helps, and what to do next.
- **Voice.**
  - No marketing words ("unlock", "supercharge", "seamless", "effortless").
  - No exclamation marks, no emoji.
- **Locale.** Format numbers, currency and dates for the user's locale.
- **Translation.** Leave about 30% room for longer text, and never put text in images.

## Never
- Gradients on backgrounds, buttons or text, purple-to-blue above all.
- Glass effects, neon glows, blurred blobs, 3D illustrations, decorative noise.
- Hero banners or marketing headers inside an app.
- Emoji as icons, or in headings and labels.
- Every block in an identical rounded card with the same soft shadow; a radius of 16 px or more on controls.
- Centered body text, or centered forms, on work screens.
- Lorem ipsum, "John Doe", KPI tiles with made-up numbers and rising arrows.
- Disabled buttons with no reason; icon-only buttons with no accessible name.
- Color as the only signal for status.
- Two component libraries or two icon sets in one app.
- Load animations, parallax, bouncing hover effects.
- Invented component props or library APIs.

## Review checklist
Report each finding with a severity, where it is, and the fix:
- **Blocker:** an accessibility failure, a risk of data loss, a missing state, or an irreversible action without confirmation.
- **Major:** an inconsistency with the design system, a confusing hierarchy, or an unclear error.
- **Minor:** spacing, alignment or wording.

Check each of these:
- Can each named task be done without guessing, and in how many steps?
- Does every view have each state from Principle 5 that applies to it?
- Does everything work with only the keyboard, with focus visible and in a logical order?
- Do text and controls meet the contrast ratios? Is status shown without relying on color?
- Do numbers align right with units, and are dates in the user's locale and time zone?
- Does every destructive or bulk action confirm with the object and the count?
- Do any never-list items appear?
- Are all components, spacing, colors and icons from one system?
- Does it hold up with long names, zero, null and 10,000 rows?

## Brief template (Brief mode)
```text
Build <screen name> for <role>, who uses it to <task 1>, <task 2>, <task 3>.
Stack: <framework>, <component library and version, from the project>. Read its current docs; do not guess props.
Layout: <pattern and regions>.
Data: <fields with formats>. Use realistic sample data generated with a fixed seed; never lorem ipsum.
Actions: primary <action>; secondary <actions>. Destructive and bulk actions confirm with the object and count.
States: each that applies of empty, no results, loading (skeleton), partial, error (retry), no permission, stale data, success.
Accessibility: WCAG 2.2 AA, full keyboard use, visible focus, labels on every control, status never by color alone.
Responsive: <desktop from 1280 px | down to 360 px>.
Never: gradients, glass effects, emoji icons, hero banners, identical card grids, a second component library.
Done when: each task works end to end with the keyboard, every state can be shown, and the review checklist has no blockers.
```

## Example
Request: "build an admin page to manage users, make it look professional, not like AI made it"

1. **Mode:** Build. **Screen:** a table with a detail drawer. **Tasks:** find a user, change a role, deactivate users.
2. **What exists:** the project uses React, Tailwind and shadcn/ui, so use its table, sheet, dialog and badge components. Ask no questions.
3. **"Professional, not like AI made it" becomes:**
   - columns for name, email, role, status and last active, with sort, search, and filters for role and status kept in the URL;
   - status as a badge with text and color;
   - row selection with a bulk bar: "Deactivate 4 users" opens a dialog that names the count;
   - states for no users yet, no results, a failed load with retry, a skeleton while loading, and a no-permission page for non-admins;
   - 60 seeded users, including long names, users who never signed in, and a deactivated admin;
   - no gradients, no emoji, no hero header, one accent color.
4. **Deliver** the code, then the assumptions (for example, that only admins can see this page), and what was checked: a keyboard pass and screenshots at 1280 and 1440 px.
