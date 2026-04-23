# CODING STANDARDS (ALWAYS ACTIVE)

1. STRICT TECH STACK & PATTERNS:
   - Strictly follow the project's existing libraries (check `package.json`). DO NOT introduce new libraries without permission.
   - Use uniform design patterns (e.g., Functional Components in React, async/await in the Backend).

2. EXPLICIT & TYPE SAFETY (AI-FRIENDLY):
   - Avoid *magic code* or complex metaprogramming.
   - Mandatory use of explicit types (TypeScript, Type Hints) as a contract and documentation.

3. NAMING & ATOMIC FILES:
   - File size must not exceed 200-300 lines. If larger, split it.
   - Naming Casing: `camelCase` (variables/functions), `PascalCase` (Classes/Components), `UPPER_SNAKE_CASE` (constants).
   - Naming Purpose: Must be explicitly descriptive (e.g., `fetchActiveUsers()`, not `getData()`).

4. INTERMEDIATE VARIABLES & NO CHAINING:
   - Avoid excessive method chaining. Break complex logic into intermediate variables for step-by-step clarity.

5. DOCUMENTATION & COMMENTS:
   - Inline comments should explain WHY a solution was chosen, not WHAT the code does.
   - Use doc-strings (JSDoc/PHPDoc) to describe parameter/return types on public functions.
   - Main files/modules must have a header indicating Purpose, Dependencies, and Side effects.

6. VERSION CONTROL & COMMITS:
   - If executing git commits, STRICTLY adhere to Conventional Commits standards (e.g., `feat:`, `fix:`, `chore:`, `refactor:`, `docs:`).
   - Commit messages must be concise, written in English, and clearly explain the *what* and *why* of the change.

7. ROBUST CODING HABITS:
   - **Immutability First:** Avoid mutating objects or arrays directly. Always prefer returning new copies (e.g., using spread operators `{...obj}` or map/filter) to ensure predictable state management.
   - **No Magic Numbers/Strings:** STRICTLY FORBIDDEN to use raw, unexplained numbers or strings in logic (e.g., `if (status === 3)`). Use descriptive constants or enums (e.g., `if (status === Status.PUBLISHED)`).
   - **Financial Accuracy:** NEVER use floating-point numbers for currency or financial calculations. Use **Integers (Cents)**, `BigInt`, or specialized decimal libraries to prevent precision loss.
   - **Cross-Platform Path Safety:** STRICTLY FORBIDDEN to use hardcoded path separators (e.g., `/` or `\`). Always use platform-agnostic utilities (e.g., `path.join()` in Node.js) to ensure seamless compatibility across Linux, Windows, and macOS.


8. DEPENDENCY MANAGEMENT & VERSION PINNING:
   - **Solid & Latest:** Always use the latest STABLE version of a library. Avoid beta/release candidates unless specifically requested.
   - **Security Audit:** Before installation, ensure the library is well-maintained and has no known critical vulnerabilities.
   - **Explicit Versioning:** When adding dependencies, use **Exact Version Numbers** (e.g., `1.2.3`) instead of ranges (e.g., `^1.2.3` or `~1.2.3`) to prevent unexpected breaking changes during future installs.
   - **No Redundancy:** STRICTLY FORBIDDEN to install new libraries that overlap in functionality with existing ones. Always audit `package.json` first and utilize existing project tools before suggesting new dependencies.

9. IMPORT EFFICIENCY (TREE-SHAKING):
   - **Modular Imports:** Favor importing specific functions or components (e.g., `import { map } from 'lodash'`) instead of entire libraries (e.g., `import _ from 'lodash'`) to enable effective tree-shaking and minimize production bundle size.

10. CONSISTENT FILE NAMING:


   - **Kebab-Case:** All filenames (components, utilities, assets, styles) MUST use **kebab-case** (e.g., `user-profile-card.tsx`). This ensures seamless compatibility across case-sensitive (Linux) and case-insensitive (macOS/Windows) filesystems.

11. MEANINGFUL DOCUMENTATION:
   - **TSDoc/JSDoc:** Every exported function, class, interface, or complex logic block MUST include **TSDoc/JSDoc** comments clearly explaining the purpose, parameters, and return values to ensure long-term maintainability.


12. FILE HYGIENE & IMPORT ORGANIZATION:
   - **Organized Imports:** Imports MUST be grouped and sorted logically:
     1. Built-in modules (e.g., `fs`, `path`).
     2. External libraries (e.g., `react`, `lodash`).
     3. Internal project aliases (e.g., `@/components`, `@/utils`).
     4. Relative path imports (e.g., `./styles.css`).
   - **No Dead Code:** STRICTLY FORBIDDEN to leave unused imports, variables, or commented-out code blocks in production-ready files.
   - **EOF Newline:** Always ensure files end with a single newline character to maintain POSIX compatibility.
