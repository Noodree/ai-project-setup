# Concept B (inline), Administrator view: design spec

**Status:** revision 3, 2026-11-12, after Audrée's second review. Her calls override the strategy. Nothing is tested with users. All data is invented.
**Sketch:** `concepts/b-inline/admin.html` (one file, no build step). Checked at 1440px wide.

## Revision 4 changes (read first, newest)

Strings changed are marked **[string]** for content-writer.

1. **Details sits right after the budget field** (small outlined button). Remove (the task) is in its own column, separated by a vertical rule and wide gap, so the two are hard to confuse.
2. **Overruns are red and carry a unit.** Overran tag **[string]**: "Over by 10 to 16 h in 4 of 5" (was "Overran in 4 of 5, by 10 to 16 h"). Drawer and chips **[string]**: "over by 16 h" (lowercase h, space). Red `#a8190f` on a pale red `#fde2dd` tag is about 6.5:1, and on white about 8:1 (estimates, verify in build). Colour is not the only signal: the words "over by" and the warning icon on the tag carry it.
3. **References as removable tags (default) or links, toggled in the sketch bar ("References: Tags / Links").** Tag chip: "Client: Project", hours, red "over by" text if any, and a round ×. Removed chips are struck through with a + to add back. Every ×/+ is a focusable button named, for example, "Remove Lumen Dental: Website redesign from QA & launch estimate". Announced **[string]**: "Removed Lumen Dental: Website redesign from QA & launch. Range 22 to 36 h." (unchanged). The ×/+ is 24px; raise the hit area to 44px in build.
4. **Banner tag moved after the headline** ("Filled from 5 past projects  Consistent"). It is now a plain pill, no border, no uppercase, so it reads as status and not a button. Tag words unchanged.
5. **Selected reference cards in the panel** get a pale orange fill and orange border (same family as the AI-filled treatment). Unchecked cards are neutral grey. The checkbox stays, so state is not colour only.

## Revision 3 changes

1. **App shell matches the real Harvest app** (from her screenshot): pale peach sidebar, logo built from three rounded orange bars (not a Harvest asset), round collapse toggle overlapping the sidebar edge, large orange stopwatch circle, white "..." circle, divider, outline icons with a clock first. Header: "← Back to Projects" in medium weight, full-width divider, large bold "New project", one-line subtitle "Describe it, or fill in the form." (for content-writer), divider.
2. **"Evidence" is now "References"** everywhere: panel title, "Show references" / "Hide references", close label, banner group label, key `R`. Plural by default. Singular is used only for one project ("Filled from only 1 past project"). The state tags are unchanged (Consistent, Conflicting, Few matches, No matches); revisit if "References" makes "evidence" tags feel off.
3. **Banner is a pale orange card** with the same dashed border and tint as AI-filled inputs, so it reads as coming from the AI. Order: tag and headline, then one sentence saying what happened, then the buttons below. Strong: "Filled from 5 past projects" / "Tasks and hours below. They tracked 310 to 414 h in total." Conflicting: "5 past projects disagree: 120 to 480 h" / "Nothing filled in. Pick the kind of work that fits." Few matches: "Only 2 close matches" / "Nothing filled in. Add a past project" (blue link, no button). Flagged variant: "Filled from only 2 past projects" / "Weak base. Check these numbers." **No matches: no banner.** The table shows one line: "No similar projects. Start from a past project or add tasks by hand." (link and text for content-writer).
4. **After the estimate the page does not scroll and focus does not move.** The user may want to set dates first. Only the hidden live region announces "Estimate ready. 5 past projects, 310 to 414 hours."
5. **Per-task references.** In a row's Details drawer each past project has Remove. It leaves that project out of that task's range and suggestion only; other tasks do not change. Removed projects stay listed, struck through, with Add back. Each button has a full label ("Remove Lumen Dental: Website redesign from QA & launch estimate"). Focus stays on the same button. Status and live region: "Removed Lumen Dental: Website redesign from QA & launch. Range 22 to 36 h." An entered value is never changed by this.
6. **Thinking state:** the Estimate button is disabled and reads "Estimating..." as well as every field and button.
7. **Open choice (not reviewed by Audrée): "Fill from Middle / Top"** is kept as is. Decide whether to keep it.

## Revision 2 changes

(Kept for history.)

1. **No tentative or draft state.** No "Save as tentative", no live gating, no confirm step, no badge. Buttons: **Save project** (primary) and **Cancel**.
2. **No accept step.** No "Accept all", no per-value accept. Typing over a suggested value makes it the lead's own. Regeneration never overwrites it.
3. **Concise copy everywhere.** Explanations of obvious interactions removed.
4. Top of page: thinking text kept, ghost loading state added, result text removed, past-project link shown only while the field is empty.
5. Evidence banner reworked (actions left, evidence-based tags).
6. Panel simplified, project cards refined.
7. Suggested chip replaced with an icon.
8. Team, Invoices, Notes sections built like Harvest's real form.

## The design in one paragraph

No chat. The AI is Harvest's existing "Describe the project" bar at the top of New project, focused on load. One line and Enter fills Tasks and hours with suggestions. A sticky pale-orange banner stays in view while editing. References open in Harvest's 440px push panel, where projects can be unticked or added and the numbers update. Suggested values are marked by a small icon, a dashed border and a tint. Saving never waits on anything.

## Click count

Focus is in the Describe field on load.

| Journey | Clicks | Other |
|---|---|---|
| **Saved project, mouse** | **1** (Save project) | type one line, press Enter |
| Same, keyboard only | **0** | type, Enter, Cmd/Ctrl+Enter |
| Read references | +1 | or press `R` |
| Drop one comparable | +2 | Show references, untick |
| Start from a past project | 1 link + 1 choice | replaces the typed line |
| Change budget type | +1 | |

"Saved" means saved and editable, not vouched for. We have no baseline for today's form, so no "faster than" claim.

## Layout (top to bottom)

1. Title "New project". Banner slot (after save: "Project saved.").
2. **Describe the project** bar (existing pattern). Under it: `/ to focus` and the link **Start from a past project**, shown only while the field is empty and nothing has run. Then one status line.
3. **Project:** client, name, code, tags, currency, dates.
4. **Billing and budget:** project type, billable rate, budget type.
5. **Tasks and hours:** evidence banner, suggestion count with "Fill from Middle / Top", task table, total, Add a task.
6. **Team:** people with Manages checkbox and cost rate, Add a person.
7. **Invoices:** due date, PO number, tax, second tax, discount.
8. **Notes:** notes, report visibility, Forecast checkbox.
9. Save bar: **Save project**, Cancel, shortcut hint.
10. Evidence panel (440px, right). Overlay below 1000px.

Team, Invoices and Notes are static in the sketch (invented people, rates and percentages) and follow the order of Harvest's New project form. Verify field names against the live form when building the demo (to verify in app).

## Thinking and ghost state

While the AI works (about 2 seconds in the sketch):
- The status line shows text with a spinner, kept as before: "Understood: new brand website for Fernwood Outdoor Supply. Matching against 38 projects you can open..." then "Reading tracked time on the closest projects...".
- **Ghost state:** the form region and save bar get `aria-busy="true"`. Every field and button is disabled and shows a shimmer. Disabled controls keep their labels, so they still read sensibly. The task table shows skeleton rows and the banner a ghost bar. The Describe field stays focused but is read-only.
- Reduced motion: the shimmer and spinner stop; the greyed state stays.
- When done, the status line goes blank. A visually hidden live region announces "Estimate ready. 5 past projects, 310 to 414 hours." Focus returns to the Describe field.

## Suggested vs entered values

Two states, marked without relying on colour:

| State | Look | Screen reader |
|---|---|---|
| Suggested | Dashed border, tint, small sparkle icon beside the field | "Suggested, range 20 to 30 hours." plus icon named "Suggested" (hidden text and `title`) |
| Entered or empty | Normal | "Entered by you." or "No value yet." |

Typing turns a suggested field into a normal one on the keystroke. Regenerating (comparable change, budget type, Fill from) only touches suggested and empty values. The tally above the table says "7 suggestions".

## Banner (superseded by revision 3 point 3 where they differ)

Order, left to right: **actions**, **tag**, **headline** with optional one-line subtext. The tags are about evidence, so each is self-explanatory:

| Tag | Headline | Subtext (for content-writer) | Actions |
|---|---|---|---|
| Consistent | 5 past projects, 310 to 414 h | none | Show references |
| Conflicting | 5 past projects disagree: 120 to 480 h | Pick the kind of work that fits. | Use the 3 full builds, Use the 2 refreshes, Show references |
| Few matches | Only 2 close matches | Add a past project, or enter hours. | Add a project, Show references |
| No matches | No similar projects | New client, no similar work. | Name a past project, Enter by hand |

Tag words are placeholders **for content-writer** (alternatives: "Agree" / "Disagree"). Each tag has a glyph and a word, so strength never depends on colour. Overruns stay on task rows, not in the banner.

Thin has the H1 toggle in the sketch strip: empty (default) or a flagged starting number, whose subtext is "Weak base. Check these numbers." (for content-writer).

## References panel

Content, in order: kind-of-work cards (Conflicting only), the project list, "Add a past project" select, one line "Hours come from tracked time." (for content-writer). No heading line over the list, no "untick" hint, no "right away".

**Project card:** checkbox and name ("Client: Project"), then one meta line: "full website build · 2025 · 356 h · 7 of 7 tasks · same client". Unticked cards go grey and stay listed, so they can be ticked back.
**Open in new window:** a small icon button at the card's right edge (`target="_blank"`, `aria-label="Open Client: Project in a new window"`, `title`). It appears on hover and also whenever focus is anywhere inside the card, including the checkbox, so keyboard users see it before tabbing to it. On touch devices it is always visible. It replaces the blue text link.

Every change writes one short status sentence: "Left out Lumen Dental: Website redesign. 4 projects. Total 358 to 349 h. Your edits kept."

## Task rows

- Columns: Task, Tracked (range and "5 projects"), Rate (fees modes only), Budget, actions.
- Suggested value is the middle of the range. "Fill from Middle / Top" re-fills only suggestions.
- **Overran tag:** "Overran in 4 of 5, by 10 to 16 h", on its own line under the task name with 8px space above and its own padding.
- **Details** drawer kept: "Client: Project, 30 h, budget 20 (over by 10)", one line per project.
- Estimates come from tracked time, never old budgets.

## Budget types

Hours per task, fees per task, total hours, total fees, none. Changing type keeps entered values and converts them at the blended rate. **Fixed Fee:** the fee is never suggested. One reference line: "For reference: $41,260 to $56,340 at current rates." Rates and dollar ranges are Administrator-only; Manager and Member views must not render them (later pass).

## States

Switch with the dark strip at the top (not part of the design). State is derived from the projects in use: 0 none, 1 to 2 few, 3 or more consistent if the totals are within 1.6 times of each other, else conflicting. The thresholds are a stand-in; "what counts as thin" is an open product question. Unticking projects can move the state, and the suggestions clear with a status sentence.

## Components: reuse and new

Reuse: frame, Describe bar, form rows, segmented radios, selects, buttons, table, 440px panel, combobox (native select in sketch). **New:** evidence banner, suggested icon and dashed field style, overran tag, project card with hover and focus icon, ghost state, status line.

## Keyboard and screen reader

- Keys: `/` focuses Describe, `R` toggles references, Enter runs, Cmd/Ctrl+Enter saves, Esc closes the panel and returns focus to Show references.
- Focus order follows the page. The panel is last in the DOM; focus moves into it on open and back on close.
- Status line is visible and for text the lead should see. A separate hidden live region carries screen reader announcements, so blank visible text does not mean silence.
- Every budget field has a unique label and a description sentence. Table has a caption and headers. Details and Remove carry the task name.
- Greyscale: tag word, icon, dashed border and overran text all survive. Small buttons are 28 to 34px; raise hit areas to 44px in build.

## Portability to Concept A

The banner sentence, the range and count, the overran line and the comparables list all work in a chat reply. The sticky banner, the field icon and the ghost state do not.

## Copy marked for content-writer

Tag words, banner subtexts, the thin flagged subtext, the panel method line, status sentences, ghost-state text, "Project saved.", "No tasks. Name a past project or add tasks by hand." The earlier copy deck is stale (it assumes tentative and accept) and should be redone against this spec.

## Open questions

1. Banner order: actions left of the tag and headline, as requested, reads action before context. If testing shows people miss the headline, try the headline first with actions on the same row.
2. Autofocus in Describe: keep for speed, or reach it by Tab.
3. Strength thresholds from product and data.
4. Hours per person budget needs the team section tied in; not designed.
5. Verify in the real app: required fields, Duplicate behaviour, Forecast, and whether Managers can create projects.

## Not covered

Manager and Member views, Preferences for excluded projects, mobile layout, user testing.

## Build notes (2026-11-16, design-builder)

Built into `concepts/b-inline/admin.html` after Audrée's direction and the approved copy deck.

**What changed**
1. **Look and feel from index.html.** Tokens, sidebar (markup, 12 icons, sizes, avatar), topbar, type sizes (H1 32/40 medium, body 15), form rows, inputs, buttons, table and panel styles are copied from index.html and checked against its computed values. The round collapse toggle and the 3-bar logo from revision 3 are gone, because the sidebar now matches index.html exactly. Header order is kept: "Back to Projects", divider, title, one-line subtitle, divider.
2. **AI-filled fields as in index.html.** The orange sparkle (same 18-viewBox path, drawn at 12px in labels, 14px beside table inputs) plus the pale orange fill and solid orange border. Applies to Client, Project name, every task budget and the total field. Typing (or choosing another client) turns the field back to normal. The icon is `aria-hidden` with `title="Filled from past projects"`; the field description carries the words. The banner uses the same fill and border (solid, no longer dashed).
3. **Details / Hide details and Remove are text buttons** (blue, no box, 44px hit area by pseudo-element).
4. **Removable reference tags use Porchlight "Tag select" (4431:37).** Default, error (over budget, red border, "over by" text stays) and disabled (left out, with +). The two SVGs are inlined exactly from `assets/`. The + is the disabled X rotated 45 degrees. 44px hit area. Names follow deck section 5.
5. **No native selects.** Custom select-only combobox (`<button role="combobox">` with `aria-controls`, `aria-expanded`, `aria-activedescendant`, `role="listbox"` and options). Keys: Enter, Space, Up, Down, Home, End, Escape (closes the list only), Tab (commits), type-ahead. Mouse and label click work.
6. **"Hours per person" is removed.**
7. **Copy deck applied.** Includes removal of the save-bar shortcut hint and of "Start another" (after saving, the bar hides and focus goes to "Project saved."). Visible status line is now `aria-hidden`; every announcement goes through the hidden live region, so nothing is read twice. "h" is shown, "hours" is read.

**Deviations and additions**
- Project type options show index.html's one-line descriptions ("Bill by the hour, with billable rates" and so on). They are real Harvest strings, not in the deck. Easy to cut.
- Dates use index.html's "Starts on / Ends on" boxes.
- Strings not in the deck, derived in its pattern: "Now N past projects disagree. Nothing filled in." and "Filled from N past projects." (state-change statuses), "Budget type: total hours.", "No tasks yet.", "Left out" chip in the panel card (deck: Unticked card).
- Flagged thin variant has no "Add a past project" link (the deck sentence is only "Check these numbers."). The panel still has the select.
- The disabled tag label (#8d8e8d on #eee) is Figma's value and is about 2.8:1. Flagged for accessibility review.
- The inlined SVGs repeat `id="icon-x"`, `Line`, `Line_2` on every tag, as in the source files.
- Descriptions for "Fill from: Middle, Top" read "Middle of range" and "Top of range".


### Revision 6 (2026-11-17, from Audrée's review)
- Logo: the Harvest symbol exported from Figma replaces the drawn vector.
- Budget table: no vertical divider before the Remove column.
- Conflicting: once the lead picks a kind of work, or changes the reference set, the fields fill. Banner reads "Filled from N past projects" and keeps the Conflicting tag.
- Per-task references: a "View" text button sits right of the tracked range ("Hide" when open); it no longer sits beside the budget field.
- Reference tags: the project name underlines on hover, since it opens the project.
- Drawer heading: "References" (the task name stays in the screen-reader label).
