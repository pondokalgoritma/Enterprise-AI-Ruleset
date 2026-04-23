# RELIABILITY & SECURITY RULES (ALWAYS ACTIVE)

1. INPUT VALIDATION & VULNERABILITIES:
   - Never trust user input. Always validate and sanitize.
   - Use parameterized queries (prevent SQLi), sanitize outputs (prevent XSS), and implement CSRF protection.

2. SENSITIVE DATA & AUTH:
   - STRICTLY FORBIDDEN to hardcode secrets, API keys, or passwords. Always use `.env`.
   - Implement *Least Privilege* and ensure strict endpoint authorization checks.

3. ERROR HANDLING (FAIL GRACEFULLY):
   - The application must not crash silently. Catch exceptions (try-catch or error boundaries).
   - Provide *user-friendly* error messages to the client; never expose raw stack traces to the UI.

4. EARLY RETURN / FAIL FAST:
   - Validate conditions at the beginning of functions and `return` errors immediately if invalid (reduces deep nesting).

5. LOGGING:
   - Log errors with sufficient context to aid debugging.
   - NEVER log sensitive data (PII, passwords, credentials).
