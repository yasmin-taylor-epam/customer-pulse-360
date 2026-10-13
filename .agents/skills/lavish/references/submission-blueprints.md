# Submission blueprints in a single HTML document

Use this procedure when a comparison must become independently usable technical proposals, especially for a hackathon or design submission.

## Establish the submission boundary

1. Read the existing document and the supplied brief. Preserve explicit exclusions from the evidence base.
2. Extract required capabilities, judging criteria, team capacity, build window, submission format, and unresolved organiser requirements.
3. Distinguish an idea proposal from a completed solution entry. Do not call a design an implemented service.

## Expand every scenario

Use the same content structure for each scenario, but make the mechanisms specific to its business.

- Submission summary: title, customer problem, intended user, proposed solution, distinctive value, and scope exclusions.
- Data contracts: record grain, identity keys, required fields, event and ingestion timestamps, source provenance, and missing-data handling.
- Architecture: historical ingestion, transformations, model training, score publication, event processing, alert evaluation, and case creation. Name interfaces and storage boundaries.
- Prediction: customer unit, outcome definition, scoring checkpoint, observation window, unknown labels, leakage controls, baseline, validation split, and review capacity.
- Segmentation: fitted features, preprocessing, cluster selection, interpretation, and limits. Do not rename routing rules as ML segments.
- Actions: eligibility, evidence freshness, owner, human approval, unique case key, retry behaviour, recovery handling, and audit fields.
- Delivery: bounded work packages for the available team, parallel interface contracts, demo sequence, counterexample, and measurable acceptance tests.
- Submission package: setup instructions, data provenance, reproducible implementation assets, evaluation, audit evidence, video, and fields requiring organiser confirmation.

Separate event arrival from feature refresh, model scoring, alert delivery, case creation, and dashboard refresh. These operations have different clocks and failure modes.

Define advance-warning claims against an explicit outcome date. Predicting an outcome within a future window does not prove that much advance warning.

Keep value at risk separate from saved revenue. Synthetic outcomes demonstrate mechanics, not commercial uplift or intervention effectiveness.

For financial-service scenarios, define the commercial prediction separately from customer-support obligations. Distinguish mortgage refinancing from default and insurer withdrawal from customer-led non-renewal. Route payment difficulties and urgent claim assistance independently of churn score or customer value. Exclude lending, pricing, coverage, and claim decisions from a service-recovery prototype unless explicitly requested and governed. Loan balance is exposure, not saved revenue.

## Build the document views

1. Keep one portable HTML artifact with stable scenario IDs and deep links.
2. Provide a main comparison page and one complete view per scenario. When adding a scenario, update its content, main-page link, route registry, page title, navigation label, and displayed scenario count together. In array-based routing, check that IDs, titles, and labels have equal lengths and corresponding entries. Content alone does not make a navigable blueprint.
3. Lead each scenario with an evidence-to-action illustration, a small architecture diagram, and a checkpoint timeline. Use short captions. Place business context and complete technical sections in labelled disclosures, closed initially. Keep the incident and counterexample available inside the context disclosure.
4. Draw historical data and event paths separately. Connect both to explicit feature refresh or scoring, not through an invented dependency. Show the case writer and human owner. Keep urgent support independent of commercial scoring where the design requires it.
5. Make timeline captions scenario-specific. A checkpoint before contract expiry does not prove the same lead time before every departure. Keep warnings about one scenario off unrelated scenario pages.
6. Preserve theme state across navigation. Include back navigation and scenario-specific printing. Open the selected blueprint's disclosures before printing and restore their prior state afterward, so the submission remains complete without changing the reading view.
7. Ensure hidden views remain hidden when printing. Do not let print overrides reveal unrelated scenario pages.

## Verify and publish

1. Check unique IDs, internal links, HTML structure, script syntax, and required section coverage for every scenario.
2. Exercise main-page links, direct deep links, back navigation, disclosures, counterexample controls, theme changes, and print scope in a browser. A deep link to a section inside a closed disclosure must open its ancestor disclosures before scrolling.
3. Run a browser verification matrix across every scenario, both themes, and desktop and narrow viewports. Open disclosures before inspecting their diagrams; hidden SVG elements can return empty bounds and falsely pass. Check page overflow with document.documentElement.scrollWidth > innerWidth. For each rendered SVG, compare getBBox() for text and shapes outside defs against its viewBox; separately check text containment within nodes and connector crossings, because fitting inside the canvas does not prove a legible diagram. Check generated IDs for duplicates and count required sections per scenario in the rendered DOM, not only the static source. Exercise theme changes through the actual control and confirm the rendered colours, not merely the checkbox state. Capture and inspect light, dark, and narrow screenshots; report screenshot capture separately from visual inspection when inspection is incomplete.
   For printing, record disclosure states, trigger beforeprint, emulate print media, and assert that only the selected page is displayed with its full specifications open. Trigger afterprint and assert that the prior disclosure states are restored. Keep these assertions separate from verifying the print button invokes printing; event simulation alone does not exercise that button.
4. Update the existing hosted site using its recovered credential and current CLI syntax. Do not create a replacement URL by default.
5. Read back the hosted artifact and count required sections per scenario.
6. Return the live URL, scenario deep links, and local artifact. State unresolved submission fields and unperformed checks explicitly.

Do not treat source-code presence as interaction evidence. If browser checks cannot complete, report that limit without recording unsuccessful attempts as a reliable workaround.
