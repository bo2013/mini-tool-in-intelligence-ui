# Rules

## 1. General

- Treat `Tools.md` as the authoritative specification for UI structure and feature scope.
- Treat `Style.md` as the authoritative source for visual style presets.
- Treat `data.yml` as the authoritative source for project metadata and default configuration.
- Read all required source files before implementing the UI.
- If a required source file is missing or unreadable, ask for clarification before proceeding.
- Do not invent features that are not specified.
- All interactive controls must function as described.
- Keep application state consistent when navigating between views.
- Follow accessibility best practices, including keyboard navigation, visible focus indicators, semantic controls, and sufficient contrast.
- Do not present simulated functionality as real functionality.
- Use the project's metadata in the UI where specified.
- Prefer reusable components and maintainable code over duplicated implementations.

## 2. Navigation

- Provide navigation between the available tools and Settings.
- Clearly indicate the current view or selected navigation item.
- Preserve relevant tool state when switching views.
- Provide a way to return to the previous view when applicable.
- Do not add navigation destinations for unspecified features.

## 3. Calculator

- Provide Simple and Advanced modes.
- Allow switching modes using a button or equivalent accessible control.
- Switching modes must preserve the current expression whenever that expression can be represented in the destination mode.
- Do not silently discard an expression when switching modes.
- Validate expressions before evaluating them.
- Handle invalid expressions and division by zero without crashing the application.
- Display calculation results clearly.
- Do not use unsafe expression evaluation such as executing arbitrary input as JavaScript.
- Keep calculation behavior deterministic and distinguish input, result, and error states.

## 4. Unit Converter

- Provide a quantity selection control.
- Update the available units when the selected quantity changes.
- Provide separate source and destination unit controls.
- Provide an input for the value to convert and a clearly displayed result.
- Update the result when the value or either unit changes, when the input is valid.
- Prevent conversions between incompatible quantities.
- Handle empty, invalid, and out-of-range inputs gracefully.
- Use appropriate conversion formulas and avoid unnecessary precision in displayed results.
- Do not claim to support quantities or units that have not been implemented.

## 5. Settings

- Provide controls for appearance, style selection, and layout density.
- Use `CONFIG.default_style` and `CONFIG.default_density` from `data.yml` as the initial settings.
- Use the style presets defined in `Style.md`; do not invent additional presets.
- Preview pending style and density changes before applying them.
- Preview changes without permanently committing them.
- Apply commits the pending settings to the active application state.
- Reset restores the configured default style and density.
- Keep the distinction between pending settings and applied settings clear.
- The density selected in Settings takes precedence over the density suggested by the selected style.
- A style's density in `Style.md` is its default recommendation, not a restriction.
- Invalid configuration values must not prevent the application from loading; use valid defaults as a fallback.

## 6. Settings Persistence

- Keep applied settings consistent across navigation.
- Persist applied settings across page reloads using localStorage.
- Do not persist unapplied preview changes.
- When saved settings are missing or invalid, fall back to the defaults in `data.yml`.
- Reset must restore the configured defaults and update the active application state and saved settings.

## 7. Visual Design

- Follow the selected preset's colors, typography, spacing, border radius, borders, shadows, control styling, and motion guidance from `Style.md`.
- Treat each preset as a coherent visual system rather than mixing unrelated styles.
- Apply the selected layout density consistently across the application.
- Compact density should reduce spacing while preserving usability and readability.
- Comfortable density should provide more generous spacing.
- Respect reduced-motion preferences where supported.
- Maintain readable text contrast and visible keyboard focus.
- Ensure the interface remains usable on narrow and wide screens.

## 8. Implementation Integrity

- Do not add nonfunctional buttons, fake controls, or placeholder interactions that appear complete.
- Do not claim that data is saved, synchronized, or processed externally unless that behavior is implemented.
- Use clear empty, loading, success, and error states wherever relevant.
- Keep dependencies and implementation complexity proportionate to the specified features.
- If a required behavior cannot be implemented as specified, explain the limitation instead of silently substituting a different behavior.