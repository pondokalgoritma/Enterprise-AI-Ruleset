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
   - **Build Validation:** Whenever possible, run the project's `lint`, `test`, or `build` commands to ensure no regressions or syntax errors were introduced during the process.