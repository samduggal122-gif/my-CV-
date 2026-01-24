# AI Copilot Instructions - Samaira's Digital CV

## Project Overview
This is a personal digital CV website showcasing Samaira Duggal's profile as a BCA student with interests in tech and orthopedic surgery. The project consists of a single HTML file that combines introductory content with an interactive CSS-animated cute robot mascot.

## Architecture

### Structure
- **Single-file approach**: All content, styling, and animations in one `index.html` file
- **Semantic HTML sections**:
  - Header section: Introduction and personal tagline (lines 7-15)
  - Contact section: Links for Google and Gmail (lines 17-22)
  - Robot visualization: Interactive CSS-animated scene (lines 50-203)

### Key Components

#### 1. Content Section (Lines 7-22)
- Heading with cyan styling (`rgb(68, 187, 220)`)
- Bio text with personality and emojis
- Contact links (external Google link and mailto Gmail)
- Consistent color scheme: accent colors are `rgb(163, 8, 5)` (heading) and `rgb(199, 63, 92)` (labels)

#### 2. Robot Mascot (Lines 50-203)
The cute robot is a CSS-only animated component with:
- **Scene container** (.scene): 400x500px flexbox positioning
- **Visual layers**:
  - `.rays`: Pulsing radial gradient background (cyan theme, 4s animation)
  - `.head`: 200x160px with 40px border-radius, contains the screen/face
  - `.screen`: 150x100px dark display area with emojis/eyes
  - `.body`: 140x120px white rounded container
  - `.arm.left/right`: 40x100px rotated limbs (z-index: 0 for depth)
  - `.eye/.blush/.mouth`: Facial expression elements with cyan glow effects

## Styling Patterns

### Color Scheme
- **Primary background**: `#0a1a2a` (dark navy)
- **Accent cyan**: `#6fffe9` (eyes, mouth, glows)
- **Robot white**: `#f5f5f5`, `#ffffff`, `#f0f0f0`
- **Text colors**: Vary by section (red `rgb(163, 8, 5)`, pink `rgb(199, 63, 92)`, cyan)

### Animation Patterns
- **Pulse**: `.rays` element uses `radial-gradient` with opacity/scale animation (reusable for emphasis)
- **Float**: Defined keyframes but currently unused - can be applied to robot for hovering effect
- **Box shadows**: Multi-layer shadows for depth (e.g., `0 20px 40px rgba(0,0,0,0.4)` for head)

### Typography
- Font families vary by context: `algerian` (main heading), `Arial rounded mt bold` (body text)
- Inline `style` attributes for text formatting (colors, text-align, font-family)

## Development Patterns

### HTML Structure Notes
- `<head>` tag appears after `<body>` content (non-standard but works) - consolidate styles if refactoring
- Missing `<!DOCTYPE>` closing tag isn't critical
- Semantic heading hierarchy could be improved (uses `<h3>` for body content)

### CSS Best Practices Observed
- Flexbox for layout (body, scene container)
- Border-radius for rounded corners (head: 40px, body: 35px, screen: 25px)
- CSS custom properties not used - consider adding for color/dimension reuse
- Z-index layering for depth effects (scene elements)

## Responsive Design Strategy

The current layout is desktop-optimized with fixed dimensions. For mobile support:

### Media Query Breakpoints
Add to the `<style>` block:
```css
/* Tablets: 768px and below */
@media (max-width: 768px) {
  body {
    padding-left: 20px;
    justify-content: center;
  }
  
  .scene {
    width: 300px;
    height: 375px;
  }
  
  .robot {
    width: 150px;
  }
  
  .head {
    width: 150px;
    height: 120px;
  }
  
  .screen {
    width: 112px;
    height: 75px;
  }
  
  .body {
    width: 105px;
    height: 90px;
  }
}

/* Mobile: 480px and below */
@media (max-width: 480px) {
  body {
    padding-left: 10px;
    height: auto;
    min-height: 100vh;
  }
  
  .scene {
    width: 200px;
    height: 250px;
  }
  
  h1, h3 {
    font-size: 14px;
  }
}
```

### Content Responsiveness
- Keep text sections flexible with `max-width: 90%`
- Use viewport meta tag (add to `<head>`): `<meta name="viewport" content="width=device-width, initial-scale=1.0">`

## Version Control & GitHub Pages Deployment

### Repository Setup
- **GitHub Pages source**: Set repository settings to deploy from `main` or `gh-pages` branch
- **Repository name**: If using user/org site, name is `<username>.github.io`; personal projects use any name and enable Pages in Settings
- **Recommended folder structure** (if expanding):
  ```
  my-CV/
  ├── index.html (main entry point)
  ├── .github/
  │   └── copilot-instructions.md
  ├── assets/ (future: images, additional stylesheets)
  └── README.md (project info)
  ```

### Deployment Workflow
1. **Local development**: Edit `index.html` directly, open in browser to preview
2. **Commit and push**:
   ```bash
   git add index.html
   git commit -m "Update CV section or robot styling"
   git push origin main
   ```
3. **GitHub Pages auto-deployment**: Changes appear at `https://<username>.github.io/my-CV/` within 1-2 minutes
4. **Custom domain** (optional): Add `CNAME` file to repo root with domain name, configure DNS settings

### Version Control Best Practices
- **Commit messages**: Be specific about changes ("Add responsive design for mobile" vs "Update")
- **Testing before push**: Open `index.html` locally and test on multiple devices/browsers
- **.gitignore**: Not needed for single HTML file, but add if storing build artifacts
- **README.md**: Create with project description, links to live site, and contribution notes

## When Modifying This Project

1. **Adding new sections**: Follow the color scheme and maintain inline styles for consistency
2. **Updating robot styling**: Remember the `z-index` layering: rays (-), head (2), body (1), arms (0)
3. **Animations**: Keyframes are CSS-based; add to `<style>` block and reference in class definitions
4. **Contact links**: Update both `href` values and display text consistently
5. **Responsive updates**: Test media query changes on actual devices; use browser DevTools to simulate

## Quick Reference
- **Main content file**: `index.html`
- **Key CSS classes**: `.scene`, `.robot`, `.head`, `.screen`, `.body`, `.arm`, `.eye`, `.blush`, `.mouth`, `.rays`
- **Animation reference**: `@keyframes pulse` (4s), `@keyframes float` (unused)
- **Primary interaction**: External links (Google, Gmail)
