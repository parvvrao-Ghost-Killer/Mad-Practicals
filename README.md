# Practical 02 - Activity Life Cycle and Basic UI

## Aim
To create an Android application that demonstrates the functions of the **Activity Life Cycle** and **Basic UI** components using `ConstraintLayout`, `TextView`, `Logcat`, `Toast`, and `Snackbar`.

## Practical Question
Create an Android Application to demonstrate functions of Activity Life Cycle and Basic UI.

Create an Activity to display "Hello World" in a `TextView` in the center of the Activity screen with a yellow (`android:background="#FFFF00"`) layout background.

TextView properties should be:
- Text Color: Holo Blue (`android:textColor="@android:color/holo_blue_bright"`)
- Font Size: `27sp` (`android:textSize="27sp"`)
- Text Style: Bold and Italic (`android:textStyle="bold|italic"`)

After creating the Activity, demonstrate functions of the Activity Life Cycle by using `Log` message, `Toast` message, and `Snackbar` message. All methods of the Activity life cycle should be printed in Logcat.

---

## Concepts Used
1. **Activity Life Cycle Callbacks**: Understanding state transitions (`onCreate`, `onStart`, `onResume`, `onPause`, `onStop`, `onRestart`, `onDestroy`).
2. **Basic UI & ConstraintLayout**: Centering UI elements using layout constraints.
3. **TextView Styling**: Applying custom text colors, font sizes, and font styles in XML.
4. **Android In-built Resources**: Accessing system colors like `@android:color/holo_blue_bright`.
5. **Logcat Logging**: Printing debug messages using `Log.d()`.
6. **Toast Messages**: Displaying brief transient notifications using `Toast.makeText()`.
7. **Snackbar Messages**: Displaying lightweight feedback popups with `Snackbar.make()`.

---

## Technologies Used
- **Language**: Kotlin
- **Platform**: Android SDK (Min SDK: 24, Target SDK: 35)
- **UI Framework**: Android XML Layout (`ConstraintLayout`)
- **Libraries**: `androidx.appcompat`, `com.google.android.material`

---

## Requirements
- Android Studio Ladybug or later / IntelliJ IDEA with Android plugin
- Android SDK 35
- Android Emulator or physical device running Android 7.0 (API 24) or higher

---

## Project Structure
```text
Practical-02-Activity-Lifecycle/
├── app/
│   ├── build.gradle.kts
│   └── src/
│       └── main/
│           ├── AndroidManifest.xml
│           ├── java/com/example/lab_practical_2/
│           │   └── MainActivity.kt
│           └── res/
│               ├── layout/
│               │   └── activity_main.xml
│               └── values/
│                   ├── colors.xml
│                   ├── strings.xml
│                   └── themes.xml
├── build.gradle.kts
└── settings.gradle.kts
```

---

## How It Works
1. When the app launches, `onCreate()` is invoked. The layout `activity_main.xml` is inflated, rendering a yellow screen with centered bold-italic "Hello World" text in Holo Blue.
2. For every lifecycle callback (`onCreate`, `onStart`, `onResume`, `onPause`, `onStop`, `onRestart`, `onDestroy`), the helper method `showLifecycleEvent()` is executed:
   - Prints a debug log entry to Logcat with tag `"ActivityLifecycle"`.
   - Shows a `Toast` message notification on screen.
   - Shows a Material `Snackbar` popup at the bottom of the layout.
3. When navigating away, putting the app in background, or rotating the device, the corresponding lifecycle callbacks (`onPause`, `onStop`, `onRestart`, `onDestroy`) trigger their respective log and notification messages.

---

## Important Classes
- **`MainActivity`**: The main entry point extending `AppCompatActivity`, overriding all 7 lifecycle callbacks.
- **`Log`**: Android utility class for writing log entries (`Log.d`).
- **`Toast`**: Class for displaying short transient popup messages.
- **`Snackbar`**: Material Design component for displaying animated bottom popups.

---

## Important Methods
- `onCreate(savedInstanceState: Bundle?)`: Called when the activity is first created. Initializes UI with `setContentView()`.
- `onStart()`: Called when the activity becomes visible to the user.
- `onResume()`: Called when the activity starts interacting with the user.
- `onPause()`: Called when the activity loses focus or is partially obscured.
- `onStop()`: Called when the activity is no longer visible.
- `onRestart()`: Called after the activity has been stopped, prior to being started again.
- `onDestroy()`: Called before the activity is destroyed.

---

## Permissions
No special permissions required for this practical.

---

## Required Assets
No external image/audio assets required. Standard Android internal color resource `@android:color/holo_blue_bright` is used.

---

## How to Run
1. Open Android Studio and import the project folder `Lab_practical_2`.
2. Sync Gradle files (`Gradle Sync`).
3. Select an Android Emulator or connected physical device.
4. Click **Run** (`Shift + F10`).
5. Open **Logcat** (`Alt + 6`) in Android Studio and filter by `tag:ActivityLifecycle` to observe lifecycle logs in real time.

---

## Expected Output
- **UI**: Full screen with bright yellow background (`#FFFF00`). "Hello World" text centered, colored in Holo Blue, 27sp font size, styled in bold and italic.
- **Lifecycle Feedback**: On screen popup notifications (`Toast` and `Snackbar`) as well as Logcat entries showing:
  - `ActivityLifecycle: onCreate called`
  - `ActivityLifecycle: onStart called`
  - `ActivityLifecycle: onResume called`
  (and subsequent states when pausing or exiting the app).

---

## Viva Questions & Answers

### Q1: What are the main callbacks of the Activity Life Cycle?
**Answer:** The 7 main callbacks are `onCreate()`, `onStart()`, `onResume()`, `onPause()`, `onStop()`, `onRestart()`, and `onDestroy()`.

### Q2: What is the difference between `onPause()` and `onStop()`?
**Answer:** `onPause()` is called when the Activity is partially visible or loses focus (e.g., a dialog overlay appears). `onStop()` is called when the Activity is completely hidden from the user.

### Q3: When is `onRestart()` called?
**Answer:** `onRestart()` is called when an Activity that was previously stopped is about to start again, right before `onStart()`.

### Q4: What is the difference between Toast and Snackbar?
**Answer:**
- **Toast**: A quick, system-level popup message that cannot be interacted with and stays visible for a set time even if the app closes.
- **Snackbar**: A Material Design component anchored to a view layout. It can contain action buttons (e.g. "Undo") and automatically dismisses.

### Q5: What parameters are needed for `Toast.makeText()`?
**Answer:** Context (e.g., `this`), the message text/resource ID, and the duration (`Toast.LENGTH_SHORT` or `Toast.LENGTH_LONG`).

### Q6: What parameters are required for `Snackbar.make()`?
**Answer:** A anchor `View` (e.g., layout root view), message text, and duration (`Snackbar.LENGTH_SHORT`, `LENGTH_LONG`, or `LENGTH_INDEFINITE`).

### Q7: How do you set font size and style for a `TextView` in XML?
**Answer:** Use `android:textSize="27sp"` for font size and `android:textStyle="bold|italic"` for font style.

### Q8: Why do we use `sp` (scale-independent pixels) for text sizes?
**Answer:** `sp` scales according to the user's system font size preferences, ensuring accessibility for users with custom display settings.

### Q9: How do you log debug messages in Android Logcat?
**Answer:** Using `Log.d(TAG, message)`, where `TAG` is a string identifier for filtering messages in Logcat.

### Q10: What is the purpose of `ConstraintLayout`?
**Answer:** `ConstraintLayout` allows creating flat, responsive UI hierarchies by positioning views relative to sibling views or parent constraints, avoiding nested layout overhead.

---

## Common Errors & Troubleshooting
1. **`Snackbar` causing crash / IllegalArgumentException**: Occurs if the theme doesn't inherit from a Material Theme or if the anchor view is `null`. Ensure `themes.xml` inherits from `Theme.Material3` or `Theme.MaterialComponents`.
2. **Missing lifecycle logs**: Ensure the tag in `Log.d(tag, ...)` matches your Logcat filter query.

---

## Notes
- Folder Name: `Practical-02-Activity-Lifecycle`
- Complies strictly with Ganpat University MAD Practical 2 specifications.
