# DispatchIQ Design System

## Design Prompt Template

Use this template to recreate this design language in future web applications. Simply replace the brand-specific values in brackets with your new project's details.

---

## 🎨 Design Specification Prompt

```
Create a modern, professional web application design with the following specifications:

### Brand Colors (60-30-10 Rule)

**Primary Brand Colors:**
- Primary: [#0048bb] (Sears Blue)
- Primary Dark: [#003a99]
- Primary Light: [#1a5ed4]
- Accent: [#66ff99] (Sears Green)
- Accent Dark: [#4de080]

**Color Distribution (60-30-10 Rule):**
- 60% Dominant: White (#ffffff) and light grays (#fafafa, #f5f5f5, #eeeeee) - Used for main backgrounds, cards, and content areas
- 30% Secondary: Primary brand color - Used for headers, buttons, links, and major UI elements
- 10% Accent: Accent color - Used strategically for CTAs, highlights, underlines, and success states

**Supporting Colors:**
- Text Primary: #212121
- Text Secondary: #757575
- Text Light: #9e9e9e

### Typography

**Font Families:**
- Headings: 'IBM Plex Mono', monospace (technical, modern feel)
- Body: 'Outfit', -apple-system, sans-serif (clean, readable)
- Code/Labels: 'IBM Plex Mono', monospace

**Font Loading:**
```html
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500;600;700&family=Outfit:wght@400;500;600;700&display=swap" rel="stylesheet">
```

### Brand Logo (Required)

**Sears Home Services Logo:**
- URL: `https://www.searshomeservices.com/static/icons/general/shs-logo.svg`
- Location: Header, left side before H1
- Height: 50px
- Filter: `brightness(0) invert(1)` (makes logo white on colored backgrounds)
- Error handling: `onerror="this.style.display='none'"` (hides if logo fails to load)

**HTML Structure:**
```html
<header>
    <div class="header-content">
        <div class="logo-container">
            <img src="https://www.searshomeservices.com/static/icons/general/shs-logo.svg"
                 alt="Sears Home Services"
                 onerror="this.style.display='none'">
        </div>
        <h1>Your App Name</h1>
    </div>
    <p>Your tagline</p>
</header>
```

**CSS:**
```css
.header-content {
    display: flex;
    align-items: center;
    gap: 20px;
    margin-bottom: 10px;
}

.logo-container {
    display: flex;
    align-items: center;
    animation: fadeInUp 0.8s cubic-bezier(0.4, 0, 0.2, 1) 0.1s backwards;
}

.logo-container img {
    height: 50px;
    width: auto;
    filter: brightness(0) invert(1);
}
```

**Typography Rules:**
- Avoid generic fonts: Inter, Roboto, Arial, Space Grotesk, system fonts
- Headings: Bold (700), tight letter-spacing (-0.5px to -1px)
- Labels: Uppercase, small size (0.85-0.95em), letter-spacing (0.5px), weight 600-700
- Body: Regular weight (400), medium line-height (1.6)

### Layout & Spacing

**Container:**
- Max-width: 1400px
- Padding: 20px
- Centered with auto margins

**Border Radius:**
- Cards: 12-16px (modern, friendly)
- Buttons: 8-10px
- Inputs: 8px
- Small elements (badges): 20px (pill-shaped)

**Shadows:**
- Subtle: `0 1px 3px rgba(0, 72, 187, 0.08), 0 4px 12px rgba(0, 72, 187, 0.05)`
- Hover: `0 8px 24px rgba(0, 72, 187, 0.12), 0 16px 48px rgba(0, 72, 187, 0.08)`
- Elevated: `0 12px 32px rgba(0, 72, 187, 0.15)`

**Grid System:**
- Use CSS Grid with: `grid-template-columns: repeat(auto-fit, minmax(220px, 1fr))`
- Gap: 20px

### Animation Principles

**Timing Function:**
- Primary: `cubic-bezier(0.4, 0, 0.2, 1)` (Material Design easing)

**Page Load Animation (Staggered Reveals):**
1. Header: slideDown from -100%, 0.6s duration
2. H1: fadeInUp, 0.8s duration, 0.2s delay
3. Subtitle: fadeInUp, 0.8s duration, 0.4s delay
4. Nav links: fadeInUp, 0.8s duration, 0.6s delay
5. Main card: fadeInUp, 0.8s duration, 0.8s delay
6. Results: slideInRight, 0.5s duration, staggered 0.1s per item

**Keyframe Animations:**
```css
@keyframes slideDown {
    from { transform: translateY(-100%); opacity: 0; }
    to { transform: translateY(0); opacity: 1; }
}

@keyframes fadeInUp {
    from { transform: translateY(30px); opacity: 0; }
    to { transform: translateY(0); opacity: 1; }
}

@keyframes slideInRight {
    from { transform: translateX(-30px); opacity: 0; }
    to { transform: translateX(0); opacity: 1; }
}

@keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.5; }
}
```

**Hover Effects:**
- Buttons: Ripple effect (expanding circle), translateY(-2px), enhanced shadow
- Cards: translateX(8px), border-left color change, enhanced shadow
- Links: Color change, translateY(-2px), glow shadow
- Transition duration: 0.3s

**Micro-interactions:**
- Focus states: 4px colored ring (box-shadow: 0 0 0 4px rgba(primary, 0.1))
- Loading states: Pulse animation (1.5s infinite)
- Success states: Slide-in or fade-in with green accent

### Component Patterns

**Header:**
- Background: Primary brand color
- Text: White
- Padding: 40px 30px
- Box-shadow with brand color tint
- **Logo + H1 in flex container with gap** (REQUIRED: https://www.searshomeservices.com/static/icons/general/shs-logo.svg)
  - Logo height: 50px
  - Logo filter: brightness(0) invert(1) to make white
  - Flex gap: 20px
  - Logo container with fadeInUp animation (0.1s delay)
  - H1 with fadeInUp animation (0.2s delay)
- Accent underline on H1 (4px height, accent color)
- Subtle animated gradient overlay (optional)

**Cards:**
- Background: White
- Border: 1px solid gray-200
- Border-radius: 12-16px
- Padding: 30-35px
- Box-shadow: Subtle elevation
- Hover: Lift effect (translateY(-4px)) with enhanced shadow
- Left border accent: 4-5px solid primary color (for list items)

**Buttons (Primary):**
- Background: Primary color gradient (optional: 135deg gradient)
- Color: White
- Padding: 14-16px 40px
- Border-radius: 8-10px
- Font-weight: 700
- Hover: Darken, translateY(-2px), enhanced shadow
- Ripple effect on hover (expanding white circle)

**Buttons (Secondary/Accent):**
- Background: Accent color gradient
- Color: Primary dark
- Same dimensions as primary
- Glow shadow on hover with accent color

**Form Inputs:**
- Background: Light gray (#fafafa)
- Border: 2px solid gray-200
- Border-radius: 8px
- Padding: 14-16px
- Transition: all 0.3s
- Focus: Border to primary color, background to white, 4px ring glow

**Badges/Pills:**
- Padding: 8px 16px
- Border-radius: 20px
- Font-size: 0.85em
- Font-weight: 600
- Text-transform: uppercase
- Letter-spacing: 0.5px
- Status colors:
  - Success/Carried: Accent color background, dark text
  - Warning/Warehouse: #ffd54f background, #f57c00 text
  - Missing/Inactive: Gray-200 background, secondary text

**Data Display Cards:**
- Background: Light gray (#f5f5f5 or #fafafa)
- Border-left: 3px solid gray-200
- Padding: 15px
- Border-radius: 8px
- Hover: Border-left to accent color, background to white, subtle shadow

### Background & Atmosphere

**Body Background:**
- Primary: White
- Subtle texture overlay (optional):
  ```css
  body::before {
      content: '';
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background-image:
          radial-gradient(circle at 20% 50%, rgba(primary, 0.03) 0%, transparent 50%),
          radial-gradient(circle at 80% 80%, rgba(accent, 0.03) 0%, transparent 50%);
      pointer-events: none;
      z-index: 0;
  }
  ```

**Header Background Effects:**
- Animated floating gradient:
  ```css
  header::before {
      content: '';
      position: absolute;
      width: 60%;
      height: 200%;
      background: radial-gradient(ellipse, rgba(accent, 0.15) 0%, transparent 70%);
      animation: float 6s ease-in-out infinite;
  }

  @keyframes float {
      0%, 100% { transform: translate(0, 0) rotate(0deg); }
      50% { transform: translate(-30px, 30px) rotate(5deg); }
  }
  ```

### Design Philosophy

**Avoid These Common Pitfalls:**
- ❌ Purple gradients on white backgrounds
- ❌ Generic fonts (Inter, Roboto, Arial)
- ❌ Overly rounded corners everywhere (>20px on large elements)
- ❌ Cookie-cutter layouts
- ❌ Evenly-distributed color palettes (use 60-30-10 rule)
- ❌ Scattered micro-interactions without orchestration

**Follow These Principles:**
- ✅ Commit to a cohesive aesthetic with clear hierarchy
- ✅ Use distinctive, beautiful typography
- ✅ Create atmosphere with layered backgrounds and subtle textures
- ✅ Orchestrate animations (page load with staggered reveals)
- ✅ High-impact moments over scattered animations
- ✅ Dominant colors with sharp, strategic accents
- ✅ Context-specific design that matches the domain

### Responsive Design

**Breakpoints:**
- Mobile: max-width 768px
  - Stack header elements vertically
  - Single column grids
  - Reduce font sizes (H1: 2em)
  - Adjust padding/margins

- Tablet: max-width 1024px
  - Adjust sidebar widths
  - 2-column grids

**Mobile-First Approach:**
- Use `@media (max-width: 768px)` for mobile overrides
- Ensure touch targets are at least 44px × 44px
- Test animations on mobile (reduce motion if needed)

### Accessibility

- Color contrast: WCAG AA minimum (4.5:1 for text)
- Focus visible states on all interactive elements
- Semantic HTML (proper heading hierarchy)
- Alt text for images
- ARIA labels where appropriate
- Keyboard navigation support

### Code Structure

**CSS Variables:**
```css
:root {
    /* Brand Colors */
    --primary: #0048bb;
    --primary-dark: #003a99;
    --primary-light: #1a5ed4;
    --accent: #66ff99;
    --accent-dark: #4de080;

    /* Neutral Colors (60%) */
    --white: #ffffff;
    --gray-50: #fafafa;
    --gray-100: #f5f5f5;
    --gray-200: #eeeeee;

    /* Text Colors */
    --text-primary: #212121;
    --text-secondary: #757575;
    --text-light: #9e9e9e;
}
```

**Global Reset:**
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

**Body Styles:**
```css
body {
    font-family: 'Outfit', -apple-system, sans-serif;
    background: var(--white);
    color: var(--text-primary);
    line-height: 1.6;
    position: relative;
    overflow-x: hidden;
}
```
```

---

## 📝 Usage Instructions

### For New Projects:

1. **Copy this entire prompt section** (everything inside the code block above)

2. **Replace brand-specific values:**
   - Color hex codes with your brand colors
   - Font families with your chosen fonts
   - Logo URL with your logo
   - Company name references

3. **Provide context about your application:**
   - Domain/industry (e.g., "field services", "e-commerce", "healthcare")
   - Target audience
   - Key user actions
   - Mood/feel desired (professional, playful, technical, etc.)

4. **Submit to AI with instructions:**
   ```
   Using the design specification above, create a [your-app-name]
   web application with the following features:
   [list your features]

   Maintain the design system exactly as specified, including:
   - Typography choices
   - Animation patterns
   - Color distribution (60-30-10 rule)
   - Component styling
   ```

### Customization Guidelines:

**Conservative Changes (Recommended):**
- Update color palette to match brand
- Adjust animation timing (but keep easing functions)
- Modify border-radius slightly (±2-4px)
- Change font families (but keep mono + sans-serif pairing)

**Moderate Changes:**
- Adjust shadow intensities
- Modify spacing scale
- Change animation choreography
- Alter background effects

**Advanced Changes:**
- Complete typography system redesign
- Different animation philosophy
- Alternative layout patterns
- Custom component patterns

## 🎯 Design Decision Rationale

### Why This Works

1. **60-30-10 Rule**: Creates visual balance and hierarchy
   - Dominant white prevents visual fatigue
   - 30% brand color establishes identity
   - 10% accent creates excitement without overwhelming

2. **Typography Pairing**: Mono + Sans-Serif
   - Mono (IBM Plex Mono): Technical, precise, distinctive for headings/labels
   - Sans-serif (Outfit): Approachable, readable for body text
   - Avoids generic system fonts for personality

3. **Staggered Animations**:
   - Creates professional "page orchestration"
   - Delays guide eye through content hierarchy
   - Single impactful moment > scattered micro-interactions

4. **Gradient Effects**:
   - Adds depth without visual clutter
   - Subtle movement creates life
   - Maintains professional appearance

5. **Border-Left Accents**:
   - Provides visual hierarchy in lists
   - Easy to animate (color change on hover)
   - Clean, modern aesthetic

## 🔄 Alternative Variations

### Dark Mode Adaptation:
```css
/* Invert the 60-30-10 distribution */
--bg-primary: #121212;  /* 60% - Dark */
--bg-secondary: #1e1e1e;
--card-bg: #252525;
--primary: #your-light-primary;  /* 30% */
--accent: #your-accent;  /* 10% */
```

### Playful Variation:
- Increase border-radius (16-24px)
- Add illustration accents
- More animated elements
- Brighter accent colors
- Rounded fonts (replace IBM Plex Mono with rounded alternative)

### Corporate/Enterprise Variation:
- Reduce animations (shorter durations, fewer elements)
- Darker, muted color palette
- Wider letter-spacing
- Larger font sizes for readability
- More whitespace

### Technical/Developer Tools Variation:
- Monospace everywhere
- Darker backgrounds with code editor aesthetic
- Terminal-inspired color scheme
- Sharp corners (border-radius: 0-4px)
- Syntax highlighting patterns

## 📚 Reference Implementation

This design was originally created for **DispatchIQ**, a CLV-aware dispatch system for field operations, using:
- Sears Home Services brand colors (#0048bb blue, #66ff99 green)
- IBM Plex Mono + Outfit font pairing
- Staggered page load animations
- 60-30-10 color distribution
- Modern web standards (CSS Grid, CSS Custom Properties)

---

## 🚀 Quick Start Checklist

When implementing this design in a new project:

- [ ] Set up CSS custom properties with brand colors
- [ ] Import Google Fonts (IBM Plex Mono + Outfit)
- [ ] Create global reset and body styles
- [ ] Implement header with logo + staggered animations
- [ ] Build card component with hover effects
- [ ] Style buttons with ripple effects
- [ ] Create form inputs with focus states
- [ ] Add page load animation choreography
- [ ] Implement responsive breakpoints
- [ ] Test accessibility (contrast, focus states)
- [ ] Optimize for performance (font loading, animation performance)

---

**Last Updated**: November 2025
**Design System Version**: 1.0
**Compatible With**: Modern browsers (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
