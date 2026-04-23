# RELIABILITY & SECURITY RULES (ALWAYS ACTIVE)

1. INPUT VALIDATION & URL SAFETY:
   - Never trust user input. Always validate and sanitize.
   - **No Hardcoded URLs:** STRICTLY FORBIDDEN to hardcode environment-specific URLs or local host addresses (e.g., `http://localhost:3000`). All API endpoints or external service URLs MUST be managed via environment variables to ensure production readiness.
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
   - **Environment-Aware Logging:** Debug logs (e.g., `console.log`) MUST be wrapped in environment checks (e.g., `if (process.env.NODE_ENV === 'development')`) to prevent unnecessary output in production.
   - **Production Hygiene:** STRICTLY FORBIDDEN to leave raw `console.log` statements in production-bound code. Only structured, necessary system logs are allowed in production.
   - **No Sensitive Data:** NEVER log sensitive data (PII, passwords, credentials).


6. EXECUTION & REAL-TIME MONITORING:
   - **Non-Blocking Logic:** Long-running or heavy computational tasks MUST NOT freeze the main thread (UI). Use multi-threading, Web Workers (frontend), or Background Jobs (backend/desktop) to ensure responsiveness.
   - **Real-time Logging:** Implementation must support "Instant Feedback." Logs must be emitted immediately as a process starts, progresses, or completes.
   - **Log Depth:** Real-time logs must include critical context: Timestamp, Process ID/Name, Status (Started/Progress/Done), and relevant metrics (e.g., memory usage or item count) to aid debugging.

7. RESOURCE CLEANUP & EDGE CASES:
   - **Mandatory Cleanup:** Any allocated resource (subscriptions, intervals, timeouts, file handles, DB connections) MUST be explicitly closed or cleared when no longer needed to prevent memory leaks.
   - **Defensive Programming:** Never assume the "Happy Path." Always handle null/undefined values, empty arrays, and network timeouts. Implement retry logic for critical transient failures.

8. STABILITY & INTEGRITY:
   - **Idempotency & Double Submit:** For state-changing operations (Create/Update/Delete), implement UI protections (e.g., disabling buttons after the first click) and backend checks to prevent duplicate actions from multiple submissions.
   - **Environment Validation:** Critically important environment variables (defined in `.env` or bindings) MUST be validated during application startup. The app should fail fast and log clear errors if a required secret or configuration is missing.
   - **Idempotent Operations:** All maintenance scripts, migrations, seeds, and background jobs MUST be **Idempotent**. Executing the same operation multiple times must yield the same state without causing errors or data duplication.

9. SILENT FAILURE PREVENTION:
   - **Strict UTC Policy:** All timestamps MUST be stored, transmitted, and processed in **UTC (ISO 8601)**. Conversion to local timezones should ONLY happen at the Presentation Layer (UI) for display purposes.

   - **Streaming for Large Data:** STRICTLY FORBIDDEN to read entire large files or datasets into memory. Use **Streams** (ReadableStream/WritableStream) for processing to keep memory usage constant and prevent OOM (Out of Memory) crashes.
   - **Rate Limit Handling:** When calling external APIs, implement **Exponential Backoff** and retry mechanisms to gracefully handle `429 Too Many Requests` or transient network errors.

10. GRACEFUL SHUTDOWN:
   - **Signal Handling:** Applications MUST handle termination signals (e.g., `SIGTERM`, `SIGINT`). 
   - **Cleanup Logic:** Upon receiving a shutdown signal, the application MUST gracefully close database connections, finish pending requests, and release resources to prevent data corruption and ensure a clean exit.

