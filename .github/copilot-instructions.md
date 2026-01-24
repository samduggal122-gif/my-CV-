# Copilot Instructions - Samaira's Digital CV

## Project Architecture

This is a **single-file HTML portfolio** with no build system or dependencies. The `index.html` contains:
- **Content section** (lines 7-22): Bio intro, personality, contact links (Google, Gmail)
- **Robot mascot** (lines 50-203): CSS-only animated scene with layered depth effects

**Key insight**: All styling is inline in `<style>` block. The `<head>` tag appears mid-document (after body content) due to the HTML structure not being refactored.

## Essential Patterns

### Color System
Primary palette for maintaining visual consistency:
- Background: `#0a1a2a` (dark navy)
- Accent cyan: `#6fffe9` (used for eyes, mouth, glows)
- Text: `rgb(163, 8, 5)` (heading red), `rgb(199, 63, 92)` (label pink), `rgb(68, 187, 220)` (cyan text)

When adding content, stick to this palette. Colors are hardcoded (no CSS variables), so search-and-replace is needed for global changes.

### Robot Component Structure
CSS layering with explicit `z-index` values:
- `.rays` (pulsing radial gradient): `inset: -20%`
- `.head` (200×160px): `z-index: 2`
- `.body` (140×120px): `z-index: 1`
- `.arm.left/right`: `z-index: 0` (behind body)

Animation reference: `@keyframes pulse` (4s infinite) on `.rays`; `@keyframes float` is defined but unused (good candidate for adding hover effects).

### Styling Conventions
- **Flexbox for layout**: Applied to `body` (justify-content: flex-start) and `.scene` container
- **Border-radius for softness**: Head (40px), body (35px), screen (25px) - consistent roundness proportional to element size
- **Box-shadow for depth**: Multi-layer shadows like `0 20px 40px rgba(0,0,0,0.4)` on head
- **Font families**: `algerian` (main h1), `Arial rounded mt bold` (body), `sans-serif` (default fallback)
- **Inline styles only**: All formatting uses `style=""` attributes; no separate stylesheet

## Modification Guidelines

### Adding new content sections
1. Add HTML after existing intro (before the robot)
2. Apply color scheme from above: use `rgb(163, 8, 5)` for accents, `rgb(68, 187, 220)` for cyan text
3. Keep structure: `<h3><p style="...">` pattern for consistency

### Updating robot styling
- Always check `z-index` layering if repositioning elements
- Animation names: `pulse`, `float` - reuse or add new keyframes in `<style>` block
- Scale proportions: Head is 200px base; arms/body/screen scale down proportionally

### Testing workflow
1. Edit `index.html` directly in editor
2. Open in browser to preview (no build step)
3. Test on desktop (current layout), then use DevTools responsive mode for tablet/mobile breakpoints
4. Push to repo → GitHub Pages auto-deploys to `https://<username>.github.io/my-CV/` (1-2 min latency)

## Current Limitations & Technical Debt

- **HTML structure issue**: `<head>` appears after `<body>` content. Should consolidate styles before refactoring.
- **No responsive design**: Fixed dimensions on `.scene` and robot elements. If adding mobile support, use media queries for breakpoints at 768px (tablets) and 480px (mobile).
- **No viewport meta tag**: Add `<meta name="viewport" content="width=device-width, initial-scale=1.0">` to `<head>` if redesigning.
- **Font family fallbacks**: Using deprecated font names (`algerian`, `Arial rounded mt bold`); consider system fonts for reliability.

## Quick Reference

| Item | Location | Purpose |
|------|----------|---------|
| Main entry | `index.html` | All content and styling |
| Config | `.github/copilot-instructions.md` | This file |
| Key classes | `.scene`, `.robot`, `.head`, `.body`, `.arm`, `.rays` | CSS selectors for styling |
| Contact links | Lines 17-22 | Google & Gmail anchors |
| Color palette | Inside `<style>` block | Global color references |
