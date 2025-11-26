---
description: Design a complete page with distinctive aesthetic
allowed-tools: ["Read", "Write", "Edit", "Bash"]
---

# Design Page

Design a complete, distinctive page (landing page, dashboard, etc.) using the distinctive-ui-design skill.

## Instructions

When this command is invoked:

1. **Load the distinctive-ui-design skill** to access design principles and patterns

2. **Gather requirements** by asking the user:
   - Page type:
     - Landing page (hero, features, CTA)
     - Dashboard (stats, charts, tables)
     - Portfolio (projects, about, contact)
     - Blog (articles, sidebar)
     - E-commerce (products, cart)
     - Custom (describe purpose)
   - Target framework:
     - React (TypeScript + Tailwind CSS)
     - Next.js (App Router + Tailwind CSS)
     - Vue (Composition API + Tailwind CSS)
     - HTML/CSS/JavaScript
   - Design direction (optional):
     - IDE theme inspiration (Tokyo Night, Dracula, Nord, etc.)
     - Cultural aesthetic (Vaporwave, Brutalism, Japanese Minimalism, etc.)
     - Natural palette (Ocean, Sunset, Forest, etc.)
     - Custom direction

3. **Plan the page structure**:
   - Identify key sections (hero, features, testimonials, CTA, etc.)
   - Determine layout strategy (grid, flexbox, sections)
   - Plan component hierarchy

4. **Design with distinctive principles**:
   - **Typography**:
     - Select distinctive heading font (avoid Inter/Arial)
     - Pair with complementary body font
     - Establish clear type scale and hierarchy
   - **Color Palette**:
     - Choose cohesive 5-7 color theme based on inspiration
     - Ensure WCAG AA contrast for accessibility
     - Consider dark mode if appropriate
   - **Backgrounds**:
     - Use layered gradients, mesh gradients, or patterns
     - Add depth with subtle textures or glassmorphism
     - Avoid flat single colors
   - **Animation**:
     - Page load stagger animations for content sections
     - Hover states for interactive elements
     - Scroll-triggered reveals for sections
     - Smooth transitions between states

5. **Generate the page file**:
   - Create complete, production-ready implementation
   - Include:
     - Semantic HTML structure
     - Responsive design (mobile-first)
     - Accessibility attributes
     - Performance optimizations (font loading, image optimization hints)
     - Clean, well-organized code with comments
   - For React/Vue: Create modular component structure if complex
   - For HTML: Single file with embedded styles and minimal JavaScript

6. **Provide setup instructions**:
   - Required dependencies (fonts, libraries)
   - How to run/build the page
   - Any configuration needed

7. **Document design decisions**:
   - Typography choices and rationale
   - Color palette with hex values
   - Design inspiration and aesthetic direction
   - Key interaction patterns used
   - Accessibility considerations

## Example Usage

```
/design-page
```

Claude will ask:
- "What type of page would you like to design?"
- "What framework are you using?"
- "Any design direction or inspiration?"

Then generate a complete, distinctive page implementation.

## Page Types Guide

### Landing Page
**Typical sections**: Hero, Features, How It Works, Testimonials, Pricing, CTA, Footer

**Design focus**:
- Hero: Bold typography, layered background, animated entrance
- Features: Card grid with glassmorphism or gradient borders
- CTA: High-contrast, prominent call-to-action

### Dashboard
**Typical sections**: Sidebar/Nav, Stats Cards, Charts, Data Tables, Notifications

**Design focus**:
- Color-coded stats with distinctive icons
- Data visualizations with cohesive palette
- Grid pattern or subtle background texture
- Card-based layout with hover states

### Portfolio
**Typical sections**: Hero/Intro, Projects Grid, About, Skills, Contact

**Design focus**:
- Large, distinctive typography for name/title
- Project cards with hover effects (zoom, tilt)
- Scroll-triggered animations for section reveals
- Personal brand colors throughout

### Blog
**Typical sections**: Header, Article Grid/List, Sidebar, Footer

**Design focus**:
- Readable typography (editorial font pairing)
- Clean article cards with hover states
- Tag/category system with color coding
- Featured articles with distinct styling

## Design Philosophy

When designing pages:

- **Cohesive aesthetic**: All sections should feel like part of the same design system
- **Visual hierarchy**: Clear distinction between primary and secondary content
- **Progressive disclosure**: Reveal information as user scrolls (don't overwhelm)
- **Performance-conscious**: Optimize images, fonts, animations
- **Accessible by default**: Semantic HTML, ARIA labels, keyboard navigation

## Reference Materials

Consult the distinctive-ui-design skill's references:
- **Typography**: `references/typography.md` for font pairings and implementation
- **Colors**: `references/color-palettes.md` for curated palettes by theme
- **Backgrounds**: `references/backgrounds.md` for gradient and effect techniques
- **Animation**: `references/animation.md` for page load and scroll patterns
- **Examples**: `examples/landing-page.html` for complete page implementation

## Tips

- Ask user about their page purpose and target audience
- Use AskUserQuestion if unclear about design direction
- Reference examples but adapt to specific use case
- Break complex pages into logical sections with clear comments
- Provide color palette and font info for easy customization
- Test responsiveness by considering mobile, tablet, desktop layouts
- Respect prefers-reduced-motion for animations