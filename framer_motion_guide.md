# Framer Motion Animation Guide

![Framer Motion](https://img.shields.io/badge/Library-Framer%20Motion-black?style=flat-square&logo=framer)
![Platform](https://img.shields.io/badge/Platform-React-61dafb?style=flat-square&logo=react)
![Category](https://img.shields.io/badge/Guides-Animations-red?style=flat-square)

A comprehensive guide for implementing high-performance animations, layout transitions, exit animations, and accessibility-compliant motion in React using Framer Motion.

---

## Table of Contents

1. [Installation and Core API Setup](#1-installation-and-core-api-setup)
2. [Core Animation Syntax](#2-core-animation-syntax)
3. [Variants for Cleaner Layouts](#3-variants-for-cleaner-layouts)
4. [Exit Animations with AnimatePresence](#4-exit-animations-with-animatepresence)
5. [Layout Animations and Shared Elements](#5-layout-animations-and-shared-elements)
6. [Performance Optimization Best Practices](#6-performance-optimization-best-practices)
7. [Accessibility and Reduced Motion](#7-accessibility-and-reduced-motion)

---

## 1. Installation and Core API Setup

Framer Motion is built specifically for React projects.

```bash
npm install framer-motion
```

To create an animated component, prepend `motion.` to standard HTML tags (e.g., `motion.div`, `motion.button`, `motion.span`):

```tsx
import { motion } from "framer-motion";

export default function App() {
  return (
    <motion.div className="w-16 h-16 bg-blue-500 rounded-lg">
      Core Component
    </motion.div>
  );
}
```

---

## 2. Core Animation Syntax

The three primary props in Framer Motion are `initial`, `animate`, and `transition`.

### Basic Slide and Fade In
```tsx
<motion.div
  initial={{ opacity: 0, y: 20 }}
  animate={{ opacity: 1, y: 0 }}
  transition={{ duration: 0.5, ease: "easeOut" }}
  className="p-6 bg-white border rounded shadow"
>
  Card Content
</motion.div>
```

### Gestures: Hover, Tap, and Focus
```tsx
<motion.button
  whileHover={{ scale: 1.05 }}
  whileTap={{ scale: 0.95 }}
  className="px-4 py-2 bg-indigo-600 text-white rounded"
>
  Click Me
</motion.button>
```

---

## 3. Variants for Cleaner Layouts

Variants allow you to define animation states (target objects) in a separate clean structure, which separates visual styling from layout markup and automates orchestration (parent-child timing).

```tsx
const containerVariants = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: {
      staggerChildren: 0.2, // Animate children sequentially
    },
  },
};

const itemVariants = {
  hidden: { opacity: 0, y: 20 },
  visible: { opacity: 1, y: 0 },
};

export function StaggeredList() {
  return (
    <motion.ul
      variants={containerVariants}
      initial="hidden"
      animate="visible"
      className="space-y-2"
    >
      <motion.li variants={itemVariants} className="p-3 bg-gray-100 rounded">
        First Item
      </motion.li>
      <motion.li variants={itemVariants} className="p-3 bg-gray-100 rounded">
        Second Item
      </motion.li>
      <motion.li variants={itemVariants} className="p-3 bg-gray-100 rounded">
        Third Item
      </motion.li>
    </motion.ul>
  );
}
```

---

## 4. Exit Animations with AnimatePresence

React components unmount immediately without waiting for CSS transitions to finish. Wrap conditional blocks inside `<AnimatePresence>` to enable exit animations.

```tsx
import { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";

export function ToggleCard() {
  const [isVisible, setIsVisible] = useState(true);

  return (
    <div className="flex flex-col items-center">
      <button onClick={() => setIsVisible(!isVisible)} className="mb-4">
        Toggle
      </button>

      <AnimatePresence mode="wait">
        {isVisible && (
          <motion.div
            initial={{ opacity: 0, scale: 0.8 }}
            animate={{ opacity: 1, scale: 1 }}
            exit={{ opacity: 0, scale: 0.8 }}
            transition={{ duration: 0.2 }}
            className="w-64 h-32 bg-green-500 rounded-lg"
          />
        )}
      </AnimatePresence>
    </div>
  );
}
```

### Exit Modes
* `mode="sync"` (default): Animates entering and exiting components simultaneously.
* `mode="wait"`: Waits for the exiting component to complete its exit transition before starting the entry transition.
* `mode="popLayout"`: Pop exiting components out of the document layout flow, preventing adjacent content from shifting during exit.

---

## 5. Layout Animations and Shared Elements

### Fluid Layout Transitions
Simply adding the `layout` prop to any motion element makes it automatically animate position and scale adjustments when the wrapper layout modifications take place.

```tsx
<motion.div layout className="p-4 bg-white rounded-lg">
  <p>Expanding card content that resizes smoothly.</p>
</motion.div>
```

### Shared Layout Animations
To morph one element into another across different components, assign them matching `layoutId` values inside an `<AnimatePresence>` context. This is highly useful for navigating header pill indicators.

```tsx
import { useState } from "react";
import { motion } from "framer-motion";

export function ActiveTabs() {
  const [activeTab, setActiveTab] = useState("Home");
  const tabs = ["Home", "Profile", "Settings"];

  return (
    <div className="flex space-x-2">
      {tabs.map((tab) => (
        <button
          key={tab}
          onClick={() => setActiveTab(tab)}
          className="relative px-4 py-2 text-sm font-medium z-10"
        >
          {activeTab === tab && (
            <motion.div
              layoutId="active-pill"
              className="absolute inset-0 bg-blue-100 rounded-full -z-10"
              transition={{ type: "spring", stiffness: 380, damping: 30 }}
            />
          )}
          {tab}
        </button>
      ))}
    </div>
  );
}
```

---

## 6. Performance Optimization Best Practices

Animations that trigger browser recalculations (reflows) can cause CPU lag. Implement these optimizations to maintain high performance.

### Animating GPU-Friendly Properties
* **Do Animate**: `opacity`, `transform` (x, y, scale, rotate, scaleX, scaleY). These are composite-only properties handled by the GPU.
* **Do Not Animate**: `width`, `height`, `top`, `left`, `margin`, `padding`. These properties trigger browser layout changes on every frame.

### Skipping React Re-renders
For high-frequency events (like scroll tracking or dragging), do not save values in React state. Use `useMotionValue` and `useTransform` to bind values directly without triggering React re-renders.

```tsx
import { useScroll, useTransform, motion } from "framer-motion";

export function ScrollProgressBar() {
  const { scrollYProgress } = useScroll();
  // Map scroll progress (0 to 1) to horizontal scale (0% to 100%)
  const scaleX = useTransform(scrollYProgress, [0, 1], ["0%", "100%"]);

  return (
    <motion.div
      style={{ scaleX }}
      className="fixed top-0 left-0 right-0 h-1 bg-blue-600 origin-left"
    />
  );
}
```

### Code Splitting with LazyMotion
By default, Framer Motion imports the full animation engine (which can bloat bundle sizes). Use `<LazyMotion>` to only load required features.

```tsx
import { LazyMotion, domAnimation, m } from "framer-motion";

export function PerformanceApp() {
  return (
    <LazyMotion features={domAnimation}>
      {/* Use m.div instead of motion.div */}
      <m.div animate={{ x: 100 }} />
    </LazyMotion>
  );
}
```

---

## 7. Accessibility and Reduced Motion

Users can toggle settings on their operating systems to reduce screen movement. Ensure your animations honor these settings.

```tsx
import { motion, useReducedMotion } from "framer-motion";

export function AccessibleCard() {
  const shouldReduceMotion = useReducedMotion();

  // If user requests reduced motion, fade in static rather than sliding
  const animateState = shouldReduceMotion 
    ? { opacity: 1 } 
    : { opacity: 1, y: 0 };

  const initialState = shouldReduceMotion 
    ? { opacity: 0 } 
    : { opacity: 0, y: 50 };

  return (
    <motion.div
      initial={initialState}
      animate={animateState}
      className="p-6 bg-white rounded shadow"
    >
      Accessible content panel.
    </motion.div>
  );
}
```
