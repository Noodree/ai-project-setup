# Heuristic evaluation: Concept B Administrator sketch (admin.html)

Date 2026-11-23. Nielsen's 10 plus cognitive walkthrough, desktop 1440x900, all four states. Severity 0 to 4 (4 = blocks the task).

## Verdict

Revise, lightly. The core loop is fast and honest: one input, one click, ranges with sources, per-task removal that visibly re-prices the budget. The usability risk is not the evidence model, it is what happens around it: the result lands off-screen, Conflicting hands the lead a number no past project supports, and a few edits silently wipe or strand budget values. Most fixes need no new visible text.

## Walkthrough results

| Task | Result | Note |
|---|---|---|
| 1 Describe, Estimate, save (Strong) | Friction | Works in 2 actions, but the result sits at y=1164 (fold is 900) and the "Understood... Looking at 38 projects" line clears when done. Only sparkle fields change above the fold. |
| 2 Conflicting: upper vs low, why disagree | Friction | Banner says projects disagree but not why. The answer (3 full builds 356-480 h vs 2 refreshes 120-142 h) lives only in the References panel. Upper/low range totals (488 h / 120 h) are sums of per-task extremes. |
| 3 Check one task, drop a project, notice "Scope change" | Pass | "N references" opens chips; x strikes the chip, budget re-prices (130 to 140 h), "3 of 5" becomes "3 of 4", re-add via the same chip. Scope change shows in chips and panel. Gap: chips lack kind of work. |
| 4 Thin and 1 reference | Friction | Honest ("Only 1 project matches", single value, no range). But unticking the last project removes the banner, wipes every budget and leaves no path back except re-ticking in the panel. |
| 5 None: start from a past project | Friction | Link opens a panel with only a dropdown of names. No hours, kind or year to choose by. Result says "Only 1 project matches", odd for a project the lead picked. |
| 6 Task vs Person rate, assign teammate | Pass with friction | Rate column moves to the assign list ($/h per person), nice. Avatar does not look clickable, shows initials only. |

## Heuristic table

| # | Heuristic | Verdict | Key finding |
|---|---|---|---|
| H1 | Visibility of status | Warn | Estimate result off-screen; no stale signal after editing the description |
| H2 | Real-world match | Pass | "Over by", "References", "Low confidence" read naturally |
| H3 | User control | Warn | Cancel discards all, no confirm; task x has no undo; re-running Estimate resets exclusions |
| H4 | Consistency | Warn | Two drawers and a panel remove references in different ways; "matches" wording |
| H5 | Error prevention | Warn | Re-added task is blank; Conflicting default sits in a gap |
| H6 | Recognition over recall | Warn | Add-a-project dropdown is names only |
| H7 | Efficiency | Pass | "/" focus, Enter, All/None, fill from median; strong path is 2 actions |
| H8 | Minimalist | Pass | Compact; the two-banner-plus-chips depth is acceptable |
| H9 | Error recovery | Warn | Zero-reference state is silent |
| H10 | Help | Pass | Evidence is the help; no extra copy needed |

## Findings by severity

**3 (major)**

1. **H1, Tasks and hours, after Estimate.** The estimate lands about 260 px below the fold and the visible status clears at completion, so the lead sees filled sparkles but not the verdict. Only a screen reader hears "Estimate ready". Fix: keep a one-line result under the Describe field (for example "5 projects, 310-414 h, strong", clickable, scrolls to the table). No new copy beyond the banner's own words.
2. **H5, Conflicting, default budget.** Mid fill is a per-task median across two clusters. Removing one build gives 249 h, a total that no past project came close to (builds 356-414, refreshes 120-142). Fix: when Conflicting, pre-select the larger cluster or leave the groups ("Use these") visible in the banner so the lead picks a cluster first; keep upper/low as secondary.
3. **H1/H6, Conflicting, why they disagree.** The cause is in the panel, behind "View references". Task 2 needs a decision the banner cannot support. Fix: move the two group cards ("3 full builds 356-480 h", "2 refreshes 120-142 h") into the banner, replacing or sitting beside Use upper/low range.
4. **H5/H3, task row.** Removing a task then re-adding via Add a task gives an empty budget and no estimate or references link, although matches exist (total silently drops 128 h). Fix: run recalc on add, so a re-added task fills from references.

**2 (moderate)**

5. **H9, Thin/Conflicting, last reference removed.** Banner disappears, all budgets clear, status only in the hidden line. Fix: keep the Thin banner ("Only 0 matches" state with Add project references), or block unticking the last project.
6. **H6, Add a past project (None, Thin).** Options show "Client: Name" only, nine unrelated projects. Fix: append kind and hours to each option ("refresh, 120 h"), as the panel already has them.
7. **H3, Cancel.** Resets the whole form, typed values included, with no confirm and no undo. Fix: Cancel returns to Back to Projects behaviour with a confirm only when the form is dirty.
8. **H3, Estimate re-run.** Run clears per-task exclusions and added projects (`excl={}`, `added=[]`). A lead who tweaked the description loses curation. Fix: keep exclusions and added projects across re-runs.
9. **H1, description edited after estimate.** Nothing marks the estimate as stale. Fix: dim the banner chip or swap the Estimate button to an active state when the text differs from the run text.
10. **H2/H5, Upper range total.** Upper range totals 488 h while the banner says "to 480 h"; low range gives 120 h, the smallest refresh. Sums of per-task extremes read as a project range but are not. Fix: label tooltips only if needed; better, drop to the two groups (see 3).

**1 (minor)**

11. **H4, wording.** "Only 1 project matches" after the lead picked it in None. Fix: use the Thin copy only for AI-matched results; for chosen projects show the tags with no status.
12. **H6, avatar button.** Reads as a static badge, initials only. Fix: show name on hover or title, add a subtle chevron on focus/hover.
13. **H4, Team vs assigned teammates.** Task avatars and the Team table are separate lists (removing Sam from Team does not change tasks). Fix: derive the avatar choices from Team.
14. **H6, chips.** Per-task chips show hours and notes, not kind (build or refresh). The lead cannot tell a refresh from a build in the drawer. Fix: add the kind as a quiet suffix or a style on the refresh chips.
15. **H1, Total vs Estimate.** Total can fall below the estimate range (230 h vs 310-414 h after a task is removed) with no signal. Fix: tint the Total or estimate when it leaves the range.

## What works well

- Per-task drawer is the strongest piece: strikethrough chip, re-priced budget, over-budget ratio updating ("3 of 4") in the same place.
- Data-quality notes ("Scope change", "Time tracked late") sit on the reference itself, in the panel and in chips, where the decision happens.
- Thin shows one value, not a fake range, for one reference.
- Banner copy is short and consistent; the tag words do their job without extra text.
- Person rate mode moves the rate to where it is used.

## Handoff

heuristic-evaluator → synthesis: "Worst problem is the result landing off-screen after Estimate (sev 3), then Conflicting giving a middle number that no past project supports while the cause of the disagreement hides in the panel; fix both by surfacing the build and refresh groups in the banner and a one-line result under Describe. Also fix the blank re-added task and the silent last-reference wipe. No new interface copy is needed for any of these. Task 3 passes, tasks 1, 2, 4 and 5 are friction, nothing blocks."
