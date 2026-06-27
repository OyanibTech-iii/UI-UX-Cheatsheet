# Inverted Corners & Reverse Border Radius UI Guide

This guide covers resources, libraries, and real-world examples for implementing the **rounded soft inverted corner** (also known as *concave corners*, *scooped corners*, or *reverse border radius*).

---

## 1. Top React Components & Libraries

While there isn't a single official "native" React package for inverted corners, several utility packages and UI frameworks specialize in this aesthetic:

### A. Arwes (Sci-Fi Web Framework)
*   **Website:** [arwes.dev](https://arwes.dev)
*   **GitHub:** [github.com/arwes/arwes](https://github.com/arwes/arwes)
*   **Description:** A complete futuristic React UI framework based on cyberpunk designs, telemetry layouts, and high-tech HUD systems. It features components with animated borders, glowing lines, and custom notched/inverted layouts.

### B. Tailwind CSS Inverted Radius Plugins
*   **Libraries:** `tailwindcss-inverted-radius` & `tailwindcss-mask-image`
*   **Usage:** These plugins extend Tailwind's core utility classes, providing class names like `rounded-r-in-md` or custom radial mask utility shapes so you can build responsive concave borders without writing inline CSS.

### C. react-native-curved-bottom-bar
*   **GitHub:** [github.com/hoaphantn7604/react-native-curved-bottom-bar](https://github.com/hoaphantn7604/react-native-curved-bottom-bar)
*   **Description:** A highly popular navigation bar utility for React Native developers that implements a soft, curved bottom bar with an inverted border radius housing a circular action floating button.

---

## 2. In-Depth React & CSS Code Implementation

Here is a ready-to-use React component that creates a seamless tab bar with soft inverted corners where the active tab blends into the content area below it.

### The React Tab Component (`InvertedTab.tsx`)
```tsx
import React, { useState } from 'react';

interface TabProps {
  label: string;
  isActive: boolean;
  onClick: () => void;
}

export const Tab: React.FC<TabProps> = ({ label, isActive, onClick }) => {
  return (
    <button
      onClick={onClick}
      className={`relative px-6 py-3 font-sans text-sm font-semibold transition-all duration-200 
        ${isActive 
          ? 'bg-zinc-900 text-cyan-400' 
          : 'bg-zinc-950 text-zinc-400 hover:text-zinc-200'}`}
    >
      {label}
      {/* Inverted Corner Connectors (Only visible on the active tab) */}
      {isActive && (
        <>
          {/* Left Inverted Corner */}
          <span className="absolute bottom-0 -left-[16px] w-[16px] h-[16px] bg-zinc-900 overflow-hidden pointer-events-none">
            <span className="absolute bottom-0 right-0 w-[32px] h-[32px] rounded-full bg-zinc-950 border border-zinc-900" />
          </span>
          {/* Right Inverted Corner */}
          <span className="absolute bottom-0 -right-[16px] w-[16px] h-[16px] bg-zinc-900 overflow-hidden pointer-events-none">
            <span className="absolute bottom-0 left-0 w-[32px] h-[32px] rounded-full bg-zinc-950 border border-zinc-900" />
          </span>
        </>
      )}
    </button>
  );
};

export const InvertedTabsDemo: React.FC = () => {
  const [activeTab, setActiveTab] = useState<number>(0);
  const tabs = ['Dashboard', 'Security', 'Telemetry', 'Logs'];

  return (
    <div className="w-full max-w-lg bg-zinc-950 p-6 rounded-xl border border-zinc-800">
      {/* Tab Header Row */}
      <div className="flex border-b border-zinc-900">
        {tabs.map((tab, idx) => (
          <Tab
            key={idx}
            label={tab}
            isActive={activeTab === idx}
            onClick={() => setActiveTab(idx)}
          />
        ))}
      </div>
      {/* Content Frame (Flush with Active Tab) */}
      <div className="bg-zinc-900 border border-zinc-800 p-6 rounded-b-lg rounded-tr-lg text-zinc-300">
        <h3 className="text-lg font-bold text-white mb-2">{tabs[activeTab]} Content</h3>
        <p className="text-sm">
          Notice how the active tab blends into the background of this main card with a soft, 
          inverted circular transition at the corners.
        </p>
      </div>
    </div>
  );
};
```

---

## 3. Real-World Websites Using This Aesthetic

### A. Linear (`linear.app`)
Linear's dashboard and landing pages are widely praised for their visual polish. They employ a subtle inverted border radius at the bottom corners of active tabs, creating a tab-to-frame transition that feels continuous.

### B. Vercel Dashboard (`vercel.com/dashboard`)
Vercel uses soft inverted-radius tabs for their main project navigation. When a project is active, the tab has a soft background that curves down into the border below it.

### C. Steam Big Picture & Steam Deck UI
Valve's handheld interface features soft, large-radius inverted notches at the bottom of navigation items, highlighting the active game or library menu panel.

### D. Apple macOS Dock
The macOS Dock uses an inverted-radius connection layout when files are dragged near the trash can or separators, showing a physical notch that bends inward around dock tiles.

---

## 4. Useful CSS Generator Tools

*   **Corner Inverter Tool:** A web utility designed to visually adjust sliders for corner shapes (convex vs. concave) and copy the CSS masking codes.
*   **CSS Clippy:** A generator showing how to use `clip-path` parameters (`polygon()`, `ellipse()`) to slice custom geometric corners in CSS.
