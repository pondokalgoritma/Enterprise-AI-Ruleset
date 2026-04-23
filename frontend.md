# FRONTEND & UI RULES (FRONTEND TASKS)

1. CUSTOM COMPONENTS ONLY:
   - STRICTLY FORBIDDEN to use native browser popups (`alert()`, `confirm()`, `prompt()`).
   - Must use custom components (Modal, Toast, Dialog) that align with the application's theme/design system.

2. ACCESSIBILITY (A11Y) & UX:
   - Custom modals must support keyboard navigation (e.g., ESC to close, focus traps).
   - Transition animations must be smooth but efficient to avoid rendering performance issues.

3. INTERNATIONALIZATION (i18n):
   - STRICTLY FORBIDDEN to hardcode text strings directly in components/views (including placeholders, labels, error messages).
   - Must use the project's built-in i18n system (e.g., `t('key')`).
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

6. DUAL THEME SUPPORT (DARK & LIGHT):
   - Every GUI component and layout must natively support at least two themes: **Dark Mode** and **Light Mode**.
   - Use CSS variables or Tailwind's `dark:` utility classes to ensure seamless switching between themes.
   - The default theme should be determined by the user's system preference (`prefers-color-scheme`), but a manual toggle must also be provided.

7. PROFESSIONAL ASSETS & ICONS:
   - MANDATORY use of professional, high-quality icon libraries (e.g., **Lucide React**, **Heroicons**, or **Radix Icons**).
   - STRICTLY FORBIDDEN to use low-quality raster images (PNG/JPG) for UI icons; icons MUST be SVG-based for infinite scalability and crispness.
   - Consistency: Ensure all icons used within the same application follow a uniform stroke weight, style (e.g., all outlined or all filled), and sizing pattern.

8. USER FEEDBACK & LAYERING:
   - **Loading & Empty States:** Every data-fetching component MUST handle and display a distinct "Loading" state and an "Empty" state (when no data is returned). DILARANG (FORBIDDEN) to show blank screens during background processes.
   - **Z-Index Management:** Avoid "Z-Index Wars" (e.g., `z-[9999]`). Use a structured layering system or Tailwind's standard z-index scale.

9. ADVANCED FRONTEND PATTERNS:
   - **Race Condition Handling:** When performing multiple asynchronous requests for the same state (e.g., search-as-you-type), always use an `AbortController` to cancel previous pending requests and prevent outdated data from overwriting new results.
   - **Debouncing & Throttling:** Rapid-fire events (input, scroll, resize) MUST be debounced or throttled to prevent performance degradation and excessive API calls.
   - **Semantic HTML:** Strictly avoid "Div-Soup." Use appropriate semantic tags (`<nav>`, `<header>`, `<main>`, `<article>`, `<button>`, etc.) to ensure accessibility (A11y) and SEO optimization.
