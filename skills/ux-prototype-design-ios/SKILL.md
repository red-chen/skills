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
- If the user asks for a flow, plan for multiple screens connected visually.

### 2. Generating the Prototype
- **Primary Method**: Single HTML file generation.
- **Base Code**: READ `resources/canvas-boilerplate.html` to understand the structure.
- **Injection**:
    - Wrap your generated UI in a `<div class="screen" id="screen-1" style="...">`.
    - Place it inside the `#canvas-content` div of the boilerplate.
    - Use absolute positioning (`top`, `left`) to place screens on the canvas.
    - Example: `<div class="screen" style="left: 50px; top: 50px; width: 360px;">...</div>`

### 3. Visual Flow (Connectors)
- To show flow between screens, add SVG lines inside `#canvas-content` but *behind* the screens (z-index).
- Generate a `<svg style="position:absolute; top:0; left:0; width:100%; height:100%; pointer-events:none;">` container.
- Add `<path d="M x1 y1 C cp1x cp1y, cp2x cp2y, x2 y2" stroke="blue" fill="none" marker-end="url(#arrow)" />` to connect elements.
- Ensure you define the `<marker id="arrow" ...>` in `<defs>`.

### 4. Interactive Canvas
- The boilerplate handles Pan/Zoom.
- **IMPORTANT**: Do not reimplement pan/zoom logic. Just output the boilerplate code with your content injected.

### 5. Examples

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

### 5. Explaining UX Decisions
- Before or after generating the code, briefly explain your design choices:
    - Why you chose this layout?
    - How color handles focus?
    - Why elements are positioned this way for usability?
