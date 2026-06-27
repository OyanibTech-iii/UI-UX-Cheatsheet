# Tailwind CSS Cheat Sheet

![Tailwind CSS](https://img.shields.io/badge/CSS-Tailwind%20CSS-38bdf8?style=flat-square&logo=tailwind-css)
![Version](https://img.shields.io/badge/Version-v3%20%2F%20v4-blue?style=flat-square)
![Category](https://img.shields.io/badge/Guides-Cheat%20Sheet-orange?style=flat-square)

A comprehensive guide for Tailwind CSS installation, core use cases, theme extensions, custom font configurations, and advanced 3D transforms.

---

## Table of Contents

1. [Installation and Setup](#1-installation-and-setup)
2. [Core Use Cases and Layout Snippets](#2-core-use-cases-and-layout-snippets)
3. [Theme Customization](#3-theme-customization)
4. [Custom Fonts Configuration](#4-custom-fonts-configuration)
5. [Advanced 3D Transform Utilities](#5-advanced-3d-transform-utilities)

---

## 1. Installation and Setup

Tailwind CSS can be integrated via several methods depending on the development stack.

### Method A: CSS-First Setup (Tailwind v4)
In Tailwind v4, configuration is handled directly in your main CSS file without requiring a JavaScript configuration file.

1. Install the CLI package:
   ```bash
   npm install tailwindcss @tailwindcss/vite
   ```
2. Import Tailwind directly in your primary entry CSS file (e.g., `app.css`):
   ```css
   @import "tailwindcss";
   ```

### Method B: JavaScript Config Setup (Tailwind v3)
Tailwind v3 uses a dedicated configuration file to extend theme parameters.

1. Install the dependencies:
   ```bash
   npm install -D tailwindcss postcss autoprefixer
   npx tailwindcss init -p
   ```
2. Configure template paths in `tailwind.config.js`:
   ```javascript
   /** @type {import('tailwindcss').Config} */
   module.exports = {
     content: [
       "./index.html",
       "./src/**/*.{js,ts,jsx,tsx}",
     ],
     theme: {
       extend: {},
     },
     plugins: [],
   }
   ```
3. Add the directives to your global CSS file:
   ```css
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
   ```

---

## 2. Core Use Cases and Layout Snippets

### Flexbox Centering
```html
<div class="flex items-center justify-center min-h-screen">
  <p>Centered Content</p>
</div>
```

### Responsive Grid
Auto-adjusting grid columns based on screen sizes:
```html
<div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
  <div class="p-4 border rounded">Item 1</div>
  <div class="p-4 border rounded">Item 2</div>
  <div class="p-4 border rounded">Item 3</div>
  <div class="p-4 border rounded">Item 4</div>
</div>
```

### Hover and Focus States (With Transitions)
Smooth button interaction styling:
```html
<button class="px-4 py-2 bg-blue-600 text-white rounded transition-colors duration-200 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2">
  Interactive Button
</button>
```

### Dark Mode Support
Apply styles prefixing with `dark:`:
```html
<div class="bg-white text-gray-900 dark:bg-gray-950 dark:text-gray-50 p-6 rounded-lg shadow">
  <h2 class="text-xl font-bold">Theme-Adaptive Card</h2>
  <p class="text-sm mt-2 text-gray-500 dark:text-gray-400">Content scales to system dark settings.</p>
</div>
```

---

## 3. Theme Customization

### Configuring in Tailwind v4 (CSS-Based)
Use the `@theme` directive in your main CSS file:
```css
@import "tailwindcss";

@theme {
  --color-brand-primary: #3b82f6;
  --color-brand-secondary: #1d4ed8;
  --spacing-18: 4.5rem;
  --radius-custom: 12px;
}
```
*Usage in HTML*: `<div class="bg-brand-primary p-18 rounded-custom">...</div>`

### Configuring in Tailwind v3 (JavaScript-Based)
Modify `tailwind.config.js` to add custom colors, spacings, or border radiuses:
```javascript
module.exports = {
  theme: {
    extend: {
      colors: {
        brand: {
          primary: '#3b82f6',
          secondary: '#1d4ed8',
        },
      },
      spacing: {
        '18': '4.5rem',
      },
      borderRadius: {
        'custom': '12px',
      }
    },
  },
}
```
*Usage in HTML*: `<div class="bg-brand-primary p-18 rounded-custom">...</div>`

---

## 4. Custom Fonts Configuration

### Step 1: Import the Font Family
Import the external font in your entry CSS file:
```css
@import url("https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;700&display=swap");
```

### Step 2: Configure the Utilities

#### In Tailwind v4:
Map the imported family to a font variable in your CSS `@theme` block:
```css
@theme {
  --font-display: "Outfit", sans-serif;
}
```

#### In Tailwind v3:
Extend the `fontFamily` configurations in `tailwind.config.js`:
```javascript
module.exports = {
  theme: {
    extend: {
      fontFamily: {
        display: ['Outfit', 'sans-serif'],
      },
    },
  },
}
```

#### Using Arbitrary Font Values (Quick Setup):
If you do not want to configure the font globally, you can invoke it in-line:
```html
<h1 class="font-['Outfit'] font-bold">Display Heading</h1>
```

---

## 5. Advanced 3D Transform Utilities

Standard 3D effects require enabling 3D render space (using perspective depth) on a parent wrapper, then translating or rotating elements on the child components.

### 3D Custom Utilities Setup

#### Setup in Tailwind v4:
```css
@theme {
  --perspective-dramatic: 500px;
  --perspective-normal: 1000px;
}

@utility transform-3d {
  transform-style: preserve-3d;
}

@utility backface-hidden {
  backface-visibility: hidden;
}
```

#### Setup in Tailwind v3:
Since v3 does not natively support 3D utilities in the theme configuration, add them as custom utilities using a plugin, or define them in your global CSS file:
```css
@layer utilities {
  .perspective-dramatic {
    perspective: 500px;
  }
  .perspective-normal {
    perspective: 1000px;
  }
  .transform-3d {
    transform-style: preserve-3d;
  }
  .backface-hidden {
    backface-visibility: hidden;
  }
}
```

### 3D Code Snippet: Interactive 3D Card Flip
An interactive HTML snippet that flips a card 180 degrees on hover:

```html
<!-- Parent container providing perspective depth -->
<div class="perspective-normal w-80 h-48 cursor-pointer group">
  <!-- Inner container establishing 3D space -->
  <div class="relative w-full h-full duration-500 transform-3d transition-transform group-hover:[transform:rotateY(180deg)]">
    
    <!-- Card Front Side -->
    <div class="absolute inset-0 w-full h-full bg-blue-600 text-white rounded-xl p-6 flex flex-col justify-between backface-hidden">
      <div>
        <p class="text-xs uppercase tracking-widest opacity-75">Credit Card</p>
        <h3 class="text-lg font-bold mt-1">Design Studio</h3>
      </div>
      <div class="flex justify-between items-end">
        <span class="text-sm">**** **** **** 4242</span>
        <span class="text-xs">12/28</span>
      </div>
    </div>

    <!-- Card Back Side (pre-rotated 180 degrees) -->
    <div class="absolute inset-0 w-full h-full bg-gray-900 text-white rounded-xl p-6 flex flex-col justify-between backface-hidden [transform:rotateY(180deg)]">
      <div class="w-full h-8 bg-black -mx-6 mt-2"></div>
      <div class="flex justify-end items-center mt-4">
        <div class="bg-white text-black px-2 py-1 text-xs font-mono rounded">123</div>
      </div>
      <p class="text-[10px] opacity-50 text-center">Authorized Signature Only</p>
    </div>

  </div>
</div>
```

### 3D Arbitrary Properties
To rotate or translate components on specific coordinates without writing custom utility classes, use inline arbitrary values:
* Rotate on X axis: `[transform:rotateX(45deg)]`
* Rotate on Y axis: `[transform:rotateY(-30deg)]`
* Translate depth (Z-axis): `[transform:translateZ(50px)]`
* Adjust Perspective: `perspective-[750px]`
