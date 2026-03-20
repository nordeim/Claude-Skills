---
name: avant-garde-web-architect
description: Elite web design skill for creating distinctive, production-grade interfaces using Next.js, Tailwind CSS v4, and systematic design frameworks. Implements the Meticulous Approach with Anti-Generic philosophy, Intentionality Compass strategic positioning, and comprehensive verification protocols.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, SearchWeb, FetchURL
---

# Avant-Garde Web Architect
## Distinctive Interface Development via Meticulous Design Intelligence

---

## Skill Metadata

| Attribute | Value |
|-----------|-------|
| **Version** | 1.0.0 |
| **Complexity** | Expert |
| **Framework** | Next.js 15+ (App Router), React 19+, Tailwind CSS v4.1+ |
| **UI Library** | shadcn/ui (Radix primitives) |
| **Animation** | Framer Motion (with reduced-motion compliance) |
| **Design Philosophy** | Anti-Generic / Intentional Minimalism |
| **Methodology** | Meticulous Approach (6-Phase SOP) |

---

## When to Activate This Skill

Activate when:
- Creating new web interfaces requiring **strategic visual positioning** (B2B trust vs. B2C energy)
- Migrating existing projects to **Tailwind CSS v4** CSS-first architecture
- Implementing **complex responsive navigation** (mobile hamburger patterns, accessibility-compliant)
- Debugging **visual discrepancies** between design intent and rendered output
- Conducting **design system audits** or creating component libraries
- Building **conversion-optimized landing pages** with psychological framing
- Architecting **accessible, WCAG AAA-compliant** interfaces

---

## Core Philosophy: The Anti-Generic Mandate

### The Design Pledge

Every interface must demonstrate **intentional differentiation**. Reject:
- Template aesthetics (Bootstrap-style grids, "Inter/Roboto" defaults without hierarchy)
- Purple-gradient-on-white clichés
- Predictable card grids and hero sections
- Surface-level logic without psychological grounding

### The Four Universal Truths

1. **Intentionality is the Only Differentiator**  
   iTrust Academy is intentionally restrained; AI Academy is intentionally bold. Unintentional design—neither clearly trustworthy nor innovative—is the only failure mode.

2. **Hierarchy is a Sacred Duty**  
   Users must never wonder what to look at next. Test by squinting—if hierarchy collapses, redesign.

3. **Whitespace is Structural Voice**  
   Not empty space to fill, but a deliberate material that communicates calm (iTrust) or drama (AI Academy).

4. **Accessibility is Mastery**  
   Engineer for inclusion from the start. Complexity is never an excuse for exclusion.

---

## Part I: Strategic Design Frameworks

### 1.1 The Intentionality Compass

Before any visual work, determine strategic positioning via psychographic assessment:

**Step 1: Audience Analysis** (15 min)
Answer these four questions in writing:

| Question | If Leans Toward... | Compass Points To... |
|----------|-------------------|---------------------|
| Primary fear? | "Wasting money on bad decision" | **Institutional Clarity** (Reduce risk) |
| | "Missing out on next big thing" | **Dynamic Modernism** (Amplify FOMO) |
| Decision style? | Rational, research-heavy | **Institutional Clarity** (Provide data) |
| | Emotional, status-driven | **Dynamic Modernism** (Create desire) |
| Trust source? | Institutions, credentials | **Institutional Clarity** (Signal legacy) |
| | Innovators, peers | **Dynamic Modernism** (Signal community) |
| Category relationship? | New, needs reassurance | **Institutional Clarity** (Build confidence) |
| | Experienced, seeking best | **Dynamic Modernism** (Signal superiority) |

**Step 2: Strategic Positioning Matrix**

```
                    AUDIENCE: RISK-AVERSE    │    AUDIENCE: ASPIRATION-DRIVEN
─────────────────────────────────────────────┼──────────────────────────────────
BRAND: ESTABLISHED                           │
  → Q1: THE GUARDIAN                        │    → Q2: LEGACY INNOVATOR
    Perfect classic execution                │      Blend trusted + bold accents
    (iTrust Academy pattern)                 │      (Harvard AI Program style)
─────────────────────────────────────────────┼──────────────────────────────────
BRAND: DISRUPTIVE                            │
  → Q3: TRUSTWORTHY UPSTART                 │    → Q4: THE VISIONARY
    Modern + ultra-clear + trust signals     │      Full commitment to bold
    (New fintech for boomers)                │      (AI Academy pattern)
```

**Step 3: Anti-Generic Litmus Test** (10 min)
For every major decision, answer:
- **Why?** Ties element to user need/psychology
- **Only?** Challenge defaults—is this the only way?
- **Without?** Enforce minimalism—does removal diminish the core?

**Step 4: Technical Commitment** (5 min)
Identify top 3 commitments based on quadrant:
- **Q1/Q3 (Institutional)**: Lighthouse 95+, AAA accessibility, semantic HTML, minimal JS
- **Q2/Q4 (Dynamic)**: Expert animation, 3D/WebGL (optional), performance budgeting, `prefers-reduced-motion`

### 1.2 Design Decision Library

**Typography Pairings by Strategy:**

| Strategy | Display Font | Body Font | Use Case |
|----------|-------------|-----------|----------|
| **Single Family** | DM Sans | DM Sans | Corporate, fast-loading (iTrust) |
| **Expressive System** | Space Grotesk | Inter | Modern tech, personality (AI Academy) |
| **Editorial** | Playfair Display | Source Sans Pro | Magazine-style content |
| **Brutalist** | System-ui (bold) | Courier Prime | Raw, technical aesthetic |

**Color Palette Architecture:**

```css
/* Institutional Clarity (iTrust-inspired) */
@theme {
  --color-primary: #F27A1A;           /* Warm authority */
  --color-primary-subtle: rgba(242,122,26,0.08);
  --color-bg-primary: #FFFFFF;
  --color-bg-secondary: #F8F9FA;
  --color-text-primary: #111827;
  --color-text-secondary: #6B7280;
  --color-success: #059669;
}

/* Dynamic Modernism (AI Academy-inspired) */
@theme {
  --color-primary: #4F46E5;           /* Indigo energy */
  --color-bg-primary: #FAFAF9;        /* Warm off-white */
  --color-bg-dark: #1E293B;           /* Slate premium sections */
  --color-accent-cyan: #06B6D4;
  --color-accent-emerald: #10B981;
  --color-accent-amber: #F59E0B;
  --color-urgency: #EF4444;
}
```

---

## Part II: Technical Architecture

### 2.1 Stack Specification

```yaml
Core Framework:
  - Next.js: 15.1.4+ (App Router, Server Components, Turbopack)
  - React: 19.0.0+
  - TypeScript: 5.7.3+ (Strict Mode)

Styling & UI:
  - Tailwind CSS: v4.1.0+ (CSS-first with @theme)
  - PostCSS: @tailwindcss/postcss plugin
  - shadcn/ui: Component primitives (Radix-based)
  - class-variance-authority: Component variants
  - tailwind-merge: Class deduplication
  - clsx: Conditional classes

Animation:
  - Framer Motion: 12.0+ (React components)
  - CSS Transitions: For simple hover states (performance)
  
Forms & Validation:
  - react-hook-form: Form state management
  - zod: Schema validation
  - @hookform/resolvers: Zod integration

Development:
  - ESLint: 9.x with TypeScript
  - Prettier: 3.x with tailwindcss plugin
```

### 2.2 Tailwind CSS v4 CSS-First Configuration

**CRITICAL:** No `tailwind.config.js`. Use CSS-only configuration.

**File: `src/app/globals.css`**

```css
@import "tailwindcss";

/* ============================================
   THEME CONFIGURATION (@theme directive)
   ============================================ */

@theme {
  /* Typography */
  --font-sans: "Inter", system-ui, sans-serif;
  --font-display: "Space Grotesk", "Inter", sans-serif;
  --font-mono: "JetBrains Mono", monospace;
  
  /* Colors - OKLCH preferred for v4 */
  --color-primary-50: oklch(0.97 0.02 250);
  --color-primary-500: oklch(0.55 0.12 250);
  --color-primary-600: oklch(0.45 0.15 250);
  
  /* Spacing Scale Extensions */
  --spacing-18: 4.5rem;
  --spacing-88: 22rem;
  
  /* Custom Breakpoints */
  --breakpoint-3xl: 1920px;
  
  /* Animation Tokens */
  --animate-float: float 25s ease-in-out infinite;
  --animate-pulse-slow: pulse-slow 4s ease-in-out infinite;
  
  @keyframes float {
    0%, 100% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-20px) rotate(5deg); }
  }
  
  @keyframes pulse-slow {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.5; }
  }
}

/* ============================================
   BASE STYLES (@layer base)
   ============================================ */

@layer base {
  * {
    @apply border-slate-200 dark:border-slate-800;
  }
  
  html {
    scroll-behavior: smooth;
  }
  
  body {
    @apply bg-background text-foreground font-sans antialiased;
  }
  
  h1, h2, h3, h4 {
    @apply font-display tracking-tight;
  }
}

/* ============================================
   CUSTOM UTILITIES (@utility directive)
   ============================================ */

@utility glass-panel {
  @apply bg-white/70 dark:bg-slate-900/70 backdrop-blur-xl 
         border border-white/20 dark:border-slate-800/50;
}

@utility text-balance {
  text-wrap: balance;
}

@utility container-tight {
  @apply max-w-[1140px] mx-auto px-4 sm:px-6 lg:px-8;
}
```

**File: `postcss.config.mjs`**

```javascript
export default {
  plugins: ["@tailwindcss/postcss"],
};
```

### 2.3 Critical v4 Migration Notes

**Breaking Changes from v3:**

| v3 Utility | v4 Replacement | Migration |
|------------|----------------|-----------|
| `bg-opacity-*` | `bg-color/*` | `bg-red-500/50` |
| `shadow-sm` | `shadow-xs` | Rename |
| `shadow` | `shadow-sm` | Rename |
| `bg-gradient-to-r` | `bg-linear-to-r` | Prefix change |
| `outline-none` | `outline-hidden` | Rename |
| `ring` | `ring-3` | Explicit width |
| `flex-shrink-*` | `shrink-*` | Rename |
| `flex-grow-*` | `grow-*` | Rename |
| `overflow-ellipsis` | `text-ellipsis` | Rename |
| Arbitrary `[--var]` | `(--var)` | Parentheses syntax |

**CSS Variable Syntax:**
```html
<!-- v3 -->
<div class="bg-[--brand-color]">

<!-- v4 -->
<div class="bg-(--brand-color)">
```

---

## Part III: The Meticulous Approach (6-Phase SOP)

### Phase 1: ANALYZE (Deep Requirement Mining)

**Deliverables:**
1. **Strategic Brief** (1 page): Quadrant position, audience psychographics, emotional goals
2. **Content Audit**: Inventory all content types, prioritize hierarchy
3. **Competitive Matrix**: 3-5 competitor screenshots with differentiation opportunities
4. **Technical Constraints**: Browser support, performance budget, accessibility requirements

**Checklist:**
- [ ] Intentionality Compass completed (Section 1.1)
- [ ] Anti-Generic Litmus Test passed for core concept
- [ ] Accessibility requirements defined (WCAG AA vs. AAA)
- [ ] Performance budget established (see Section 6.1)

**Anti-Patterns to Flag:**
- "Make it look like [competitor]" without differentiation strategy
- Undefined audience (B2B vs. B2C undetermined)
- Feature lists without priority ranking

### Phase 2: PLAN (Structured Execution Roadmap)

**Deliverables:**
1. **Component Architecture**: Tree diagram of components (Server vs. Client)
2. **File Structure**:
   ```
   src/
   ├── app/
   │   ├── layout.tsx (fonts, metadata, providers)
   │   ├── page.tsx (composition)
   │   └── globals.css (theme tokens)
   ├── components/
   │   ├── layout/ (Navbar, Footer, Shell)
   │   ├── sections/ (Hero, Features, Pricing)
   │   └── ui/ (shadcn primitives)
   │       ├── Button.tsx
   │       ├── Card.tsx
   │       └── Input.tsx
   ├── lib/
   │   ├── utils.ts (cn(), formatters)
   │   └── hooks/ (useReducedMotion, useMediaQuery)
   └── types/
   ```
3. **Animation Strategy**: Which elements animate, which respect `prefers-reduced-motion`
4. **Data Flow**: Server Components vs. Client Components boundary map

**Decision Points:**
- Navigation pattern: Inline (mobile-visible) vs. Hamburger (Sheet overlay)
- Color strategy: Single accent (Institutional) vs. Multi-accent (Dynamic)
- Typography: Single family vs. Two-family system

### Phase 3: VALIDATE (Explicit Confirmation Checkpoint)

**Review Meeting Agenda:**
1. Present Intentionality Compass positioning
2. Show 3 style tiles (mood boards) with color/typography swatches
3. Review component hierarchy diagram
4. Confirm accessibility target (AA vs. AAA)
5. Verify performance budget feasibility

**Sign-off Required Before Proceeding:**
- [ ] Strategic positioning approved
- [ ] Color palette contrast ratios verified (WebAIM)
- [ ] Component architecture reviewed
- [ ] Animation complexity approved

### Phase 4: IMPLEMENT (Modular, Tested Builds)

**Sub-phase 4.1: Foundation**
- Configure Tailwind v4 theme tokens (`@theme`)
- Set up fonts in `layout.tsx` (Next.js font optimization)
- Implement base layout (Navbar, Footer, container system)
- **Verification**: Theme variables render correctly in DevTools

**Sub-phase 4.2: Components (Library Discipline)**
Use shadcn/ui primitives. Do not rebuild from scratch.

```tsx
// Pattern: Extend shadcn, don't replace
import { Button as ShadcnButton } from "@/components/ui/button";
import { cva, type VariantProps } from "class-variance-authority";

const buttonVariants = cva(
  "inline-flex items-center justify-center rounded-lg font-medium transition-colors",
  {
    variants: {
      variant: {
        // Extend with brand-specific styles
        brand: "bg-primary-600 text-white hover:bg-primary-500",
        ghost: "hover:bg-slate-100 dark:hover:bg-slate-800",
      },
      size: {
        default: "h-10 px-4 py-2",
        lg: "h-12 px-6 text-lg", // For hero CTAs
      },
    },
  }
);
```

**Sub-phase 4.3: Sections (Composition)**
- Hero section with strategic positioning (text-focused vs. image-focused)
- Feature grids with intentional whitespace
- Trust signals (logos or stats depending on quadrant)
- Pricing/CTA with conversion psychology

**Sub-phase 4.4: Responsive Behavior**
- Mobile-first implementation
- Navigation breakpoint strategy (symmetrical: `hidden md:flex` / `md:hidden`)
- Touch targets minimum 44x44px
- Font scaling (clamp() or Tailwind's fluid type)

**Sub-phase 4.5: Animation Implementation**

```tsx
"use client";

import { motion } from "framer-motion";
import { useReducedMotion } from "@/lib/hooks/useReducedMotion";

export function AnimatedSection({ children }) {
  const prefersReducedMotion = useReducedMotion();

  return (
    <motion.div
      initial={prefersReducedMotion ? {} : { opacity: 0, y: 20 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.5, ease: [0.4, 0, 0.2, 1] }}
    >
      {children}
    </motion.div>
  );
}
```

**Animation Guidelines:**
- Duration: 150ms (micro), 300ms (standard), 500ms (dramatic)
- Easing: `[0.4, 0, 0.2, 1]` (Material ease-out)
- Properties: Only animate `transform` and `opacity` (compositor-only)
- Respect `prefers-reduced-motion`: Disable or simplify for `reduce`

### Phase 5: VERIFY (Rigorous QA)

**5.1 Visual Debugging Protocol**

Run this decision tree for any visual discrepancy:

```
Step 1: Is element present in DOM?
  └─ No → Check component rendering, conditional logic
  
Step 2: Is it hidden by computed CSS?
  └─ Check: display: none, visibility: hidden, opacity: 0
  
Step 3: Is it off-screen or clipped?
  └─ Check: position, transform, overflow:hidden on ancestors
  
Step 4: Is it behind another layer?
  └─ Check z-index, stacking contexts (parent transforms)
  
Step 5: Is JS failing to toggle state?
  └─ Check console errors, event listeners, state management
  
Step 6: Production-only disappearance?
  └─ Check Tailwind class extraction (no dynamic strings)
```

**5.2 Mobile Navigation Verification**

**Critical Checks:**
- [ ] Viewport meta tag present: `<meta name="viewport" content="width=device-width, initial-scale=1">`
- [ ] Symmetrical breakpoints: Desktop nav `hidden md:flex`, Mobile trigger `md:hidden`
- [ ] Semantic button: `<button type="button">` not `<div onClick>`
- [ ] ARIA attributes: `aria-expanded`, `aria-controls`, `aria-label`
- [ ] Z-index scale: Modal > Dropdown > Sticky > Base
- [ ] Scroll lock: Body scroll disabled when overlay open
- [ ] Focus trap: Focus moves to first link when opened, returns to trigger when closed
- [ ] Escape key: Closes mobile menu

**Common Failure Classes:**
- **Class A**: Destructive hiding without substitution (hiding nav without menu trigger)
- **Class B**: Hidden by visibility/opacity state (CSS state not toggling)
- **Class C**: Clipped by overflow (parent has `overflow: hidden`)
- **Class D**: Behind another layer (z-index issues)
- **Class E**: Breakpoint mismatch (viewport meta missing)
- **Class F**: JavaScript state bug (click handler not attached)
- **Class G**: Keyboard inaccessible (not focusable)
- **Class H**: Click-outside race condition (handler closes immediately after open)

**5.3 Accessibility Audit**

- [ ] WCAG contrast ratios met (4.5:1 normal text, 3:1 large text/UI)
- [ ] Focus visible on all interactive elements (`focus-visible:ring-2`)
- [ ] Heading hierarchy logical (H1 → H2 → H3, no skips)
- [ ] Alt text on images (decorative images have `alt=""`)
- [ ] Form labels associated (`htmlFor` or wrapping)
- [ ] `prefers-reduced-motion` respected
- [ ] Keyboard navigation path logical (Tab order follows visual order)
- [ ] ARIA labels on icon-only buttons
- [ ] Screen reader testing (VoiceOver/NVDA)

**5.4 Performance Verification**

```bash
# Build analysis
npm run build

# Lighthouse CI
npx lighthouse http://localhost:3000 \
  --chrome-flags="--headless" \
  --only-categories=performance,accessibility,best-practices,seo \
  --output=json \
  --output-path=./lighthouse-report.json

# Bundle analysis
npm run analyze  # If configured
```

**Budgets:**
- First Contentful Paint < 1.5s (Institutional) or < 2.5s (Dynamic)
- Largest Contentful Paint < 2.5s
- Total Blocking Time < 200ms
- Cumulative Layout Shift < 0.1

### Phase 6: DELIVER (Complete Handoff)

**Deliverables:**
1. **Source Code**: Git repository with clean commit history
2. **Design Documentation**: 
   - Intentionality Compass decisions recorded
   - Component usage examples
   - Animation timing specifications
3. **Runbook**:
   - Environment setup instructions
   - Build commands (`npm run build`, `npm run dev`)
   - Deployment notes
4. **Quality Report**:
   - Lighthouse scores screenshot
   - Accessibility audit results
   - Browser testing matrix results
5. **Knowledge Transfer Session** (if applicable):
   - Architecture decisions explained
   - Extension points identified

---

## Part IV: Implementation Patterns

### 4.1 Mobile Navigation Pattern (React + shadcn)

**File: `components/layout/MobileNav.tsx`**

```tsx
"use client";

import * as React from "react";
import Link from "next/link";
import { usePathname } from "next/navigation";
import { Menu, X } from "lucide-react";
import { Button } from "@/components/ui/button";
import {
  Sheet,
  SheetContent,
  SheetHeader,
  SheetTitle,
  SheetTrigger,
  SheetClose,
} from "@/components/ui/sheet";

const NAV_ITEMS = [
  { href: "/courses", label: "Courses" },
  { href: "/about", label: "About" },
  { href: "/contact", label: "Contact" },
] as const;

export function MobileNav() {
  const [open, setOpen] = React.useState(false);
  const pathname = usePathname();

  // Close on route change
  React.useEffect(() => {
    setOpen(false);
  }, [pathname]);

  return (
    <Sheet open={open} onOpenChange={setOpen}>
      <SheetTrigger asChild>
        <Button
          variant="ghost"
          size="icon"
          className="md:hidden"
          aria-label={open ? "Close navigation" : "Open navigation"}
        >
          {open ? <X className="h-5 w-5" /> : <Menu className="h-5 w-5" />}
        </Button>
      </SheetTrigger>

      <SheetContent side="right" className="w-[300px] sm:w-[400px]">
        <SheetHeader className="border-b pb-4">
          <SheetTitle>Navigation</SheetTitle>
        </SheetHeader>
        
        <nav className="flex flex-col gap-2 py-6" aria-label="Mobile navigation">
          {NAV_ITEMS.map((item) => (
            <SheetClose asChild key={item.href}>
              <Link
                href={item.href}
                className="flex items-center rounded-lg px-3 py-3 text-lg font-medium hover:bg-muted transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring"
              >
                {item.label}
              </Link>
            </SheetClose>
          ))}
        </nav>
      </SheetContent>
    </Sheet>
  );
}
```

**File: `components/layout/DesktopNav.tsx`**

```tsx
import Link from "next/link";

const NAV_ITEMS = [
  { href: "/courses", label: "Courses" },
  { href: "/about", label: "About" },
  { href: "/contact", label: "Contact" },
] as const;

export function DesktopNav() {
  return (
    <nav className="hidden md:flex items-center gap-8" aria-label="Main navigation">
      {NAV_ITEMS.map((item) => (
        <Link
          key={item.href}
          href={item.href}
          className="text-sm font-medium hover:text-primary transition-colors"
        >
          {item.label}
        </Link>
      ))}
    </nav>
  );
}
```

**Usage in Header:**
```tsx
<header className="sticky top-0 z-50 w-full border-b bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60">
  <div className="container-tight flex h-16 items-center justify-between">
    <Link href="/" className="font-display text-xl font-bold">
      Brand
    </Link>
    <DesktopNav />
    <MobileNav />
  </div>
</header>
```

### 4.2 Hero Section Patterns

**Institutional Clarity (iTrust-style):**
```tsx
<section className="relative py-20 md:py-32 overflow-hidden">
  {/* Subtle background texture */}
  <div className="absolute inset-0 bg-[linear-gradient(to_right,#80808012_1px,transparent_1px),linear-gradient(to_bottom,#80808012_1px,transparent_1px)] bg-[size:24px_24px]" />
  
  <div className="container-tight relative">
    <div className="max-w-3xl mx-auto text-center">
      <h1 className="text-4xl md:text-6xl font-display font-bold tracking-tight mb-6">
        Professional Certification Training
      </h1>
      <p className="text-xl text-muted-foreground mb-8 max-w-2xl mx-auto">
        Authorized training partner for leading enterprise technologies. 
        Advance your career with industry-recognized credentials.
      </p>
      <div className="flex flex-col sm:flex-row gap-4 justify-center">
        <Button size="lg">Explore Programs</Button>
        <Button size="lg" variant="outline">Contact Sales</Button>
      </div>
    </div>
  </div>
</section>
```

**Dynamic Modernism (AI Academy-style):**
```tsx
<section className="relative py-20 md:py-32 overflow-hidden">
  {/* Decorative gradient orbs */}
  <div className="absolute top-0 right-0 -translate-y-1/4 translate-x-1/4 w-96 h-96 bg-primary/20 rounded-full blur-3xl" />
  <div className="absolute bottom-0 left-0 translate-y-1/4 -translate-x-1/4 w-96 h-96 bg-cyan-500/20 rounded-full blur-3xl" />
  
  <div className="container-tight relative">
    <div className="grid lg:grid-cols-2 gap-12 items-center">
      <div>
        <div className="inline-flex items-center rounded-full border px-3 py-1 text-sm font-medium mb-6">
          <span className="flex h-2 w-2 rounded-full bg-emerald-500 mr-2" />
          Now enrolling for Q2 2026
        </div>
        <h1 className="text-5xl md:text-7xl font-display font-bold tracking-tighter mb-6">
          Master AI Engineering
        </h1>
        <p className="text-xl text-muted-foreground mb-8">
          Join 50,000+ engineers advancing their careers with hands-on AI training.
        </p>
        <div className="flex flex-wrap gap-4">
          <Button size="lg" className="rounded-full">
            Start Learning
          </Button>
          <Button size="lg" variant="ghost" className="rounded-full">
            View Curriculum
          </Button>
        </div>
      </div>
      
      {/* Visual element: Code snippet or abstract illustration */}
      <div className="relative">
        <div className="glass-panel rounded-2xl p-6 shadow-2xl">
          <pre className="text-sm font-mono overflow-x-auto">
            <code>{`import { openai } from '@ai-sdk/openai';

const model = openai('gpt-4o');
const result = await generateText({
  model,
  prompt: 'Build the future...',
});`}</code>
          </pre>
        </div>
      </div>
    </div>
  </div>
</section>
```

### 4.3 Card Component with Category Colors

```tsx
interface CourseCardProps {
  title: string;
  description: string;
  category: "ai" | "cloud" | "security" | "data";
  duration: string;
  level: string;
}

const CATEGORY_COLORS = {
  ai: "border-t-violet-500 bg-violet-500/10",
  cloud: "border-t-cyan-500 bg-cyan-500/10",
  security: "border-t-emerald-500 bg-emerald-500/10",
  data: "border-t-amber-500 bg-amber-500/10",
};

export function CourseCard({ title, description, category, duration, level }: CourseCardProps) {
  return (
    <div className={`group relative rounded-xl border bg-card p-6 border-t-4 ${CATEGORY_COLORS[category]} hover:shadow-lg transition-shadow`}>
      <div className="flex items-center justify-between mb-4">
        <span className="text-xs font-mono uppercase tracking-wider text-muted-foreground">
          {category}
        </span>
        <span className="text-xs text-muted-foreground">{duration}</span>
      </div>
      <h3 className="text-xl font-display font-semibold mb-2 group-hover:text-primary transition-colors">
        {title}
      </h3>
      <p className="text-muted-foreground text-sm mb-4 line-clamp-2">
        {description}
      </p>
      <div className="flex items-center justify-between">
        <span className="text-xs font-medium px-2 py-1 rounded-full bg-muted">
          {level}
        </span>
        <Button variant="ghost" size="sm" className="opacity-0 group-hover:opacity-100 transition-opacity">
          Details →
        </Button>
      </div>
    </div>
  );
}
```

---

## Part V: Quality Assurance & Debugging

### 5.1 Pre-Commit Checklist

```bash
# Run these commands before every commit
npm run typecheck  # TypeScript strict mode
npm run lint       # ESLint with TypeScript
npm run build      # Production build verification
```

**Code Quality Gates:**
- [ ] No `any` types (use `unknown` with type guards)
- [ ] Proper error boundaries for Client Components
- [ ] Loading states for async operations
- [ ] Error states with user-friendly messages
- [ ] Disabled buttons during form submission
- [ ] `useEffect` cleanup functions where needed
- [ ] Memoization for expensive calculations (`useMemo`, `useCallback`)

### 5.2 Visual Debugging Playbook

**Symptom: Styles not applying**
1. Check DevTools → Elements → Computed styles
2. Verify Tailwind v4 classes use correct syntax (no `bg-opacity-`, use `/` syntax)
3. Check for dynamic class strings (Tailwind can't parse `className={variable}`)

**Symptom: Layout broken on mobile**
1. Check viewport meta tag presence
2. Verify `md:hidden` / `hidden md:flex` symmetry
3. Check for fixed widths exceeding viewport (use `max-w-full` or `w-full`)
4. Verify `min-w-0` on flex children containing text

**Symptom: Animations janky**
1. Check DevTools → Performance → Record
2. Verify only `transform` and `opacity` are animated
3. Check for `layout` property animations (width, height, top, left)
4. Verify `will-change` is set (sparingly) on animated elements

**Symptom: Flash of unstyled content (FOUC)**
1. Verify fonts are loaded via `next/font` (CSS variables)
2. Check for hydration mismatches (Server vs Client HTML mismatch)
3. Use `suppressHydrationWarning` only when truly necessary (theme toggles)

### 5.3 Accessibility Quick Test

Run this keyboard-only navigation:
1. Tab through entire page — can you reach every interactive element?
2. Activate buttons with Enter/Space
3. Check focus visibility — is the focused element clearly indicated?
4. Test Escape key in modals/dropdowns — does it close and return focus?
5. Run axe DevTools extension — address all Critical and Serious issues

---

## Part VI: Verification Gates Summary

### Before Design Begins
- [ ] Intentionality Compass completed
- [ ] Quadrant position documented (Q1-Q4)
- [ ] 3 Anti-Generic prompts answered
- [ ] Technical commitments defined

### Before Development Begins
- [ ] Component architecture diagram approved
- [ ] Color contrast ratios verified (WebAIM)
- [ ] Animation strategy documented
- [ ] Mobile navigation pattern selected

### Before Deployment
- [ ] Lighthouse Performance > 90 (Institutional) or > 85 (Dynamic)
- [ ] Lighthouse Accessibility > 95
- [ ] Mobile navigation tested on actual device
- [ ] Reduced motion preferences tested
- [ ] All interactive elements keyboard accessible
- [ ] No console errors in production build
- [ ] Cross-browser tested (Chrome, Safari, Firefox)

---

## Appendices

### A. Tailwind v4 Quick Reference

| Task | v4 Syntax |
|------|-----------|
| Import | `@import "tailwindcss";` (single import) |
| Theme vars | `@theme { --color-brand: #F27A1A; }` |
| Custom utility | `@utility glass { @apply ... }` |
| Arbitrary values | `w-(--custom-width)` (parentheses, not brackets) |
| Dark mode | `dark:` prefix (media query based) |
| Container queries | `@container`, `@md:`, `@max-lg:` |

### B. Z-Index Scale

```css
@theme {
  --z-base: 0;
  --z-dropdown: 200;
  --z-sticky: 300;
  --z-modal-backdrop: 400;
  --z-modal: 500;
  --z-popover: 600;
  --z-tooltip: 700;
}
```

### C. Animation Timing Reference

| Type | Duration | Easing |
|------|----------|--------|
| Micro (hover) | 150ms | ease-out |
| Standard | 300ms | cubic-bezier(0.4, 0, 0.2, 1) |
| Dramatic (hero) | 500-800ms | cubic-bezier(0.3, 0, 0, 1) |
| Stagger delay | 50ms per item | — |

### D. Design Prompt Library (Emergency Use)

If stuck, ask:
- "If our brand were a person, would they be a tenured professor or a startup founder?"
- "Does our user need a handshake or a high-five?"
- "Would this work without any color?"
- "Is this element structural or decorative? (If decorative, delete it)"

---

**Skill Version:** 1.0.0  
**Compatible With:** Next.js 15+, Tailwind CSS v4+, React 19+  
**Classification:** Production-Ready / Expert Level
