# TESTING RULES (STRICT / QA)

1. FOCUS ON BEHAVIOR & EDGE CASES:
   - Write tests to ensure business logic performs exactly as expected.
   - Always include tests for edge cases (boundary values, empty inputs, extreme values) and error/failure paths.

2. MOCKING & DEPENDENCIES:
   - Isolate unit tests by mocking external dependencies (Databases, Third-party APIs, File Systems).
   - Ensure tests execute quickly and independently without side effects.

3. TEST READABILITY:
   - Use the AAA pattern (Arrange, Act, Assert) or Given-When-Then structure.
   - Test function names must be highly descriptive, explaining the scenario being tested and the expected outcome.

4. TEST-DRIVEN DEVELOPMENT (TDD) WORKFLOW:
   - **TDD Skill Mandate:** AI MUST explicitly use the `test-driven-development` and `unit-testing-test-generate` skills when implementing new features or bugfixes to enforce the RED-GREEN-REFACTOR cycle.
   - **Red-Green-Refactor:** For every new feature or bug fix, follow the TDD cycle:
     1. **RED:** Write a failing test that defines the expected behavior.
     2. **GREEN:** Write the minimal code to pass the test.
     3. **REFACTOR:** Clean up the implementation while keeping the test passing.
   - **Mandatory Coverage:** 100% unit test coverage is MANDATORY for all Business/Service Layer logic. UI components and Repositories should have coverage for critical interactions only.
