# Design critic review: Concept B inline, Administrator (2026-11-23)

Checked at 1440x900 against design-state.md (P1 to P5, H1 to H4, 2026-11-23 decisions override the copy deck). Brief and strategy not opened; relied on design-state.md.

## Verdict: polish

The sketch delivers the brief's core: one entry point, one click to a filled budget, every number a click from its past projects (P1, P5). The 2026-11-23 table is clean and reads as Harvest. The banner copy is short and honest. What is left is craft and truthfulness at the edges: a few numbers that contradict each other, a degenerate range, and a confidence signal that stops at the banner. Fix the major items and it is demo-ready.

## What works
- The Conflicting banner is the strongest moment: "5 past projects disagree: 120 to 480 h" plus "Use upper range / Use low range" gives the lead a decision, not a verdict (P3).
- Per-task "N references" opens the evidence at the row where it matters (P2, P4). The overrun note sits beside the estimate in small red, not louder than the number.
- None state is quiet and honest: no banner, one line, one action. No fake fill.
- The 1-reference case shows tracked time, not a range, and the Left out tag keeps the card in the panel so the lead can undo (P3).
- Copy is concise throughout. Nothing needs adding.

## Blockers
None.

## Major

1. **Upper range total breaks its own ceiling.** Conflicting, "Use upper range": Total reads 488 h while the banner says 120 to 480 h and the Total row says 120-480 h. The row maxima sum to more than the project maximum. Hurts P1 (a number that does not trace) and the demo's credibility on camera. Fix: derive the total range from the per-task ranges, or let the banner say the range of the sum; at least make the two agree.

2. **Confidence stops at the banner.** Strong, Conflicting, Thin and 1-reference all fill budget fields with the identical orange field and sparkle. A 9 h budget from 2 projects looks as sure as a 24 h one from 5. The lead has to remember the banner while editing 7 rows. Hurts P2 and H1 (honest vs flagged number). Fix: in Low confidence states, mark only the Estimate cell or field mark differently (for example a hollow marker or a muted dashed border), no new words.

3. **"Over by 2-2 h in 1 of 2" and "Over by 2-2 h in 2 of 2" (Thin, Development and QA).** A range with equal ends is a bug in the copy logic, and it is the most visible overrun line in Thin. Hurts P2 and polish. Fix: collapse equal ends to "Over by 2 h".

4. **The result is below the fold after Estimate.** The decision to not scroll is respected, but at 1440x900 the banner starts around 600px down; the demo's key moment (the banner, the filled column) is invisible when Estimate is pressed. Only a hidden live region announces it. Hurts P5 for sighted users and the video. Fix: keep the no-scroll rule, but add a visible cue at Describe (for example the Estimate button becoming a "5 projects" jump link) that scrolls to the banner on click.

## Minor

5. **Conflicting and Thin share the same "Low confidence" tag** and the same orange card, so the two failure modes (disagree vs not enough data) differ only in headline words. They need different next actions (choose a range vs add projects), and the card does not signal that. Fix: keep the tag, vary the card lead icon or tint weight; no extra copy.

6. **Summary total is the weakest line on the page.** "Total 358 h" is bold, the project range beside it is tiny grey at the far right, below the estimate column's visual weight. In Conflicting it is where the lead needs it most. Fix: match the Estimate column's type size for the total range.

7. **Panel opening reflows the table** (Assigned teammates wraps, "Discovery & strategy" wraps to two lines, columns shift). Everything the lead is looking at moves. Fix: overlay the panel, or reserve the width so columns hold.

8. **Thin panel is mostly empty** with the "Add a past project" select as the only action after two cards. The banner button "Add project references" opens the panel but does not focus or open the add control, so the promised action takes a second step. Fix: the banner button should land focus on the select.

9. **Overrun line weight differs between rows and drawer.** The row note is small red regular; the drawer tag is bold red on pink. Same fact, two intensities. Fix: share one treatment.

10. **Strong state has one overrun (QA & launch) and no other cue,** so the banner says "Strong confidence" while a red warning sits in the table. Not wrong, but the strong state reads as slightly contradicting itself in the demo. Fix: keep, but choose demo data where the overrun is explained in the drawer's first line.

11. **Assigned teammates "None" renders plain "Nobody"** with no way back except "All". Fine for a sketch; one tap in the video could look broken. Fix: show "Assign" as a link in that cell.

12. **Hidden sketch strip toggles** (Empty, Flagged number) still exist in the DOM although H1 was removed. Remove them so a stray key press does not reveal a dead state.

## Principle check
- P1 pass (drawer and panel), except finding 1.
- P2 partial (findings 2, 3).
- P3 pass; Use upper/low range is a good move.
- P4 pass.
- P5 pass; finding 4 is the one threat to the fast path being visible.

Hypotheses: H1 is no longer testable in the sketch (agreed). H2 (compact headline is enough) is exposed by finding 2.

## Handoff for synthesis
design-critic to synthesis: Verdict polish. Fix first: the upper range total exceeding 480 h (1), the "2-2 h" overrun copy (3), the confidence signal that disappears at the field level (2) and the below-the-fold result (4). Everything else is minor and safe to bank as design debt. No copy additions are needed; every fix above is visual or logic.
