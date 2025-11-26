---
name: Distinctive UI Design
description: This skill should be used when the user asks to "create a component", "design a page", "build UI", "make a landing page", or requests frontend design work. Provides guidance for generating distinctive, non-generic UI designs that avoid common AI aesthetic patterns.
version: 0.1.0
---

# Distinctive UI Design

## Purpose

Generate distinctive, production-grade frontend interfaces that avoid the "distributionally convergent" aesthetic typical of AI-generated designs. This skill addresses the tendency for AI to converge on safe, generic design choices (Inter font, purple gradients, white backgrounds) by providing concrete guidance across four key design domains: typography, color and theming, background effects, and animation.

## When to Use This Skill

Apply this skill when:
- Creating new UI components (buttons, cards, forms, etc.)
- Designing full pages (landing pages, dashboards, etc.)
- Building frontend applications from scratch
- Refactoring existing UI to be more distinctive
- The user explicitly requests creative or non-generic design

## Core Design Principles

### 1. Typography: Avoid Generic Fonts

**Goal**: Use distinctive, characterful typefaces instead of safe, boring defaults.

**Implementation approach**:
- **Primary heading fonts**: Select display fonts with personality (Playfair Display, Bricolage Grotesque, Space Grotesk, Crimson Pro)
- **Body text fonts**: Pair with complementary sans-serif or serif fonts
- **Font pairing**: Create contrast between headings and body (serif + sans-serif, or geometric + humanist)
- **Web font loading**: Use Google Fonts, Adobe Fonts, or self-hosted fonts
- **Fallbacks**: Always provide system font fallbacks

**Quick reference for font pairing**:
| Heading Font | Body Font | Style |
|-------------|-----------|-------|
| Playfair Display | Inter | Classic editorial |
| Bricolage Grotesque | System UI | Modern, technical |
| Space Grotesk | DM Sans | Geometric, futuristic |
| Crimson Pro | Open Sans | Traditional, readable |

See `references/typography.md` for complete font pairing guide and implementation examples.

#### Japanese Typography (日本語タイポグラフィ)

**Goal**: For Japanese content, select distinctive fonts that avoid generic defaults like default Gothic fonts.

**Japanese font categories**:

1. **Gothic (ゴシック体)** - Clean, uniform strokes:
   - **Distinctive options**: Zen Kaku Gothic New, M PLUS Rounded 1c, Kosugi Maru
   - **Avoid**: Default system Gothic (Yu Gothic without customization)
   - **Use for**: Modern, clean interfaces, technical content

2. **Mincho (明朝体)** - Elegant serif style:
   - **Distinctive options**: Shippori Mincho, Zen Old Mincho, Noto Serif JP
   - **Use for**: Editorial content, traditional aesthetics, formal contexts
   - **Pairing**: Works well with Western serif fonts for bilingual designs

3. **Rounded Gothic (丸ゴシック体)** - Soft, approachable:
   - **Distinctive options**: Zen Maru Gothic, M PLUS Rounded 1c, Kosugi Maru
   - **Use for**: Friendly interfaces, children's content, casual designs
   - **Character**: Conveys warmth and accessibility

4. **Handwriting/Decorative** - Human, irregular:
   - **Distinctive options**: Kiwi Maru, RocknRoll One, Yusei Magic
   - **Use for**: Accent elements, titles, creative projects
   - **Impact**: Maximum distinctiveness, breaks AI aesthetic

**Google Fonts Japanese options** (free for commercial use):
- **Headings**: Shippori Mincho B1, Dela Gothic One, Yusei Magic, RocknRoll One
- **Body text**: Noto Sans JP, Zen Kaku Gothic New, M PLUS 1p, Kosugi
- **Rounded**: Zen Maru Gothic, M PLUS Rounded 1c, Kiwi Maru

**Japanese font pairing guide**:
| Heading (見出し) | Body (本文) | Style |
|-----------------|------------|-------|
| Shippori Mincho B1 | Noto Sans JP | Classic editorial |
| Dela Gothic One | Zen Kaku Gothic New | Bold, modern |
| Yusei Magic | M PLUS 1p | Playful, creative |
| Zen Old Mincho | Kosugi | Traditional, elegant |
| RocknRoll One | Zen Maru Gothic | Fun, distinctive |

**Implementation example**:
```html
<!-- Google Fonts for Japanese -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Shippori+Mincho+B1:wght@400;700;800&family=Noto+Sans+JP:wght@300;400;500;700&display=swap" rel="stylesheet">

<style>
  h1, h2, h3 { font-family: 'Shippori Mincho B1', serif; }
  body { font-family: 'Noto Sans JP', sans-serif; }
</style>
```

**Key considerations**:
- **File size**: Japanese fonts are larger; use `font-display: swap` and subset when possible
- **Fallbacks**: Always include system font fallbacks
- **Performance**: Consider variable fonts (Noto Sans JP supports variable weight)
- **Readability**: Ensure appropriate line-height (1.7-2.0 for Japanese is common)

**Bilingual design strategy**:
- Use language-specific font stacks with CSS `lang` attribute
- Pair Japanese and Western fonts thoughtfully (e.g., Mincho + Serif, Gothic + Sans-serif)
- Example:
```css
:root { font-family: 'Inter', sans-serif; }
:lang(ja) { font-family: 'Noto Sans JP', sans-serif; }
h1 { font-family: 'Playfair Display', serif; }
h1:lang(ja) { font-family: 'Shippori Mincho B1', serif; }
```

### 2. Color and Theming: Draw from Cultural and Technical Aesthetics

**Goal**: Create cohesive color palettes inspired by IDE themes, cultural movements, or natural phenomena rather than generic gradients.

**Inspiration sources**:
- **IDE themes**: Dracula, Nord, Tokyo Night, Catppuccin, Gruvbox
- **Cultural aesthetics**: Vaporwave, Brutalism, Swiss design, Japanese minimalism
- **Natural palettes**: Sunset, forest, ocean, desert
- **Era-specific**: 80s neon, 90s web, Y2K, mid-century modern

**Implementation approach**:
- Define 5-7 color palette: primary, secondary, accent, background, text, success/error
- Use CSS custom properties for theme switching capability
- Maintain WCAG AA contrast ratios for accessibility
- Consider dark mode alternatives from the start

**Example palette (Tokyo Night inspired)**:
```css
--bg-primary: #1a1b26;
--bg-secondary: #24283b;
--accent-blue: #7aa2f7;
--accent-purple: #bb9af7;
--text-primary: #c0caf5;
--text-muted: #565f89;
```

See `references/color-palettes.md` for curated palette collections and theming strategies.

### 3. Background Effects: Create Depth and Atmosphere

**Goal**: Replace flat, single-color backgrounds with layered gradients, patterns, or effects that add visual interest.

**Techniques**:
- **Layered gradients**: Stack multiple CSS gradients with blend modes
- **Mesh gradients**: Use tools like CSS mesh gradients or SVG
- **Noise textures**: Add subtle grain or noise overlays
- **Geometric patterns**: SVG patterns, grids, dots
- **Glassmorphism**: Frosted glass effects with backdrop-filter

**Implementation approach**:
```css
/* Layered gradient example */
background:
  linear-gradient(135deg, rgba(100, 50, 200, 0.1) 0%, transparent 50%),
  linear-gradient(45deg, rgba(50, 150, 250, 0.1) 0%, transparent 50%),
  #0a0a0f;
```

**Performance considerations**:
- Use CSS gradients over images when possible
- Optimize SVG patterns
- Test on lower-end devices

See `references/backgrounds.md` for advanced background techniques and code examples.

### 4. Animation: Focus on High-Impact Moments

**Goal**: Add meaningful motion at key interaction points rather than animating everything.

**High-impact moments**:
- **Page load**: Staggered fade-in, slide-up animations for content sections
- **User interactions**: Button hover states, card lifts, focus indicators
- **Transitions**: Page transitions, modal appearances, notifications
- **Micro-interactions**: Success confirmations, loading states

**Implementation approach**:
- Use CSS transitions for simple hover/focus states
- Use CSS animations or Framer Motion for complex sequences
- Respect `prefers-reduced-motion` for accessibility
- Keep animations under 300ms for responsiveness

**Animation timing functions**:
- `ease-out`: For entrances (elements coming into view)
- `ease-in`: For exits (elements leaving view)
- `ease-in-out`: For continuous motion
- Custom cubic-bezier: For branded motion personality

See `references/animation.md` for animation patterns and implementation details.

## Technology Stack Support

### React (Preferred)

**Component structure**:
```tsx
// Use TypeScript for type safety
interface ComponentProps {
  variant?: 'primary' | 'secondary';
  children: React.ReactNode;
}

// Use modern React patterns (hooks, functional components)
const Component: React.FC<ComponentProps> = ({ variant = 'primary', children }) => {
  return <div className={styles[variant]}>{children}</div>;
};
```

**Styling options**:
- **Tailwind CSS**: Utility-first, rapid development (preferred for this plugin)
- **CSS Modules**: Scoped styles, good for component libraries
- **Styled Components**: CSS-in-JS, dynamic styling

### Vue

**Component structure** (Vue 3 Composition API):
```vue
<script setup lang="ts">
interface Props {
  variant?: 'primary' | 'secondary';
}

const props = withDefaults(defineProps<Props>(), {
  variant: 'primary'
});
</script>

<template>
  <div :class="variant">
    <slot />
  </div>
</template>
```

### HTML/CSS/JavaScript

**Modern approach**:
- Use semantic HTML5 elements
- CSS custom properties for theming
- Modern JavaScript (ES6+, optional TypeScript)
- Web Components for reusability

## Accessibility Guidelines

Maintain basic accessibility while pursuing distinctive design:

**Essential practices**:
- **Color contrast**: WCAG AA minimum (4.5:1 for normal text, 3:1 for large text)
- **Semantic HTML**: Use proper heading hierarchy, landmarks, form labels
- **ARIA attributes**: Add when semantic HTML insufficient (aria-label, aria-describedby)
- **Keyboard navigation**: Ensure all interactive elements are keyboard accessible
- **Focus indicators**: Visible focus states for keyboard users

**Testing approach**:
- Use browser DevTools accessibility panel
- Test keyboard navigation manually
- Run automated checks (axe, Lighthouse)

Balance creativity with usability—distinctive design should enhance, not hinder, user experience.

## Workflow

When creating a component or page:

1. **Understand requirements**: Clarify component purpose, content, and interactions
2. **Select design direction**: Choose aesthetic inspiration (IDE theme, cultural movement, etc.)
3. **Define typography**: Pick font pairing from references or create custom
4. **Build color palette**: Create cohesive 5-7 color theme based on inspiration
5. **Design layout**: Structure with semantic HTML and responsive design
6. **Add background effects**: Layer gradients, patterns, or textures
7. **Implement animations**: Add motion at high-impact interaction points
8. **Verify accessibility**: Check contrast, keyboard nav, and semantic markup
9. **Test responsiveness**: Ensure works on mobile, tablet, desktop

## Additional Resources

### Reference Files

For detailed guidance and examples:
- **`references/typography.md`** - Complete font pairing guide, web font loading, best practices
- **`references/color-palettes.md`** - Curated palette collections, theming strategies, dark mode
- **`references/backgrounds.md`** - Advanced background techniques, gradients, patterns, performance
- **`references/animation.md`** - Animation patterns, timing, Framer Motion examples

### Example Files

Working component examples in `examples/`:
- **`examples/hero-section.tsx`** - React hero section with distinctive typography and background
- **`examples/card-component.tsx`** - Card with glassmorphism and hover animations
- **`examples/landing-page.html`** - Complete HTML landing page with all principles applied

### Assets

Design resources in `assets/`:
- **`assets/patterns/`** - SVG patterns for backgrounds
- **`assets/gradients/`** - Pre-built gradient combinations

## Common Pitfalls to Avoid

**Don't**:
- Default to Inter font without considering alternatives
- Use generic purple/blue gradients as primary design element
- Leave backgrounds flat white or single color
- Animate everything indiscriminately
- Sacrifice accessibility for aesthetics
- Copy designs exactly from examples (use as inspiration)

**Do**:
- Experiment with distinctive typography
- Create cohesive color stories with cultural/technical inspiration
- Layer background effects for depth
- Animate strategically at high-impact moments
- Maintain WCAG AA contrast minimums
- Adapt designs to specific project context

## Implementation Tips

**For Tailwind CSS projects**:
- Extend default theme with custom fonts and colors in `tailwind.config.js`
- Use arbitrary values for one-off distinctive effects: `bg-[#specific-color]`
- Leverage plugins: @tailwindcss/typography, @tailwindcss/forms

**For React projects**:
- Use Framer Motion for complex animations
- CSS Modules or styled-components for component-scoped styles
- Consider design systems (Radix UI, Headless UI) as base, customize heavily

**For Vue projects**:
- Use Composition API for cleaner component logic
- Scoped styles with CSS custom properties for theming
- Consider Nuxt UI or similar, but customize extensively

**General**:
- Start with mobile-first responsive design
- Test on actual devices, not just browser DevTools
- Use design tokens (CSS custom properties) for consistency
- Document color palette and font choices in project README

---

Apply these principles consistently to create frontend designs that stand out from generic AI aesthetics while maintaining professional quality and accessibility standards.
