# Flutter Basics Lab Answers

## 1. GitHub Repository Link
https://github.com/renalynmesias30-lgtm/flutter_basics_lab

---

## 2. Activity 2: Debug Console Logs
build() called: 4 glasses
build() called: 5 glasses
build() called: 6 glasses

---

## 3. Experiment Observations

### Activity 2 Experiment
* **Action:** Moved `_glasses++` outside of `setState()` in `_addGlass()`.
* **Observation:** The `_glasses` variable value increments internally in the background, but the UI on screen does not update when clicking the button. The screen only updates when a rebuild is triggered later. Calling `setState()` is required to notify Flutter to re-render the UI with new state values.

### Activity 3 Experiment
* **Action:** Removed `Expanded` from one `StatBox` widget.
* **Observation:** The `StatBox` without `Expanded` shrunk down to fit only its immediate contents' minimum width. Meanwhile, the remaining `Expanded` boxes expanded dynamically to share the leftover horizontal space equally.

### Activity 5 Experiment
* **Action:** Changed `borderRadius` in `buildTheme()` from `8` to `20` for `ElevatedButton`.
* **Observation:** The outer corners of all `ElevatedButton` components became significantly more rounded/curved across the app, demonstrating centralized theme styling.

---

## 4. Review Questions Answers

1. **What is the difference between a StatelessWidget and a StatefulWidget? Give one example of each from this lab.**
   * A `StatelessWidget` is immutable and cannot change its appearance or state after being drawn (e.g., `ProfileApp` / `ProfileCard` in Activity 1). A `StatefulWidget` holds mutable state and can update dynamically on the screen using `setState()` (e.g., `WaterTrackerPage` in Activity 2).

2. **Why is a StatefulWidget written as two classes? What does each class do?**
   * It is split into two classes because widgets in Flutter are immutable and discarded frequently. The first class extends `StatefulWidget` and creates the state object, while the second class extends `State` to preserve the mutable data across widget rebuilds and execute the `build()` method.

3. **In Activity 2, what happened when you changed `_glasses` outside `setState()`? Why?**
   * The variable's value updated internally, but the counter text on screen did not change. This happens because Flutter needs `setState()` to be called to mark the widget as dirty and trigger a rebuild of the `build()` method.

4. **Looking at the Debug Console in Activity 2, when is `build()` called?**
   * `build()` is called when the widget is first rendered on screen and every time `setState()` is executed after tapping a button (`+`, `-`, or `Reset`).

5. **Explain the main axis and the cross axis of a Row and of a Column.**
   * For a `Row`, the main axis is horizontal (left-to-right) and the cross axis is vertical (top-to-bottom). For a `Column`, the main axis is vertical (top-to-bottom) and the cross axis is horizontal (left-to-right).

6. **In Activity 3, what happened when you removed `Expanded` from a `StatBox`? What does `Expanded` do?**
   * Removing `Expanded` made the box shrink to fit its text/icon size only. `Expanded` forces a child widget inside a `Row` or `Column` to expand and take up remaining available space along the main axis.

7. **Why do we use `GridView.builder` for the menu instead of a `Column` with many children?**
   * `GridView.builder` creates items lazily (only when visible on screen), making it performance-efficient for potentially long lists. In contrast, a `Column` builds all children at once and does not scroll automatically, causing overflow errors.

8. **How do `Stack` and `Positioned` create the Best seller badge in Activity 4?**
   * `Stack` overlays widgets on top of each other in layers. `Positioned` is used inside a `Stack` to pin the "Best seller" badge at precise relative offsets (e.g., top: 8, left: 8) over the card background.

9. **What is the difference between customizing with `ThemeData` and with a style on one widget? Give one example of each from Activity 5.**
   * `ThemeData` applies styles globally across all matching widgets in the app (e.g., setting global button rounded corners via `elevatedButtonTheme` in `buildTheme()`). A widget-level style applies locally to a single element only (e.g., setting local padding directly on a specific `Card` or `Padding` widget).

10. **When you flip the dark-mode switch in Activity 5, which widget holds the state, and how does the change reach `MaterialApp`?**
    * The root widget `ThemeDemoApp` (`_ThemeDemoAppState`) holds the `_isDark` boolean state. When flipped in `SettingsPage`, a callback function (`onDarkChanged`) is executed, which runs `setState()` in `_ThemeDemoAppState` and updates the `themeMode` property passed into `MaterialApp`.