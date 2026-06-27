# Graphs & Data Visualization Library Directory

A curated resource index of the best free, open-source charting libraries, dashboard component packages, and low-level data visualization primitives for web applications.

---

## 📊 UI/UX Guidelines for Data Visualization

Designing usable charts requires balancing visual aesthetics with high information density:

1.  **Select the Right Chart Type**:
    *   **Line Charts**: Trends over time (continuous datasets).
    *   **Bar Charts**: Comparing separate categories (discrete datasets).
    *   **Area Charts**: Accumulation or volume trends over time.
    *   **Pie/Donut Charts**: Parts-of-a-whole comparisons *(limit to < 5 slices; otherwise use a bar chart)*.
2.  **Color Accessibility (Contrast)**: Ensure color palettes have distinct contrast. Do not rely on color alone to differentiate data series—use varying stroke patterns (dashed, dotted) or layout grids.
3.  **Tooltip vs. Static Labels**: Use interactive tooltips to show precise value coordinates on hover, keeping the main chart clean. Provide static data labels only if there are few data points (< 10 total).
4.  **Responsive Handling**: Charts must adapt fluidly to screen width changes. Wrap Canvas/SVG grids inside responsive wrappers and dynamically truncate axis labels on small mobile screens.

---

## 📂 Categories

- [1. React-Specific Chart Libraries (Declarative & Easy)](#1-react-specific-chart-libraries-declarative--easy)
- [2. Tailwind CSS-Native Dashboard Systems](#2-tailwind-css-native-dashboard-systems)
- [3. High-Performance & Massive Dataset Engines](#3-high-performance--massive-dataset-engines)
- [4. Low-Level Primitives for Custom Design Systems](#4-low-level-primitives-for-custom-design-systems)
- [5. Cross-Platform Chart Libraries (Web & Mobile)](#5-cross-platform-chart-libraries-web--mobile)

---

## 1. React-Specific Chart Libraries (Declarative & Easy)
*Best for modern React web applications that need standard interactive charts with quick setup.*

*   **[Recharts](https://recharts.org/)**
    *   **Rendering**: SVG.
    *   **Key Strengths**: Extremely popular, declarative component layout. Written with native React bindings over D3 computations. Very easy to customize styling and animation attributes.
    *   **License**: MIT.
*   **[shadcn/ui Charts](https://ui.shadcn.com/docs/components/chart)**
    *   **Rendering**: SVG (Built on top of Recharts).
    *   **Key Strengths**: The shadcn implementation provides a thin, composable wrapper in your local files (`components/ui/chart.tsx`). It features built-in theme color support (using CSS variables) and responsive tooltip components that match shadcn's visual aesthetic out of the box.
    *   **License**: MIT.
*   **[Nivo](https://nivo.rocks/)**
    *   **Rendering**: SVG, HTML, or Canvas (based on needs).
    *   **Key Strengths**: Beautiful defaults with motion physics built-in. Provides unique data representations like Sunbursts, Chord diagrams, calendars, and Choropleth maps.
    *   **License**: MIT.

---

## 2. Tailwind CSS-Native Dashboard Systems
*Best for rapid building of admin dashboard mockups using pre-designed components styled with Tailwind utility classes.*

*   **[Tremor](https://tremor.so/)**
    *   **Rendering**: SVG (uses Recharts internally).
    *   **Key Strengths**: Provides pre-configured, complete charting cards (e.g. AreaChart, BarChart, LineChart) and matching indicators (badges, cards, legend trackers) designed specifically for dashboard layout assembly. Styling is done via Tailwind variables.
    *   **License**: Apache 2.0.

---

## 3. High-Performance & Massive Dataset Engines
*Best for real-time applications, financial market charts, and dashboard portals loading thousands of concurrent data coordinates.*

*   **[Apache ECharts](https://echarts.apache.org/)**
    *   **Rendering**: Canvas or SVG (supports toggle).
    *   **Key Strengths**: A powerhouse created by Baidu and maintained by Apache. It handles millions of data points effortlessly using a lightweight Canvas grid. Offers extensive configurations, advanced data zooming sliders, and built-in 3D charts.
    *   **License**: Apache 2.0.
*   **[Chart.js / react-chartjs-2](https://www.chartjs.org/)**
    *   **Rendering**: Canvas.
    *   **Key Strengths**: Classic, highly reliable, and very lightweight. It offers a simple, configuration-object API that is highly familiar to web developers. `react-chartjs-2` is the React wrapper package.
    *   **License**: MIT.

---

## 4. Low-Level Primitives for Custom Design Systems
*Best for design teams building a bespoke charting system from scratch where standard charts do not meet specific layout grids.*

*   **[Visx (by Airbnb)](https://airbnb.io/visx/)**
    *   **Rendering**: SVG.
    *   **Key Strengths**: A collection of small, unopinionated React components for rendering SVG shapes, axes, layouts, grids, and paths. It handles the math and structure while letting you decide the final visual output and styling. Highly performant since you only import the individual packages you need (e.g., `@visx/grid`, `@visx/axis`).
    *   **License**: MIT.
*   **[D3.js](https://d3js.org/)**
    *   **Rendering**: HTML, SVG, Canvas.
    *   **Key Strengths**: The foundation of nearly all web data visualizations. It is not a charting library, but a data-manipulation library. Extremely powerful for custom, complex interactive visual math.
    *   **License**: ISC.

---

## 5. Cross-Platform Chart Libraries (Web & Mobile)
*Best for projects sharing charting code across a web portal (React) and a companion mobile app (React Native).*

*   **[Victory](https://formidable.com/open-source/victory/)**
    *   **Rendering**: SVG.
    *   **Key Strengths**: Maintained by Formidable. It provides identical component APIs for web wrappers (`victory`) and mobile Native wrappers (`victory-native`), facilitating smooth cross-platform sharing of business charting logic.
    *   **License**: MIT.
