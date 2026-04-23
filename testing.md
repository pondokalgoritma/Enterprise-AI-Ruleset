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
