# ux-prototype-ios Specification

## Purpose
TBD - created by archiving change add-ux-prototype-skill. Update Purpose after archive.
## Requirements
### Requirement: Generate High-Fidelity iOS HTML Prototype
The system SHALL provide a skill that generates high-fidelity iOS-style HTML/CSS/JS prototypes.

#### Scenario: Interactive Login
- **WHEN** the user requests a "High-fidelity login screen"
- **THEN** the agent generates a functional HTML file mimicking iOS design language (HIG)
- **AND** the buttons have correct tappable areas and the inputs use iOS styling

### Requirement: Interactive Canvas
The generated prototype SHALL be contained within an interactive canvas that supports panning, zooming, and moving.

#### Scenario: Zooming the Canvas
- **WHEN** the user interacts with the generated prototype container
- **THEN** they can zoom in/out and pan across the "infinite canvas" view

### Requirement: Visual Flow
The system SHALL be able to represent visual flows (connections) between different screens or UI elements.

#### Scenario: Login Flow
- **WHEN** the user asks to see the flow from Login to Dashboard
- **THEN** the prototype visualizes both screens with a visual connection (e.g., arrow or line) indicating the transition

### Requirement: UX Explanation
The system SHALL provide a rationale for User Experience decisions made during the prototype generation.

#### Scenario: Explain Layout
- **WHEN** a prototype is generated
- **THEN** the agent explains why certain elements were placed in specific positions (e.g., "Placed the CTA button at the bottom for thumb reachability")

