# Aave Liquid Glass Skill

## Skill Context

**Domain:** Advanced Frontend Engineering, UI Systems, Cross-Browser Graphics, Interaction Design, SVG Filters, Web Optics.

**Trigger this skill when users mention:**

* Liquid Glass
* Apple Liquid Glass
* Aave Glass
* Glass UI
* Physical Glassmorphism
* Refractive UI
* DOM Refraction
* Lens UI
* Interactive Glass
* Dynamic Glass Components

---

# Core Philosophy

## Glass Is A Lens

Liquid Glass is NOT traditional glassmorphism.

Traditional glass:

* backdrop blur
* translucent cards
* frosted overlays

Liquid Glass:

* bends live content
* behaves like a physical lens
* refracts underlying pixels
* contains moving highlights
* responds physically to interaction

Every glass surface should appear to manipulate light.

---

## Glass Exists To Enhance Interaction

Prefer glass on:

* slider thumbs
* switches
* toggle indicators
* floating actions
* navigation highlights
* media controls
* draggable elements
* QR interactions
* active tabs

Avoid:

* entire pages made from glass
* huge decorative glass cards
* fullscreen glass overlays

Rule:

Interactive glass > decorative glass.

---

## Depth Is Mandatory

Every implementation must establish:

1. Background layer
2. Content layer
3. Glass lens layer
4. Highlight layer
5. Shadow/refraction layer

Glass without depth is invalid.

---

# Architectural Decision Tree

Before implementation:

### Step 1

Determine the content beneath the lens.

If underlying content is:

* Standard DOM → use SVG pipeline.
* Video/WebGL/Canvas → use WebGL shader pipeline.

---

### Step 2

Determine browser engine.

* Chromium
* Safari/WebKit
* Firefox

Never assume Chromium behavior exists everywhere.

---

### Step 3

Determine accessibility preferences.

Check:

* prefers-reduced-transparency
* prefers-reduced-motion

Accessibility overrides aesthetics.

---

# Rendering Architecture

# DOM Pipeline (Default)

Use for:

* HTML
* React
* Next.js
* Forms
* Navigation
* Text-heavy interfaces

Pipeline:

```text
DOM
↓
duplicate backdrop
↓
counter-position duplicate
↓
SVG displacement filter
↓
glass highlights
↓
foreground UI overlay
```

---

# WebGL Pipeline

Use automatically when:

* refracting video
* refracting canvas
* refracting WebGL scenes
* Safari blocks SVG media rendering

Pipeline:

```text
media texture
↓
GLSL fragment shader
↓
displacement texture
↓
refraction shader
↓
foreground overlay
```

---

# Architectural Mandates

These rules are mandatory.

## 1. Refract A Copy, Not The Backdrop

NEVER rely on:

```css
backdrop-filter: url(#glass-filter);
```

Safari and Firefox silently fail.

Instead:

1. Duplicate background.
2. Counter-position duplicate.
3. Apply:

```css
filter: url(#glass-filter);
```

to duplicated content.

The real interface must remain untouched.

---

## 2. Foreground Must Remain Native

Interactive elements:

* buttons
* inputs
* text
* icons
* links

must exist above the filtered layer.

Example:

```text
glass copy layer
z-index: 1

interactive layer
z-index: 2
```

This preserves:

* pointer events
* selection
* accessibility
* focus management

---

## 3. Blob URL Delivery

Displacement maps MUST:

```text
Canvas
→ Blob
→ URL.createObjectURL()
→ feImage
```

Never use:

```text
data:image/png;base64
```

inside SVG feImage.

WebKit blocks this.

---

## 4. Dynamic Filter IDs

If:

* shape changes
* dimensions change
* layout changes

generate a new UUID:

```html
<filter id="uuid">
```

Safari aggressively caches SVG filters.

Changing the ID invalidates cache.

---

## 5. Source Clipping

Containers holding duplicated backdrops MUST use:

```css
overflow: hidden;
```

or

```css
contain: strict;
```

Never feed entire viewports into Safari SVG filters.

Clip to lens bounds.

---

## 6. sRGB Requirement

SVG filters must explicitly declare:

```html
color-interpolation-filters="sRGB"
```

This prevents browser gamma shifts.

---

# Mathematical Engine

The displacement map is generated using:

* Signed Distance Fields (SDF)
* Surface normals
* Snell's Law

---

## Lens Geometry

Model every lens as:

```text
convex squircle dome
```

Properties:

* flat center
* curved rim
* smooth corners
* continuous curvature

The center should remain visually stable.

Distortion increases toward edges.

---

## Channel Encoding

Displacement texture channels:

| Channel | Purpose         |
| ------- | --------------- |
| Red     | X displacement  |
| Green   | Y displacement  |
| Blue    | Specular height |
| Alpha   | Lens mask       |

Neutral:

```text
RGB(128,128,x)
```

means:

```text
no distortion
```

---

## Symmetry Optimization

Only compute optics for:

```text
top-left quadrant
```

Mirror results into:

* top-right
* bottom-left
* bottom-right

Invert displacement vectors accordingly.

Reduces compute cost by ~75%.

---

# SVG Filter Pipeline

Minimum structure:

```text
feImage
↓
feDisplacementMap
↓
feColorMatrix
↓
feComposite
↓
Output
```

---

# Optional Chromatic Aberration

For premium implementations:

1. Split source image.
2. Isolate RGB channels.
3. Apply slightly different displacement scales.
4. Blend channels.

Result:

subtle red/blue color fringing near lens edges.

Use sparingly.

---

# Motion Rules

Motion is essential.

Recommended durations:

```text
tap: 120ms
hover: 180ms
state changes: 250ms
travel transitions: 350ms
```

Preferred easing:

```css
cubic-bezier(0.22,1,0.36,1)
```

Avoid:

```css
ease
linear
```

---

# Physical Interaction Rules

Hover:

* increase brightness
* move highlights
* slight magnification

Tap:

* compress lens
* reduce shadow
* shift reflections

Drag:

* maintain inertia
* use spring dynamics
* animate highlights continuously

---

# Shared Lens Principle

Prefer:

```text
one moving lens
```

instead of:

```text
many independent lenses
```

Example:

Navigation bars should use a single traveling glass indicator.

---

# Browser-Specific Rules

## Chromium

Supports:

* full SVG pipeline
* chromatic aberration
* multi-pass filters

Use complete effects.

---

## Safari/WebKit

Limit complexity.

Prefer:

* single-pass displacement
* isolated highlights

Use:

* Blob URLs
* unique filter IDs
* clipped sources

Avoid:

* fullscreen displacement
* repeated map regeneration

---

## Firefox

Treat similarly to Safari.

Always test manually.

---

# Performance Budget

Glass is expensive.

Never:

* regenerate displacement maps every frame
* animate width/height continuously
* nest multiple backdrop filters
* filter entire viewports

Animate only:

```css
transform
opacity
```

Use:

```javascript
requestAnimationFrame()
```

for lens movement.

Regenerate maps ONLY when:

```text
width or height changes
```

Movement alone should update coordinates.

---

# React Architecture

Recommended pattern:

```text
GlassScene
    ↓
GlassLens
```

---

## GlassScene

Responsibilities:

* owns background reference
* shares backdrop through context
* prevents unnecessary re-renders

---

## GlassLens

Responsibilities:

* receives x/y/width/height
* generates displacement texture
* creates Blob URL
* renders duplicated backdrop
* applies SVG filter
* updates coordinates during movement

---

# Accessibility Rules

Always support:

```css
prefers-reduced-motion
prefers-reduced-transparency
```

---

## Reduced Transparency

Disable:

* canvas generation
* SVG filters
* optical effects

Fallback:

```css
background: rgba(var(--theme-bg),0.95);
```

---

## Reduced Motion

Disable:

* spring animations
* inertia
* lens travel

Use instant transitions.

---

## Contrast

Maintain WCAG AA minimum.

If readability suffers:

reduce transparency.

Text readability always wins.

---

# Component Guidelines

## Switches

Use:

* glass thumb
* refracted track
* spring motion

---

## Sliders

Use:

* lens handle
* distorted progress track
* dynamic highlights

---

## Toggle Groups

Use:

* single moving lens
* smooth interpolation

---

## Floating Action Buttons

Use:

* circular lens
* hover magnification
* soft shadow

---

## Navigation

Use glass for:

* active indicators
* floating docks
* selected states

Avoid fully glass navigation bars.

---

## Cards

Prefer:

solid cards with glass accents.

Avoid:

massive frosted panels.

---

# Forbidden Patterns

NEVER:

* use plain backdrop blur and call it Liquid Glass
* apply SVG filters directly to backdrop-filter
* distort foreground text
* place interactive elements inside filtered layers
* regenerate maps on pointer movement
* use React state for high-frequency drag updates
* use data URIs inside feImage
* filter full viewport copies in Safari
* overuse glass decoratively
* build entire pages from glass panels

---

# Final Validation Checklist

Before shipping verify:

* [ ] Glass behaves like a lens.
* [ ] Underlying content refracts.
* [ ] Depth is visible.
* [ ] Motion feels physical.
* [ ] Text remains readable.
* [ ] Accessibility preferences work.
* [ ] Safari renders correctly.
* [ ] Firefox renders correctly.
* [ ] Performance remains smooth.
* [ ] Interactive elements remain native.
* [ ] Glass enhances interaction rather than decoration.

If any answer is "No", revise implementation.
