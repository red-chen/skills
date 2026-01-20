---
name: iOS UX Prototype Design
description: Generate high-fidelity iOS HTML/CSS/JS prototypes with interactive canvas and visual flows.
---

# iOS UX Prototype Design

This skill enables you to generate high-fidelity iOS-style HTML prototypes. The output is wrapped in an interactive canvas that supports panning and zooming.

## Instructions

### 1. Understanding the Request
- Analyze the user's description (e.g., "login screen", "dashboard flow").
- **Strict Adherence**: Follow Apple's Human Interface Guidelines (HIG).
- **Fonts**: Use system fonts (San Francisco simulation via `-apple-system`).
- **Components**: Use iOS standard components (Tab Bars, Navigation Bars, Large Titles, Rounded corners 12px-20px).
- **Aesthetic**: Clean, white/light-gray backgrounds (or systematic Dark Mode), vibrant accent colors, blurred backdrops (`backdrop-filter: blur()`).
- **Images**: You MAY use the `generate_image` tool to create assets if needed (e.g., hero images, avatars).
- If the user asks for a flow, plan for multiple screens connected visually.

### 2. Storyboard Verification (CRITICAL)
- **Do NOT generate the prototype immediately.**
- First, present a text-based "Storyboard Plan" describing the screens and the flow.
- Ask the user: "Shall I proceed with this plan?"
- **Wait for user confirmation** before generating any HTML code.

### 3. Generating the Prototype
- **Efficiency**: To minimize output size, follow these rules:
    - **External Styles**: ALWAYS use `ios-base.css` for common iOS styles (Status Bar, Buttons, Cards, Home Indicator).
    - **JS Helpers**: Use the built-in `injectCommonUI()` in the boilerplate to automatically add Status Bars and Home Indicators to your `.screen` divs.
    - **Batching**: For complex prototypes (10+ screens), generate the core flow first, then use `multi_replace_file_content` to add additional screens/vectors in subsequent steps.
- **Base Code**: READ `resources/canvas-boilerplate.html` to understand the structure.
    - **Injection**:
    - Wrap your generated UI in a `<div class="screen" id="screen-1" style="...">`.
    - Place it inside the `#canvas-content` div of the boilerplate.
    - **Screen Title**: You MUST add a `<div class="screen-title">Scene Name</div>` immediately before each `.screen` div to label the scenario.
    - Use absolute positioning (`top`, `left`) to place screens on the canvas.
    - **Spacing**: Ensure screens are spaced far apart for clarity (recommend at least **500px-800px** horizontal gap between screens).
    - **Branching Layout (CRITICAL)**: Do NOT simply place screens in a single linear row.
        - Analyze the flow: If a screen has multiple distinct actions leading to different outcomes, branch the layout vertically.
        - Example: If "Home" leads to "Settings" and "Profile", place "Home" as the root, "Settings" in one row (e.g., top), and "Profile" in another row (e.g., bottom).
        - Map the X/Y coordinates to the logical user journey.
    - Example:
      ```html
      <div class="screen-title">Login Screen</div>
      <div class="screen" style="left: 100px; top: 100px; width: 390px;">...</div>
      ```

### 4. Visual Flow (Connectors)
- To show flow between screens, add SVG lines inside `#canvas-content` but *behind* the screens (z-index).
- Generate a `<svg style="position:absolute; top:0; left:0; width:100%; height:100%; pointer-events:none;">` container.
- **Bezier Flows (MANDATORY)**: Never use straight lines. Use cubic Bezier curves in "Figma blue" (`#007AFF`) with text annotations on the curve. 
    - **Style**: Use dashed lines (`stroke-dasharray="8,8"`) for all flow connections to distinguish them from UI elements.
    - **Layering**: Ensure flow lines are rendered **BEHIND** the screens (lower z-index) so they never obstruct UI elements.
- **Syntax**: `<path d="..." stroke="#007AFF" stroke-width="3" stroke-dasharray="8,8" fill="none" marker-end="url(#arrow)" />`
- **Annotations**: You MUST add a text label on the curve explaining the action.
- Ensure you define the `<marker id="arrow" ...>` in `<defs>`.

### 5. Interactive Canvas
- The boilerplate handles Pan/Zoom.
- **IMPORTANT**: Do not reimplement pan/zoom logic. Just output the boilerplate code with your content injected.

### 6. Examples

#### Example Request: "Login flow to Home"
**Output Structure**:
```html
<!DOCTYPE html>
<html>
<head>...boilerplate styles...</head>
<body>
<div id="canvas-container">
    <div id="canvas-content">
        <!-- SVG Connections Layer -->
        <svg style="...">...</svg>

        <!-- Screen 1: Login -->
        <div class="screen" style="left:100px; top:100px; width:300px;">
           <!-- Login Form HTML -->
        </div>

        <!-- Screen 2: Home -->
        <div class="screen" style="left:500px; top:100px; width:300px;">
           <!-- Home Dashboard HTML -->
        </div>
    </div>
</div>
...boilerplate scripts...
</body>
</html>
```

### 7. Explaining UX Decisions
- Before or after generating the code, briefly explain your design choices:
    - Why you chose this layout?
    - How color handles focus?
    - Why elements are positioned this way for usability?

### 8. Performance & Scalability Optimization
- **Rule of Thumb**: Keep single tool output under 500 lines of HTML.
- **Shared Assets**: Reference shared resources in `resources/` instead of inlining large SVG or CSS blocks.
- **Incremental Growth**: Avoid "Big Bang" generation for large storyboards. Build, Verify, Extend.
- **Canvas Layout**: Use generous white space between screens (600px+ horizontally) to accommodate long flow labels and curved paths without overlap.
