# MOBILE APPLICATION RULES (MOBILE TASKS ONLY)

1. CROSS-PLATFORM & FRAMEWORKS:
   - Default to cross-platform frameworks (e.g., React Native, Expo, Flutter) unless Native (Swift/Kotlin) is explicitly required.
   - Maintain a unified codebase that compiles seamlessly to both iOS and Android.

2. NATIVE UX & GESTURES:
   - Respect platform-specific UX paradigms: Apple Human Interface Guidelines (iOS) and Material Design (Android).
   - Implement standard mobile gestures (e.g., pull-to-refresh, swipe-to-go-back, bottom-sheet dragging).
   - ALWAYS use Safe Area contexts to prevent content from rendering under notches, camera cutouts, or home indicators.

3. PERFORMANCE & MEMORY OPTIMIZATION:
   - Mobile devices have strict RAM limits. Optimize large data lists using virtualization (e.g., `FlatList` or `FlashList` in React Native). NEVER render massive lists at once.
   - Images must be resized, compressed, and cached aggressively to prevent Out-Of-Memory (OOM) crashes.

4. OFFLINE-FIRST & NETWORK RESILIENCE:
   - Gracefully handle slow, unstable, or completely disconnected network states.
   - Cache critical data locally (e.g., using MMKV, SQLite, or WatermelonDB) to ensure the core app remains usable offline.

5. PERMISSIONS & PRIVACY:
   - Request sensitive permissions (Camera, Location, Notifications) *Just-In-Time* (only when the user interacts with the specific feature), NEVER on app startup.
   - Always provide a clear, user-friendly rationale explaining *why* the permission is necessary before triggering the OS prompt.
