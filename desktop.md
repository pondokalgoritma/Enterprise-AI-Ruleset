# DESKTOP APPLICATION RULES (DESKTOP TASKS ONLY)

1. CROSS-PLATFORM COMPATIBILITY:
   - All desktop applications must be built to be fully cross-platform (Windows, Linux, macOS).
   - Use cross-platform APIs and gracefully handle OS-specific edge cases without breaking compatibility.

2. SIDECAR & BINARY DIRECTORIES:
   - All external sidecars, tools, and shared binaries must be centrally stored under a `<vendor_name>` folder (defaulting to `denox`).
   - **Windows:** `%APPDATA%\<vendor_name>\bin`
   - **Linux:** `~/.local/share/<vendor_name>\bin` (or standard XDG data home)
   - **macOS:** `~/Library/Application Support/<vendor_name>\bin`

3. APP CONFIGURATION & DATA DIRECTORIES:
   - Application-specific settings, caches, and local data must be isolated per application inside the `<vendor_name>` folder.
   - **Windows:** `%APPDATA%\<vendor_name>\<appname>`
   - **Linux:** `~/.config/<vendor_name>\<appname>` (or standard XDG config home)
   - **macOS:** `~/Library/Application Support/<vendor_name>\<appname>`

4. DYNAMIC PATH RESOLUTION & CONFIG VARIABLES:
   - STRICTLY FORBIDDEN to hardcode OS-specific string paths (e.g., `C:\Users\...`).
   - **Use Framework Configs:** Do not manually hardcode the vendor name (e.g., `"denox"`) or `"<appname>"` in the code if the framework can handle it. Instead, define them in the project configuration (e.g., `bundle.identifier` like `com.denox.appname` in `tauri.conf.json`, or `productName` in `package.json`).
   - **Native Resolvers:** Let the framework's native path resolver (e.g., `tauri::api::path::app_data_dir()`) automatically resolve and inject the vendor and app name dynamically based on those configurations.

5. RESPONSIVE & MOBILE-FIRST UI:
   - Even though it is a desktop application, the UI MUST be fully responsive and designed with a "Mobile-First" approach.
   - The application window must gracefully handle resizing down to small, mobile-like dimensions (e.g., side-panel sizes) without breaking the layout or causing horizontal scroll issues.
   - Rely on flexible grids, flexbox, CSS variables, and relative units rather than rigid, fixed pixel dimensions.

6. NATIVE DUAL THEMING:
   - Desktop applications must support both **Dark** and **Light** themes.
   - UI components must respond to the system-level theme change automatically.
   - Ensure high contrast and accessibility standards are met in both themes.

7. PREMIUM DESKTOP UX & TITLE BAR:
   - **Custom Title Bar:** Always prefer **Custom Title Bars** over native OS frames to ensure a seamless, premium, and branded user experience.
   - **Window Controls:** The custom title bar MUST implement functional **Minimize**, **Maximize/Restore**, and **Close** buttons using the framework's native API (e.g., `window.minimize()`).
   - **Draggable Region:** The title bar MUST be defined as a draggable region (e.g., `-webkit-app-region: drag` or framework equivalent) to allow users to move the window.
   - **Non-Draggable Controls:** All interactive elements within the title bar (buttons, menus, inputs) MUST be explicitly excluded from the draggable region (e.g., `no-drag`) to ensure they remain interactive.

