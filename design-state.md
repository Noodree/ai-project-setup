# Design state: Harvest AI project setup

Full brief (single source of truth): https://claude.ai/artifact/SbDbEiPRPzdjBgwbiP7qrL
Approved by Audrée on 2026-11-09.

## Brief summary
- **Problem:** project leads set up tasks and budgets by hand, while the evidence of what similar projects took sits in tracked time, so budgets repeat past overruns.
- **Primary persona:** the person who scopes new work at a small service firm with project history in Harvest.
- **Success metric:** budget vs actual hours at project close, overall and per task, compared with projects set up by hand.
- **Core constraint:** Harvest data only; the AI must judge and show similarity to past projects.

## Design principles
Draft, pending Audrée's approval. Full text, costs, related UX patterns and tests in the strategy doc: https://claude.ai/artifact/6jWSRJicixLpU3ZmUBYLJZ
1. Every number carries the past projects it came from.
2. Show where it went wrong, at the task where it happened.
3. The lead owns every number.
4. Evidence is part of the product, not a layer on top (inclusive).
5. The fast path is the default path: compact by default, detail on demand.
Hypotheses to test: H1 honest empty fields vs flagged starting number (was principle 2), H2 compact headline is enough, H3 access hint sends PMs to the admin, H4 chatbot faster for detail-heavy input.

## Decisions
This list is the decision record for the case study and the video demo. Every decision Audrée makes goes here, dated, newest first.
- 2026-11-23: case study angle set by Audrée: show Claude's multiple concepts and why inline won over the chatbot, privacy (only projects the viewer can open), accuracy vs speed (always estimate, flag certainty), alignment with the Premium squad's Pro plan work and ideal customer, first draft vs final, confidence banners side by side, link to clickable demo.
- 2026-11-23: demo video done; project pushed to a new private GitHub repo named without "Harvest" (ai-project-setup). Next: the portfolio case study (user direction).
- 2026-11-23: result line reads "Estimating 358 h from 5 projects"; demo mode added for recording (?demo hides the sketch strip, Ctrl+1 to 4 switch states) (user direction).
- 2026-11-23: review triage. Applied: a clickable result line under Describe ("356 h from 5 projects", jumps to Tasks and hours) so the result is visible without auto-scrolling. Rejected: kind-of-work groups (full builds / refreshes) in the Conflicting banner; deciding which projects are similar is the AI's job, not the lead's. Ignored for now: the other review items (field-level confidence, shared Low confidence tag, Porchlight border contrast, Cancel confirm, design debt list) (user direction).
- 2026-11-23: one avatar per task, a different teammate per task (user direction).
- 2026-11-23: data-quality notes on some references only (e.g. "Scope change", "Time tracked late"), shown in the reference tags and the References panel (user direction).
- 2026-11-23: no more Figma updates needed for this round; the HTML sketch is the working artefact (user direction).
- 2026-11-23 (later): confidence tags regular weight; Estimate column ranges as "8-34 h"; teammate avatars side by side, no overlap; references link reads "Hide references" when open; overrun moved next to the estimate as small red text; Conflicting banner gets "Use upper range" and "Use low range" (press again to go back to the middle). Actions column narrowed, Estimate column widened (user direction).
- 2026-11-23: Audrée's Figma (banners node 152:1962, page 83:2333) applied to admin.html. Banners: Strong "Estimate based on N projects" + "Strong confidence"; Conflicting "N past projects disagree: X to Y h" + "Low confidence", "Verify estimates below."; Thin "Only N projects match" + "Low confidence", "Verify estimates below, or add past projects.", button "Add project references"; no icons in tags. Every state with at least 1 reference fills (conflicting and thin included); the H1 empty-vs-flagged test and the kind-of-work buttons are gone. None: no banner, "No matches. Start from a past project." Table columns: remove (x icon button), Task, Assigned teammates (All/None), Billable (All/None), Billable rate (per hour) in Task rate mode only, Budget (hours), Actions, Estimate (range or single value, "N references" link opens the per-task drawer). One reference shows the tracked time, not a range. Fill from Middle/Top removed (user direction).
- 2026-11-17: Tasks table becomes a hybrid of Harvest's real Tasks table and the AI table: assigned teammates with Edit (per-task assignment), Billable, Billable rate (Task billable rate only), Tracked with View, Budget. With Person billable rate the rate column moves to Team and the edit-task row shows each teammate's rate. Designed in Figma first; HTML not updated yet (user direction).
- 2026-11-17: Audrée's review of revision 5: Harvest logo exported from Figma (assets/harvest-logo.svg, inlined); no vertical divider in the budget table; Conflicting fills once the lead picks a kind of work or changes the references; per-task "View" sits right of the tracked range ("Hide" when open); reference tag names underline on hover (opens the project); drawer heading is just "References". Earlier drafts kept in concepts/b-inline/archive/ for the case study (user direction).
- 2026-11-16: the Admin sketch takes index.html's look and feel (sidebar, icons, font sizes) and its AI-filled field treatment (icon next to the field plus orange highlight); Details is a text button; reference tags follow Porchlight's Tag select (Figma 8997KDhiBWxDNEHt3ussIT node 4431:37); no 'not in this sketch' placeholders (user direction).
- 2026-11-16: copy deck approved by Audrée ("copy is good").
- 2026-11-12: Evidence renamed References; banner is a pale orange card with copy first and buttons below; no banner in the none state; thin uses an 'Add a past project' link; references removable per task; no scroll after the estimate; shell matches the real Harvest sidebar and header (user direction).
- 2026-11-12: Audrée's sketch review. No tentative or draft state in the New project flow: "Let's not create a new feature that doesn't exist." Buttons are Save project and Cancel. This reverses the 2026-11-09 "tentative stays core" decision; brief and strategy still describe tentative and need updating. No accept step: AI values sit in ordinary fields, the lead edits what they don't like. Suggested values marked by the input treatment plus a small icon, no "Suggested" word per field. Team and Invoices sections stay in the sketch (demo). Interface copy must be much more concise (user direction).
- 2026-11-12: content-writer delivered Concept B Administrator copy (docs/designpowers/content/2026-11-12-concept-b-admin-copy.md). Thin has two copy variants for H1; none and thin use the same actions (Add a past project); "close matches" and "past projects" are the shared terms; Manager access hint written for later, no count.
- 2026-11-12: Concept B keeps a single AI entry point at the top of the New project page; no second action inside Budget (user direction).
- 2026-11-09: speed is a primary goal next to accuracy (time to a usable budget); principle 2 becomes hypothesis H1; strategy compares Concept A (extend Harvest AI chatbot, which Audrée tested and found weak at project creation) and Concept B (inline, Linear-style, her lean), no winner yet. UI per role, starting with the full Administrator in Concept B (user direction).
- 2026-11-09: estimates use only projects the viewer can open; no hidden-project counts. Assumption: at a small firm the admin grants PMs broader access in settings. Thin and none copy points to the admin setting (user direction).
- 2026-11-09: strategy names the related UX pattern for each principle, evidence state and journey moment (user direction).
- 2026-11-09: brief approved; tentative stays core; tentative projects visible only to their creator until activated; no research phase on this project.
- 2026-11-06: feature = project setup from historical tracked time, for accurate tasks and budgets.

- 2026-11-16: design-builder rebuilt admin.html with index.html's look (sidebar, type, controls), AI-filled field treatment from index.html, text-button Details, Porchlight Tag select chips, custom accessible dropdowns (no native selects), "Hours per person" removed, copy deck applied. See Build notes in the spec.

## After the demo (agreed 2026-11-23)
Less visible AI-feature work to add once the demo is made:
- Evaluation plan: backtest estimates on finished projects; check confidence calibration.
- Feedback loop: estimate vs actual at project close; capture edits, removed references and range choices as signals.
- Say where the AI is: similarity and reading the description vs plain math for the numbers.
- Confirm what the AI understood before estimating, editable.
- Validation: test H1 to H4; sketch Concept A for comparison.
- Working-with-AI story: how agents were directed and where Audrée overruled them.

## Open questions
- Concept A (chatbot) or Concept B (inline)? Decided by testing, H4 first.
- Should AI suggest a fixed fee, or only hours and fee-based budgets?

## Artefacts
- Brief: link above
- Strategy (draft, revision 4): https://claude.ai/artifact/6jWSRJicixLpU3ZmUBYLJZ
- Concept B Admin spec: docs/designpowers/design/2026-11-09-concept-b-admin-spec.md
- Concept B Admin sketch: concepts/b-inline/admin.html
- Case study (Claude Doc): https://claude.ai/artifact/X7cFjjXgJxL1SBivnpDTbU ; images in case-study/images/
- GitHub (private): https://github.com/Noodree/ai-project-setup
- Demo script: demo/script.md
- Draft archive (r0 to r5, for the portfolio case study): concepts/b-inline/archive/
- Figma Tasks section for Audrée's own design work: EXPLORATIONS-AI, page "Tentative project", frame "Tasks section (for design)" (default and editing a task) plus local component "Tasks / Row"
- Figma, current Admin page with the hybrid table: frame "Admin / New project / Conflicting, task billable rate"; person-rate variant: "Admin / Tasks and Team / Person billable rate" (EXPLORATIONS-AI, page "Tentative project")
- First concept sketch (before the brief): index.html, Figma EXPLORATIONS-AI page "Tentative project"

## Handoff chain
- design-discovery: done (brief approved)
- research-planning: skipped by Audrée's decision
- design-strategy: draft delivered by design-strategist (2 revisions), awaiting Audrée's approval
  - design-strategist → design-lead: "Estimates use only projects the viewer can open, with no hidden counts, so write thin and none copy that points narrow-access PMs to the admin setting. Design the admin access moment as carefully as the PM screens. Still prototype thin and none first, and keep prompt vs in-form open."
- design-lead: Concept B, New project as Administrator, delivered 2026-11-09 (spec + clickable sketch). 1 click + Enter to a saved tentative project. Audrée answered: AI at top only. Handed to content-writer 2026-11-12.
  - design-lead → content-writer: "Thin and none carry the trust, so please own that copy. The Administrator sees every project, so don't use the 'beyond your access' hint here. Keep the headline under about 60 characters, the subtext to one line, and the word 'Suggested' exactly as is. The status-line sentences also need your voice."
  - content-writer -> design-builder (2026-11-12): copy ready in docs/designpowers/content/2026-11-12-concept-b-admin-copy.md. Thin variants A and B must not be mixed; use aria-disabled on Save as live; Manager strings are for later.
- design-lead: revision 2 of the Admin sketch delivered 2026-11-12 after Audrée's review (no tentative, no accept, ghost state while thinking, banner actions left, tags Consistent / Conflicting / Few matches / No matches, icon-only AI marker, Team, Invoices and Notes built). Brief and strategy updated to drop tentative (strategy revision 4).
  - design-lead → content-writer: "Your deck assumes tentative and accept, so redo it against the spec. New or short strings are marked 'for content-writer' in the spec. Keep every string short. She cut the copy twice."
- design-lead: revision 3 of the Admin sketch delivered 2026-11-12 after Audrée's second review. Open choice: keep or cut 'Fill from Middle / Top'.
  - design-lead → content-writer: "Copy is concise; new strings are marked for you in the spec. The deck is still stale (tentative, accept, evidence); redo it against spec revision 3. If 'References' makes the tag words feel off, say so."
  - content-writer -> design-builder (2026-11-12, copy deck revision 2): deck rewritten against spec revision 3 (References, icon-only marker named "Filled from past projects", no tentative or accept). Tags kept: Consistent / Conflicting / Few matches / No matches. Flagged-thin recommendation: fact in headline ("only"), instruction in sentence.
- design-lead: revision 4 delivered 2026-11-12 after Audrée's third review (Details beside the budget field, red 'over by N h', removable reference tags with a Tags/Links toggle, status pill after the banner headline, pale orange selected reference cards).
- content-writer: copy deck rebuilt 2026-11-12 against spec revisions 3 and 4 (docs/designpowers/content/2026-11-12-concept-b-admin-copy.md). Recommends keeping tag words; flagged-thin keeps 'only' in the headline, subtext 'Check these numbers.'
  - content-writer → design-builder: "Use the deck strings as written. Strip tentative, accept and Suggested from the UI. Chip × and + buttons use the full names in section 5; removed chips need hidden 'left out' text. 'h' on screen, 'hours' for screen readers. Flagged-thin strings go with the H1 toggle, never mixed. Manager strings are for later."
- design-builder: dispatched 2026-11-16 to apply the approved copy, index.html look, Porchlight tags and working custom dropdowns.

- design-builder (2026-11-16): revision 5 built. Deviations in the spec's Build notes. design-builder → reviewers: "Look and feel now comes from index.html. Check the custom listbox keyboard model, the tag contrast on the left-out state (Figma value, about 2.8:1), duplicate SVG ids, and the deck strings I derived for state-change statuses."

- review (2026-11-23): design-critic, accessibility-reviewer and heuristic-evaluator dispatched in parallel on concepts/b-inline/admin.html; reports go to docs/designpowers/review/2026-11-23-*.md, then reconciliation for Audrée.
- review synthesis (2026-11-23): docs/designpowers/review/2026-11-23-synthesis.md. A = fix now (bugs, a11y), B = six calls for Audrée, C = design debt. Awaiting her go-ahead.
- review triage (2026-11-23): Audrée applied B1 (result line), rejected B2 (kind-of-work groups), set the rest aside. Synthesis A fixes not applied.
