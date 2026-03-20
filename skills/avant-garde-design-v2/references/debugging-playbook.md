# Debugging Playbook

Detailed workflows for debugging common frontend issues.

---

## Visual Debugging Protocol

### Master Decision Tree

When an element is not appearing as expected, follow this decision tree:

```
Step 1: Is element present in DOM?
│
├─ NO → Component not rendering
│   └─ Check: conditional rendering logic, props, state
│       - console.log() component before return
│       - Check parent component's render conditions
│       - Verify imports are correct
│
└─ YES → Continue to Step 2

Step 2: Is it hidden by computed CSS?
│
├─ YES → CSS hiding the element
│   └─ Check in DevTools → Computed:
│       - display: none → Find which rule sets it
│       - visibility: hidden → Find which rule sets it
│       - opacity: 0 → Find which rule sets it
│       - width/height: 0 → Find which rule sets it
│       - clip-path: inset(100%) → Find which rule sets it
│
└─ NO → Continue to Step 3

Step 3: Is it off-screen or clipped?
│
├─ YES → Positioning issue
│   └─ Check:
│       - position: absolute/fixed with wrong coordinates
│       - transform: translate with wrong values
│       - overflow: hidden on ancestor clipping content
│       - Negative margins pushing off-screen
│       - z-index stacking context issues
│
└─ NO → Continue to Step 4

Step 4: Is it behind another layer?
│
├─ YES → Z-index or stacking context issue
│   └─ Check:
│       - z-index value of element and siblings
│       - Parent stacking contexts (transform, opacity < 1, z-index)
│       - Positioning context (position: relative/absolute/fixed)
│       - Use 3D view in DevTools to see layers
│
└─ NO → Continue to Step 5

Step 5: Is JS failing to toggle state?
│
├─ YES → JavaScript/React issue
│   └─ Check:
│       - Console for errors
│       - Event listeners attached correctly
│       - State not updating (missing dependency, stale closure)
│       - Hydration mismatch (server/client HTML differs)
│
└─ NO → Continue to Step 6

Step 6: Production-only issue?
│
└─ Check:
    - Tailwind class extraction (no dynamic strings)
    - CSS purging important classes
    - Build process stripping code
    - Environment variables missing
```

---

## Mobile Navigation Debugging

### Symptom: Nav Not Visible on Mobile

#### Check 1: Viewport Meta Tag

```html
<!-- REQUIRED in <head> -->
<meta name="viewport" content="width=device-width, initial-scale=1">
```

**How to check:**
1. Open DevTools → Elements
2. Search for `<meta name="viewport"`
3. Verify content attribute exists

#### Check 2: Breakpoint Symmetry

```tsx
// ✅ Correct: Symmetrical breakpoints
<nav className="hidden md:flex">...</nav>  // Desktop
<button className="md:hidden">Menu</button>  // Mobile trigger

// ❌ Wrong: Asymmetrical (desktop hides, no mobile trigger)
<nav className="hidden md:flex">...</nav>  // Desktop hides on mobile
{/* No mobile trigger! */}
```

**How to check:**
1. Use DevTools device toolbar
2. Resize to mobile width
3. Verify mobile trigger appears
4. Verify desktop nav disappears

#### Check 3: State Management

```tsx
// Debug state changes
const [isOpen, setIsOpen] = useState(false);

// Add debug logging
useEffect(() => {
  console.log('Mobile nav state:', isOpen);
}, [isOpen]);

// Check click handler
<Button onClick={() => {
  console.log('Toggle clicked, current state:', isOpen);
  setIsOpen(!isOpen);
}}>
```

#### Check 4: Z-Index Stack

```css
/* Typical z-index scale */
.modal-overlay { z-index: 400; }
.modal-content { z-index: 500; }
.dropdown { z-index: 200; }
.sticky-header { z-index: 300; }
```

**How to check:**
1. Inspect mobile nav element
2. Check computed z-index
3. Check siblings and ancestors for higher z-index
4. Check for stacking contexts (transform, opacity < 1 on ancestors)

### Symptom: Mobile Menu Opens Then Closes Immediately

**Cause:** Click-outside handler fires on the same click that opened the menu.

**Solution:**

```tsx
// ❌ Wrong: Trigger is inside the "outside" area
<div ref={containerRef}>
  <button onClick={toggle}>Menu</button>
  {isOpen && <nav>...</nav>}
</div>
// Clicking button opens menu, but containerRef detects "outside" click

// ✅ Correct: Exclude trigger from outside detection
<div ref={containerRef}>
  <button onClick={toggle} ref={triggerRef}>Menu</button>
  {isOpen && <nav>...</nav>}
</div>

// In useClickOutside hook
useEffect(() => {
  const handler = (e: MouseEvent) => {
    // Exclude trigger from detection
    if (triggerRef.current?.contains(e.target as Node)) return;
    if (containerRef.current?.contains(e.target as Node)) return;
    setIsOpen(false);
  };
  // Use mousedown instead of click for faster response
  document.addEventListener('mousedown', handler);
  return () => document.removeEventListener('mousedown', handler);
}, []);
```

### Symptom: Mobile Menu Not Scrollable

**Cause:** Body scroll not locked or overflow issues.

**Solution:**

```tsx
// Lock body scroll when modal opens
useEffect(() => {
  if (isOpen) {
    const originalStyle = window.getComputedStyle(document.body).overflow;
    document.body.style.overflow = 'hidden';
    return () => {
      document.body.style.overflow = originalStyle;
    };
  }
}, [isOpen]);

// Or use a library
import { useLockBodyScroll } from '@/lib/hooks/useLockBodyScroll';

function MobileMenu({ isOpen }) {
  useLockBodyScroll(isOpen);
  // ...
}
```

---

## Tailwind CSS Debugging

### Symptom: Styles Not Applying

#### Check 1: Class Name Syntax

```tsx
// ❌ Wrong: v3 syntax in v4
<div className="bg-opacity-50">
<div className="bg-[--custom-color]">

// ✅ Correct: v4 syntax
<div className="bg-primary/50">
<div className="bg-(--custom-color)">
```

#### Check 2: Dynamic Class Strings

```tsx
// ❌ Tailwind can't detect these at build time
<div className={`bg-${color}-500`}>
<div className={`p-${size}`}>

// ✅ Use static strings or safelist
<div className={color === 'red' ? 'bg-red-500' : 'bg-blue-500'}>
<div className={size === 'lg' ? 'p-8' : 'p-4'}>

// Or use CSS variables for dynamic values
<div style={{ '--color': color }} className="bg-[var(--color)]">
```

#### Check 3: Content Configuration

```javascript
// postcss.config.mjs - Ensure correct setup
export default {
  plugins: ["@tailwindcss/postcss"],
};

// Check content paths in v4 (if using custom paths)
// In your CSS file:
@source "../node_modules/my-lib/**/*.{js,ts,jsx,tsx}";
```

### Symptom: Dark Mode Not Working

#### Check 1: Dark Mode Configuration

```css
/* v4: Dark mode works via media query by default */
@media (prefers-color-scheme: dark) {
  .dark-mode-element {
    @apply bg-slate-900 text-white;
  }
}

/* Or use class-based dark mode */
.dark .dark-mode-element {
  @apply bg-slate-900 text-white;
}
```

#### Check 2: Class Application

```tsx
// For class-based dark mode, ensure class is on <html> or <body>
// Usually handled by next-themes or similar

import { ThemeProvider } from 'next-themes';

<ThemeProvider attribute="class">
  {children}
</ThemeProvider>
```

### Symptom: Custom Colors Not Working

```css
/* ❌ Wrong: Not using --color-* naming */
@theme {
  --brand-primary: oklch(0.5 0.2 250);
}

/* ✅ Correct: Use --color-* prefix */
@theme {
  --color-brand-primary: oklch(0.5 0.2 250);
}

/* Usage */
<div className="bg-brand-primary"> <!-- Now works! -->
```

---

## Animation Debugging

### Symptom: Animations Janky/Stuttering

#### Check 1: Properties Being Animated

```css
/* ❌ Bad: Triggers layout (reflow) */
@keyframes bad {
  from { width: 0; }
  to { width: 100%; }
}
@keyframes bad2 {
  from { top: 0; left: 0; }
  to { top: 100px; left: 100px; }
}

/* ✅ Good: Compositor-only properties */
@keyframes good {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}
@keyframes good2 {
  from { transform: translate(0, 0); }
  to { transform: translate(100px, 100px); }
}
```

**Properties safe to animate:**
- `transform` (all functions)
- `opacity`

**Properties to avoid animating:**
- `width`, `height`
- `top`, `left`, `right`, `bottom`
- `margin`, `padding`
- `font-size`

#### Check 2: Will-Change Hint

```css
/* Add will-change for complex animations */
.animated-element {
  will-change: transform, opacity;
}

/* Remove after animation completes */
.animated-element:not(.animating) {
  will-change: auto;
}
```

#### Check 3: Reduced Motion Preference

```tsx
// Always check for reduced motion preference
import { useReducedMotion } from '@/lib/hooks/useReducedMotion';

function AnimatedComponent() {
  const prefersReducedMotion = useReducedMotion();

  return (
    <motion.div
      initial={prefersReducedMotion ? {} : { opacity: 0 }}
      animate={{ opacity: 1 }}
      transition={{ duration: prefersReducedMotion ? 0 : 0.5 }}
    >
      Content
    </motion.div>
  );
}
```

### Symptom: Animation Not Running

#### Check 1: Keyframes Definition

```css
/* Ensure keyframes are defined in @theme */
@theme {
  --animate-custom: custom 1s ease-in-out;

  @keyframes custom {
    from { opacity: 0; }
    to { opacity: 1; }
  }
}

/* Usage */
<div className="animate-custom">
```

#### Check 2: Animation Fill Mode

```tsx
// Element snaps back after animation
// Add fill mode to preserve final state
<motion.div
  initial={{ opacity: 0 }}
  animate={{ opacity: 1 }}
  // Framer Motion handles this by default
/>

// CSS alternative
.element {
  animation: fadeIn 0.5s forwards; /* forwards preserves final state */
}
```

---

## React/Next.js Debugging

### Symptom: Hydration Mismatch

```
Error: Hydration failed because the initial UI does not match what was rendered on the server.
```

**Common Causes:**

1. **Browser-only APIs during SSR:**
```tsx
// ❌ Wrong: Date is different on server vs client
<span>{new Date().toLocaleString()}</span>

// ✅ Correct: Use useEffect for client-only rendering
const [date, setDate] = useState('');
useEffect(() => {
  setDate(new Date().toLocaleString());
}, []);
return <span>{date}</span>;
```

2. **Random values during SSR:**
```tsx
// ❌ Wrong
<div id={`item-${Math.random()}`}>

// ✅ Correct: Use useId hook
const id = useId();
<div id={`item-${id}`}>
```

3. **localStorage/sessionStorage during SSR:**
```tsx
// ❌ Wrong: Crashes on server
const theme = localStorage.getItem('theme');

// ✅ Correct: Check for window
const [theme, setTheme] = useState('light');
useEffect(() => {
  setTheme(localStorage.getItem('theme') || 'light');
}, []);
```

### Symptom: Component Not Re-rendering

#### Check 1: State Mutation

```tsx
// ❌ Wrong: Mutating state directly
const handleClick = () => {
  items.push(newItem);
  setItems(items);
};

// ✅ Correct: Create new reference
const handleClick = () => {
  setItems([...items, newItem]);
};
```

#### Check 2: Object/Array Dependencies

```tsx
// ❌ Wrong: New object on every render
useEffect(() => {
  // ...
}, [{ id: 1 }]); // New object every render!

// ✅ Correct: Use primitive values
useEffect(() => {
  // ...
}, [id]);

// Or memoize
const config = useMemo(() => ({ id }), [id]);
useEffect(() => {
  // ...
}, [config]);
```

### Symptom: useEffect Running Multiple Times

#### Check 1: Strict Mode

```tsx
// React 18 Strict Mode runs effects twice in dev
// This is expected behavior - do not remove Strict Mode!

// Ensure cleanup functions are implemented
useEffect(() => {
  const controller = new AbortController();

  fetchData({ signal: controller.signal });

  return () => controller.abort();
}, []);
```

---

## Performance Debugging

### Tool: React DevTools Profiler

1. Install React DevTools browser extension
2. Open DevTools → Profiler tab
3. Click record, interact with page
4. Analyze flame graph for slow components

### Tool: Chrome DevTools Performance

1. Open DevTools → Performance tab
2. Click record, interact with page
3. Look for:
   - Long tasks (>50ms)
   - Layout shifts
   - Large repaints

### Tool: Lighthouse

```bash
# Run Lighthouse from CLI
npx lighthouse http://localhost:3000 \
  --chrome-flags="--headless" \
  --only-categories=performance,accessibility,best-practices,seo \
  --output=html \
  --output-path=./lighthouse-report.html
```

### Common Performance Issues

| Issue | Symptom | Solution |
|-------|---------|----------|
| Large bundle | Slow initial load | Code splitting, lazy loading |
| Unnecessary re-renders | Sluggish interactions | useMemo, useCallback, React.memo |
| Layout thrashing | Janky scrolling | Batch DOM reads/writes |
| Memory leaks | Increasing memory over time | useEffect cleanup |
| Heavy images | Slow LCP | Next.js Image, lazy loading |

