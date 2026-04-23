# PROJECT METADATA (AI GUARDRAILS)

> [!IMPORTANT]
> This file is the "Source of Truth" for AI Agents. AI MUST read this file before any task to align with the technical map and business logic.

## 1. PROJECT IDENTITY
- **Project Name:** 
- **Developer/Owner:** 
- **Primary Domain:** (e.g., E-commerce, Fintech, Internal Tool)
- **Primary Goal:** 
- **Target Audience:** 

## 2. TECHNICAL STACK MATRIX (STRICT)
| Layer | Technology | Version/Note |
| :--- | :--- | :--- |
| **Runtime** | | |
| **Frontend Framework** | | |
| **Styling** | Vanilla CSS / Tailwind v4 | |
| **Backend/Edge** | | |
| **Database** | | |
| **Auth Provider** | | |
| **State Management** | | |
| **Testing** | | |

## 3. ARCHITECTURAL BOUNDARIES
- **Pattern:** (e.g., Layered Architecture, Hexagonal, MVC)
- **Module System:** (e.g., ESM only, CommonJS)
- **Primary UI Components:** (e.g., Radix UI, Headless UI, Custom)
- **Data Fetching:** (e.g., TanStack Query, tRPC, Fetch API)

## 4. CRITICAL CONSTRAINTS (ANTI-HALLUCINATION)
- **Allowed External APIs:** (List only specific APIs, e.g., Stripe, SendGrid)
- **Forbidden Libraries:** (Libraries AI should NEVER suggest or use)
- **Legacy Compatibility:** (e.g., Must support IE11, or Chrome 100+)
- **Mobile Support:** (Responsive Web / Native / None)

## 5. DIRECTORY MAP (X-RAY VIEW)
- `/src/components`: UI Components only (Atomic Design)
- `/src/lib`: Third-party adapters/initialization
- `/src/services`: Business logic and data fetching
- `/src/types`: Centralized TypeScript definitions
- `/migrations`: Database schema history

## 6. SIDECARS & EXTERNAL BINARIES (IF APPLICABLE)
- **Sidecar Name:** (e.g., `file-processor`)
- **Runtime/Language:** (e.g., Rust, Go, Python)
- **Communication Method:** (e.g., JSON over Stdin/Stdout, Command Line Args, Local WebSocket)
- **Binary Storage Path:** (e.g., `/src-tauri/binaries/`)
- **OS-Specific Notes:** (e.g., Require `.exe` on Windows)

## 7. ENVIRONMENT VARIABLES (.env)
*AI MUST update .env.example if new variables are added.*
- `DATABASE_URL`: Required for migrations.
- `API_KEY_...`: 

## 7. DEFINITION OF DONE (PROJECT SPECIFIC)
1. [ ] Pass all unit tests (`npm test`).
2. [ ] Zero TypeScript errors (`tsc --noEmit`).
3. [ ] Responsive verified (Mobile, Tablet, Desktop).
4. [ ] Documentation updated in `README.md` and `API.md`.
5. [ ] Accessibility (WCAG 2.1) compliant.

---
*Created using Enterprise AI Ruleset Framework.*
