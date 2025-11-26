---
description: Create a distinctive UI component with creative design
allowed-tools: ["Read", "Write", "Edit", "Bash"]
---

# Create Component

Create a distinctive, non-generic UI component using the distinctive-ui-design skill.

## Instructions

When this command is invoked:

1. **Load the distinctive-ui-design skill** to access design principles and patterns

2. **Gather requirements** by asking the user:
   - Component name (e.g., "Button", "Card", "HeroSection")
   - Component type/purpose (e.g., "Call-to-action button", "Feature card", "Landing page hero")
   - Target framework:
     - React (TypeScript + Tailwind CSS)
     - React (TypeScript + CSS Modules)
     - Vue (Composition API + Tailwind CSS)
     - HTML/CSS/JavaScript
   - Any specific design direction (optional, e.g., "Tokyo Night theme", "Glassmorphism", "Gradient borders")

3. **Design the component** following distinctive-ui-design principles:
   - **Typography**: Select distinctive fonts appropriate for the component (avoid Inter/Arial defaults)
   - **Colors**: Choose or generate a cohesive palette (consider IDE themes, cultural aesthetics)
   - **Background**: Add depth with gradients, patterns, or glassmorphism (avoid flat white/gray)
   - **Animation**: Include meaningful hover states and transitions at high-impact moments
   - **Accessibility**: Maintain WCAG AA contrast ratios, semantic HTML, keyboard navigation

4. **Generate the component file**:
   - Create file in current directory or ask for desired location
   - Include comprehensive implementation with:
     - TypeScript types (if applicable)
     - Styled with chosen framework (Tailwind classes, CSS Modules, Vue scoped styles, etc.)
     - Hover/focus states with smooth animations
     - Responsive design (mobile-first)
     - Accessibility attributes (ARIA labels, semantic HTML)
   - Add inline comments explaining design choices

5. **Provide usage example** showing how to use the component

6. **Summarize design decisions**:
   - Font choices and rationale
   - Color palette and inspiration
   - Animation approach
   - Any special effects used (glassmorphism, gradients, etc.)

## Example Usage

```
/create-component
```

Claude will ask:
- "What component would you like to create?"
- "What framework are you using?"
- "Any specific design direction?"

Then generate a distinctive, production-ready component file.

## Design Philosophy

Apply these principles when creating components:

- **Avoid defaults**: Don't use Inter font, purple gradients, or white backgrounds unless intentionally chosen
- **Tell a story**: Every color, font, and animation should contribute to a cohesive aesthetic
- **Meaningful motion**: Animate only at high-impact moments (hover, focus, entrance)
- **Professional quality**: Code should be production-ready with proper types, accessibility, and responsiveness

## Reference Materials

Consult the distinctive-ui-design skill's reference files for:
- Font pairings (`references/typography.md`)
- Color palettes (`references/color-palettes.md`)
- Background techniques (`references/backgrounds.md`)
- Animation patterns (`references/animation.md`)
- Working examples (`examples/`)

## Tips

- Start by asking user for their component requirements
- Use AskUserQuestion tool if you need clarification on design direction
- Reference the skill's examples for inspiration, but adapt to the specific use case
- Ensure generated code is complete and immediately usable
- Explain design choices so user understands the distinctive approach