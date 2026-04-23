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
