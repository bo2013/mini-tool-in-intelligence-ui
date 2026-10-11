# Rules

## 1. General

- Treat `Tools.md` as the specification for UI structure and feature scope.
- Treat `Style.md` as the source for visual style presets.
- Treat `data.yml` as the source for project metadata and default configuration.
- Read the required source files before implementing the UI.
- If a required source file is missing or unreadable, ask for clarification before proceeding.
- Stay within the specified feature scope.
- Keep application state consistent when navigating between views.
- Follow accessibility best practices, including keyboard navigation, visible focus indicators, semantic controls, and sufficient contrast.
- Do not present simulated functionality as real functionality.
- Use the project's metadata in the UI where specified.
- Prefer reusable components and maintainable code over duplicated implementations.

## 2. Navigation

- Provide navigation between the available tools and Settings.
- Indicate the current view or selected navigation item.
- Preserve relevant tool state when switching views.
- Provide a way to return to the previous view when applicable.

## 3. Calculator

- Provide Simple and Advanced modes, switchable via an accessible control.
- Preserve the current expression when switching modes whenever it can be represented in the destination mode; do not silently discard it.
- Validate expressions before evaluating them.
- Handle invalid expressions and division by zero without crashing the application.
- Display results clearly.
- Do not evaluate arbitrary input as code.
- Distinguish input, result, and error states in the display.

## 4. Unit Converter

- Provide a quantity selector and update the available units when the quantity changes.
- Provide separate source and destination unit controls with an input for the value and a clearly displayed result.
- Recalculate when the value or either unit changes, when the input is valid.
- Prevent conversions between incompatible quantities.
- Handle empty and invalid input without breaking the interface.
- Use appropriate conversion formulas and avoid unnecessary precision in results.
- Do not claim quantities or units that have not been implemented.

## 5. Settings

- Provide controls for appearance, style selection, and layout density.
- Use `CONFIG.default_style` and `CONFIG.default_density` from `data.yml` as the initial settings.
- Use only the style presets defined in `Style.md`.
- Preview pending style and density changes before applying them, without committing them.
- Apply commits the pending settings to the active application state.
- Reset restores the configured default style and density.
- Keep the distinction between pending and applied settings clear.
- The density chosen in Settings takes precedence over the density suggested by the selected style.
- A style's density in `Style.md` is a default recommendation, not a restriction.
- Invalid configuration values should not prevent the application from loading; fall back to valid defaults.

## 6. Settings Persistence

- Keep applied settings consistent across navigation.
- Persist applied settings across page reloads using localStorage.
- Do not persist unapplied preview changes.
- When saved settings are missing or invalid, fall back to the defaults in `data.yml`.
- Reset restores the configured defaults and updates the active application state and saved settings.

## 7. Visual Design

- Follow the selected preset's colors, typography, spacing, border radius, borders, shadows, control styling, and motion guidance from `Style.md`.
- Treat each preset as a coherent visual system rather than mixing unrelated styles.
- Apply the selected layout density consistently across the application.
- Favor readability and usability, especially in Compact density.
- Respect reduced-motion preferences where supported.
- Maintain readable text contrast and visible keyboard focus.
- Keep the interface usable on narrow and wide screens.

## 8. Implementation Integrity

- Avoid placeholder interactions or nonfunctional controls that appear complete.
- Do not claim that data is saved, synchronized, or processed externally unless that behavior is implemented.
- Use clear empty, loading, success, and error states wherever relevant.
- Keep dependencies and implementation complexity proportionate to the specified features.
- If a required behavior cannot be implemented as specified, explain the limitation instead of silently substituting a different behavior.