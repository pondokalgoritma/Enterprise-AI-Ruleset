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
   - **Authorization Placement (RBAC):**
     - **Presentation Layer:** Perform initial "Guard" checks (e.g., check if the user is authenticated and has the basic role required to access the route).
     - **Business Layer (Service):** Perform deep authorization checks (e.g., ownership validation, complex business-rule-based permissions).
     - **Data Layer:** MUST NOT contain authorization logic. It only handles data retrieval/persistence as instructed by the Service Layer.

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

8. API CONTRACT & RESPONSE STANDARDIZATION:
   - **Uniform Response Format:** All API responses MUST follow a consistent structure to prevent frontend parsing errors.
   - **Standard Success Format:** `{ "success": true, "data": Object|Array, "message": string }`.
   - **Standard Error Format:** `{ "success": false, "error": { "code": string, "message": string, "details": any } }`.
   - **Consistent HTTP Status Codes:** Use appropriate status codes: 200 (OK), 201 (Created), 400 (Bad Request), 401 (Unauthorized), 403 (Forbidden), 404 (Not Found), 500 (Internal Error).

9. CONSISTENT STATE MANAGEMENT:
   - **Pattern Uniformity:** Use a single, unified state management pattern across the application (e.g., **Zustand** for global state, **Signals** or **Context** for UI-specific state). STRICTLY FORBIDDEN to mix multiple competing state libraries.
   - **Single Source of Truth:** Ensure that shared data is never duplicated across multiple states. Use derived states (selectors/computed) to keep data synchronized.

10. STANDARDIZED UTILITIES (FORMATTING):
   - **Centralized Logic:** STRICTLY FORBIDDEN to perform raw formatting (Dates, Currency, Numbers) directly in components.
   - **Utility Functions:** Always use centralized utility functions or dedicated libraries (e.g., `date-fns`, `Intl`) to ensure consistency across the entire UI.


11. OOP & DOMAIN-DRIVEN DESIGN (DDD) PRINCIPLES:
   - **Object-Oriented Programming (OOP):** Favor OOP patterns (Classes, Inheritance, Polymorphism, Encapsulation) for complex logic to improve reusability and maintainability.
   - **Domain-Based Grouping:** Organize the codebase by **Business Domain** (e.g., `src/modules/auth`, `src/modules/billing`, `src/modules/users`) rather than technical type (e.g., all controllers in one folder).
   - **Reusability:** Design modules and components to be highly reusable and independent. Business logic MUST be decoupled from specific transport layers (API/CLI/Web) or storage engines.

12. FRONTEND RESILIENCE:
   - **Error Boundaries:** Every major business domain or UI module MUST be wrapped in an **Error Boundary**. This ensures that a failure in one component does not crash the entire application, providing a more stable user experience.