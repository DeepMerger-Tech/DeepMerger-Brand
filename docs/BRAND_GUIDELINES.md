DeepMerger Design Architecture

This document defines the visual infrastructure of DeepMerger. Adhering to these guidelines ensures our brand remains consistent, authoritative, and instantly recognizable across all deployment environments, from high-density data dashboards to public-facing repositories.

## 1. Brand Philosophy

Our visual identity mirrors the nature of our tech stack: **strictly minimalist, monochromatic, and precise.** We rely on stark contrasts, sharp geometric alignment, and the complete absence of unnecessary visual noise. Form follows function. Every pixel and vector path serves a purpose.

## 2. The Logo System

Core Brand assets are located in the `logos/` directory. All primary marks are engineered as scalable vector graphics (`.svg`) with `shape-rendering="geometricPrecision"` to ensure flawless, artifact-free scaling from massive displays down to microscopic UI elements.

### 2.1 The Full Signature (`logo-full-light.svg` / `logo-full-dark.svg`)
The primary expression of the DeepMerger identity. It structurally balances the geometric icon with our custom-tuned typographic wordmark.
* **Engineering Note:** The typography has been meticulously refined—specifically the structural weight, continuous curvature, and negative space of the initial "D"—to eliminate visual bumps and ensure perfect harmony with the icon's sharp angles.
* **Deployment:** Primary use for web headers, official documentation, pitch decks, and broad external communications.
* **Clear Space:** Always maintain a protective margin of clear space around the logo equal to the exact height of the "D" in the wordmark.

### 2.2 The Geometric Mark (`logo-icon-light.svg` / `logo-icon-dark.svg`)
The standalone geometric icon. It is designed with continuous, fluid path transitions and perfect node alignment.
* **Deployment:** Utilize when real estate is severely constrained or when the brand context is heavily established (e.g., application interfaces, floating action buttons, minimalistic footers, and avatars).

### 2.3 The Wordmark (`logo-text-only-light.svg` / `logo-text-only-dark.svg`)
The standalone typography, optimized for high-contrast legibility. 
* **Deployment:** Best utilized alongside partner logos, in dense repository layouts, or complex UI environments where the geometric mark would introduce visual redundancy.

---

## 3. Structural Rules & Integrity

To maintain the authority of the brand, the logo must never be compromised.

### DO
* **Respect Contrast:** Use the **Light** variations (black paths, `#030303`) exclusively on pure white or highly light-grey backgrounds. Use the **Dark** variations (white paths, `#FFFFFF`) on pitch black or dark-grey backgrounds.
* **Lock Aspect Ratios:** Always scale the SVG assets proportionately. 
* **Maintain Orientation:** Keep the logo strictly horizontal on a 0-degree axis.

### DON'T
* **Do not alter the colour space.** The logo architecture is binary—strictly black or strictly white. Never apply gradients, drop shadows, or accent colours to the vector paths.
* **Do not stretch, skew, or distort** the geometric proportions.
* **Do not place over complex imagery.** If overlaying on a photograph or complex terrain map, ensure a heavily darkened or lightened protective gradient is placed beneath the logo to guarantee absolute contrast.

---

## 4. The Colour System

DeepMerger relies on a strict, high-contrast monochromatic OKLCH palette to reduce cognitive load and prioritize data parsing.

| Infrastructure Role | Light Mode (OKLCH) | Dark Mode (OKLCH) | Hex Equivalent (Approx) |
| :--- | :--- | :--- | :--- |
| **Base / Canvas** | `oklch(1 0 0)` | `oklch(0.07 0 0)` | `#FFFFFF` / `#121212` |
| **Primary Foreground** | `oklch(0.07 0 0)` | `oklch(0.97 0 0)` | `#121212` / `#F8F8F8` |
| **Muted / Boundaries** | `oklch(0.96 0 0)` | `oklch(0.15 0 0)` | `#F5F5F5` / `#262626` |

---

## 5. Typography Standards

**Primary Typeface: Inter**
*(System Fallbacks: `-apple-system`, `system-ui`, `sans-serif`)*

Our typography must reflect the density and speed of our intelligence infrastructure. 
* **Headings:** Deploy Semi-Bold or Bold weights with slightly tightened tracking (`letter-spacing: -0.02em` to `-0.04em`). This compacts the text, conveying intelligence and authority.
* **Body & UI:** Deploy Regular or Medium weights with standard tracking for optimal, fatigue-free readability over long sessions.
* **Data Streams:** For tabular data, hex codes, or code snippets, default to a clean monospaced font (e.g., `JetBrains Mono` or system `monospace`).

---

## 6. Production Asset Pipeline

While native `.svg` rendering is mandatory for our codebase to ensure crisp Retina display performance, external deployment platforms (legacy browsers, Slack/Discord link previews, iOS manifests) require specific rasterized formats.

Follow this pipeline to generate production-ready assets:

### Pipeline A: Automated Web Conversion (Rapid Deployment)
1. Navigate to a robust generator like [Favicon.io](https://favicon.io/favicon-converter/) or [RealFaviconGenerator.net](https://realfavicongenerator.net/).
2. Upload the `logo-icon-dark.svg` (or light variant) from the `brand_assets` repository.
3. Extract the generated `.zip` archive, which compiles:
    * `favicon.ico` (Browser tab targeting)
    * `apple-touch-icon.png` (iOS PWA manifests)
    * `android-chrome-192x192.png` and `512x512.png` (Android Web App manifests)
4. Commit these assets directly to the `public/` directory of your frontend architecture.

### Pipeline B: Figma Rendering (Precision Control & OpenGraph)
1. Initialize a new canvas in [Figma](https://www.figma.com).
2. Import the native `.svg` source files.
3. **Favicon Extraction:** Create a `512x512` Frame. Center the `logo-icon-only-dark.svg` within it. Export as `@1x PNG`.
4. **OpenGraph (Social) Metadata:** Create a `1200x630` Frame. Fill the background with canvas dark (`#121212`). Center the `logo-full-dark.svg` on both the X and Y axis. Export as `@1x PNG` to use as the default image for Twitter, LinkedIn, and Discord link unfurling.

> **Developer Note:**
> Always implement the `.svg` format natively in your React/Vite components (e.g., `<img src={Logo} />` or inline `<svg>`). Only utilize `.png` or `.ico` assets when strictly forced by external platform constraints.