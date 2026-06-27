# Icon Libraries & SVG Illustration Directory

![Assets](https://img.shields.io/badge/Assets-Icons%20%26%20Illustrations-e74c3c?style=flat-square)
![Formats](https://img.shields.io/badge/Formats-SVG%20%26%20Vector-27ae60?style=flat-square)
![License](https://img.shields.io/badge/License-MIT%20%2F%20CC0-34495e?style=flat-square)

A curated list of the best free, open-source icon libraries, SVG illustration packages, and aggregator tools for UI/UX designers and web developers.

---

## Best Practices for Using Icons in UI/UX

Before choosing a library, keep these fundamental design guidelines in mind:

1.  **Visual Consistency**: Never mix different icon families within the same application interface. Ensure all icons share the same stroke weight (e.g., 2px), corner radius (rounded vs. sharp), and fill style (outline vs. solid).
2.  **Stroke Scale Bounds**: Use SVGs that scale vector paths cleanly. Set `vector-effect="non-scaling-stroke"` in CSS/SVG properties if you want the stroke weight to remain constant regardless of size scaling.
3.  **Click Target (Fitts's Law)**: If an icon serves as an interactive button, ensure its bounding target area is at least **44x44px** (on mobile screens) or **32x32px** (on desktop views), even if the visual icon size is smaller (e.g., 16px or 20px).
4.  **Semantic Naming & a11y**: Always provide a screen reader label (`aria-label` or `<span class="sr-only">`) for icon-only buttons (e.g., a magnifying glass icon button needs a label of "Search").

---

## Categories

- [1. Core UI Icon Libraries (Modern & Consistent)](#1-core-ui-icon-libraries-modern--consistent)
- [2. Massive Scale & Framework Libraries](#2-massive-scale--framework-libraries)
- [3. Icon Aggregators & SVG Search Engines](#3-icon-aggregators--svg-search-engines)
- [4. SVG Illustration Libraries (Customizable & Free)](#4-svg-illustration-libraries-customizable--free)
- [5. Hand-Drawn & Abstract Elements](#5-hand-drawn--abstract-elements)

---

## 1. Core UI Icon Libraries (Modern & Consistent)
*Highly recommended for modern SaaS apps, dashboard software, and complex web tools where visual consistency is crucial.*

*   **[Lucide Icons](https://lucide.dev/)**
    *   **Style**: Clean, balanced, modern outline style.
    *   **Highlights**: Community-driven evolution of the famous *Feather Icons*. Extremely lightweight, supports tree-shaking, and provides official wrapper libraries for React, Vue, Svelte, Angular, and React Native.
    *   **License**: MIT (Free for personal & commercial use).
*   **[Heroicons](https://heroicons.com/)**
    *   **Style**: Solid, Outline, Mini (20x20), and Micro (16x16) styles.
    *   **Highlights**: Created by the makers of Tailwind CSS. Designed specifically to pair with modern web dashboards and forms.
    *   **License**: MIT.
*   **[Phosphor Icons](https://phosphoricons.com/)**
    *   **Style**: 6 distinct weights (Thin, Light, Regular, Bold, Fill, Duotone).
    *   **Highlights**: Excellent for mobile product design due to its weight range. You can match the icon thickness perfectly to your typography weights.
    *   **License**: MIT.
*   **[Tabler Icons](https://tabler.io/icons)**
    *   **Style**: Clean outline, highly structural.
    *   **Highlights**: Offers over 5,200+ highly consistent icons. Perfect for data-heavy dashboard panels and enterprise platforms.
    *   **License**: MIT.
*   **[Iconoir](https://iconoir.com/)**
    *   **Style**: Minimalist, thin geometric outline.
    *   **Highlights**: One of the fastest-growing open-source libraries. Over 1,600+ icons, zero dependencies, support for CSS, React, React Native, Figma, and Flutter.
    *   **License**: MIT.

---

## 2. Massive Scale & Framework Libraries
*Best when you need a huge variety of specialized icons and reliable standards.*

*   **[Google Material Symbols & Icons](https://fonts.google.com/icons)**
    *   **Style**: Outlined, Rounded, Sharp, Two-Tone.
    *   **Highlights**: Google's official design system library. Provides massive coverage of categories. "Symbols" are modern and support variable font parameters (weight, grade, fill, optical size) directly in CSS.
    *   **License**: Apache 2.0.
*   **[Remix Icon](https://remixicon.com/)**
    *   **Style**: Neutrally designed, open-source editor icons in both Outline and Solid variants.
    *   **Highlights**: Excellent coverage of tech brands, document tools, and editor tools. Very clean alignment.
    *   **License**: Apache 2.0.
*   **[Boxicons](https://boxicons.com/)**
    *   **Style**: Rounded, friendly vector style in Solid, Regular (Outline), and Brand categories.
    *   **Highlights**: High-quality standard web icons designed to fit comfortably with clean, playful interfaces.
    *   **License**: CC 4.0 / SIL OFL.

---

## 3. Icon Aggregators & SVG Search Engines
*Best for searching across multiple libraries simultaneously, matching multiple collections, or looking for specific standalone SVG assets.*

*   **[Iconify](https://iconify.design/)**
    *   **Search Engine**: Search through 100+ icon sets (including Lucide, Material Icons, FontAwesome, etc.) at once.
    *   **Highlights**: Provides universal framework components and allows you to import only the icons you use on-demand.
*   **[SVG Repo](https://www.svgrepo.com/)**
    *   **Search Engine**: A database of over 500,000 free SVG icons and vectors.
    *   **Highlights**: Built-in SVG editing features (flip, rotate, adjust colors) directly on the website before downloading. Has a great filter for selecting only "Monocolor" or "Multicolor" sets.
*   **[Icons8](https://icons8.com/icons)**
    *   **Search Engine**: Massive library organized by distinct visual genres (e.g., iOS style, Fluent style, Doodle style).
    *   **Highlights**: Offers consistent aesthetic packs. Note that the free tier may require link attribution.

---

## 4. SVG Illustration Libraries (Customizable & Free)
*Vector illustrations designed to fill empty landing page blocks, user onboarding cards, success states, and empty states.*

*   **[unDraw](https://undraw.co/illustrations)**
    *   **Style**: Clean flat, minimalist flat vector scenes.
    *   **Highlights**: Built-in color customization. You can paste your brand's Hex color code directly on the site, and the entire catalog instantly updates to match your palette.
    *   **License**: Free for personal/commercial use (No attribution required).
*   **[Storyset](https://storyset.com/)**
    *   **Style**: Modern corporate flat, organized into 5 design personalities (Rafiki, Bro, Amico, Pana, Cuate).
    *   **Highlights**: Highly interactive customization. You can hide specific layers, change colors, and animate elements before exporting as SVG, PNG, or GIF/Lottie.
    *   **License**: Free with attribution to Freepik.
*   **[DrawKit](https://www.drawkit.io/)**
    *   **Style**: Mixed vector illustrations, both hand-drawn and flat graphic packs.
    *   **Highlights**: Releases packs based on specific projects (e.g., Finance, Tech, Medical, Remote Work). Includes both free and premium items.
    *   **License**: Free for personal & commercial projects.
*   **[ManyPixels Gallery](https://www.manypixels.co/gallery)**
    *   **Style**: Curated flat vectors, outline vectors, isometric shapes.
    *   **Highlights**: Similar to unDraw, includes a color picker tool to custom color-match SVG files instantly.
    *   **License**: Free (No attribution required).

---

## 5. Hand-Drawn & Abstract Elements
*Playful, human, or artistic style components to break visual monotony.*

*   **[Open Doodles](https://www.opendoodles.com/)**
    *   **Style**: Playful, raw hand-drawn cartoon characters.
    *   **Highlights**: Created by Pablo Stanley. Add sketch humans to landing pages or loading panels for a friendly, warm voice.
    *   **License**: CC0 (Public Domain / Free for any use).
*   **[Absurd Design](https://absurd.design/)**
    *   **Style**: Surrealist, abstract, experimental sketches.
    *   **Highlights**: Combines hand-drawn creativity with digital minimalism. Perfect for high-end web portals that want to break away from typical "tech-flat" visual styles.
    *   **License**: Free for personal & commercial use with attribution.
*   **[Highlights Design](https://www.highlights.design/)**
    *   **Style**: Sketch annotations (underlines, circles, squiggles, stars).
    *   **Highlights**: Perfect for UI designers who want to accent text headings, badges, or buttons with hand-drawn focus marks.
    *   **License**: CC0 (Public Domain).
