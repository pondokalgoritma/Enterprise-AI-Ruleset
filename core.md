# CORE & EFFICIENCY RULES (ALWAYS ACTIVE)

1. FOCUS & NO ASSUMPTIONS:
   - Focus exclusively on the user's request. Do not expand the scope, take unsolicited initiatives, or add unauthorized features.
   - If instructions are ambiguous or information is missing, DO NOT ASSUME. Clarify/ask the user before executing.

2. EFFICIENCY & INCREMENTAL EXECUTION:
   - Avoid reading entire large files unless necessary. Read only specific, relevant functions or sections.
   - Minimize terminal commands, redundant file reads, and unnecessary log outputs to save tokens.
   - Work incrementally (step-by-step starting from the smallest, simplest part) rather than attempting a brute-force system overhaul.

3. BOY SCOUT RULE & NON-DESTRUCTIVE EDITS:
   - Always leave the code cleaner than you found it. 
   - **Non-Destructive:** Always prioritize appending or extending logic over rewriting or deleting existing code. Proactively ensure that existing functionalities are preserved unless explicitly asked to refactor or remove them.
   - **Refactor proactively:** Small improvements (e.g., better naming, removing dead code) should be made during every task, but MUST NOT break existing logic.

4. SELF-VERIFICATION & AUTO-MAINTENANCE:
   - Before declaring a task "DONE," the AI MUST perform a critical self-review of the code.
   - **Mandatory Checks:** Scan for typos, verify logic against edge cases, check for linting errors, and confirm that ALL user requirements have been fully addressed.
   - **Feature Preservation Audit:** AI MUST audit all previously "completed" features in **`PROJECT.md`** to ensure they remain fully functional. STRICTLY FORBIDDEN to let new features break old ones.
   - **Build Validation:** Whenever possible, run the project's `lint`, `test`, or `build` commands. Additionally, perform a **Manual Log Audit** to ensure no raw `console.log` statements remain in production-ready files.
   - **Documentation Sync:** AI MUST automatically update **`PROJECT.md`** (roadmap), **`ARCHITECTURE.md`** (tech map), and domain **`README.md`** files before finishing.

5. NO PLACEHOLDERS & COMMIT STANDARDS:
   - **Fully Functional:** STRICTLY FORBIDDEN to use placeholders, `// TODO` comments, or incomplete logic. Every line of code must be fully functional and integrated.
   - **Atomic Commits:** AI MUST NOT combine multiple unrelated changes or features in a single commit. Each commit MUST represent one logical, atomic change to facilitate easy reverts and clear history.
   - **Conventional Commits:** All git commits MUST follow the **Conventional Commits** specification (e.g., `feat:`, `fix:`, `chore:`, `refactor:`, `docs:`).
   - **Handover Summary:** Upon task completion, the AI MUST provide a concise summary including:
     - **What Changed:** A clear list of modifications and new files.
     - **Why:** Brief rationale for the implementation strategy.
     - **How to Test:** Specific steps for the user to verify the changes work as intended.

6. PROJECT CONTEXT & NAVIGATION WORKFLOW:
   - **Mandatory Files:** Every project MUST have standardized **`README.md`** (Public Setup), **`PROJECT.md`** (Roadmap), **`ARCHITECTURE.md`** (Technical Map), **`TROUBLESHOOTING.md`** (Error Log), and **`.gitignore`** files in the root.
   - **Environment Sync:** AI MUST automatically update **`.env.example`** whenever a new environment variable is introduced in the local `.env` file to ensure setup reproducibility.
   - **Security First:** AI MUST ensure a robust **`.gitignore`** exists and covers sensitive files (e.g., `.env`, `node_modules`, `dist`, `build`) before performing the first commit.

   - **Initial Setup:** If these files are missing, the AI MUST proactively ask for Project Metadata (Name, Purpose, Developer, Domain, URL) and Features to initialize them.
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