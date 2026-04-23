# CLOUDFLARE NATIVE RULES (CLOUDFLARE PROJECTS ONLY)

1. BINDING & CONFIGURATION AWARENESS:
   - **Check Bindings First:** Before implementing logic that uses external resources, always check `wrangler.jsonc` or `wrangler.toml` for available D1, KV, R2, or Service Bindings.
   - **Type Safety:** Always refer to `worker-configuration.d.ts` (if available) to ensure binding names and types match the actual environment.

2. EDGE RUNTIME CONSTRAINTS:
   - **No Native Node.js:** Strictly avoid using native Node.js modules (e.g., `fs`, `child_process`, `os`, `path`) unless the project has explicit Node.js compatibility flags enabled and the module is supported.
   - **Worker Memory/Time:** Optimize for low memory footprint and execution time (under 50ms for free tier, 30ms for default Workers). Use streaming responses for large data.
   - **Global Scope:** Avoid heavy initializations in the global scope. Initialize resources inside the `fetch` handler or use singleton patterns that benefit from Worker warm starts.

3. ENVIRONMENT & SECRETS:
   - **Dependency Injection:** Access environment variables and bindings exclusively via the `env` object passed to the handler. NEVER use `process.env`.
   - **Secret Protection:** STRICTLY FORBIDDEN to commit raw secrets to `wrangler.jsonc`. Secrets must be managed via Cloudflare Dashboard or `wrangler secret put`.

4. DATABASE (D1) & PERSISTENCE:
   - **Migration & Reset Policy:**
     - **Development:** STRICTLY FORBIDDEN to use `ALTER` commands in migrations during the development phase. Schema changes must be implemented by updating the initial schema/migration and performing a database **RESET**.
     - **User Confirmation:** Always ask the user to run the reset/seed command (e.g., `npx wrangler d1 execute ...`) after modifying the schema in the code.
   - **Batching:** Use D1's `.batch()` method for multiple SQL operations to minimize round-trips and optimize performance.
   - **KV Usage:** Use KV for read-heavy, low-latency data that doesn't require ACID transactions. Implement TTL (Time To Live) where appropriate to save storage.
   - **Schema Workflow:** Adhere strictly to the **Schema-First Workflow** and **External Seeding** rules defined in `database.md` before initiating any D1 changes.

5. PERFORMANCE & EDGE OPTIMIZATION:
   - **Lazy Loading:** Dynamically import heavy libraries only when needed to keep the Worker bundle size small.
   - **Streaming:** Utilize the `TransformStream` and `ReadableStream` APIs for handling large payloads or long-running responses to reduce TTFB (Time to First Byte).
   - **Subrequests:** Be mindful of the subrequest limit (default 50 per request). Batch external API calls where possible.
