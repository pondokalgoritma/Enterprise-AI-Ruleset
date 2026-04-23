# FRONTEND & UI RULES (FRONTEND TASKS)

1. ATOMIC & REUSABLE CUSTOM COMPONENTS:
   - **STRICTLY FORBIDDEN** to use native browser popups (`alert()`, `confirm()`, `prompt()`) or generic, unstyled native HTML elements (e.g., raw `<button>`, `<input>`, `<select>`) directly in views.
   - **Custom UI Library:** All UI elements MUST be abstracted into a dedicated, centralized component folder (e.g., `src/components/ui`).
   - **Headless Logic:** For complex accessible interactions (e.g., Modals, Dropdowns), the use of **Headless UI** or **Radix Primitives** is HIGHLY RECOMMENDED to ensure robust logic and A11y.
   - **100% Custom Styling:** Regardless of the underlying logic library, the visual appearance MUST be 100% custom-styled using project-specific design tokens and Tailwind CSS. STRICTLY FORBIDDEN to use pre-styled UI kits (e.g., MUI, Chakra UI, Ant Design).
   - **Reusability & Consistency:** Every UI element must be highly reusable, modular, and strictly follow a uniform design language (consistent typography, padding, borders, and shadows) throughout the entire application.


2. ACCESSIBILITY (A11Y) & UX:
   - **Resilience (Error Boundaries):** Every major UI module (e.g., Sidebar, Main Layout, Dashboard Widgets) MUST be wrapped in an **Error Boundary** to prevent a single component failure from crashing the entire application.
   - Custom modals must support keyboard navigation (e.g., ESC to close, focus traps).
   - Transition animations must be smooth but efficient to avoid rendering performance issues.


3. INTERNATIONALIZATION (i18n):
   - STRICTLY FORBIDDEN to hardcode text strings directly in components/views (including placeholders, labels, error messages).
   - Must use the project's built-in i18n system (e.g., `t('key')`).
   - **External YAML Files:** All translation keys and strings MUST be stored in external **YAML** files. STRICTLY FORBIDDEN to hardcode translations inside JSON or TypeScript files to maintain maximum readability for the user.
   - Default support: must include string definitions for at least two languages, Indonesian (id) and English (en).
   - Key naming: use a descriptive hierarchical format (e.g., `auth.login.title`), not raw text like `login_text`.

4. RESPONSIVE & MOBILE-FIRST DESIGN:
   - All web interfaces must be built using a strict "Mobile-First" approach.
   - Design layouts for small screens first, then use `min-width` media queries to progressively enhance the UI for tablets and desktops.
   - Use flexible units (rem, %, vh/vw) and modern CSS layouts (Flexbox/Grid) to ensure fluid responsiveness across all devices without horizontal scrolling.

5. STYLING & TAILWIND CSS:
   - Mandatory use of **Tailwind CSS** for all UI styling across both Web and Desktop applications.
   - **Subtle Border Radii:** Avoid excessive rounding (e.g., `rounded-2xl`, `rounded-full`) for main UI components like Cards, Inputs, and Modals. Use subtle, sharp-but-elegant radii (e.g., `rounded-md` or `rounded-lg`) to maintain a professional, high-end aesthetic.
   - STRICTLY FORBIDDEN to write custom raw CSS files unless dealing with complex, highly specific animations or edge cases that Tailwind cannot handle natively.
   - Utilize Tailwind's built-in responsive utility classes (e.g., `sm:`, `md:`, `lg:`) to easily implement the Mobile-First approach.


6. DUAL THEME SUPPORT (DARK/LIGHT):
   - **Theme-Aware Components:** EVERY custom component MUST be fully responsive to theme changes.
   - **Modular Theme Configuration:** All theme-related settings (color palettes, design tokens, CSS variables) MUST be stored in dedicated, standalone configuration files (e.g., `theme.css`, `src/styles/theme/`) to ensure high maintainability and a single source of truth for design.
   - **No Hardcoded Colors:** STRICTLY FORBIDDEN to use fixed colors (e.g., `bg-white`, `text-black`, `#FFFFFF`). Always use **Design Tokens** or **CSS Variables** (e.g., `var(--background)`, `text-primary`, `bg-secondary`) that adapt automatically to both Dark and Light modes.
   - **System Preference:** Default to the user's system theme preference unless a specific theme is selected; a manual toggle must also be provided.

7. PROFESSIONAL ASSETS & ICONS:
   - MANDATORY use of professional, high-quality icon libraries (e.g., **Lucide React**, **Heroicons**, or **Radix Icons**).
   - STRICTLY FORBIDDEN to use low-quality raster images (PNG/JPG) for UI icons; icons MUST be SVG-based for infinite scalability and crispness.
   - Consistency: Ensure all icons used within the same application follow a uniform stroke weight, style (e.g., all outlined or all filled), and sizing pattern.

8. USER FEEDBACK & LAYERING:
   - **Skeleton Loading:** For a premium experience, favor **Skeleton Screens** (pulsing shadows) over generic spinners or "Loading..." text during data fetching.
   - **Micro-interactions:** Implement subtle animations and transitions (hover scales, smooth fades, focus rings) for all interactive elements to make the UI feel responsive and "alive".
   - **Z-Index Layering System:** Avoid arbitrary or extreme values (e.g., `z-[9999]`). Use a structured, tiered scale (e.g., Modals: `z-50`, Overlays: `z-40`, Navigation: `z-30`, Dropdowns: `z-20`) to maintain a predictable visual order.

9. ADVANCED FRONTEND PATTERNS:
   - **Race Condition Handling:** When performing multiple asynchronous requests for the same state (e.g., search-as-you-type), always use an `AbortController` to cancel previous pending requests and prevent outdated data from overwriting new results.
   - **Debouncing & Throttling:** Rapid-fire events (input, scroll, resize) MUST be debounced or throttled to prevent performance degradation and excessive API calls.
   - **Semantic HTML:** Strictly avoid "Div-Soup." Use appropriate semantic tags (`<nav>`, `<header>`, `<main>`, `<article>`, `<button>`, etc.) to ensure accessibility (A11y) and SEO optimization.

10. ASSET OPTIMIZATION (PERFORMANCE):
   - **Modern Formats:** Prefer modern, highly-compressed formats for images (e.g., **WebP** or **AVIF**) over legacy formats (PNG/JPG).
   - **Lazy Loading:** All non-critical images and media MUST use native `loading="lazy"` to preserve bandwidth and improve initial page load speed.
   - **Sizing:** STRICTLY FORBIDDEN to serve oversized images. Always resize and compress assets to their intended display dimensions.

11. DEPENDENCY ISOLATION (NO EXTERNAL CDNs):
   - **Local Bundling:** STRICTLY FORBIDDEN to load libraries, scripts, or styles via external CDNs (e.g., `<script src="https://cdn...">`). 
   - **Self-Hosted:** All dependencies MUST be installed via a Package Manager (npm/yarn/pnpm) and bundled locally to ensure security (XSS prevention), privacy, and offline reliability.

12. STRICT FORM MANAGEMENT & VALIDATION:
   - **Schema-Based Validation:** MANDATORY use of schema validation libraries (e.g., **Zod**, **Valibot**) for all forms to ensure data integrity.
   - **No Manual Validation:** STRICTLY FORBIDDEN to write ad-hoc, manual validation logic inside components. All rules MUST be defined in centralized, reusable schemas.

13. PREMIUM FINISHING TOUCHES:
   - **Empty States:** Every data list or search result MUST have a polished "Empty State" UI. STRICTLY FORBIDDEN to leave a blank white screen; use subtle illustrations, icons, and clear call-to-action (CTA) text.
   - **Interactive Feedback:** Any button or interactive element that triggers an asynchronous action MUST show a clear loading/busy state (e.g., replace icon with spinner, disable with visual feedback) to provide immediate user acknowledgment.
   - **Custom Scrollbars:** Implement sleek, theme-aware custom scrollbar styling for all scrollable containers.
   - **Seamless Integration:** Scrollbars MUST be unified with the container borders (zero gap/padding). Even in resizable components, the scrollbar must remain flush with the edge to ensure a single, cohesive, and seamless aesthetic.

   - **Professional Branding:** Every project MUST include a custom Favicon and full Social Media (OpenGraph/SEO) metadata to ensure a professional appearance when shared.

14. CORE COMPONENT STANDARDS:
   - **Rich Inputs:** EVERY custom input component MUST support optional **Icon Prefix** and **Icon Suffix** slots/props for enhanced functionality.
   - **Hybrid Dropdowns:** Custom Select/Dropdown components MUST natively support both **Single** and **Multiple** selection modes with a consistent visual style (e.g., using chips/tags for multiple items).
   - **Modern Option Selection:** Favor **Toggle Buttons** (Segmented Controls) for selecting options instead of raw, unstyled radio buttons or checkboxes to maintain a premium UI feel.

15. PREMIUM AESTHETICS (VISUAL EXCELLENCE):
   - **Glassmorphism:** Use `backdrop-filter: blur()` and semi-transparent backgrounds for overlays, floating headers, and modals to create a high-end "frosted glass" effect.
   - **Subtle Layered Shadows:** Use multi-layered box-shadows (diffused shadows) instead of single-layer ones to create a natural, organic sense of depth and elevation.
   - **Organic Animations:** Implement **Spring Physics** (e.g., Framer Motion spring) for transitions and hover effects to make the UI feel alive and responsive.
   - **Glow Borders & Soft Gradients:** Apply very subtle gradients and high-contrast "glow" borders (0.5px to 1px) to UI cards and containers for a sleek, modern finish.





16. SEO & SEARCH ENGINE OPTIMIZATION (MANDATORY):
    - **Semantic Foundation:** STRICTLY FORBIDDEN to use "Div-Soup." AI MUST use appropriate semantic tags (<header>, <main>, <footer>, <nav>, <article>, <section>) to define the document structure, which is vital for search engine crawlers.
    - **Automated Metadata:** Every unique view/page MUST have its own unique <title> (max 60 chars) and <meta name="description"> (max 160 chars) that accurately describes the content.
    - **Heading Hierarchy:** AI MUST ensure only ONE <h1> exists per page, acting as the primary topic. Subheadings MUST follow a logical hierarchy (H1 -> H2 -> H3) without skipping levels.
    - **Social Media Readiness (OpenGraph):** Every project MUST include essential OpenGraph (og:) and Twitter Card meta tags, including a mandatory og:image for professional link previews.
    - **Alt-Text Discipline:** Every <img> tag MUST include a descriptive alt attribute. STRICTLY FORBIDDEN to use generic text like "image" or "placeholder"; use context-rich descriptions for accessibility and image SEO.
    - **Structured Data (JSON-LD):** For primary content types (e.g., Articles, Products, FAQ), the AI MUST automatically generate or recommend JSON-LD Structured Data (Schema.org) to enable rich snippets in search results.
    - **Visual Stability (CLS Prevention):** Every image MUST have explicit width and height attributes (or aspect-ratio styles) to prevent Layout Shifts, which negatively impact SEO rankings.
