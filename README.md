# Customer Intelligence Engine

**Customer Pulse 360 | Hackathon Challenge 4**

This repository holds a proposal for a real-time customer intelligence system on Microsoft Fabric. It joins customer history with live activity, groups accounts, scores churn risk, and sends retention alerts for human review.

**Status:** Proposal. The team has not selected a scenario.

## Review the proposal

- [Open the scenario page](site/index.html) for the challenge, candidate scenarios, and design.
- [Open the hosted review copy](https://efeeb7a1.ht-ml.app). The page requires a password.

The scenario page is the current source for the project. This repository does not contain a deployed Customer 360 service or production churn model.

## Candidate scenarios

Both companies are fictional. The team is reviewing two options:

- **HomeBridge** is a mortgage lender. The proposal identifies external refinancing risk before a fixed-rate deal ends. It routes payment difficulties to support before any commercial retention action.
- **HavenCover** is a home insurer. The proposal identifies non-renewal risk before a policy expires. It investigates claim and repair problems before any commercial action.

## Shared challenge

The challenge asks for four capabilities:

1. A real-time Customer 360 view that joins live activity with customer history.
2. Machine-learning customer segments.
3. A churn-risk model with drivers, aimed at a warning about 90 days before renewal.
4. A retention alert that responds to live events and reaches a person.

The scenario page maps these goals to Microsoft Fabric tools. The suggested tools are not mandatory components.

## Evidence limits

- A 90-day prediction horizon does not prove a 90-day early warning. Score the customer at a fixed point before renewal. Freeze the available information. Then evaluate the later renewal outcome.
- Feature attributions explain how model inputs affect a score. They do not prove the customer's true motivation or that an action will work.
- Synthetic results can show that a workflow works. They cannot prove improved retention. That claim needs evidence from real actions and a comparison group.

## Repository contents

- `site/index.html` — current scenario page and proposal.
- `docs/archive/previous-readme.md` — previous repository overview.
- `docs/archive/technical-blueprint.md` — earlier technical blueprint, retained for reference.

## Preview

Open `site/index.html` in a browser. The page loads styling from public CDNs. Connect to the network to see the full page design.
