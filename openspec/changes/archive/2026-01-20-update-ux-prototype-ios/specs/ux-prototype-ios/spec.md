## ADDED Requirements
### Requirement: Canvas Grid
The canvas SHALL display a light, faint grid background to aid in visual alignment, similar to professional design tools (e.g., Figma).

#### Scenario: Visual Grid
- **WHEN** the prototype is rendered
- **THEN** the background shows a subtle grid pattern (e.g., 20px squares)
- **AND** the grid remains visible while panning/zooming

### Requirement: Storyboard Verification
The system SHALL NOT generate the prototype immediately. It must first present a text-based storyboard or scene breakdown and wait for user confirmation.

#### Scenario: Verify then Generate
- **GIVEN** the user asks for "A fitness app"
- **WHEN** the agent understands the intent
- **THEN** it outputs a "Storyboard Plan" listing the screens and flow
- **AND** asks "Shall I proceed?"
- **WHEN** the user says "Yes"
- **THEN** the agent generates the HTML prototype

## MODIFIED Requirements
### Requirement: Generate High-Fidelity iOS HTML Prototype
The system SHALL provide a skill that generates high-fidelity iOS-style HTML/CSS/JS prototypes, optionally using generated images for assets.

#### Scenario: Interactive Login with Images
- **WHEN** the user requests a "Login screen with a hero image"
- **THEN** the agent generates HTML with an `<img>` tag pointing to a generated asset or placeholder
- **AND** the rest of the UI follows iOS HIG

### Requirement: Visual Flow
The system SHALL represent visual flows using annotated Bezier curves.

#### Scenario: Login Flow with Annotations
- **WHEN** the user asks to see the flow from Login to Dashboard
- **THEN** connection lines are drawn as smooth Bezier curves (not straight lines)
- **AND** each line has a label explaining the trigger (e.g., "Tap 'Log In'")
