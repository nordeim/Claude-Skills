# WCAG AAA Accessibility Checklist

A comprehensive checklist for achieving WCAG AAA compliance in web interfaces.

---

## Level A Requirements (Minimum)

### Perceivable

#### 1.1 Text Alternatives
- [ ] All images have meaningful `alt` text
- [ ] Decorative images have empty `alt=""`
- [ ] Complex images have extended descriptions
- [ ] Image maps have appropriate text alternatives
- [ ] Form inputs have associated labels
- [ ] Icons used as buttons have accessible names

#### 1.2 Time-based Media
- [ ] Prerecorded audio has text transcript
- [ ] Prerecorded video has captions
- [ ] Prerecorded video has audio description
- [ ] Live audio has captions
- [ ] Live video has audio description

#### 1.3 Adaptable
- [ ] Content structure is semantic (proper heading hierarchy)
- [ ] Meaningful sequence is preserved
- [ ] Instructions don't rely solely on sensory characteristics
- [ ] Orientation is not locked to portrait/landscape
- [ ] Form inputs have visible labels
- [ ] Form inputs have accessible names

#### 1.4 Distinguishable
- [ ] Color is not the only visual means of conveying information
- [ ] Audio control is provided for auto-playing audio
- [ ] Text can be resized up to 200% without loss of content
- [ ] Text can be resized up to 200% without horizontal scrolling
- [ ] Reflow: Content reflows at 320px width
- [ ] Contrast ratio: 4.5:1 for normal text (AA), 7:1 for AAA
- [ ] Contrast ratio: 3:1 for large text (AA), 4.5:1 for AAA
- [ ] Non-text contrast: 3:1 for UI components
- [ ] Text spacing can be modified without loss of content
- [ ] Content on hover/focus is dismissable, hoverable, and persistent

### Operable

#### 2.1 Keyboard Accessible
- [ ] All functionality is keyboard accessible
- [ ] No keyboard traps
- [ ] Keyboard shortcuts can be turned off/remapped
- [ ] Character key shortcuts have modifiers

#### 2.2 Enough Time
- [ ] Time limits can be turned off, adjusted, or extended
- [ ] Moving content can be paused, stopped, or hidden
- [ ] No timing interruptions
- [ ] Re-authenticating preserves user data

#### 2.3 Seizures and Physical Reactions
- [ ] No content flashes more than 3 times per second
- [ ] Animation from interactions can be disabled

#### 2.4 Navigable
- [ ] Skip links are provided
- [ ] Pages have descriptive titles
- [ ] Focus order is logical
- [ ] Focus state is visible
- [ ] Multiple ways to find pages (navigation, search, sitemap)
- [ ] Headings and labels are descriptive
- [ ] Focus is visible on all interactive elements
- [ ] Current location is indicated in navigation

#### 2.5 Input Modalities
- [ ] Touch targets are at least 44x44 pixels
- [ ] Pointer gestures have single-pointer alternatives
- [ ] Motion-activated functions have alternatives
- [ ] Label in name: Accessible name matches visible label

### Understandable

#### 3.1 Readable
- [ ] Page language is specified (`lang` attribute)
- [ ] Language of parts is specified
- [ ] Unusual words have definitions
- [ ] Abbreviations have expansions
- [ ] Reading level is appropriate (or supplementary content provided)
- [ ] Pronunciation is available where needed

#### 3.2 Predictable
- [ ] Focus doesn't trigger context change
- [ ] Input doesn't trigger context change
- [ ] Navigation is consistent across pages
- [ ] Components are identified consistently
- [ ] Changes of context are announced

#### 3.3 Input Assistance
- [ ] Error identification is provided
- [ ] Labels or instructions are provided
- [ ] Error suggestions are provided
- [ ] Error prevention for legal/financial actions
- [ ] Help is available
- [ ] Error prevention for all actions that submit data

### Robust

#### 4.1 Compatible
- [ ] Parsing: Valid HTML
- [ ] Name, Role, Value: All UI components have accessible properties
- [ ] Status messages can be programmatically determined
- [ ] Changes in content are announced to assistive technologies

---

## Level AA Requirements

### Perceivable

#### 1.2 Time-based Media (Additional)
- [ ] Captions are live for live audio
- [ ] Audio descriptions are provided for video

#### 1.4 Distinguishable (Additional)
- [ ] Contrast ratio minimum 4.5:1 for normal text
- [ ] Contrast ratio minimum 3:1 for large text
- [ ] Text can be resized up to 200%

### Operable

#### 2.4 Navigable (Additional)
- [ ] Multiple ways to find pages within a site
- [ ] Headings and labels describe topic or purpose

### Understandable

#### 3.1 Readable (Additional)
- [ ] Language of each passage is identified

#### 3.2 Predictable (Additional)
- [ ] Navigation appears in same relative order
- [ ] Consistent identification for components with same functionality

#### 3.3 Input Assistance (Additional)
- [ ] Error suggestions provided for input errors
- [ ] Error prevention for legal/financial/submission actions

---

## Level AAA Requirements (Enhanced)

### Perceivable

#### 1.2 Time-based Media
- [ ] Sign language interpretation for prerecorded audio
- [ ] Extended audio description for prerecorded video
- [ ] Media alternative for prerecorded media

#### 1.3 Adaptable
- [ ] Instructions do not rely solely on sensory characteristics

#### 1.4 Distinguishable
- [ ] Contrast ratio minimum 7:1 for normal text
- [ ] Contrast ratio minimum 4.5:1 for large text
- [ ] Low or no background audio
- [ ] Visual presentation: Width does not exceed 80 characters
- [ ] Visual presentation: Text is not justified
- [ ] Visual presentation: Line spacing is at least 1.5
- [ ] Visual presentation: Paragraph spacing is at least 1.5x line spacing
- [ ] Visual presentation: Text can be resized to 200% without assistive tech

### Operable

#### 2.1 Keyboard Accessible
- [ ] All keyboard shortcuts can be turned off or remapped

#### 2.2 Enough Time
- [ ] Timing is not an essential part of the activity
- [ ] Interruptions can be postponed or suppressed
- [ ] Re-authenticating preserves user data for at least 20 hours

#### 2.3 Seizures and Physical Reactions
- [ ] All animations can be disabled

#### 2.4 Navigable
- [ ] Link purpose is clear from link text alone
- [ ] Section headings are provided
- [ ] A visual indication of current location is provided

#### 2.5 Input Modalities
- [ ] Touch targets are at least 44x44 CSS pixels

### Understandable

#### 3.1 Readable
- [ ] Unusual words have definitions available
- [ ] Abbreviations have expansions available
- [ ] Reading level does not exceed lower secondary education
- [ ] Pronunciation guides are available for words where meaning depends on pronunciation

#### 3.2 Predictable
- [ ] Context changes are initiated only by user request

#### 3.3 Input Assistance
- [ ] Context-sensitive help is available
- [ ] All submissions can be reversed, checked, or confirmed

---

## Implementation Code Examples

### Semantic Structure

```tsx
// Correct heading hierarchy
<main>
  <h1>Page Title</h1>
  <section>
    <h2>Section Heading</h2>
    <article>
      <h3>Article Heading</h3>
      <h4>Subsection</h4>
    </article>
  </section>
</main>
```

### Skip Links

```tsx
<a href="#main-content" className="sr-only focus:not-sr-only">
  Skip to main content
</a>

<main id="main-content">
  {/* Content */}
</main>
```

### Focus Management

```tsx
// Custom focus ring
<button className="focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 focus-visible:ring-offset-2">
  Click me
</button>

// Focus trap for modals
import { FocusTrap } from '@headlessui/react';

<Dialog>
  <FocusTrap>
    <DialogPanel>
      {/* Content */}
    </DialogPanel>
  </FocusTrap>
</Dialog>
```

### Form Accessibility

```tsx
// Accessible form field
<div>
  <label htmlFor="email" className="block mb-1 font-medium">
    Email Address <span className="text-red-500" aria-hidden="true">*</span>
  </label>
  <input
    id="email"
    type="email"
    name="email"
    required
    aria-required="true"
    aria-describedby="email-hint email-error"
    className="w-full px-3 py-2 border rounded-lg focus:ring-2 focus:ring-brand-500"
  />
  <p id="email-hint" className="text-sm text-muted-foreground mt-1">
    We'll never share your email.
  </p>
  {error && (
    <p id="email-error" role="alert" className="text-sm text-red-500 mt-1">
      {error}
    </p>
  )}
</div>
```

### Icon Button Accessibility

```tsx
// Icon-only button
<button
  aria-label="Close dialog"
  className="p-2 rounded-lg hover:bg-muted focus-visible:ring-2 focus-visible:ring-brand-500"
>
  <XIcon aria-hidden="true" className="w-5 h-5" />
</button>

// Button with visible text and icon
<button className="flex items-center gap-2">
  <SaveIcon aria-hidden="true" className="w-4 h-4" />
  <span>Save Changes</span>
</button>
```

### Screen Reader Announcements

```tsx
// Live region for announcements
<div role="status" aria-live="polite" className="sr-only">
  {statusMessage}
</div>

// Alert for errors
<div role="alert" className="text-red-500">
  {errorMessage}
</div>

// Loading state
<div role="status" aria-live="polite">
  <span className="sr-only">Loading...</span>
  <Spinner aria-hidden="true" />
</div>
```

### Reduced Motion Support

```tsx
// Hook for detecting reduced motion preference
import { useEffect, useState } from 'react';

export function useReducedMotion(): boolean {
  const [prefersReducedMotion, setPrefersReducedMotion] = useState(false);

  useEffect(() => {
    const mediaQuery = window.matchMedia('(prefers-reduced-motion: reduce)');
    setPrefersReducedMotion(mediaQuery.matches);

    const handler = (event: MediaQueryListEvent) => {
      setPrefersReducedMotion(event.matches);
    };

    mediaQuery.addEventListener('change', handler);
    return () => mediaQuery.removeEventListener('change', handler);
  }, []);

  return prefersReducedMotion;
}

// Usage
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

### Color Contrast Testing

```typescript
// Utility to check contrast ratio
function getContrastRatio(foreground: string, background: string): number {
  // Implementation using WCAG formula
  // Returns contrast ratio (e.g., 7.1)
}

// Usage
const ratio = getContrastRatio('#333333', '#ffffff');
console.log(ratio); // 12.63 - Passes AAA
```

---

## Testing Tools

### Automated Testing
- **axe DevTools**: Browser extension for automated testing
- **Lighthouse**: Built into Chrome DevTools
- **WAVE**: Web Accessibility Evaluation Tool
- **Pa11y**: Command-line accessibility tester

### Manual Testing
- **Keyboard Navigation**: Tab through entire page
- **Screen Reader Testing**: VoiceOver (Mac), NVDA (Windows)
- **Zoom Testing**: 200% zoom, reflow at 400%
- **Color Contrast**: WebAIM Contrast Checker

### Checklists
- **WebAIM WCAG Checklist**: https://webaim.org/standards/wcag/checklist
- **A11Y Project Checklist**: https://www.a11yproject.com/checklist/

