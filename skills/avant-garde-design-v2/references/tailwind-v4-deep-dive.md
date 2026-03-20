# Tailwind CSS v4 Deep Dive

A comprehensive guide to Tailwind CSS v4 CSS-first architecture, migration from v3, and advanced patterns.

---

## Overview of v4 Architecture

Tailwind CSS v4 represents a fundamental shift from JavaScript-based configuration to CSS-first configuration. This eliminates the `tailwind.config.js` file entirely and moves all customization into CSS using the `@theme` directive.

### Key Changes

| Aspect | v3 | v4 |
|--------|-----|-----|
| Configuration | `tailwind.config.js` | CSS `@theme` directive |
| Import | Multiple directives | Single `@import "tailwindcss"` |
| Arbitrary values | `[--var]` syntax | `(--var)` syntax |
| Opacity modifiers | `bg-opacity-*` utilities | `/` syntax (e.g., `bg-red-500/50`) |
| Gradient prefix | `bg-gradient-*` | `bg-linear-*` |

---

## Complete Theme Configuration

### Basic Setup

```css
/* globals.css */
@import "tailwindcss";

@theme {
  /* ============================================
     TYPOGRAPHY
     ============================================ */

  /* Font Families */
  --font-sans: "Inter", system-ui, sans-serif;
  --font-display: "Space Grotesk", "Inter", sans-serif;
  --font-serif: "Instrument Serif", "Georgia", serif;
  --font-mono: "JetBrains Mono", "Fira Code", monospace;

  /* Font Sizes (extending defaults) */
  --text-xxs: 0.625rem;
  --text-10xl: 8rem;

  /* Line Heights */
  --leading-tighter: 1.1;
  --leading-looser: 2;

  /* Letter Spacing */
  --tracking-tighter: -0.04em;
  --tracking-super-tight: -0.06em;

  /* ============================================
     COLORS (OKLCH recommended)
     ============================================ */

  /* Brand Colors */
  --color-brand-50: oklch(0.98 0.02 250);
  --color-brand-100: oklch(0.95 0.03 250);
  --color-brand-200: oklch(0.90 0.05 250);
  --color-brand-300: oklch(0.80 0.08 250);
  --color-brand-400: oklch(0.70 0.10 250);
  --color-brand-500: oklch(0.55 0.12 250);
  --color-brand-600: oklch(0.45 0.15 250);
  --color-brand-700: oklch(0.35 0.12 250);
  --color-brand-800: oklch(0.25 0.08 250);
  --color-brand-900: oklch(0.18 0.05 250);
  --color-brand-950: oklch(0.12 0.03 250);

  /* Semantic Colors */
  --color-success: oklch(0.65 0.2 145);
  --color-warning: oklch(0.75 0.18 80);
  --color-error: oklch(0.6 0.22 25);
  --color-info: oklch(0.65 0.15 230);

  /* ============================================
     SPACING (extending defaults)
     ============================================ */

  --spacing-18: 4.5rem;    /* 72px */
  --spacing-22: 5.5rem;    /* 88px */
  --spacing-26: 6.5rem;    /* 104px */
  --spacing-30: 7.5rem;    /* 120px */
  --spacing-34: 8.5rem;    /* 136px */
  --spacing-38: 9.5rem;    /* 152px */
  --spacing-42: 10.5rem;   /* 168px */
  --spacing-46: 11.5rem;   /* 184px */
  --spacing-50: 12.5rem;   /* 200px */
  --spacing-54: 13.5rem;   /* 216px */
  --spacing-58: 14.5rem;   /* 232px */
  --spacing-62: 15.5rem;   /* 248px */
  --spacing-66: 16.5rem;   /* 264px */
  --spacing-70: 17.5rem;   /* 280px */
  --spacing-74: 18.5rem;   /* 296px */
  --spacing-78: 19.5rem;   /* 312px */
  --spacing-82: 20.5rem;   /* 328px */
  --spacing-86: 21.5rem;   /* 344px */
  --spacing-88: 22rem;     /* 352px */
  --spacing-92: 23rem;     /* 368px */
  --spacing-96: 24rem;     /* 384px */

  /* ============================================
     BREAKPOINTS
     ============================================ */

  --breakpoint-xs: 475px;
  --breakpoint-sm: 640px;
  --breakpoint-md: 768px;
  --breakpoint-lg: 1024px;
  --breakpoint-xl: 1280px;
  --breakpoint-2xl: 1536px;
  --breakpoint-3xl: 1920px;

  /* ============================================
     BORDERS & RADIUS
     ============================================ */

  --radius-4xl: 2rem;
  --radius-5xl: 2.5rem;

  /* ============================================
     SHADOWS
     ============================================ */

  --shadow-glow: 0 0 40px -10px var(--color-brand-500);
  --shadow-glow-lg: 0 0 60px -10px var(--color-brand-500);
  --shadow-inner-glow: inset 0 0 30px -10px var(--color-brand-500);

  /* ============================================
     ANIMATIONS
     ============================================ */

  --animate-fade-in: fade-in 0.5s ease-out;
  --animate-fade-in-up: fade-in-up 0.5s ease-out;
  --animate-fade-in-down: fade-in-down 0.5s ease-out;
  --animate-scale-in: scale-in 0.3s ease-out;
  --animate-slide-in-right: slide-in-right 0.3s ease-out;
  --animate-slide-in-left: slide-in-left 0.3s ease-out;
  --animate-float: float 6s ease-in-out infinite;
  --animate-pulse-slow: pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite;
  --animate-shimmer: shimmer 2s linear infinite;

  /* Keyframes */
  @keyframes fade-in {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  @keyframes fade-in-up {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fade-in-down {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes scale-in {
    from { opacity: 0; transform: scale(0.95); }
    to { opacity: 1; transform: scale(1); }
  }

  @keyframes slide-in-right {
    from { opacity: 0; transform: translateX(20px); }
    to { opacity: 1; transform: translateX(0); }
  }

  @keyframes slide-in-left {
    from { opacity: 0; transform: translateX(-20px); }
    to { opacity: 1; transform: translateX(0); }
  }

  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
  }

  @keyframes shimmer {
    0% { background-position: -200% 0; }
    100% { background-position: 200% 0; }
  }

  /* ============================================
     Z-INDEX SCALE
     ============================================ */

  --z-behind: -1;
  --z-base: 0;
  --z-raised: 10;
  --z-dropdown: 200;
  --z-sticky: 300;
  --z-overlay: 400;
  --z-modal: 500;
  --z-popover: 600;
  --z-tooltip: 700;
  --z-toast: 800;
  --z-max: 999;
}
```

---

## Custom Utilities

### Creating Custom Utilities

```css
/* Define custom utilities with @utility */

@utility glass-panel {
  @apply bg-white/70 dark:bg-slate-900/70 backdrop-blur-xl
         border border-white/20 dark:border-slate-800/50;
}

@utility container-tight {
  @apply max-w-[1140px] mx-auto px-4 sm:px-6 lg:px-8;
}

@utility container-wide {
  @apply max-w-[1400px] mx-auto px-4 sm:px-6 lg:px-8;
}

@utility text-balance {
  text-wrap: balance;
}

@utility text-pretty {
  text-wrap: pretty;
}

@utility no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
  &::-webkit-scrollbar {
    display: none;
  }
}

@utility gradient-text {
  @apply bg-clip-text text-transparent bg-gradient-to-r from-brand-500 to-brand-700;
}

@utility animate-delay-100 {
  animation-delay: 100ms;
}

@utility animate-delay-200 {
  animation-delay: 200ms;
}

@utility animate-delay-300 {
  animation-delay: 300ms;
}

@utility animate-delay-400 {
  animation-delay: 400ms;
}

@utility animate-delay-500 {
  animation-delay: 500ms;
}
```

---

## Base Styles

### Using @layer base

```css
@layer base {
  /* Reset and base styles */
  * {
    @apply border-slate-200 dark:border-slate-800;
  }

  html {
    scroll-behavior: smooth;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  body {
    @apply bg-background text-foreground font-sans antialiased;
  }

  /* Typography defaults */
  h1, h2, h3, h4, h5, h6 {
    @apply font-display tracking-tight font-bold;
  }

  h1 {
    @apply text-4xl md:text-5xl lg:text-6xl leading-tight;
  }

  h2 {
    @apply text-3xl md:text-4xl leading-tight;
  }

  h3 {
    @apply text-2xl md:text-3xl;
  }

  h4 {
    @apply text-xl md:text-2xl;
  }

  /* Focus styles */
  :focus-visible {
    @apply outline-none ring-2 ring-brand-500 ring-offset-2 ring-offset-background;
  }

  /* Selection */
  ::selection {
    @apply bg-brand-500/20 text-brand-900;
  }

  /* Links */
  a {
    @apply transition-colors duration-200;
  }

  /* Code */
  code {
    @apply font-mono text-sm bg-muted px-1.5 py-0.5 rounded;
  }

  pre {
    @apply font-mono text-sm bg-slate-900 text-slate-50 p-4 rounded-lg overflow-x-auto;
  }

  pre code {
    @apply bg-transparent p-0;
  }
}
```

---

## Component Styles

### Using @layer components

```css
@layer components {
  /* Button base styles */
  .btn {
    @apply inline-flex items-center justify-center rounded-lg font-medium
           transition-all duration-200 focus-visible:outline-none
           focus-visible:ring-2 focus-visible:ring-offset-2
           disabled:pointer-events-none disabled:opacity-50;
  }

  /* Card styles */
  .card {
    @apply rounded-xl border bg-card text-card-foreground shadow-sm;
  }

  .card-hover {
    @apply card transition-all duration-200 hover:shadow-lg hover:-translate-y-1;
  }

  /* Input styles */
  .input {
    @apply flex h-10 w-full rounded-lg border bg-background px-3 py-2
           text-sm ring-offset-background file:border-0 file:bg-transparent
           file:text-sm file:font-medium placeholder:text-muted-foreground
           focus-visible:outline-none focus-visible:ring-2
           focus-visible:ring-brand-500 focus-visible:ring-offset-2
           disabled:cursor-not-allowed disabled:opacity-50;
  }

  /* Section containers */
  .section {
    @apply py-16 md:py-24 lg:py-32;
  }

  .section-sm {
    @apply py-8 md:py-12 lg:py-16;
  }
}
```

---

## Migration from v3

### Complete Migration Checklist

1. **Remove old config file**
   ```bash
   rm tailwind.config.js
   rm tailwind.config.ts
   ```

2. **Update package.json**
   ```json
   {
     "dependencies": {
       "tailwindcss": "^4.0.0"
     }
   }
   ```

3. **Update CSS file**
   ```css
   /* OLD v3 */
   @tailwind base;
   @tailwind components;
   @tailwind utilities;

   /* NEW v4 */
   @import "tailwindcss";
   ```

4. **Update PostCSS config**
   ```javascript
   // OLD v3
   module.exports = {
     plugins: {
       tailwindcss: {},
       autoprefixer: {},
     },
   }

   // NEW v4
   export default {
     plugins: ["@tailwindcss/postcss"],
   }
   ```

5. **Update utility classes** (see migration table in main skill)

### Breaking Changes Reference

| Category | v3 | v4 |
|----------|-----|-----|
| **Configuration** | `tailwind.config.js` | `@theme` in CSS |
| **Import** | `@tailwind base/components/utilities` | `@import "tailwindcss"` |
| **Opacity** | `bg-opacity-50` | `bg-color/50` |
| **Gradients** | `bg-gradient-to-r` | `bg-linear-to-r` |
| **Shadow scale** | `shadow-sm` smallest | `shadow-xs` smallest |
| **Outline** | `outline-none` | `outline-hidden` |
| **Ring default** | `ring` = `ring-3` | Must specify width |
| **Flex grow/shrink** | `flex-grow`, `flex-shrink` | `grow`, `shrink` |
| **Arbitrary values** | `w-[100px]` | Same, but CSS vars use `(--var)` |

---

## Advanced Patterns

### Container Queries

```css
@theme {
  --container: 320px;
  --container-lg: 640px;
}

/* Usage */
.container-query-example {
  container-type: inline-size;
}

@container (min-width: 640px) {
  .responsive-element {
    /* styles for containers >= 640px */
  }
}
```

### Dark Mode

```css
/* v4 uses media query by default */
.dark-mode-element {
  @apply bg-white text-slate-900;
}

@media (prefers-color-scheme: dark) {
  .dark-mode-element {
    @apply bg-slate-900 text-white;
  }
}

/* Or with class strategy (manual in @theme) */
@theme {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
}

:root {
  --background: #ffffff;
  --foreground: #0a0a0a;
}

.dark {
  --background: #0a0a0a;
  --foreground: #ffffff;
}
```

### Responsive Design with Container Queries

```tsx
<div className="@container">
  <div className="@lg:grid-cols-2 @xl:grid-cols-3">
    {/* Responsive to container, not viewport */}
  </div>
</div>
```

---

## Performance Tips

### 1. Avoid Dynamic Class Strings

```tsx
// ❌ Bad - Tailwind can't detect these
<div className={`bg-${color}-500`}>

// ✅ Good - Use static strings or variants
<div className={color === 'red' ? 'bg-red-500' : 'bg-blue-500'}>
```

### 2. Use Compositor-Only Animations

```css
/* ❌ Bad - Triggers layout */
.animate-bad {
  animation: bad 0.3s;
}
@keyframes bad {
  from { width: 0; }
  to { width: 100%; }
}

/* ✅ Good - Compositor only */
.animate-good {
  animation: good 0.3s;
}
@keyframes good {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}
```

### 3. Minimize CSS Variable Lookups

```css
/* ❌ Slower - Multiple lookups */
.element {
  background: var(--color-primary);
  border-color: var(--color-primary);
  color: var(--color-primary);
}

/* ✅ Faster - Use @apply */
.element {
  @apply bg-primary border-primary text-primary;
}
```

---

## Troubleshooting

### Common Issues

**Styles not applying:**
1. Check import order (`@import "tailwindcss"` must be first)
2. Verify `@theme` is inside the imported file
3. Check for typos in custom property names

**Dark mode not working:**
1. Verify `dark:` prefix usage
2. Check if `prefers-color-scheme` media query is working
3. If using class strategy, ensure `.dark` class is on ancestor

**Custom colors not working:**
1. Use `--color-*` naming convention
2. Check OKLCH/LCH/RGB format
3. Verify `@theme` block placement

**Build errors:**
1. Clear `.next` cache
2. Remove old v3 config files
3. Check for conflicting PostCSS plugins

