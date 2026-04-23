# FRONTEND & UI RULES (FRONTEND TASKS)

1. ATOMIC & REUSABLE CUSTOM COMPONENTS:
   - **STRICTLY FORBIDDEN** to use native browser popups (`alert()`, `confirm()`, `prompt()`) or generic, unstyled native HTML elements (e.g., raw `<button>`, `<input>`, `<select>`) directly in views.
   - **Custom UI Library:** All UI elements MUST be abstracted into a dedicated, centralized component folder (e.g., `src/components/ui`).
   - **Reusability & Consistency:** Every UI element must be highly reusable, modular, and strictly follow a uniform design language (consistent typography, padding, borders, and shadows) throughout the entire application.


2. ACCESSIBILITY (A11Y) & UX:
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


