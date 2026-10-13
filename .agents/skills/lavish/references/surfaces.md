# Surfaces

Load this file when writing the art-direction brief. Choose the surface from the reader's task, not from the subject or a preferred style. Name the surface and the reader task in the brief.

## Reader task to surface

| Reader task | Surface | Signature figure | Rhythm | Use when | Not when |
|---|---|---|---|---|---|
| Understand something that exists | **Broadsheet** | One explanatory figure beside the one-sentence answer | Answer, figure, mechanism, evidence, deliberately left out | Explaining a PR, incident, architecture or past decision | The reader must choose or approve |
| Approve a build before it starts | **Blueprint** | Annotated component sheet with the change highlighted | Intent, blueprint, gates, risks, acceptance checks | Plans and proposals that need sign-off | Nothing will be built |
| Follow a process or journey | **Transit map** | Route with numbered stops; the layout follows the route | Start, stops in order, where it can fail, end state | Workflows, customer journeys, rollouts, runbooks | Steps have no fixed order |
| Weigh evidence | **Evidence board** | Records linked by threads: solid = direct, dashed = circumstantial | Question, records, links, gaps, verdict | Investigations, root cause, audits of claims | Evidence is not in dispute |
| Explore options or scenarios | **Editorial atlas** | Options placed on two meaningful axes (for example effort and risk) | Map, regions, each option, trade-offs | Comparing several scenarios before narrowing | There are only two options |
| Make a decision between options | **Specimen sheet** | Options side by side in the same shape, with aligned details | Decision, options, costs, recommendation, choice control | Two to four options with a recommendation | The options are not comparable |
| Specify a system | **Engineering sheet** | Drafting-grid boundary diagram, with edges called out | Invariants, data contract, sequence, failure cases, not specified | APIs, data flows, contracts, state machines | The audience is not technical |
| Audit status or compliance | **Ledger** | Status table with pills and a visible total | Total, exceptions, full ledger, owners | Inventories, checklists, coverage reports | The reader needs reasoning, not status |

One artifact has one primary surface. A secondary section can borrow another surface's figure when its reader task differs (for example, a broadsheet with one engineering-sheet appendix).

## Shape legend

Use these meanings consistently across every figure in an artifact. Show the legend once, beside the first figure that uses it.

| Shape | Meaning |
|---|---|
| Cylinder | Persisted data store |
| Drawer or tray | Disposable or cached data |
| Pipe or parallel lines | Stream or queue |
| Diamond | Gate or decision point |
| Rounded pill | Actor or external system |
| Rectangle | Component or service |
| Solid line | Direct dependency or direct evidence |
| Dashed line or border | Circumstantial, unverified or proposed |
| Error-coloured arrow | The path where the risk sits |

## Honesty labels

Put the label on the figure, beside the claim it qualifies:

- `Hypothesis · not measured`: reasoning that has not been tested.
- `Proposed target`: a goal, not an observation.
- `Illustrative`: example values or a sequence drawn for explanation.
- `Evidence gap`: a link the argument needs but the evidence does not yet show.
- `Measured · <source>`: an observed value, with where it came from.

## Composition notes

- Derive tints with `color-mix(in oklab, var(--color-primary) 18%, transparent)` and similar mixes from the DaisyUI tokens, so tints follow light and dark themes.
- Place a full-width pause band (neutral background) at the decision, so the reader slows down where it matters.
- Avoid more than two consecutive sections with the same shape. Vary width, weight and figure type by explanatory purpose.
