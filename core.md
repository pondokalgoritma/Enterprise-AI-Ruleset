# CORE OPERATIONAL RULES (ALWAYS ACTIVE)

1. NO DUPLICATION:
   - Always check the existing codebase before creating new functions or components. Use `grep` or `find` to locate similar logic.
   - Reuse existing utilities and constants. Redundant implementations are STRICTLY FORBIDDEN.

2. ATOMICITY & MODULARITY:
   - Each file should serve ONE clear purpose.
   - Functions must be small, testable, and follow the *Single Responsibility Principle (SRP)*.

3. CONTINUOUS REFACTORING:
   - Leave the code cleaner than you found it. 
   - **Refactor proactively:** Small improvements (e.g., better naming, removing dead code) should be made during every task, but MUST NOT break existing logic.

4. SELF-VERIFICATION & AUTO-MAINTENANCE:
   - Before declaring a task "DONE," the AI MUST perform a critical self-review of the code.
   - **Mandatory Checks:** Scan for typos, verify logic against edge cases, check for linting errors, and confirm that ALL user requirements have been fully addressed.
   - **Feature Preservation Audit:** AI MUST audit all previously "completed" features in **`PROJECT.md`** to ensure they remain fully functional. STRICTLY FORBIDDEN to let new features break old ones.
   - **Build & Lint Validation:** Before declaring a major feature "SHIP-READY," the AI MUST perform a local production build check (e.g., `npm run build` or `npm run lint`) to catch environment or type-safety issues that don't appear in dev mode.
   - **Manual Log Audit:** Ensure no raw `console.log` statements remain in production-ready files.
   - **Documentation Sync:** AI MUST automatically update **`PROJECT.md`** (roadmap), **`ARCHITECTURE.md`** (tech map), domain **`README.md`**, and **API specifications** (e.g., `API.md` or Swagger) before finishing.
   - **Link Integrity Audit:** Whenever a route, file name, or directory structure changes, the AI MUST verify and update all internal links (Sidebar, Navigation, Redirects) to prevent 404 errors.

5. NO PLACEHOLDERS & COMMIT STANDARDS:
   - **Fully Functional:** STRICTLY FORBIDDEN to use placeholders, `// TODO` comments, or incomplete logic. Every line of code must be fully functional and integrated.
   - **Atomic Commits:** AI MUST NOT combine multiple unrelated changes or features in a single commit. Each commit MUST represent one logical, atomic change to facilitate easy reverts and clear history.
   - **Conventional Commits:** All git commits MUST follow the **Conventional Commits** specification (e.g., `feat:`, `fix:`, `chore:`, `refactor:`, `docs:`).
   - **Handover Summary:** Upon task completion, the AI MUST provide a concise summary including:
     - **What Changed:** A clear list of modifications and new files.
     - **Why:** Brief rationale for the implementation strategy.
     - **How to Test:** Specific steps for the user to verify the changes work as intended.
     - **Action Required:** Explicitly notify the user if they need to run `npm install`, apply new migrations, or update their local `.env` file.

   - **Folder Persistence (.gitkeep):** AI MUST add a `.gitkeep` file to any newly created empty directory that is part of the required project architecture to ensure folder structures are preserved in Version Control.

6. PROJECT CONTEXT & NAVIGATION WORKFLOW:
   - **Mandatory Files:** Every project MUST have standardized **`README.md`** (Public Setup), **`PROJECT.md`** (Roadmap), **`ARCHITECTURE.md`** (Technical Map), **`TROUBLESHOOTING.md`** (Error Log), and **`.gitignore`** files in the root.
   - **Environment Sync:** AI MUST automatically update **`.env.example`** whenever a new environment variable is introduced in the local `.env` file to ensure setup reproducibility.
   - **Security First:** AI MUST ensure a robust **`.gitignore`** exists and covers sensitive files (e.g., `.env`, `node_modules`, `dist`, `build`) before performing the first commit.

   - **Initial Setup:** If `PROJECT.md` is missing, the AI MUST proactively use `PROJECT_TEMPLATE.md` from the ruleset to ask for Project Metadata (Name, Purpose, Technical Stack, Constraints) and initialize it. This file serves as the primary anti-hallucination guardrail and technical source of truth.
   - **Search-First Policy:** In large codebases, the AI MUST use `grep` or `find` to locate specific logic instead of reading directories recursively to preserve context window and efficiency.
   - **Navigation Map:** AI MUST update `ARCHITECTURE.md` whenever new domains or major architectural changes occur to ensure a clear "X-Ray" view of the project structure.
   - **Execution Alignment:** AI MUST read these files first to understand the project's technical map, functional progress, and past troubleshooting lessons before writing any code.

7. ANTI-HALLUCINATION & SANITY RULES:
   - **Verification First:** AI MUST verify the existence of any local file, function, or library before importing it. 
   - **No Ghost Imports:** STRICTLY FORBIDDEN to use "imaginary" imports or libraries that are not in the codebase or `package.json`.
   - **Truncated Output Handling:** If a tool output is truncated, AI MUST NOT assume the remaining data. It MUST perform targeted reads or pagination to see the full content before making logic decisions.
   - **Apology-Loop Breach:** If a task fails twice using the same approach, AI MUST NOT repeat the same strategy. It MUST pause and ask the User for guidance or propose a radically different solution.
   - **No Zombie Files:** When a file is referenced in code, it MUST be fully implemented and functional immediately. References to empty or "TODO" files are strictly prohibited.


8. KNOWLEDGE MANAGEMENT & COLLECTIVE MEMORY:
   - **Learning Capture:** Every time a non-trivial build error, environment issue, or complex bug is solved, the AI MUST record the **Symptom**, **Root Cause**, and **Solution** in the project's `TROUBLESHOOTING.md`.
   - **Global Knowledge Sync:** If a fix is general and applicable to other projects, the AI MUST suggest adding it to a centralized knowledge base or the global ruleset's `/knowledge` directory.
   - **Pre-flight Knowledge Check:** Before starting any new task or resolving an error, the AI MUST check for relevant patterns in the local `TROUBLESHOOTING.md` and global knowledge to avoid repeating past mistakes and ensure the most efficient solution is used.

9. DEVELOPER EXPERIENCE & CLARITY (DX):
   - **Rationale Headers:** Every major logic file or complex utility MUST include a brief header or JSDoc explaining the **Architecture Decision** or rationale for unconventional patterns used.
   - **Legacy-to-New Mapping:** During refactoring, the AI MUST provide a clear mapping in the task summary of what has been moved, renamed, or replaced to ensure the developer doesn't lose context.
   - **Config Visibility:** Any modification to critical configuration files (e.g., `tsconfig.json`, `package.json`, `tauri.conf.json`) MUST be explicitly highlighted in the handover summary.
   - **No "Magic" Without Disclosure:** If the AI utilizes complex or non-obvious framework features (e.g., obscure hooks, native bindings, or custom compilers), it MUST provide a brief "Developer Note" explaining how it works.

10. PLAN-FIRST WORKFLOW (ANTI-CHAOS):
    - **Mandatory Planning:** For any task involving more than one file change, new feature implementation, or complex logic, the AI MUST use the `plan-writing` skill (or equivalent structured planning) before writing any code.
    - **Wait for Approval:** The generated plan MUST be presented to the user for review. AI MUST NOT proceed to implementation until the user provides explicit approval or feedback on the plan.
    - **Atomic Execution:** Plans must break down work into small, verifiable steps. Each step should be completed and verified before moving to the next to prevent compound errors.
    - **Refinement Loop:** If a plan is rejected or needs adjustment, the AI MUST refine the plan and present it again, ensuring all user concerns are addressed in the logic flow.