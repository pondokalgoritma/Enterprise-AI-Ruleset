# RELIABILITY & SECURITY RULES (ALWAYS ACTIVE)

1. INPUT VALIDATION & VULNERABILITIES:
   - Never trust user input. Always validate and sanitize.
   - Use parameterized queries (prevent SQLi), sanitize outputs (prevent XSS), and implement CSRF protection.

2. SENSITIVE DATA & AUTH:
   - STRICTLY FORBIDDEN to hardcode secrets, API keys, or passwords. Always use `.env`.
   - Implement *Least Privilege* through Role-Based Access Control (RBAC):
     - **Centralized Definition:** Roles and permissions must be defined in a single source of truth (e.g., a constants file or database schema). Avoid hardcoded strings across the codebase.
     - **Permission-Based Access:** Prefer checking for specific permissions (e.g., `can_edit_post`) rather than checking for raw role names (e.g., `is_admin`) to ensure future flexibility.
     - **Resource Ownership:** Beyond roles, always validate data ownership (e.g., a user can only update their own profile/records) within the Service Layer.
     - **Security Auditing:** Log all authorization failures (403 Forbidden) and sensitive administrative actions for security audits.

3. ERROR HANDLING (FAIL GRACEFULLY):
   - The application must not crash silently. Catch exceptions (try-catch or error boundaries).
   - Provide *user-friendly* error messages to the client; never expose raw stack traces to the UI.

4. EARLY RETURN / FAIL FAST:
   - Validate conditions at the beginning of functions and `return` errors immediately if invalid (reduces deep nesting).

5. LOGGING:
   - Log errors with sufficient context to aid debugging.
   - NEVER log sensitive data (PII, passwords, credentials).
