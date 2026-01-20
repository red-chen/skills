## Context
The user wants a skill to "give UI and UX on a canvas" based on input.

## Goals
- Goal: Enable the agent to generate visual iOS prototypes.
- Goal: Provide UX rationale alongside visuals.

## Decisions
## Decisions
- **Decision**: The skill will generate **High-Fidelity iOS HTML/CSS/JS** prototypes as the primary output.
- **Decision**: The output will be wrapped in an **Interactive Canvas** container that supports panning, zooming, and moving the view.
- **Decision**: The skill will support **Visual Flow** visualization to show connections.

## Risks
- **Risk**: Complex JS interactions (pan/zoom) might be buggy.
    - **Mitigation**: Create a robust, reusable HTML/JS boilerplate for the "Canvas" wrapper.
