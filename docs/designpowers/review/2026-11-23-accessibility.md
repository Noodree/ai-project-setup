# Accessibility review: Concept B, Administrator New project (2026-11-23)

Standard: WCAG 2.2 AA plus cognitive accessibility. Method: read markup, CSS and script; ran the Conflicting state in the browser pane at 1440x900; measured contrast, target sizes and focus behaviour in the DOM. Muoto falls back, so sizes only.

## Verdict
Conditional pass. Semantics are strong (named controls, aria-pressed, aria-expanded, SR-only hours, reduced motion, forced-colors). Two blockers are about what screen reader and keyboard users get after an action, and one is the primary button contrast. All are small markup fixes with no new visible copy.

## Blockers

**B1. Most status changes are silent. WCAG 4.1.3.**
Where: `say()` writes to `#live`, which is `aria-hidden="true"`. Only `announce()` and `srsay()` reach `#srlive`. Task removal, All/None (teammates, billable), Add a task and Billable rate change all call `say()` only. Verified: after removing a task, `#srlive` still holds the old estimate text.
Fix: call `announce()` in those five handlers.

**B2. Focus is lost after removing a task. WCAG 2.4.3.**
Where: x button, `data-act="rm"`. The row vanishes and `document.activeElement` becomes BODY (verified).
Fix: after render, focus the next row's x button, else the previous row's, else the "Add a task" combobox.

**B3. The estimate announcement can be swallowed. WCAG 4.1.3.**
Where: `#srlive` sits inside `#scroll`, and `applyBusy()` sets `aria-busy="true"` on `#scroll` while estimating. Many screen readers suppress live regions inside a busy container, so "Understood..." and "Estimate ready..." may never be read.
Fix: move `#srlive` outside `#scroll` (next to `<body>` content root). Keep aria-busy on the table region only.

## Major

**M1. Estimate button contrast. WCAG 1.4.3.** `.send` white on #fa5d00 is 3.17:1 at about 15px medium. Fix: background `var(--orange-700)` #bf3b00 (about 5.2:1), hover #a83300. The busy state (#616261 on #c6c6c6, about 3.6:1) is a disabled state, so exempt.

**M2. Single-key shortcuts "/" and "R". WCAG 2.1.4.** They fire globally; "R" fires even with focus on a button and cannot be turned off. Fix: remove both, or require focus inside the Describe form. Delete the "/ to focus" kbd hint with them (less copy).

**M3. Left-out tag contrast. WCAG 1.4.3.** Confirmed: #8d8e8d on #eee is 2.83:1 (border 1.92:1). Not exempt: the tag carries content and has an active re-add button. State is not colour-only (strikethrough plus hidden ", left out"), which helps. Fix: text #616261 (about 5.0:1), border #a5a5a4. Keep strikethrough. Apply to the disabled x icon too (#8d8e8d, use #737472).

**M4. Control boundaries. WCAG 1.4.11.** Input borders are rgba(.25 to .3) = 1.7 to 1.9:1; AI-filled inputs use #ffa26c on #fff8f1 = 1.88:1; the Describe pill is 1.71:1. Inherited from Porchlight but fails here. Fix at minimum for this sketch: `--control-border` and `--border` to #8d8e8d (3.3:1); AI-filled border #bf3b00 or keep orange fill plus a 3:1 grey border.

**M5. "Use upper / Use low range" pressed state. WCAG 1.4.1 / 1.4.11.** aria-pressed is correct for AT. Visually the pressed fill is orange-100 on #fff8f1 (1.13:1) and the border #ff8036 is 2.5:1. Fix: pressed gets 2px border #bf3b00 and a leading check glyph (aria-hidden).

**M6. All / None targets. WCAG 2.5.8.** Measured 14x16 and 30x16 with 3px gap; the 24px spacing exception fails because they neighbour each other. Fix: extend the hit area as `.tbtn` does (`::after{inset:-6px -5px}`) and use 8px gap. Also text-subtle on white around them is 3.25:1; set the "/" and label colour to #616261.

## Minor

- **m1. Double state on toggles. 4.1.2.** "Hide references" plus aria-expanded (reflink and `#evbtn`) is read as "Hide references, expanded". Keep the directed text swap; drop aria-expanded on those two and add aria-controls to the drawer row.
- **m2. Combobox keyboard model: cleared.** Select-only APG pattern is correct: Down/Up/Home/End, Enter/Space, Esc (stopPropagation, so the panel stays open), typeahead, Tab commits, aria-activedescendant, aria-selected, disabled options skipped. A button with role combobox is acceptable here.
- **m3. AI marker: cleared with one nit.** The sparkle is aria-hidden; the name travels via aria-describedby ("Filled from past projects. Range 8 to 34 hours."), the correct place. Sparkle 3.17:1 meets 3:1. Shape plus fill, not colour alone. Nit: the visible meaning is a hover `title` only, so sighted keyboard and touch users get no explanation (1.4.13 is satisfied only for mouse).
- **m4. Avatar buttons.** Name is good ("Assigned teammates for X: Jordan Patel. Edit"). Initials-only, no visible cue it opens a list. Add `aria-controls` to the opened detail row.
- **m5. Column headers.** All/None buttons inside `<th>` get read into every cell's header announcement. Fix: give each `th` title span an id and point cells at it with `headers`, or move the two link buttons out of the th. The empty "Actions" column (`c-ac`) is an empty column for SR table navigation; make that th empty and `aria-hidden`.
- **m6. Tag link is invisible as a link. 1.4.1.** `.tag a.rn` has no underline until hover and the text colour is inherited. Fix: `text-decoration:underline; text-underline-offset:2px`.
- **m7. Duplicate SVG ids** (`icon-x`, `Line`, `Line_2`) repeat per tag. Strip ids and add `aria-hidden="true"` to the svg. `.p-body` is opened twice in `renderPanel()`.
- **m8. Landmarks.** `role="search"` on the Describe form is wrong (it is a command field); drop the role. No `<main>`: change `.main` to `<main>`. The decorative nav is an empty `nav` landmark; drop `<nav>` to `<div>`.
- **m9. Narrow screens.** Below 1000px the References panel overlays the page without focus containment; the form stays tabbable behind it. Add `role="dialog"` semantics and Esc/focus return (return exists), or inert the form.
- **m10. Over-budget text** is 12px, 5.95:1: passes. `.dqt` yellow-700 on orange-100 is 5.13:1: passes. Scope change notes pass (5.43:1, warning icon plus text).

## Works well
Estimating has a ghost state with `prefers-reduced-motion` handled; all inputs have real names and units ("hours" for SR, "h" visible); remove and add-back buttons carry full names; teammate and billable controls have clear labels; confidence is words, never colour alone; the strikethrough plus hidden "left out"; focus returns to Describe after estimating; focus-visible ring everywhere; 18px checkboxes pass by spacing; Esc closes the panel and returns focus.

## Handoff
accessibility-reviewer -> synthesis: Fix B1 to B3 first (announce on every change, move focus when a task is removed, take the live region out of the busy container), then Estimate button contrast and the 3:1 control borders. The left-out tag is a real fail but a one-line colour change; keep the strikethrough. Combobox and AI-marker are cleared. The overall interaction model is accessible; no layout or copy changes are needed.
