# Review synthesis: Concept B Administrator sketch (2026-11-23)

Sources: 2026-11-23-design-critic.md (verdict: polish), 2026-11-23-accessibility.md (conditional pass), 2026-11-23-heuristics.md (revise lightly). No blockers to the core journey. Reconciled with the Designpowers rules: accessibility over aesthetics, usability over style, brief over opinion, Audrée breaks ties. Her dated decisions in design-state.md win over reviewer opinion.

## A. Fix now (bugs and accessibility, no design change)
1. Announce every change to screen readers: task removal, All / None, Add a task and Billable rate are silent (`say()` writes to a hidden region). [a11y B1]
2. Move focus after removing a task to the next row's x button (now drops to the page). [a11y B2]
3. Move the live region out of the busy container so "Estimate ready" is heard. [a11y B3]
4. Upper range totals 488 h while the banner says 120 to 480 h. Make the total range and the task ranges agree. [critic 1, heuristics]
5. "Over by 2-2 h": collapse equal ends to "Over by 2 h". [critic 3]
6. A re-added task comes back blank with no estimate; recalculate it. [heuristics 4]
7. Unticking the last reference in Thin wipes every budget and the banner; keep the None state's behaviour instead. [heuristics]
8. Contrast: Estimate button 3.17:1, left-out tag 2.83:1, range button pressed state nearly invisible, All / None targets 14x16 px. [a11y M1, M3, M5, M6]
9. Remove the global "/" and "R" shortcuts and the "/ to focus" hint (not switchable off). [a11y M2]
10. Minor markup: drop `aria-expanded` where the label already swaps, duplicate SVG ids, `role="search"`, add `<main>`, remove the hidden Empty / Flagged toggles. [a11y minor, critic 12]

## B. Needs Audrée's call
1. Result below the fold. After Estimate, the banner sits 260 to 600 px below the fold and nothing visible says it is done. Both critic and heuristics flag it. Option: one clickable line under Describe, e.g. "356 h from 5 projects", which jumps to the table. Adds one line of copy; keeps the no-scroll rule.
2. Conflicting default. The fill is a per-task median across two different kinds of work, which can give a total no past project resembles. Heuristics wants the "3 full builds / 2 refreshes" groups back in the banner. You replaced those with Use upper / low range, so this reverses your decision unless you want both.
3. Confidence at field level. Low-confidence fills look the same as Strong ones in the table. Option: a lighter field treatment in Low confidence states, no new words.
4. Conflicting and Thin share one tag and card style though they need different actions.
5. Control borders are about 1.8:1 (Porchlight's value). Darkening to 3:1 meets WCAG 1.4.11 but departs from the design system.
6. Cancel discards everything with no confirm.

## C. Design debt (bank, not now)
Total range text is small and grey; panel opening reflows the table; overrun style differs between row and drawer; Strong next to a red overrun; "Nobody" has no way back in the cell; avatar does not look clickable; teammates and Team are separate lists; Add a past project list lacks kind and hours; re-running Estimate resets exclusions; editing the description after an estimate shows no stale signal; References panel has no focus containment on narrow screens.

## Handoff
synthesis → design-builder: apply A as one pass once Audrée confirms; B items only as she decides them.
