# CORE & EFFICIENCY RULES (ALWAYS ACTIVE)

1. FOCUS & NO ASSUMPTIONS:
   - Focus exclusively on the user's request. Do not expand the scope, take unsolicited initiatives, or add unauthorized features.
   - If instructions are ambiguous or information is missing, DO NOT ASSUME. Clarify/ask the user before executing.

2. EFFICIENCY & INCREMENTAL EXECUTION:
   - Avoid reading entire large files unless necessary. Read only specific, relevant functions or sections.
   - Minimize terminal commands, redundant file reads, and unnecessary log outputs to save tokens.
   - Work incrementally (step-by-step starting from the smallest, simplest part) rather than attempting a brute-force system overhaul.

3. BOY SCOUT RULE (CONTINUOUS IMPROVEMENT):
   - Always leave the code cleaner than you found it. 
   - **Refactor proactively:** If a file or function is already too complex (exceeding length limits) or contains tech debt, refactor it before adding new features. 
   - Small improvements (e.g., better naming, removing dead code) should be made during every task without explicitly being asked.

4. SELF-VERIFICATION (THE FINAL CHECK):
   - Before declaring a task "DONE," the AI MUST perform a critical self-review of the code.
   - **Mandatory Checks:** Scan for typos, verify logic against edge cases, check for linting errors, and confirm that ALL user requirements have been fully addressed.
   - **Build Validation:** Whenever possible, run the project's `lint`, `test`, or `build` commands. Additionally, perform a **Manual Log Audit** to ensure no raw `console.log` statements remain in production-ready files.


5. NO PLACEHOLDERS & COMPLETION SUMMARY:
   - **Fully Functional:** STRICTLY FORBIDDEN to use placeholders, `// TODO` comments, or incomplete logic. Every line of code must be fully functional and integrated.
   - **Handover Summary:** Upon task completion, the AI MUST provide a concise summary including:
     - **What Changed:** A clear list of modifications and new files.
     - **Why:** Brief rationale for the implementation strategy.
     - **How to Test:** Specific steps for the user to verify the changes work as intended.

6. PROJECT CONTEXT & NAVIGATION WORKFLOW:
   - **Mandatory Files:** Every project MUST have standardized **`PROJECT.md`** (Roadmap/Features) and **`ARCHITECTURE.md`** (Folder Map/Data Flow) files in the root.
   - **Initial Setup:** If these files are missing, the AI MUST proactively ask for Project Metadata (Name, Purpose, Developer, Domain, URL) and Features to initialize them.
   - **Search-First Policy:** In large codebases, the AI MUST use `grep` or `find` to locate specific logic instead of reading directories recursively to preserve context window and efficiency.
   - **Navigation Map:** AI MUST update `ARCHITECTURE.md` whenever new domains or major architectural changes occur to ensure a clear "X-Ray" view of the project structure.
   - **Execution Alignment:** AI MUST read these files first to understand the project's technical map and functional progress before writing any code.