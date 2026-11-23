# Concept B, Administrator: interface copy (revision 2)

**Status:** DRAFT for Audrée's review. 2026-11-12. Replaces the first deck, which assumed tentative, accept and "Evidence". Written against spec revision 3 and its follow-up changes (removable reference tags, "over by", strength tag at the right of the banner, Details next to the budget).
**All names and numbers are invented.** Untested with users.

## Rules

- As short as it can be. If a screen already shows it, no sentence.
- Calm, factual, no "I", no AI personality, no em dashes. Digits for counts, never percentages.
- One word per idea: **filled** (what the AI did), **References** (the past projects behind it), **close matches** (how well they fit), **left out / added back** (a reference taken out or put back), **your values** (what the lead typed), **saved** (the project).
- Gone from the UI: tentative, draft, accept, confirm, Suggested (as a word), evidence, comparable, "not old budgets".

## 1. Page frame

| Where | Current | Proposed | Chars | Why |
|---|---|---|---|---|
| Subtitle | Describe it, or fill in the form. | Describe it, or fill in the form. | 33 | Keep. 33 characters, says both ways in. |
| Describe, placeholder | Client and a few words, for example: Fernwood Outdoor Supply, brand website | Client and a few words: Fernwood Outdoor Supply, brand website | 62 | Drops "for example". The sample shows it. |
| Estimate button | Estimate / Estimating... | Estimate / Estimating... | 24 | Keep. Disabled controls during thinking keep their own labels. |
| Past-project link | Start from a past project | Start from a past project | 25 | Keep. |
| Thinking, line 1 | Understood: new brand website for Fernwood Outdoor Supply. Matching against 38 projects you can open... | Understood: new brand website for Fernwood Outdoor Supply. Looking at 38 projects... | 84 | Plainer verb. "you can open" is not needed for an Administrator. |
| Thinking, line 2 | Reading tracked time on the closest projects... | Reading tracked time... | 23 | "On the closest projects" is implied. |
| Save bar | Save project, Cancel, shortcut hint | Save project, Cancel | 20 | Keep. No tentative, no accept. |
| After save | Project saved. | Project saved. | 14 | Keep. |


## 2. Banner (pale orange card: tag at the right of the headline, then one sentence, then actions)

Headline up to 40 characters. Sentence up to 60.

Tag words: **Consistent, Conflicting, Few matches, No matches.** Recommendation: keep them. They describe the projects, not "evidence", so renaming to References does not break them. "No matches" appears only in the table line, because that state has no banner. Alternative if "Consistent" reads vague: "Agree" / "Disagree", but "Few matches" has no pair there.

| Where | Current | Proposed | Chars | Why |
|---|---|---|---|---|
| Consistent, headline | Filled from 5 past projects | Filled from 5 past projects | 27 | Keep. Counts the projects, says what was done. |
| Consistent, sentence | Tasks and hours below. They tracked 310 to 414 h in total. | They tracked 310 to 414 h in total. | 35 | "Tasks and hours below" points at what is already below. |
| Consistent, actions | Show references | Show references | 15 | Toggles to Hide references. Key R. |
| Conflicting, headline | 5 past projects disagree: 120 to 480 h | 5 past projects disagree: 120 to 480 h | 38 | Keep. |
| Conflicting, sentence | Nothing filled in. Pick the kind of work that fits. | Nothing filled in. Pick the kind of work that fits. | 51 | Keep. 50 characters. |
| Conflicting, actions | Use the 3 full builds, Use the 2 refreshes, Show references | Use the 3 full builds, Use the 2 refreshes, Show references | 59 | Keep. |
| Few matches, headline | Only 2 close matches | Only 2 close matches | 20 | Keep. |
| Few matches, sentence | Nothing filled in. Add a past project | Nothing filled in. Add a past project | 37 | Keep. "Add a past project" is a blue link, not a button. |
| Few matches, flagged variant (H1), headline | Filled from only 2 past projects | Filled from only 2 past projects | 32 | Keep. "Only" carries the warning, so the headline alone is not misleading. |
| Few matches, flagged variant, sentence | Weak base. Check these numbers. | Check these numbers. | 20 | "Weak base" is judgment and jargon. "Check" is the action. |
| No matches (no banner), table line | No similar projects. Start from a past project or add tasks by hand. | No matches. Start from a past project, or add tasks by hand. | 60 | Same word as the tag family ("matches"). Two exits, one sentence. |


**Recommendation on your open question (flagged):** put the fact in the headline and the instruction in the sentence, as the table shows. The headline says "only 2", so a lead who reads only the headline still sees the thinness. The sentence says what to do. No extra warning word in the headline, because "Weak" or "rough" adds length and judgment.

## 3. Fields, tags and labels

| Where | Current | Proposed | Chars | Why |
|---|---|---|---|---|
| AI-filled icon, accessible name | Suggested (hidden text and title) | Filled from past projects | 25 | The visible word is gone, so the name carries the meaning. Says what happened, not who did it. Use as the icon's `title`; the field description (below) carries the same words, so mark the icon `aria-hidden` to avoid a double announcement. |
| Filled field, description (screen reader) | Suggested, range 20 to 30 hours. | Filled from past projects. Range 20 to 30 hours. | 48 | Same facts, matches the icon name. |
| Typed field, description | Entered by you. | Entered by you. | 15 | Keep. No visible chip any more. |
| Empty field, description | No value yet. | No value yet. | 13 | Keep. |
| Tally above the table | 7 suggestions | 7 filled in | 11 | One verb everywhere. Singular: "1 filled in". |
| Fill from (open choice) | Fill from Middle / Top | Fill from: Middle, Top | 22 | Keep the short labels. Each radio needs the full name for screen readers: "Middle of range", "Top of range". |
| Fill from, status | Suggested budgets now fill from the middle of each range | Now filled from the middle of each range. | 41 | Shorter, same facts. Add "Your values kept." only if the lead has any. |
| Details button, next to the budget | Details | Details | 7 | Screen reader name: "Details for QA & launch". |
| Overrun, on the row | Overran in 4 of 5, by 10 to 16 h | Over by 10 to 16 h in 4 of 5 | 28 | Adopted from revision 4. Better than my "up to 16 h": it keeps the range, carries a unit, and puts the size before the count. Red text, warning icon and the words "over by" mean colour is not alone. Screen reader: "Over budget by 10 to 16 hours in 4 of 5 past projects." |
| Details line, per project | Lumen Dental: Website redesign, 30 h, budget 20 (over by 10) | Lumen Dental: Website redesign. 30 h, budget 20 h, over by 10 h. | 64 | Units on every number. Lowercase "over by" in red, as in revision 4. |
| Fixed Fee reference | For reference: $41,260 to $56,340 at current rates. | For reference: $41,260 to $56,340 at current rates. | 51 | Keep. |


## 4. References panel

| Where | Current | Proposed | Chars | Why |
|---|---|---|---|---|
| Title, show, hide, close | Evidence / Show evidence / Hide evidence / Close evidence | References / Show references / Hide references / Close references | 65 | Plural by default. Singular only for one project. |
| Method line | Hours come from tracked time, not old budgets. | Hours come from tracked time. | 29 | Cut as requested. |
| Add select label | Add a past project | Add a past project | 18 | Keep. |
| Unticked card | Not used in this estimate | Left out | 8 | Short, and matches the status sentence. Also gives the greyed card a text state. |
| Open in new window | Open Client: Project in a new window | Open Client: Project in a new window | 36 | Keep. Not new copy. |
| Whole-estimate change, status | Left out Lumen Dental: Website redesign. 4 projects. Total 358 to 349 h. Your edits kept. | Left out Lumen Dental: Website redesign. 4 projects. Total now 349 h, was 358 h. Your values kept. | 98 | "358 to 349" reads as a range. Drop the last sentence when the lead has typed nothing. |
| Added, status | (same pattern) | Added Lumen Dental: Website redesign. 5 projects. Total now 358 h, was 349 h. | 77 | Same shape. |
| State changes, status | Suggestions clear with a status sentence | Now only 2 close matches. Nothing filled in. Your values kept. | 62 | Flagged variant: "Now only 2 close matches. Check these numbers." |


## 5. Per-task reference tags (new)

In a row's Details drawer, each past project is a removable tag with an x. Removing leaves the project out of that task only. Removed tags stay, struck through, and can be added back. Focus stays on the same control.

| Where | Current | Proposed | Chars | Why |
|---|---|---|---|---|
| Group label | (none) | References for QA & launch | 26 | Names the task for screen readers. |
| Tag, visible text | Remove link | Lumen Dental: Website redesign, 30 h, over by 16 h × | 52 | Name, hours, red "over by" only when over, then the x (a glyph, `aria-hidden`). Removed tag: struck through with + in place of x. |
| Tag remove button, accessible name | Remove Lumen Dental: Website redesign from QA & launch estimate | Remove Lumen Dental: Website redesign from QA & launch | 54 | The name contains the visible text, so voice control works, and adds the action and the task. Dropped "estimate". |
| Removed tag, visible | struck through, Add back | Lumen Dental: Website redesign, struck through, with a + button | 63 | Strikethrough is not the only signal: add visually hidden "left out". |
| Removed tag, accessible name | (none) | Add back Lumen Dental: Website redesign to QA & launch | 54 | One verb pair: Remove and Add back. |
| Removed tag, hidden text | (none) | Left out | 8 | Read with the name: "Lumen Dental: Website redesign, left out". |
| Remove, announcement | Removed Lumen Dental: Website redesign from QA & launch. Range 22 to 36 h. | Removed Lumen Dental: Website redesign from QA & launch. Range 22 to 36 h. | 74 | Keep. Add "Your value kept." if the field holds a value the lead typed. |
| Add back, announcement | (none) | Added back Lumen Dental: Website redesign to QA & launch. Range 20 to 36 h. | 75 | Mirror of remove. |
| Last reference removed | (none) | Removed Lumen Dental: Website redesign from QA & launch. No range left. Nothing filled in. | 90 | Honest end state. If the lead typed a value: "Your value kept." |


## 6. Hidden live region (screen reader only)

The visible status line stays blank when done. The hidden region speaks:

| Event | Announcement |
|---|---|
| Consistent | Estimate ready. 5 past projects, 310 to 414 hours. |
| Conflicting | Estimate ready. 5 past projects disagree, 120 to 480 hours. Nothing filled in. |
| Few matches | Estimate ready. Only 2 close matches. Nothing filled in. |
| Few matches, flagged | Estimate ready. Only 2 close matches. Check the filled numbers. |
| No matches | No matches. Nothing filled in. |
| Saved | Project saved. |

Other screen reader notes: "h" is read as "hours" (hidden expansion). Focus returns to Describe after the estimate and does not move to the table. The banner has `aria-label` "References". The strength tag (a plain pill, not uppercase) follows the headline in the DOM, so it reads as "Filled from 5 past projects, Consistent". No prefix needed.

## 7. Manager variants (FOR LATER, do not build for the Administrator)

A Manager sees only projects they can open. The hint says more history may exist, never how much, and never names anything they cannot open. For testing H3.

| Where | Proposed (Manager, for later) | Chars | Why |
|---|---|---|---|
| Few matches, headline | Only 2 close matches | 20 | Same as Administrator. |
| Few matches, sentence | Nothing filled in. More history may exist beyond your access. Ask your Administrator. | 85 | No count. Names who to ask. |
| No matches, table line | No matches in projects you can open. More history may exist beyond your access. Ask your Administrator. | 103 | Scope is the Manager's. |
| Access hint, one line | More history may exist beyond your access. Ask your Administrator. | 66 | Reusable. Count how many leads act on it (H3). |


Open: "Ask your Administrator" is plain text today. A real link or message action is a product question.

## 8. Handoff notes for design-builder

- Remove every use of: tentative, draft, accept, confirm, "Suggested" (visible), "evidence".
- Pluralise: 1 past project, 2 past projects; 1 close match, 2 close matches; 1 filled in. Leave a sentence out when its part is zero or empty ("Your values kept." only if values exist).
- Hours are "h" on screen, "hours" for screen readers.
- Flagged-thin strings go together with the H1 toggle; do not mix with the empty variant.
- Manager strings are for later.
