# AI Agent Rules Framework

A modular, highly optimized, and enterprise-ready rule system designed to govern AI coding agents (like Claude, GPT, or Gemini). This framework guarantees maximum token efficiency, prevents hallucinations, strictly enforces clean code standards (SOLID, DRY), and ensures cross-platform and localization compliance.

## 🌟 Core Philosophy
- **Token Efficiency:** All rules are written in native English to maximize LLM parsing speed and reduce token overhead. 
- **Modular Load Order:** Rules are broken into distinct domains to prevent context-window overflow and overlapping instructions.
- **Strict Agnosticism:** Promotes a `Plug-and-Play` architecture (Hexagonal/Ports & Adapters). No vendor lock-ins.
- **Production-Ready Default:** Enforces strict error-handling, security, validation, and testing as default behaviors.

## 📂 Architecture & Files

The framework is divided into 8 atomic markdown files, orchestrated by a central `index.md`.

### 1. The Core
* **`index.md`** - The entry point. Dictates the load order and defines the agent's operating mode (FAST, SAFE, STRICT).
* **`core.md`** - General rules of engagement: Focus strictly on the task, no assumptions, and work incrementally.

### 2. Engineering Standards
* **`coding-standards.md`** - Enforces atomic file sizes, explicit type safety (TypeScript/Type Hints), descriptive naming, and Conventional Commits.
* **`architecture.md`** - Enforces N-Tier strict layering, SOLID/DRY/KISS principles, and Database/API agnosticism (Adapter/Repository patterns).

### 3. Safety & Assurance
* **`reliability.md`** - Governs input validation, security, credential protection, graceful failure handling, and logging without sensitive data.
* **`testing.md`** - Mandates the AAA (Arrange, Act, Assert) testing pattern, mock usage, and boundary/edge-case evaluation.

### 4. Platform-Specific
* **`frontend.md`** - Mandates Tailwind CSS, Custom UI components, Mobile-First responsiveness, and mandatory i18n localization.
* **`desktop.md`** - Governs cross-platform compatibility, centralized binary sidecar storage, dynamic OS-aware path resolution, and responsive desktop windows.
* **`database.md`** - Optimizes database querying, index usage, cardinality, and strict avoidance of N+1 problems.

## 🚀 How to Use
Whenever you assign a task to the AI, instruct it to parse the rules in the exact order defined in `index.md`. 
The AI will selectively load the modular rules based on the context of the task (e.g., loading `frontend.md` only for UI tasks, saving immense token costs).

---
*Built to ensure AI writes code that human engineers actually enjoy maintaining.*
