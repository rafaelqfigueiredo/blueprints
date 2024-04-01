# Use Blueprints
Introduce _blueprints_ (_aka_ decision records), a way to formalize and document important architectural decisions within the team. _Blueprints_ will provide a structured approach to capture, communicate and enforce architectural decisions, enabling developers to understand the rationale behind each decision, and define an architectural roadmap for our codebase.

## Status
Proposed

## Context
Discussing and documenting broader decisions only through Trello cards presents challenges. Ultimately, these decisions are typically discussed and approved during team meetings, only to fade into the Trello void over time, and erased from our memories.

This leads to ambiguity, misunderstandings, inconsistencies, and difficulty in tracking the rationale behind design choices (_eg_, "Why do we use service objects?", "Why is the project splitted by app?"). As our project scales and becomes more complex, it's crucial to establish a formalized system for capturing, communicating, and enforcing these decisions.

Without understanding the rationale behind a decision, a developer has only two choices when faced with a past decision:

1. **Blindly accept the decision**
This may not be good if the context has changed and the decision should really be revisited. If the project accumulates too many decisions accepted without understanding, then the development team becomes afraid to change anything and the tech debt keeps accumulating over time.

2. **Blindly change it**
Changing a decision without understanding its motivation or consequences could mean damaging the project's overall value without realizing it.

It's better to avoid either blindly accept or blindly reverse a decision.

- We want to think deeply about all our architectural decisions, exploring all alternatives and making a careful, considered, well-researched choice.
- We don't want to keep having the same technical discussions when the context hasn't changed.
- We want to be as transparent as possible in our decision-making process. Developers can review past and recent decisions taken, together with the rationale and circumstances that affected them at the time.
- We want to keep track of every decision (even if they are rejected) so we can steer our development practices.
- We don't want decisions to be made unilaterally based on personal preference. We want to give our steering group the opportunity to review every major decision.
- We want everyone to have a strong shared understanding of the technical rationale behind decisions.
- We want to prevent knowledge silos and rather promote knowledge sharing.
- We want to be able to revisit prior decisions to determine fairly if they still make sense, and if the motivating circumstances or conditions have changed.

## Proposal
A _blueprint_ is a document that captures an important decision made along with its context and consequences. The document you are reading is itself a _blueprint_!

### Workflow
1. A developer creates a PR with a _blueprint_, [using this template](../_template.md), outlining an approach for a particular question or problem. The _blueprint_ has an initial status of "proposed".
2. The developers discuss the _blueprint_. During this period, the _blueprint_ should be updated to reflect additional context, concerns raised, and proposed changes.
3. Once consensus is reached, the _blueprint_ can be transitioned to either an "accepted" or "rejected" state.
4. Only after a _blueprint_ is accepted should implementing code be committed (status "ongoing" or "implemented").
5. If a decision is revisited and a different conclusion is reached, a new _blueprint_ should be created documenting the context and rationale for the change. The new _blueprint_ should reference the old one, and once the new one is accepted, the old one should be updated to "deprecated" and point to the new one (_eg_, "Deprecated by `00x-blueprint-example`").

### Conventions
A new _blueprint_ must be stored under `docs/blueprints` in a specific folder with the following requirements:

- The folder name should have an ordered identifier (_eg_, `001`) to track the evolution of our decisions over time.
- The folder name should use present tense imperative verb phrases (_eg_, `choose-database`).
- The folder name should consist of lowercase characters and dashes.
- The folder must contain an `index.md` markdown file with the content of the _blueprint_.

### When to create a _blueprint_?
- When the proposed decision impacts development practices.
- When the proposed decision requires effort exploring solutions and more implementation time.
- When the proposed decision changes the current system in a significant way.
- When the proposed decision impacts the development lifecycle and deployments.

### When **NOT** to create a _blueprint_?
- When the proposed decision is about fixing a flicker test.
- When the proposed decision is about minor refactoring of code.
- When the proposed decision is about small performance improvements.
- When the proposed decision is about upgrading versions of dependencies.

### When to update an existing _blueprint_?
If there are new details that belong in the _blueprint_, create a PR to edit the existing _blueprint_. Once a _blueprint_ has become "implemented", major changes should get new _blueprints_.

## Consequences
- Developers must write a _blueprint_ and submit it for review before going for any decision that affects the way application is put together at a high level.
- We will have a concrete artifact around which to focus discussion, before finalizing decisions.
- If we follow the process, decisions will be made deliberately, as a group.
- The master branch of our repository will reflect the high-level consensus of the steering group.
- We will have a useful persistent record of why the system is the way it is.
