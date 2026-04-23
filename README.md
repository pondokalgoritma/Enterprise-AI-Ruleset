# Enterprise AI Ruleset

**Repository:** [https://github.com/pondokalgoritma/Enterprise-AI-Ruleset](https://github.com/pondokalgoritma/Enterprise-AI-Ruleset)

A modular, highly optimized, and enterprise-ready rule system designed to govern AI coding agents (like Claude, GPT, or Gemini). This framework guarantees maximum token efficiency, prevents hallucinations, strictly enforces clean code standards (SOLID, DRY), and ensures cross-platform and localization compliance.

## 🌟 Core Philosophy
- **Token Efficiency:** All rules are written in native English to maximize LLM parsing speed and reduce token overhead. 
- **Modular Load Order:** Rules are broken into distinct domains to prevent context-window overflow and overlapping instructions.
- **Strict Agnosticism:** Promotes a `Plug-and-Play` architecture (Hexagonal/Ports & Adapters). No vendor lock-ins.
- **Production-Ready Default:** Enforces strict error-handling, security, validation, and testing as default behaviors.

## 📂 Architecture & Files

The framework is divided into atomic markdown files, orchestrated by a central `index.md`.

### 1. The Core
* **`index.md`** - The entry point. Dictates the load order and defines the agent's operating mode (FAST, SAFE, STRICT).
* **`core.md`** - General rules of engagement: Focus strictly on the task, no assumptions, and work incrementally.
* **`PROJECT_TEMPLATE.md`** - The definitive metadata template for preventing AI hallucinations and setting technical guardrails.

### 2. Engineering Standards
* **`coding-standards.md`** - Enforces atomic file sizes, explicit type safety (TypeScript/Type Hints), descriptive naming, and Conventional Commits.
* **`architecture.md`** - Enforces N-Tier strict layering, SOLID/DRY/KISS principles, and Database/API agnosticism (Adapter/Repository patterns).

### 3. Safety & Assurance
* **`reliability.md`** - Governs input validation, security, credential protection, graceful failure handling, and logging without sensitive data.
* **`testing.md`** - Mandates the AAA (Arrange, Act, Assert) testing pattern, mock usage, and boundary/edge-case evaluation.

### 4. Platform-Specific
* **`frontend.md`** - Mandates Tailwind CSS, Custom UI components, Mobile-First responsiveness, and mandatory i18n localization.
* **`desktop.md`** - Governs cross-platform compatibility, centralized binary sidecar storage, dynamic OS-aware path resolution, and responsive desktop windows.
* **`mobile.md`** - Governs cross-platform mobile frameworks, native UX/gestures, memory optimization, offline-first states, and Just-In-Time permissions.
* **`database.md`** - Optimizes database querying, index usage, cardinality, and strict avoidance of N+1 problems.
* **`cloudflare.md`** - Governs Cloudflare-specific bindings (D1, KV, R2), Edge Runtime constraints, and automated migration systems.

## 🚀 Quick Start

### 1. Installation
Copy all `.md` files from this repository into your project root:
* **For General Agents (Cline, Roo, etc.):** Put them in a folder named `.ai-rules/` and point your agent to `index.md`.
* **For Cursor:** Consolidate these rules into your `.cursorrules` file or keep them in the root and instruct Cursor to "Always follow rules in the `.md` files".

### 2. First-Time Project Initiation Prompt
Copy and paste the following prompt to start a new project with this ruleset:

```text
I am starting a new project. Read 'index.md' and follow the 'CORE OPERATIONAL RULES' 
in 'core.md' to initiate the project. 

1. Perform a Pre-flight Check.
2. Ask me for the required Project Metadata based on `PROJECT_TEMPLATE.md`.
3. Initialize the mandatory project files (README.md, PROJECT.md, ARCHITECTURE.md, .gitignore).
```

## 🛠️ Modular Loading
The AI will selectively load the modular rules based on the context of the task (e.g., loading `frontend.md` only for UI tasks, saving immense token costs).

---
*Built to ensure AI writes code that human engineers actually enjoy maintaining.*

