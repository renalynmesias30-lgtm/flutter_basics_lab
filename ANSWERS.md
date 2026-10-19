# Flutter Basics Lab Answers

## 1. GitHub Repository Link
https://github.com/renalynmesias30-lgtm/flutter_basics_lab


## 2. Activity 2: Debug Console Logs
build() called: 4 glasses
build() called: 5 glasses
build() called: 6 glasses


## 3. Experiment Observations

### Activity 2 Experiment

I moved `_glasses++` outside `setState()` and tapped the **+** button. The screen did not change. It stayed at "0 / 6 glasses" and the progress bar did not fill. No new `build() called` line showed in the Debug Console. The number changed inside the memory, but the screen did not update. This is because `setState()` tells Flutter to run `build()` again. Without it, the screen is not redrawn. I put the code back to the original after the test.

### Activity 3 Experiment

When I removed `Expanded` from one StatBox, that box became small. It only took the size of what is inside it (the icon and the text). It was not the same width as the other three boxes. The other boxes used all the extra space. `Expanded` makes a widget fill the extra space in a Row, and many Expanded widgets share the space equally. I put `Expanded` back after the test.

### Activity 5 Experiment

I changed the button corner radius in `elevatedButtonTheme` from **8 to 20**. The corners of the **Elevated** button became rounder, almost like a pill shape. The **Outlined** and **Filled** buttons did not change because `elevatedButtonTheme` is only for ElevatedButton.

## 4. Review Questions Answers

**1. What is the difference between a StatelessWidget and a StatefulWidget? Give one example of each.**
A **StatelessWidget** does not change after it is drawn. Example: `ProfileCard` in Activity 1. A **StatefulWidget** has data that can change while the app is running. Example: `WaterTrackerPage` in Activity 2.


**2. Why is a StatefulWidget written as two classes? What does each class do?**
The **widget class** (`WaterTrackerPage`) only creates the State object. The **State class** (`_WaterTrackerPageState`) keeps the data that changes (`_glasses`) and has the `build()` method. They are separate because the widget can be made again, but the State keeps the data.


**3. In Activity 2, what happened when you changed `_glasses` outside `setState()`? Why?**
The number changed in memory, but the screen did not change. This is because `setState()` tells Flutter to run `build()` again. Without it, the screen is not redrawn.


**4. Looking at the Debug Console in Activity 2, when is `build()` called?**
`build()` is called when the screen is first shown. It is also called every time `setState()` is called, like when I tap +, - or Reset.


**5. Explain the main axis and the cross axis of a Row and of a Column.**
In a **Row**, the main axis goes left to right (horizontal) and the cross axis goes up and down (vertical). In a **Column**, the main axis goes up and down (vertical) and the cross axis goes left to right (horizontal).


**6. In Activity 3, what happened when you removed Expanded from a StatBox? What does Expanded do?**
The box became small and was not the same width as the others. It only took the size of what is inside it. `Expanded` makes a widget fill the extra space in a Row or Column. If there are many Expanded widgets, they share the space equally.


**7. Why do we use GridView.builder for the menu instead of a Column with many children?**
`GridView.builder` only builds the cards that you can see on the screen, so it is fast even with many items. It can also scroll by itself. A Column builds all the items at once and does not scroll by itself.


**8. How do Stack and Positioned create the Best seller badge in Activity 4?**
A **Stack** puts widgets on top of each other. **Positioned** puts the badge in one exact place (`top: 8, left: 8`). The badge only shows when `item.bestSeller` is true.


**9. What is the difference between customizing with ThemeData and with a style on one widget? Give one example of each from Activity 5.**
**ThemeData** changes the look of the whole app. Example: `elevatedButtonTheme` in `buildTheme()`, which changes all ElevatedButtons. A **style on one widget** changes only that one widget. Example: `TextStyle(fontSize: 24)` on one `Text`.


**10. When you flip the dark-mode switch in Activity 5, which widget holds the state, and how does the change reach MaterialApp?**
`_ThemeDemoAppState` holds the state (`_isDark`). When I flip the switch, it calls `onDarkChanged` (`_setDark`), which calls `setState()`. Then `ThemeDemoApp` builds again, and `MaterialApp` picks the dark or light theme using `themeMode`. This is called lifting state up.