# DATABASE RULES (STRICT / DB-HEAVY)

1. PRINCIPLES:
   - Minimum cost (compute/memory)
   - Minimum I/O operations
   - Minimum lock contention

2. MANDATORY EVALUATION:
   - Cardinality & selectivity
   - Proper index usage
   - Join order & optimization strategies
   - Execution Impact: CPU, Memory, Disk, Network

3. ANTI-PATTERNS TO AVOID:
   - N+1 query problems
   - Queries inside loops
   - Unnecessary temporary tables
   - Layered/cascading writes

4. PREFERRED STRATEGIES:
   - Use `upsert` / `merge` when applicable
   - Employ batch processing for bulk operations
   - Utilize query rewriting for performance
   - Choose strategies contextually, not as rigid templates

5. SCALABILITY:
   - Must be safe for large datasets
   - Ensure minimal database locking
   - Must remain performant as data volume grows

6. FINAL VERIFICATION:
   - Provide a brief explanation regarding: efficiency reasons, trade-offs made, and risks avoided.

7. DEVELOPMENT SCHEMA MANAGEMENT:
   - **NO ALTER DURING DEVELOPMENT:** To maintain a clean and deterministic schema, using `ALTER TABLE` during the development phase is STRICTLY FORBIDDEN.
   - **RESET-FIRST APPROACH:** If the database structure needs to change, the existing database must be **RESET** (Dropped and Recreated) with the new schema.
   - **USER CONFIRMATION:** AI Agents MUST NOT perform a database reset automatically. Always ask the user to execute the reset/seed command (e.g., `npm run db:reset`) after a schema change is implemented in the source code.

8. SCHEMA-FIRST WORKFLOW (MANDATORY):
   - **Design Phase:** Before writing any implementation code or migration files, the AI MUST propose a complete and optimized database schema.
   - **Detailed Documentation:** For every proposed table, the AI must explain its purpose, primary keys, relationships (Foreign Keys), and indexing strategy for high-performance queries.
   - **Mandatory Approval:** The AI MUST explicitly ask for User Approval of the schema design. Implementation is STRICTLY FORBIDDEN until the user provides clear consent for the proposed structure.

9. EXTERNAL SEEDING (MANDATORY):
   - **No Hardcoded Data:** STRICTLY FORBIDDEN to hardcode seed data inside migration files, services, or repository logic.
   - **External Files:** Seed data must be stored in external files (preferred format: **YAML** or **SQL**).
   - **User Readability:** YAML is the preferred format for seed data to ensure it is easily readable and editable by the user without technical complexity.

10. QUERY PERFORMANCE & N+1 PREVENTION:
   - **Performance First:** AI MUST proactively check for and prevent **N+1 query patterns** in all data fetching logic.
   - **Strict Fetching Strategy:** Always prefer **Eager Loading**, **Joins**, or **Batching** techniques to fetch related data in a single operation. Performing individual database queries inside a loop is STRICTLY FORBIDDEN.
   - **Indexing Strategy:** Every table MUST have an indexing strategy designed for its most frequent query patterns. All Foreign Keys and high-cardinality search columns MUST be indexed.
   - **Large Dataset Pagination:** For list/collection endpoints, AI MUST implement **Offset** or **Cursor-based** pagination to prevent OOM (Out of Memory) and database performance degradation.