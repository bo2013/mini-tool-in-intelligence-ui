# Tools & UI Structure

## 1. Application Shell

### 1.1 Header

- Display the application name from `DATA.name`.
- Display the application version from `DATA.version`.
- Display the author from `DATA.author`.
- Keep metadata visually secondary to the active tool.

### 1.2 Navigation

- Provide access to Calculator, Unit Converter, and Settings.
- Indicate the currently active view.
- Use clear labels and accessible controls.
- Adapt the navigation to the available screen width.

### 1.3 Main Content

- Display the selected view.
- Keep each tool's state when navigating away and returning.
- Avoid displaying unrelated tools simultaneously when they are not part of the active view.

### 1.4 Footer

- Display the text: "Hi."

## 2. Calculation

### 2.1 Calculator

#### Modes

- Provide Simple and Advanced modes.
- Provide a control to switch between modes.
- Preserve the current expression when switching modes whenever possible.

#### Simple Mode

- Provide a numeric input and controls for basic arithmetic.
- Support addition, subtraction, multiplication, division, decimals, and parentheses.
- Provide controls to evaluate and clear the expression.
- Display the expression and result separately.

#### Advanced Mode

- Support exponentiation, square roots, percentages, and common mathematical functions.
- Provide a clear way to enter functions and parentheses.
- Display the expression and result separately.
- Reject invalid expressions safely.

#### Error Handling

- Handle malformed expressions and division by zero.
- Display understandable error feedback.
- Do not execute arbitrary code entered into the calculator.

### 2.2 Unit Converter

#### Controls

- Quantity selection.
- Source unit selection.
- Destination unit selection.
- Value input.
- Conversion result.
- A control to swap source and destination units.

#### Initial Quantities

- Length: millimeter, centimeter, meter, kilometer, inch, foot, yard, mile.
- Mass: milligram, gram, kilogram, ounce, pound.
- Temperature: Celsius, Fahrenheit, Kelvin.
- Time: second, minute, hour, day.
- Volume: milliliter, liter, US gallon.
- Area: square meter, square kilometer, square foot, acre.

#### Behavior

- Update the available units when the quantity changes.
- Recalculate when valid input or unit selections change.
- Handle temperature conversions using the appropriate formulas.
- Do not mix units belonging to different quantities.
- Display the result with appropriate precision.
- Handle empty or invalid input without crashing.

## 3. Settings

### 3.1 Appearance

- Provide appearance-related settings without inventing unsupported operating-system integrations.

### 3.2 Style Selection

- Provide all presets defined in `Style.md`:
  - Obsidian
  - Swiss
  - Soft Glass
  - Neo Brutal
  - Midnight
  - Warm Paper
- Identify the currently selected style.
- Allow the user to preview a different style before applying it.

### 3.3 Layout Density

- Provide Compact and Comfortable options.
- Apply the selected density consistently throughout the interface.
- Allow density to be configured independently of the selected style.
- Use the configured default density when no saved preference exists.

### 3.4 Settings Preview

- Show a preview of pending style and density changes.
- Update the preview immediately when pending values change.
- Keep the active application appearance unchanged until Apply is selected, except within the preview area.
- Provide a clear indication of which settings are pending.

### 3.5 Apply Button

- Commit pending settings to the active application state.
- Save applied settings using localStorage.
- Preserve the applied settings when navigating between views.

### 3.6 Reset Button

- Restore the configured default style and density.
- Update the pending values and preview.
- Apply the reset settings to the active application state and saved settings.
- Provide clear feedback that the reset has completed.

## 4. Responsive Layout

- Support desktop and narrow-screen layouts.
- Keep controls usable without horizontal overflow.
- Reflow cards and tool sections when necessary.
- Preserve the visual hierarchy of the selected style.

## 5. Accessibility

- Use semantic controls and descriptive labels.
- Support keyboard navigation.
- Show visible focus indicators.
- Do not rely on color alone to communicate state.
- Respect reduced-motion preferences.