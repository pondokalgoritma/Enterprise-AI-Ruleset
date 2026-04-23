# ARCHITECTURE & CLEAN CODE RULES (STRICT)

1. SOLID PRINCIPLES:
   - **SRP (Single Responsibility):** A file/class/function must have only ONE reason to change. Separate routing, business logic, and UI layers.
   - **OCP (Open/Closed):** Code must be open for extension but closed for modification.
   - **LSP, ISP, DIP (Dependency Inversion):** Avoid *tight coupling*. High-level modules must not depend directly on low-level modules (use abstractions/interfaces).

2. DRY (Don't Repeat Yourself):
   - Copy-pasting identical code across multiple places is FORBIDDEN.
   - If logic/UI is reused, extract it into a *utility function*, *helper*, *service*, or *reusable component*.
   - *Exception (Rule of Three):* Only extract after the code appears 3 times. Avoid premature abstractions that harm readability.

3. KISS & YAGNI:
   - **KISS (Keep It Simple, Stupid):** Code must be as clear as possible. Prioritize human *readability* over *clever code* (overly complex one-liners).
   - **YAGNI (You Aren't Gonna Need It):** Do not build complex infrastructure/abstractions for hypothetical future features. Solve the current problem only.

4. LAYERED ARCHITECTURE (N-TIER) & SEPARATION OF CONCERNS:
   - The application MUST be separated into at least 3 layers (Strict Layering):
     1. **Presentation / Delivery Layer (Controllers/Routers/UI):** Handles HTTP Request/Response, auth, input validation (DTO), and output formatting. NO DB queries or heavy logic here.
     2. **Business / Service Layer (Services/Use Cases):** The core of the application holding business logic. This layer must remain unaware of HTTP/Web concerns.
     3. **Data Access / Persistence Layer (Repositories/DAOs):** The ONLY place allowed to execute DB queries or call third-party APIs.
   - **Strict Communication Rule:** Higher layers may ONLY call the layer directly below them (Controller -> Service -> Repository). Lower layers are STRICTLY FORBIDDEN from calling or depending on layers above them (Dependency Rule).

5. CLEAN CODE PRACTICES:
   - Remove *dead code*, commented-out code, *unused imports*, and empty functions.

6. PERFORMANCE & OPTIMIZATION:
   - **Frontend:** Implement *Lazy Loading* for heavy components or routes. Use *Memoization* (e.g., `useMemo`, `useCallback` in React) strategically to prevent unnecessary re-renders.
   - **Backend:** Implement *Caching* mechanisms (e.g., Redis, Memcached) for expensive data computations that are frequently accessed and rarely change.
   - **General:** Always evaluate and optimize the Big-O time and space complexity of loops and large data transformations.

7. DATABASE & API AGNOSTICISM (ADAPTER PATTERN):
   - The core business logic must remain completely agnostic to specific Database engines (e.g., Postgres, MongoDB) and external 3rd-party APIs.
   - **Repository Pattern:** All database operations must be abstracted behind interfaces. Do not leak DB-specific ORM methods or SQL syntax into the Service layer.
   - **Adapter/Gateway Pattern:** Wrap all 3rd-party API integrations inside generic Adapter or Gateway classes. 
   - *Goal:* Swapping a database engine or changing an API provider later should only require creating a new Adapter/Repository file, with ZERO changes required in the Business Logic (Service Layer).