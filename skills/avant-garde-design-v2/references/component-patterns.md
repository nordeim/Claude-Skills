# Component Patterns Reference

Additional component examples and patterns for building distinctive interfaces.

---

## Navigation Patterns

### Sticky Header with Backdrop Blur

```tsx
// components/layout/Header.tsx
"use client";

import Link from "next/link";
import { DesktopNav } from "./DesktopNav";
import { MobileNav } from "./MobileNav";

export function Header() {
  return (
    <header className="sticky top-0 z-50 w-full border-b bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60">
      <div className="container-tight flex h-16 items-center justify-between">
        <Link href="/" className="font-display text-xl font-bold">
          Brand
        </Link>
        <DesktopNav />
        <MobileNav />
      </div>
    </header>
  );
}
```

### Mega Menu Navigation

```tsx
// components/layout/MegaMenu.tsx
"use client";

import * as React from "react";
import { ChevronDown } from "lucide-react";
import { cn } from "@/lib/utils";

interface MenuItem {
  label: string;
  href: string;
  description?: string;
  icon?: React.ReactNode;
}

interface MenuCategory {
  label: string;
  items: MenuItem[];
}

const CATEGORIES: MenuCategory[] = [
  {
    label: "Products",
    items: [
      {
        label: "Analytics",
        href: "/products/analytics",
        description: "Track and analyze user behavior",
      },
      {
        label: "Dashboard",
        href: "/products/dashboard",
        description: "Beautiful data visualization",
      },
    ],
  },
];

export function MegaMenu() {
  const [openCategory, setOpenCategory] = React.useState<string | null>(null);

  return (
    <nav
      className="hidden lg:flex items-center gap-1"
      onMouseLeave={() => setOpenCategory(null)}
    >
      {CATEGORIES.map((category) => (
        <div key={category.label} className="relative">
          <button
            className="flex items-center gap-1 px-4 py-2 text-sm font-medium hover:text-primary transition-colors"
            onMouseEnter={() => setOpenCategory(category.label)}
            aria-expanded={openCategory === category.label}
          >
            {category.label}
            <ChevronDown className={cn(
              "w-4 h-4 transition-transform",
              openCategory === category.label && "rotate-180"
            )} />
          </button>

          {openCategory === category.label && (
            <div className="absolute top-full left-0 w-[400px] p-4 bg-background border rounded-lg shadow-lg">
              <div className="grid gap-2">
                {category.items.map((item) => (
                  <a
                    key={item.href}
                    href={item.href}
                    className="p-3 rounded-lg hover:bg-muted transition-colors"
                  >
                    <div className="font-medium">{item.label}</div>
                    {item.description && (
                      <p className="text-sm text-muted-foreground">
                        {item.description}
                      </p>
                    )}
                  </a>
                ))}
              </div>
            </div>
          )}
        </div>
      ))}
    </nav>
  );
}
```

---

## Card Patterns

### Feature Card with Category Color

```tsx
// components/cards/FeatureCard.tsx
interface FeatureCardProps {
  title: string;
  description: string;
  category: "ai" | "cloud" | "security" | "data";
  icon: React.ReactNode;
}

const CATEGORY_STYLES = {
  ai: {
    border: "border-t-violet-500",
    badge: "bg-violet-500/10 text-violet-600",
  },
  cloud: {
    border: "border-t-cyan-500",
    badge: "bg-cyan-500/10 text-cyan-600",
  },
  security: {
    border: "border-t-emerald-500",
    badge: "bg-emerald-500/10 text-emerald-600",
  },
  data: {
    border: "border-t-amber-500",
    badge: "bg-amber-500/10 text-amber-600",
  },
};

export function FeatureCard({ title, description, category, icon }: FeatureCardProps) {
  const styles = CATEGORY_STYLES[category];

  return (
    <div className={`group relative rounded-xl border bg-card p-6 border-t-4 ${styles.border} hover:shadow-lg transition-all duration-300 hover:-translate-y-1`}>
      <div className="flex items-center gap-3 mb-4">
        <div className={`p-2 rounded-lg ${styles.badge}`}>
          {icon}
        </div>
        <span className="text-xs font-mono uppercase tracking-wider text-muted-foreground">
          {category}
        </span>
      </div>
      <h3 className="text-xl font-display font-semibold mb-2 group-hover:text-primary transition-colors">
        {title}
      </h3>
      <p className="text-muted-foreground text-sm">
        {description}
      </p>
    </div>
  );
}
```

### Testimonial Card

```tsx
// components/cards/TestimonialCard.tsx
interface TestimonialCardProps {
  quote: string;
  author: string;
  role: string;
  company: string;
  avatar?: string;
}

export function TestimonialCard({ quote, author, role, company, avatar }: TestimonialCardProps) {
  return (
    <figure className="rounded-2xl bg-muted/50 p-8">
      <blockquote className="text-lg leading-relaxed mb-6">
        "{quote}"
      </blockquote>
      <figcaption className="flex items-center gap-4">
        {avatar ? (
          <img src={avatar} alt={author} className="w-12 h-12 rounded-full object-cover" />
        ) : (
          <div className="w-12 h-12 rounded-full bg-primary/10 flex items-center justify-center">
            <span className="text-lg font-semibold text-primary">
              {author.charAt(0)}
            </span>
          </div>
        )}
        <div>
          <div className="font-semibold">{author}</div>
          <div className="text-sm text-muted-foreground">
            {role} at {company}
          </div>
        </div>
      </figcaption>
    </figure>
  );
}
```

### Pricing Card

```tsx
// components/cards/PricingCard.tsx
import { Check } from "lucide-react";
import { Button } from "@/components/ui/button";

interface PricingFeature {
  text: string;
  included: boolean;
}

interface PricingCardProps {
  name: string;
  price: string;
  period?: string;
  description: string;
  features: PricingFeature[];
  highlighted?: boolean;
  cta: string;
}

export function PricingCard({
  name,
  price,
  period = "/month",
  description,
  features,
  highlighted = false,
  cta,
}: PricingCardProps) {
  return (
    <div className={`relative rounded-2xl p-8 ${
      highlighted
        ? "bg-primary text-primary-foreground ring-2 ring-primary ring-offset-4"
        : "bg-card border"
    }`}>
      {highlighted && (
        <div className="absolute -top-3 left-1/2 -translate-x-1/2">
          <span className="bg-primary px-3 py-1 text-xs font-semibold rounded-full text-primary-foreground">
            Most Popular
          </span>
        </div>
      )}

      <div className="text-center mb-6">
        <h3 className="text-lg font-semibold mb-2">{name}</h3>
        <div className="flex items-baseline justify-center gap-1">
          <span className="text-4xl font-bold">{price}</span>
          <span className={highlighted ? "text-primary-foreground/70" : "text-muted-foreground"}>
            {period}
          </span>
        </div>
        <p className={`mt-2 text-sm ${highlighted ? "text-primary-foreground/70" : "text-muted-foreground"}`}>
          {description}
        </p>
      </div>

      <ul className="space-y-3 mb-8">
        {features.map((feature, i) => (
          <li key={i} className="flex items-start gap-3">
            <Check className={`w-5 h-5 shrink-0 ${
              feature.included
                ? highlighted ? "text-primary-foreground" : "text-primary"
                : "text-muted-foreground/30"
            }`} />
            <span className={feature.included ? "" : "text-muted-foreground line-through"}>
              {feature.text}
            </span>
          </li>
        ))}
      </ul>

      <Button
        className="w-full"
        variant={highlighted ? "default" : "outline"}
      >
        {cta}
      </Button>
    </div>
  );
}
```

---

## Section Patterns

### CTA Section

```tsx
// components/sections/CTASection.tsx
import { Button } from "@/components/ui/button";
import { ArrowRight } from "lucide-react";

interface CTASectionProps {
  title: string;
  description: string;
  primaryCTA: {
    label: string;
    href: string;
  };
  secondaryCTA?: {
    label: string;
    href: string;
  };
}

export function CTASection({ title, description, primaryCTA, secondaryCTA }: CTASectionProps) {
  return (
    <section className="relative py-20 overflow-hidden">
      {/* Background gradient */}
      <div className="absolute inset-0 bg-gradient-to-br from-primary/5 via-transparent to-transparent" />

      <div className="container-tight relative">
        <div className="max-w-3xl mx-auto text-center">
          <h2 className="text-3xl md:text-4xl font-display font-bold mb-4">
            {title}
          </h2>
          <p className="text-lg text-muted-foreground mb-8">
            {description}
          </p>
          <div className="flex flex-col sm:flex-row gap-4 justify-center">
            <Button size="lg" asChild>
              <a href={primaryCTA.href}>
                {primaryCTA.label}
                <ArrowRight className="ml-2 w-4 h-4" />
              </a>
            </Button>
            {secondaryCTA && (
              <Button size="lg" variant="outline" asChild>
                <a href={secondaryCTA.href}>
                  {secondaryCTA.label}
                </a>
              </Button>
            )}
          </div>
        </div>
      </div>
    </section>
  );
}
```

### Logo Cloud / Trust Signals

```tsx
// components/sections/LogoCloud.tsx
interface Logo {
  name: string;
  src: string;
}

interface LogoCloudProps {
  title?: string;
  logos: Logo[];
}

export function LogoCloud({ title, logos }: LogoCloudProps) {
  return (
    <section className="py-12 border-y bg-muted/30">
      <div className="container-tight">
        {title && (
          <p className="text-center text-sm font-medium text-muted-foreground mb-8">
            {title}
          </p>
        )}
        <div className="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 gap-8 items-center">
          {logos.map((logo) => (
            <div key={logo.name} className="flex items-center justify-center">
              <img
                src={logo.src}
                alt={logo.name}
                className="h-8 w-auto opacity-60 hover:opacity-100 transition-opacity grayscale hover:grayscale-0"
              />
            </div>
          ))}
        </div>
      </div>
    </section>
  );
}
```

### Stats Section

```tsx
// components/sections/StatsSection.tsx
interface Stat {
  value: string;
  label: string;
}

interface StatsSectionProps {
  stats: Stat[];
}

export function StatsSection({ stats }: StatsSectionProps) {
  return (
    <section className="py-16 bg-primary text-primary-foreground">
      <div className="container-tight">
        <div className="grid grid-cols-2 md:grid-cols-4 gap-8">
          {stats.map((stat, i) => (
            <div key={i} className="text-center">
              <div className="text-4xl md:text-5xl font-bold mb-2">
                {stat.value}
              </div>
              <div className="text-sm text-primary-foreground/80">
                {stat.label}
              </div>
            </div>
          ))}
        </div>
      </div>
    </section>
  );
}
```

---

## Form Patterns

### Search Input

```tsx
// components/ui/SearchInput.tsx
"use client";

import * as React from "react";
import { Search, X } from "lucide-react";
import { cn } from "@/lib/utils";

interface SearchInputProps extends React.InputHTMLAttributes<HTMLInputElement> {
  onClear?: () => void;
}

export const SearchInput = React.forwardRef<HTMLInputElement, SearchInputProps>(
  ({ className, value, onClear, ...props }, ref) => {
    return (
      <div className="relative">
        <Search className="absolute left-3 top-1/2 -translate-y-1/2 w-4 h-4 text-muted-foreground" />
        <input
          ref={ref}
          type="search"
          value={value}
          className={cn(
            "w-full pl-10 pr-10 py-2 rounded-lg border bg-background",
            "focus:outline-none focus:ring-2 focus:ring-primary",
            className
          )}
          {...props}
        />
        {value && onClear && (
          <button
            type="button"
            onClick={onClear}
            className="absolute right-3 top-1/2 -translate-y-1/2 p-1 rounded hover:bg-muted"
            aria-label="Clear search"
          >
            <X className="w-4 h-4" />
          </button>
        )}
      </div>
    );
  }
);

SearchInput.displayName = "SearchInput";
```

### Form Field with Error

```tsx
// components/ui/FormField.tsx
import { forwardRef, type InputHTMLAttributes } from "react";
import { cn } from "@/lib/utils";

interface FormFieldProps extends InputHTMLAttributes<HTMLInputElement> {
  label: string;
  error?: string;
  hint?: string;
}

export const FormField = forwardRef<HTMLInputElement, FormFieldProps>(
  ({ label, error, hint, className, id, ...props }, ref) => {
    const inputId = id || label.toLowerCase().replace(/\s+/g, "-");
    const errorId = `${inputId}-error`;
    const hintId = `${inputId}-hint`;

    return (
      <div className="space-y-2">
        <label htmlFor={inputId} className="block text-sm font-medium">
          {label}
        </label>
        <input
          ref={ref}
          id={inputId}
          className={cn(
            "w-full px-3 py-2 rounded-lg border bg-background",
            "focus:outline-none focus:ring-2 focus:ring-primary",
            error && "border-red-500 focus:ring-red-500",
            className
          )}
          aria-invalid={error ? "true" : "false"}
          aria-describedby={[hint && hintId, error && errorId].filter(Boolean).join(" ")}
          {...props}
        />
        {hint && !error && (
          <p id={hintId} className="text-sm text-muted-foreground">
            {hint}
          </p>
        )}
        {error && (
          <p id={errorId} role="alert" className="text-sm text-red-500">
            {error}
          </p>
        )}
      </div>
    );
  }
);

FormField.displayName = "FormField";
```

---

## Layout Patterns

### Container Variants

```tsx
// components/layout/Container.tsx
import { cn } from "@/lib/utils";

interface ContainerProps {
  children: React.ReactNode;
  className?: string;
  size?: "default" | "narrow" | "wide" | "full";
}

export function Container({ children, className, size = "default" }: ContainerProps) {
  const sizeClasses = {
    narrow: "max-w-3xl",
    default: "max-w-5xl",
    wide: "max-w-7xl",
    full: "max-w-full",
  };

  return (
    <div className={cn(
      "mx-auto px-4 sm:px-6 lg:px-8",
      sizeClasses[size],
      className
    )}>
      {children}
    </div>
  );
}
```

### Section Wrapper

```tsx
// components/layout/Section.tsx
import { cn } from "@/lib/utils";

interface SectionProps {
  children: React.ReactNode;
  className?: string;
  id?: string;
  background?: "default" | "muted" | "primary" | "dark";
}

export function Section({ children, className, id, background = "default" }: SectionProps) {
  const bgClasses = {
    default: "bg-background",
    muted: "bg-muted/30",
    primary: "bg-primary text-primary-foreground",
    dark: "bg-slate-900 text-white",
  };

  return (
    <section
      id={id}
      className={cn(
        "py-16 md:py-24 lg:py-32",
        bgClasses[background],
        className
      )}
    >
      {children}
    </section>
  );
}
```

### Grid Pattern

```tsx
// components/layout/Grid.tsx
import { cn } from "@/lib/utils";

interface GridProps {
  children: React.ReactNode;
  className?: string;
  cols?: 1 | 2 | 3 | 4;
  gap?: "sm" | "md" | "lg";
}

export function Grid({ children, className, cols = 3, gap = "md" }: GridProps) {
  const colClasses = {
    1: "grid-cols-1",
    2: "grid-cols-1 md:grid-cols-2",
    3: "grid-cols-1 md:grid-cols-2 lg:grid-cols-3",
    4: "grid-cols-1 md:grid-cols-2 lg:grid-cols-4",
  };

  const gapClasses = {
    sm: "gap-4",
    md: "gap-6 lg:gap-8",
    lg: "gap-8 lg:gap-12",
  };

  return (
    <div className={cn("grid", colClasses[cols], gapClasses[gap], className)}>
      {children}
    </div>
  );
}
```

---

## Animation Patterns

### Staggered List Animation

```tsx
// components/animations/StaggeredList.tsx
"use client";

import { motion } from "framer-motion";
import { useReducedMotion } from "@/lib/hooks/useReducedMotion";

interface StaggeredListProps {
  children: React.ReactNode[];
  className?: string;
  staggerDelay?: number;
}

export function StaggeredList({ children, className, staggerDelay = 0.1 }: StaggeredListProps) {
  const prefersReducedMotion = useReducedMotion();

  const containerVariants = {
    hidden: { opacity: prefersReducedMotion ? 1 : 0 },
    visible: {
      opacity: 1,
      transition: {
        staggerChildren: prefersReducedMotion ? 0 : staggerDelay,
      },
    },
  };

  const itemVariants = {
    hidden: { opacity: 0, y: prefersReducedMotion ? 0 : 20 },
    visible: { opacity: 1, y: 0 },
  };

  return (
    <motion.div
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: "-100px" }}
      variants={containerVariants}
      className={className}
    >
      {children.map((child, i) => (
        <motion.div key={i} variants={itemVariants}>
          {child}
        </motion.div>
      ))}
    </motion.div>
  );
}
```

### Scroll-Triggered Animation

```tsx
// components/animations/ScrollReveal.tsx
"use client";

import { motion } from "framer-motion";
import { useReducedMotion } from "@/lib/hooks/useReducedMotion";

interface ScrollRevealProps {
  children: React.ReactNode;
  className?: string;
  direction?: "up" | "down" | "left" | "right";
  delay?: number;
}

export function ScrollReveal({ children, className, direction = "up", delay = 0 }: ScrollRevealProps) {
  const prefersReducedMotion = useReducedMotion();

  const directionOffset = {
    up: { y: 40 },
    down: { y: -40 },
    left: { x: 40 },
    right: { x: -40 },
  };

  return (
    <motion.div
      initial={prefersReducedMotion ? {} : { opacity: 0, ...directionOffset[direction] }}
      whileInView={{ opacity: 1, x: 0, y: 0 }}
      viewport={{ once: true, margin: "-100px" }}
      transition={{ duration: 0.5, delay, ease: [0.4, 0, 0.2, 1] }}
      className={className}
    >
      {children}
    </motion.div>
  );
}
```

