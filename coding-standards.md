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
