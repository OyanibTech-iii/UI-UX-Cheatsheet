# Tailwind CSS Cursor & Pointer Tracking Effects

A comprehensive guide to constructing modern, interactive cursor-tracking and spotlight-reveal effects using Tailwind CSS utilities, CSS custom variables, and optimized Vanilla JavaScript.

---

## Table of Contents

1. [Introduction to Pointer Tracking](#1-introduction-to-pointer-tracking)
2. [Performance & Best Practices (60fps Motion)](#2-performance--best-practices-60fps-motion)
3. [Spotlight and Radial-Gradient Reveal Effects](#3-spotlight-and-radial-gradient-reveal-effects)
4. [Custom Cursor Elements](#4-custom-cursor-elements)
5. [Magnetic Snap Utilities](#5-magnetic-snap-utilities)
6. [Interactive Components & Snippets](#6-interactive-components--snippets)

---

## 1. Introduction to Pointer Tracking

Pointer tracking involves updating element positions, gradients, or masks based on the real-time coordinates of a user's mouse/pointer device. 

In Tailwind CSS, pointer tracking is typically accomplished by:
1. Monitoring mouse movements via a JavaScript event listener (`mousemove` or `pointermove`).
2. Writing the current coordinates into CSS custom variables (`--mouse-x`, `--mouse-y`) on the parent wrapper.
3. Leveraging Tailwind's arbitrary properties to consume those variables (e.g., `bg-[at_var(--mouse-x)_var(--mouse-y)]` or `[transform:translate3d(var(--mouse-x),var(--mouse-y),0)]`).

---

## 2. Performance & Best Practices (60fps Motion)

Animating elements relative to mouse movement can lead to performance bottlenecks (layout thrashing) if not handled properly. Follow these rules:

*   **Avoid Top/Left Modification**: Never animate elements using `top` and `left` properties. This triggers full layout reflows. Instead, use 3D hardware-accelerated transforms like `translate3d()` or `transform: translate(x, y)`.
*   **Throttle / requestAnimationFrame**: If calculating heavy physics (like elastic trailing), throttle the callback inside a `requestAnimationFrame` loop.
*   **Respect Accessibility**: Disabling cursor custom effects on touch devices (mobile/tablets) is mandatory, as they do not have true hover states. Use Tailwind's `pointer-events-none` and hover queries.
*   **Reduced Motion**: Always respect the `prefers-reduced-motion` media query using Tailwind's `motion-reduce:` modifier.

---

## 3. Spotlight and Radial-Gradient Reveal Effects

A popular pattern in SaaS landing pages is the "spotlight grid card" or "card border glow" where a radial gradient follows the user's cursor.

### Core Setup

We bind a mousemove listener on a container and write coordinates as percentages or pixel offsets:

```html
<div 
  id="spotlight-card"
  class="relative h-64 w-96 rounded-2xl border border-white/10 bg-zinc-950 p-6 overflow-hidden group"
  onmousemove="
    const rect = this.getBoundingClientRect();
    const x = event.clientX - rect.left;
    const y = event.clientY - rect.top;
    this.style.setProperty('--mouse-x', `${x}px`);
    this.style.setProperty('--mouse-y', `${y}px`);
  "
>
  <!-- Spotlight Overlay -->
  <div class="absolute inset-0 -opacity-0 transition-opacity duration-300 group-hover:opacity-100 pointer-events-none bg-[radial-gradient(600px_circle_at_var(--mouse-x)_var(--mouse-y),rgba(255,255,255,0.06),transparent_40%)]"></div>

  <!-- Content -->
  <div class="relative z-10">
    <h3 class="text-white font-semibold">Hover Spotlight Card</h3>
    <p class="text-sm text-zinc-400 mt-2">The subtle backing glow tracks the cursor inside this container dynamically.</p>
  </div>
</div>
```

---

## 4. Custom Cursor Elements

To create a fully custom cursor (a circle that replaces the system mouse), we first hide the default pointer and overlay a hardware-accelerated element tracking coordinates globally.

### Configuration

1. Hide default cursor globally:
   ```html
   <body class="lg:cursor-none">
   ```
2. Place a fixed custom cursor dot:
   ```html
   <div 
     id="custom-cursor" 
     class="hidden lg:block fixed top-0 left-0 w-6 h-6 rounded-full border border-white mix-blend-difference pointer-events-none z-50 -translate-x-1/2 -translate-y-1/2 will-change-transform"
   ></div>
   ```
3. Update its transform in JavaScript:
   ```javascript
   const cursor = document.getElementById('custom-cursor');
   
   document.addEventListener('pointermove', (e) => {
     cursor.style.transform = `translate3d(${e.clientX}px, ${e.clientY}px, 0)`;
   });
   ```

### State Modification (Hovering Links)
Make the cursor expand or change blend modes when hovering interactive elements.

*   **HTML target**: `<a href="#" class="cursor-trigger">Link</a>`
*   **Script**:
    ```javascript
    const interactiveElements = document.querySelectorAll('a, button, [role="button"]');
    interactiveElements.forEach(el => {
      el.addEventListener('pointerenter', () => cursor.classList.add('scale-150', 'bg-white'));
      el.addEventListener('pointerleave', () => cursor.classList.remove('scale-150', 'bg-white'));
    });
    ```

---

## 5. Magnetic Snap Utilities

Magnetic components pull themselves towards the cursor once the pointer gets within a certain radius. This creates a highly satisfying "click feel" on premium buttons.

```html
<button
  class="magnetic-button relative px-6 py-3 bg-white text-black font-semibold rounded-lg will-change-transform transition-transform duration-200 ease-out"
  onmousemove="
    const rect = this.getBoundingClientRect();
    const x = event.clientX - rect.left - rect.width/2;
    const y = event.clientY - rect.top - rect.height/2;
    // Move button 35% of the distance to the mouse
    this.style.transform = `translate3d(${x * 0.35}px, ${y * 0.35}px, 0)`;
  "
  onmouseleave="
    this.style.transform = 'translate3d(0, 0, 0)';
  "
>
  Magnetic CTA
</button>
```

---

## 6. Interactive Components & Snippets

Below are production-ready code setups showing advanced implementations of pointer-tracking designs.

### Snippet A: Modern Grid Border Spotlight Glow (SaaS Cards)
This snippet maps the cursor over a parent grid, lighting up the borders of child cards as the pointer glides over them.

```html
<div 
  class="grid grid-cols-1 md:grid-cols-2 gap-4 max-w-2xl group/grid"
  onmousemove="
    const cards = this.querySelectorAll('.spotlight-card');
    for (const card of cards) {
      const rect = card.getBoundingClientRect();
      const x = event.clientX - rect.left;
      const y = event.clientY - rect.top;
      card.style.setProperty('--mouse-x', `${x}px`);
      card.style.setProperty('--mouse-y', `${y}px`);
    }
  "
>
  <!-- Card 1 -->
  <div class="spotlight-card relative bg-zinc-900 border border-zinc-800 rounded-xl p-6 overflow-hidden">
    <!-- Border Mask Glow -->
    <div class="absolute inset-0 opacity-0 group-hover/grid:opacity-100 pointer-events-none transition-opacity duration-300 bg-[radial-gradient(350px_circle_at_var(--mouse-x)_var(--mouse-y),rgba(99,102,241,0.15),transparent_80%)]"></div>
    <div class="relative z-10">
      <div class="text-indigo-400 font-bold mb-2">01</div>
      <h3 class="text-white font-medium text-lg">Serverless DB</h3>
      <p class="text-sm text-zinc-400 mt-1">Scale up your instances instantly without cluster setup overhead.</p>
    </div>
  </div>

  <!-- Card 2 -->
  <div class="spotlight-card relative bg-zinc-900 border border-zinc-800 rounded-xl p-6 overflow-hidden">
    <!-- Border Mask Glow -->
    <div class="absolute inset-0 opacity-0 group-hover/grid:opacity-100 pointer-events-none transition-opacity duration-300 bg-[radial-gradient(350px_circle_at_var(--mouse-x)_var(--mouse-y),rgba(99,102,241,0.15),transparent_80%)]"></div>
    <div class="relative z-10">
      <div class="text-indigo-400 font-bold mb-2">02</div>
      <h3 class="text-white font-medium text-lg">Edge Cache</h3>
      <p class="text-sm text-zinc-400 mt-1">Deliver data globally at sub-millisecond response rates.</p>
    </div>
  </div>
</div>
```

---

### Snippet B: Cursor Follower Trail (Elastic Physics)
A dual-dot cursor tracking layout. A tiny dot reacts immediately, while a larger outer circle catches up with a dampening delay (elastic trailing effect).

```html
<!-- HTML cursor nodes -->
<div id="dot-cursor" class="fixed w-2 h-2 bg-indigo-500 rounded-full pointer-events-none z-50 -translate-x-1/2 -translate-y-1/2 will-change-transform"></div>
<div id="ring-cursor" class="fixed w-8 h-8 border border-indigo-500/50 rounded-full pointer-events-none z-50 -translate-x-1/2 -translate-y-1/2 will-change-transform"></div>

<script>
  const dot = document.getElementById('dot-cursor');
  const ring = document.getElementById('ring-cursor');

  let mouse = { x: 0, y: 0 }; // Current mouse coordinates
  let ringPos = { x: 0, y: 0 }; // Outer circle coordinates

  document.addEventListener('mousemove', (e) => {
    mouse.x = e.clientX;
    mouse.y = e.clientY;
    dot.style.transform = `translate3d(${mouse.x}px, ${mouse.y}px, 0)`;
  });

  // Smooth animation loop using interpolation (lerp)
  function render() {
    // Lerp formula: current + (target - current) * speed
    ringPos.x += (mouse.x - ringPos.x) * 0.15;
    ringPos.y += (mouse.y - ringPos.y) * 0.15;

    ring.style.transform = `translate3d(${ringPos.x}px, ${ringPos.y}px, 0)`;
    
    requestAnimationFrame(render);
  }
  
  // Start the frame loop
  render();
</script>
```

---

### Snippet C: Interactive Card Hover Tilt & Shine
This combines cursor coordinate tracking with a rotation matrix to tilt a card in 3D space, creating a realistic "sholographic foil" shine.

```html
<div 
  class="w-80 h-48 bg-gradient-to-br from-zinc-800 to-zinc-950 border border-zinc-700/50 rounded-2xl shadow-xl transition-all duration-200 ease-out preserve-3d cursor-pointer relative overflow-hidden"
  style="perspective: 1000px;"
  onmousemove="
    const rect = this.getBoundingClientRect();
    const x = event.clientX - rect.left;
    const y = event.clientY - rect.top;
    
    // Normalize coordinates around the card center (values range from -0.5 to 0.5)
    const px = (x / rect.width) - 0.5;
    const py = (y / rect.height) - 0.5;
    
    // Tilt intensity parameters (max 15 degrees)
    const rotateY = px * 30; 
    const rotateX = -py * 30; 
    
    this.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
    
    // Calculate light reflection position
    this.style.setProperty('--shine-x', `${x}px`);
    this.style.setProperty('--shine-y', `${y}px`);
  "
  onmouseleave="
    // Return to flat state
    this.style.transform = 'rotateX(0deg) rotateY(0deg)';
  "
>
  <!-- Foil Shine Layer -->
  <div class="absolute inset-0 pointer-events-none opacity-40 mix-blend-color-dodge bg-[radial-gradient(150px_circle_at_var(--shine-x)_var(--shine-y),rgba(255,255,255,0.4),transparent_80%)]"></div>

  <!-- Content -->
  <div class="p-6 flex flex-col justify-between h-full select-none">
    <span class="text-zinc-500 font-mono tracking-widest text-xs">MEMBER CARD</span>
    <span class="text-white font-medium tracking-wide">SHOLOGRAPHIC STUDIO</span>
  </div>
</div>
```
