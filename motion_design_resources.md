# Interactive Motion & Motion Design Resource Directory

![Motion Design](https://img.shields.io/badge/Motion-Design%20%26%20Interactive-e74c3c?style=flat-square)
![Resources](https://img.shields.io/badge/Resources-Curated%20Directory-3498db?style=flat-square)
![Access](https://img.shields.io/badge/Access-Free%20%2F%20Open%20Source-2ecc71?style=flat-square)

A curated collection of free websites, animation libraries, SVG rendering engines, timeline editors, WebGL utilities, and motion design inspiration catalogs to build high-end interactive interfaces.

---

## UI/UX Guidelines for Motion Design

Motion design should enhance usability, not degrade it. Keep these fundamental laws in mind:

1.  **Motion is Functional**: Do not animate purely for decoration. Good animation guides user attention (e.g., highlighting a primary CTA), explains spatial relationships (e.g., a card expanding into a modal), and provides feedback (e.g., button presses).
2.  **Timing & Durations**: 
    *   **Micro-interactions** (button hover, switch toggle): `100ms - 200ms`.
    *   **Mid-level UI transitions** (drawer slide-in, tooltip reveal): `250ms - 400ms`.
    *   **Large scale viewport movements** (page fades, layout shifts): `400ms - 600ms`.
3.  **Use Hardware-Accelerated Properties**: Only animate CSS `transform` (scale, translate, rotate) and `opacity`. Animating properties like `width`, `height`, `margin`, or `top`/`left` forces the browser's layout engine to redraw, causing performance lag.
4.  **Support Accessibility (a11y)**: Respect the `prefers-reduced-motion` settings of your users. If animation is essential for conveying information, make sure static alternatives are provided.

---

## Categories

- [1. Web Animation Libraries (Code Primitives)](#1-web-animation-libraries-code-primitives)
- [2. Interactive 3D & WebGL Tools](#2-interactive-3d--webgl-tools)
- [3. Lottie & Vector Animation Repositories](#3-lottie--vector-animation-repositories)
- [4. CSS Animation Generators & Timeline Editors](#4-css-animation-generators--timeline-editors)
- [5. Motion Design Inspiration Galleries](#5-motion-design-inspiration-galleries)

---

## 1. Web Animation Libraries (Code Primitives)
*The programming engines used to drive complex timelines, spring physics, layout morphing, and interactive canvas components.*

*   **[GSAP (GreenSock Animation Platform)](https://gsap.com/)** *(Free Core library)*
    *   **Focus**: Ultra-high-performance timeline animations.
    *   **Why use it**: The industry standard for complex interactive sequences, canvas renderings, and scroll-driven page animations. GSAP’s ScrollTrigger plugin is the premier tool for building high-end storytelling sites.
*   **[Framer Motion](https://www.framer.com/motion/)** *(Free)*
    *   **Focus**: Declarative animation engine for React.
    *   **Why use it**: Perfect for React apps. It supports layout transitions, gestural triggers (hover, tap, pan), keyframe configurations, and exit animations seamlessly out-of-the-box.
*   **[Motion One](https://motion.dev/)** *(Free)*
    *   **Focus**: Animation engine built directly on the Web Animations API (WAAPI).
    *   **Why use it**: Super tiny bundle footprint (under 6kb) while matching or beating the performance of larger libraries. Perfect for lightweight UI interactions.
*   **[Anime.js](https://animejs.com/)** *(Free)*
    *   **Focus**: Lightweight JavaScript animation library.
    *   **Why use it**: Excellent for SVG path morphing, line drawing animations, and grid/stagger calculations in vanilla JS.
*   **[Theatre.js](https://www.theatrejs.com/)** *(Free)*
    *   **Focus**: Motion design editor with programmatic API.
    *   **Why use it**: Provides a visual workspace (like After Effects or Blender) directly in your browser. You can design camera moves and 3D rigs visually, then load the coordinates into your site code.

---

## 2. Interactive 3D & WebGL Tools
*Tools that bring 3D elements, physics environments, and WebGL rendering shaders into the web interface.*

*   **[Spline 3D](https://spline.design/)** *(Free Tier)*
    *   **Focus**: Collaborative 3D web design editor.
    *   **Why use it**: The absolute best tool for developers who want to add interactive 3D elements without writing thousands of lines of Three.js. Export directly to Web Components, React components, or raw iframe embeds.
*   **[React Three Fiber](https://r3f.docs.pmnd.rs/)** *(Free)*
    *   **Focus**: React wrapper for Three.js.
    *   **Why use it**: Allows you to construct Three.js 3D scenes declaratively inside a standard React component tree.
*   **[Shadertoy](https://www.shadertoy.com/)** *(Free)*
    *   **Focus**: WebGL fragment shader code compiler.
    *   **Why use it**: A gallery of creative GLSL code examples. You can study mathematical pixel logic to create custom landing page particle noise patterns, water ripples, and background warps.

---

## 3. Lottie & Vector Animation Repositories
*Websites providing pre-made, scale-independent vector icons and character animations that run at 60fps via JSON/JSON-LD.*

*   **[LottieFiles](https://lottiefiles.com/)** *(Free Tier)*
    *   **Focus**: Community repository of Lottie (JSON) animations.
    *   **Why use it**: Browse and download thousands of free animations. Modify animation colors directly in the browser editor before downloading code wrappers.
*   **[Rive](https://rive.app/)** *(Free Tier)*
    *   **Focus**: Real-time vector animation tool and interactive runtime.
    *   **Why use it**: Rive is the modern successor to Flash. It creates complex, state-machine-driven vector animations that respond to clicks, pointer moves, or custom input variables with incredibly small file sizes.
*   **[Lordicon](https://lordicon.com/)** *(Free Tier)*
    *   **Focus**: Animated SVG icon catalog.
    *   **Why use it**: Provides a comprehensive pack of interactive vector icons. Set loop conditions, click play loops, or hover triggers directly inside the embed settings.

---

## 4. CSS Animation Generators & Timeline Editors
*Visual prototyping tools that auto-generate CSS `@keyframes` or cubic-bezier curves for developer integration.*

*   **[Animista](https://animista.net/)** *(Free)*
    *   **Focus**: Code playground for CSS animation presets.
    *   **Why use it**: Quickly test and configure entrance/exit motions, text shimmers, card bounces, and flip animations. Output raw CSS keyframe code instantly.
*   **[Keyframes.app](https://keyframes.app/)** *(Free)*
    *   **Focus**: Browser timeline editor for custom keyframes.
    *   **Why use it**: An animation GUI allowing you to adjust multiple keyframe steps (0% to 100%) and watch the live preview before copying the compiled CSS.
*   **[Cubic-Bezier.com](https://cubic-bezier.com/)** *(Free)*
    *   **Focus**: Visual curve comparison playground.
    *   **Why use it**: Adjust bezier handles to create custom timing curves (anticipation, spring overshoot) and preview how they behave in comparison to standard CSS curves like `ease-in` or `linear`.

---

## 5. Motion Design Inspiration Galleries
*Portals showing creative implementation of interactive animations on production websites to reference for layouts and designs.*

*   **[Godly](https://godly.website/)** *(Free)*
    *   **Focus**: Premium interactive web showcase.
    *   **Why use it**: High-end landing page inspiration featuring advanced GSAP triggers, WebGL scenes, custom cursor interactions, and layout transitions.
*   **[Codrops Blueprints](https://tympanus.net/codrops/)** *(Free)*
    *   **Focus**: Highly creative experimental frontend concepts.
    *   **Why use it**: Excellent tutorials and source code downloads for advanced layouts (grid morphing, page transitions, text hover warps, custom sliders).
*   **[Hover.dev](https://www.hover.dev/)** *(Free Code Snippets)*
    *   **Focus**: Tailwind and Framer Motion components repository.
    *   **Why use it**: Provides copy-pasteable snippets for custom hover grids, navigation dropdown animations, magnetic buttons, and visual reveals.
*   **[CodePen](https://codepen.io/)** *(Free)*
    *   **Focus**: Open-source frontend design playground.
    *   **Why use it**: Search terms like "mouse trail", "spring physics", or "svg path reveal" to clone and dissect production-ready animation experiments written by elite developers.
