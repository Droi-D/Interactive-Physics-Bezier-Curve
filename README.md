# Interactive Physics Bézier Curve

## Overview
This project simulates a dynamic cubic Bézier curve that behaves like a physical rope. It features a custom physics engine and vector math library built from scratch, without external dependencies.

## Implementation Details

### 1. Bézier Mathematics
The curve is rendered using the explicit cubic formula:
```
B(t) = (1−t)³P₀ + 3(1−t)²tP₁ + 3(1−t)t²P₂ + t³P₃
```

The curve is sampled at 100 intervals (step = 0.01) to ensure a smooth path at 60 FPS.

### 2. Physics Engine (Spring-Mass-Damper)
Instead of static positioning, the control points (P₁, P₂) utilize a custom spring physics model:

- **Hooke's Law:** `F = -k * (position - target)` provides the elastic "pull" toward the mouse.
- **Damping:** `F_damping = -d * velocity` simulates air resistance to prevent infinite oscillation.
- The system uses semi-implicit Euler integration for stability.

### 3. Tangent Visualization
Tangent vectors are calculated using the analytical derivative of the cubic Bézier function (B'(t)). The resulting vectors are normalized and rendered as red indicators along the curve to visualize flow direction.

### 4. Rendering & Architecture
- **No Libraries:** A custom Vec2 class handles all vector operations (addition, subtraction, normalization).
- **Performance:** The simulation runs on the main thread using requestAnimationFrame for synchronized rendering.
- **Visuals:** Implements HTML5 Canvas API with gradient strokes and shadow effects for a polished look.

## How to Run
- Open `index.html` in any modern web browser. No local server or build process is required.
- To preview the demo, open **`bezier_demo.mp4`** located in the repository.
