---
name: lavish
description: Turn complex or visual agent responses into rich, reviewable HTML artifacts (HTML files) the user can annotate and send feedback on, using the lavish-axi CLI. Use when about to give a plan, comparison, diagram, table, code diff, report, or anything easier to grasp visually than as prose.
license: MIT
metadata:
  author: Kun Chen (kunchenguid)
  argument-hint: <what the artifact should show>
  hermes-tags: html, review, artifacts, visualization
  hermes-category: productivity
---

# Lavish Editor

Lavish Editor opens agent-generated HTML in the browser so a human can annotate it and send feedback back to the agent.
Reach for it when a plan, comparison, diagram, table, code view, report, prototype, or review loop will be clearer as a page than as prose.

## Current guidance lives in the CLI

Use this file for durable user preferences and artifact requirements. Get current command syntax, design snippets, and playbook procedures from the CLI:

- `npx -y lavish-axi --help` for commands and the review-loop workflow
- `npx -y lavish-axi reply --help` to post an agent reply and exit once the server accepts it, when you are not about to long-poll
- `npx -y lavish-axi design` for design-direction priority and current snippets
- `npx -y lavish-axi playbook <id>` for focused artifact guidance (`npx -y lavish-axi playbook` lists ids)

You do not need lavish-axi installed globally - invoke it with `npx -y lavish-axi <html-file>`.
If lavish-axi output shows a follow-up command starting with `lavish-axi`, run it as `npx -y lavish-axi ...` instead.

## Mandatory Light & Dark Mode Requirements

Every generated Lavish HTML artifact must support both light and dark modes out of the box:

1. **Theme Controller in Header**: Always place an interactive DaisyUI theme toggle in the header or navbar so reviewers can easily switch between light and dark themes:
   ```html
   <label class="flex cursor-pointer gap-2 items-center text-xs bg-base-200 py-1 px-3 rounded-full border border-base-content/10">
     <span class="font-medium">☀️ Light</span>
     <input type="checkbox" value="luxury" class="toggle toggle-xs theme-controller" />
     <span class="font-medium">🌙 Dark</span>
   </label>
   ```
2. **Semantic Theme Colors**: Never hardcode fixed hex colors for surfaces, borders, or text. Always use semantic utility classes:
   - Surfaces: `bg-base-100`, `bg-base-200`, `bg-base-300`
   - Typography & borders: `text-base-content`, `text-base-content/70`, `border-base-content/10`
   - Status & accents: `primary`, `secondary`, `accent`, `info`, `success`, `warning`, `error`
3. **Theme-Aware Illustrations & Diagrams**:
   - **Inline SVGs**: Style shapes and text using `currentColor` and CSS theme variables (e.g. `var(--color-primary)`, `var(--color-base-100)`).
   - **Mermaid Whiteboards**: Include the theme observer script from `npx -y lavish-axi design` so diagrams re-render seamlessly when switching themes.
4. **Default Theme**: Default to `<html lang="en" data-theme="light">` (with `luxury` as the dark theme counterpart) unless dark mode is specifically requested.

## Visual-first presentation

Introduce each scenario with one or two plain sentences: name the customer's problem first, then describe the proposed solution and who takes action. Put this description on the overview card and visibly below the scenario page heading, outside disclosures; a hidden summary cannot orient a reader arriving by deep link. Keep the descriptions consistent through one shared content source. Follow with visuals rather than a wall of text. This user expects diagrams to explain the solution, not decorate a prose document. Show the customer problem, evidence-to-action path, architecture, and warning checkpoint with short labels and captions. Keep detailed contracts, evaluation, controls, and submission requirements in labelled expandable sections. Preserve the full blueprint rather than deleting the depth needed for submission. Apply this hierarchy to the main page as well as each scenario page.

Use scenario-specific evidence and actions in each visual. Keep historical ingestion and live-event processing separate until their actual integration point. Show support obligations independently of commercial risk thresholds. Label illustrative sequences and proposed targets explicitly. Do not invent chart values or imply measured performance.

Read the relevant source ranges once, batch a coherent revision, then move to rendered checks. Reuse unchanged skill and CLI guidance already loaded during the task; repeated identical reads do not establish additional evidence. When replacing a diagram helper, update every caller in the same edit and render immediately, because a stale helper call can prevent all later routes from being constructed.

## Art direction

Every artifact gets a composed form, not a default stack of equal cards. A creative choice earns its place only when it changes what the reader can see, do or trust. Change composition and explanatory metaphors, not just colours or rounded boxes. Preserve existing semantic theme tokens, factual boundaries and full specifications; imagination must improve comprehension without inventing evidence.

1. **Brief first, in every artifact.** Before writing HTML, put this brief as an HTML comment at the top of the document:
   ```html
   <!-- ART DIRECTION
   surface: <surface from references/surfaces.md> - reader task: <understand | approve | follow | weigh | specify | audit | choose>
   type voice: <roles for headline, body and evidence, from the system stacks below>
   signature figure: <the one figure that carries the whole argument>
   rhythm: <section order, and where the reader pauses at the decision>
   sameness check: <how this page differs from a column of equal cards>
   -->
   ```
   If you cannot name a signature figure, the argument is not ready to draw. Resolve it before writing markup.
2. **Pick the form from the reader's task.** Load `references/surfaces.md` and choose the surface whose reader task matches the request. When editing an existing artifact, keep its surface and design system unless the user asks for a redesign.
3. **One signature figure near the top.** It shows the whole argument in one picture, beside the one-sentence answer. Other figures support it; do not give three figures equal billing.
4. **Shapes carry meaning.** Use the shape legend in `references/surfaces.md` consistently (for example cylinder = persisted, pipe = stream, diamond = gate, solid line = direct evidence, dashed line = circumstantial or unverified). Show the legend once where the first such figure appears.
5. **Make honesty visible.** Label hypotheses, proposed targets, illustrative sequences and evidence gaps on the figure itself with a short stamp or tag, such as `Hypothesis · not measured`, `Proposed target`, `Illustrative` or `Evidence gap`. Draw weak evidence with dashed strokes.
6. **Say why this form.** Under each signature figure, or at the end of each major section, add one line: `Why this form: <what it lets the reader do>. Trade-off: <what it hides>.`
7. **Engineering specifications lead with invariants.** Order: invariants (`INV-1` …, one line each), data contract, failure cases (`T01` …, with the expected behaviour), then `Deliberately not specified`.
8. **System font stacks only**, so exported artifacts render offline. Serif `"Iowan Old Style","Palatino Linotype",Palatino,Georgia,serif`; sans `system-ui,-apple-system,"Segoe UI",Roboto,sans-serif`; mono `ui-monospace,"Cascadia Code",Consolas,monospace`. Do not load web fonts.
9. **Render check before serving.** Screenshot the artifact in light and dark at 1440px and 390px wide, and inspect every figure: Lavish's layout audit skips SVG interiors, so overlaps and clipped labels inside figures only show up in screenshots. Fix any defect and re-check. Then run the sameness check on the 1440px light screenshot and ask: does this read as a column of equal cards? If yes, revise the rhythm (answer, signature figure, pause at the decision, evidence) before serving.

Optional forms, only when their condition holds:

- **Present mode.** Use when the artifact will be shown in a meeting. Add `#present/1`, `#present/2` and `#present/3` routes that rewrite the content as three beats (problem, turn, decision), one sentence and one image each, with arrow-key navigation and Esc to return. Do not just shrink the page.
- **Physical texture** (stamps, tilted paper records, pinned evidence board). Use when the subject is records or evidence under investigation, so the metaphor carries meaning. Do not use it for plans, specifications or API designs.

## Review feedback and layout repairs

1. Start feedback collection with `npx -y lavish-axi poll <html-file>`. Treat each poll as a single-delivery operation, not a permanent listener: once it returns feedback, that process is no longer listening. Claim active monitoring only while a poll is running and its completion will return to the current agent. On completion, retrieve the complete result from the same tracked process before responding; a truncated notification can omit the prompts while retaining only the DOM snapshot. In Hermes, use `process_manage` with `action=log` and the known session ID, paging from the beginning when necessary. Read the session status and every prompt before using the snapshot as supporting evidence. After an interruption, recover that completed result rather than starting another consumer or asking the user to resend, because delivery consumes queued feedback. If the user reports missing feedback, compare the recovered result with the exact review session's Conversation panel through an authorised browser. Distinguish feedback received but unhandled from feedback not retrieved; an exited listener alone does not prove delivery failed. Treat feedback pasted into chat as actionable without requiring it to arrive again through the poll.
2. Reproduce queued layout issues inside the actual Lavish artifact iframe at the reported viewport and route. Inspect disclosure state, computed overflow, control visibility, and clipping ancestors before changing layout; standalone geometry does not reproduce the editor's embedding constraints. Distinguish ordinary below-the-fold content that scrolls into reach from content clipped by a container or hidden inside a closed disclosure. For overlapping custom layouts built alongside a component library, inspect the library's matching selectors and direct-child placement rules as well as the artifact CSS: a shared class name can inherit positioning that the custom layout never overrides. Treat this as a hypothesis until the relevant rules or computed styles establish it. If browser inspection fails, separate diagnosis and editing from rendered verification: use available source evidence for a justified repair, but leave the visual outcome explicitly unverified. Do not repeatedly reread unchanged source or retry the same failed inspection without a new diagnostic hypothesis.
3. Apply every queued repair in one coherent save so the review refreshes once. For closed disclosures whose descendants retain diagnostic geometry, explicitly hide non-summary children with `details:not([open]) > :not(summary) { display: none !important; }`. Remove `overflow: hidden` from expanding document containers when it clips required controls; retain any genuinely needed clipping on a non-interactive decorative wrapper instead. Preserve disclosure toggling, deep-link opening, and print expansion.
4. Verify the newer artifact revision in the same review session and viewport. Open the relevant disclosures, scroll each required control into view, click it, and check both viewport reachability and containment. Wait for Lavish's complete diagnostic pass and read its current unresolved-issue status; queued issue text remains historical evidence, and a successful save or reply receipt does not establish resolution. Report browser interaction results separately if diagnostic completion cannot be confirmed.
5. Act on all received feedback before treating the review turn as complete; explaining a missed delivery does not discharge the requested repair. When the user asks whether a repair is happening, report the actual artifact state: inspected, edited, rendered, or verified, and identify any blocker. A failed tool call must lead to a concrete alternative action or a clear blocked handoff, never an empty response or another unsupported promise. If a newer user instruction redirects or pauses the work, state what remains outstanding instead of claiming completion. Do not send a completion-shaped editor reply merely to restore responsiveness: Lavish replies mark delivered notes Done, so a reply receipt is not evidence that the repair succeeded. After handling feedback, use `npx -y lavish-axi reply <html-file> --agent-reply "<concise result>"` for a handoff, or `npx -y lavish-axi poll <html-file> --agent-reply "<concise result>"` when continuing the review loop. Confirm acceptance before claiming the editor received the reply. A reply-only handoff does not restart listening: when continuing review, start exactly one replacement poll with a completion-aware return path before claiming to be waiting for further feedback. Respect an ended session and do not reopen it without permission. Keep local review repair separate from hosted publication; an update key alone does not identify the published site and must never be saved in a skill or artifact.

## Existing artifacts and submission blueprints

1. Read the existing artifact before editing. Identify its actual scenario names and scope before drafting summaries; business scenarios and technical capabilities are different lists, and an unrelated repository overview can describe the wrong material. Preserve its design system and working interactions unless the user requests a redesign. For a description-only change, update the overview and scenario introductions together without redesigning or expanding the technical specification.
2. When the user requests separate scenario pages inside one HTML document, provide individually addressable views linked from the main page. Include return navigation and a print action for each blueprint. Opening a blueprint must not select that scenario as a business decision.
3. Make each submission blueprint independently usable. Include its problem, proposed solution, data contracts, architecture, model design, action controls, ownership, acceptance tests, and submission requirements. Keep assumptions, proposed targets, and measured results distinct. Load `references/submission-blueprints.md` for the detailed content and verification sequence.
4. When updating a live document, recover the exact URL and update credential from the user-designated source. For Hermes history, use `session_search` with the specified session and profile, not another harness's history store. Read a bounded window around the publishing operation when an anchor is available. Run `npx -y lavish-axi share --help`, then use the existing site update operation. Preserve password settings unless the user requests a change. Never place update credentials in the HTML, repository files, or the handoff.
5. Read back the exact hosted document and check scenario coverage. Report content verification separately from browser interaction verification: HTTP success and script presence do not establish working navigation or printing. If readback returns HTTP 401, preserve access controls. Use an authorised browser session if available. Otherwise, report that the publisher accepted the update but hosted content verification remains blocked. Do not remove protection or create a public replacement to make verification pass.
6. When the user changes the publishing destination, stop work on the superseded destination and publish the latest edited artifact to the requested existing site. Distinguish completed repository writes from local unpublished changes. Report earlier commits or workflows that remain. Do not revert them without approval.

## Request

$ARGUMENTS

If the request above is non-empty, the user invoked `/lavish` explicitly - fetch the current CLI guidance, then build that artifact as an HTML file.
If it is empty, infer what to visualize from the conversation.
