# RBX Code v1.2: Luau editor for Android

A fast, touch-friendly Luau code editor for writing Roblox scripts on your phone or tablet.
Scripts are saved on the device; copy or share them into Roblox Studio when you want to run them.

## What's in the editor
**Writing**
- Syntax colors modeled on Roblox Studio's dark theme: keywords, strings, numbers, comments, services and
  globals, function calls, and member access
- Context-aware completions: `game:GetService("` lists services, `Instance.new("` lists classes,
  `Enum.` drills into enum values, `task.`, `math.`, `Vector3.` and similar libraries list their members,
  and `:` / `.` suggest common methods and properties. Words from your own file are suggested too
- Snippets (`if`, `for i`, `for in`, `pcall`, `PlayerAdded`, module template, and more)
- Symbol row above the keyboard (brackets, quotes, `==`, `~=`, `..`, `#`, Tab)
- Smart auto-pairing with type-over, pair deletion on backspace, and auto-indent
- Press Enter after `then` / `do` / `function` / `repeat` and the matching `end` / `until` is added for you;
  typing `end` / `else` / `until` dedents the line
- Bracket matching highlight and current-line highlight

**Editing**
- Undo / redo with history (kept while you browse the library), Find and replace (case toggle),
  Comment toggle, Indent / Outdent, Duplicate / Delete / Move line, Go to line
- **Format**: re-indents the whole script by block structure; long strings and comments are left alone
- **Problems**: unclosed or extra `end`, `until`, brackets and unterminated strings, listed with line numbers
  (tap the status chip to jump to each one). This is a structural check, not a full Luau type checker
- Hardware keyboard shortcuts: Ctrl+S, Ctrl+Z / Ctrl+Y, Ctrl+F, Ctrl+/, Ctrl+D, Tab / Shift+Tab

**Files**
- Searchable script library with previews, delete confirmation, and unsaved-change prompts
- Your work is auto-saved as a draft when the app is backgrounded, so nothing is lost if Android closes it
- Share or copy scripts out; text size adjustable from the More menu
- Handles Android 15 edge-to-edge and keeps the toolbar above the keyboard

## Scope
This is a code editor. It does not inject code into the Roblox app or execute scripts inside the Roblox client.
To run your scripts, paste them into Roblox Studio, or use Roblox's supported tools for experiences you own.

## Build the APK
1. Extract the ZIP and open the `RBXCodeAndroid` folder in Android Studio (JDK 17).
2. Let Gradle sync (Android Studio creates the Gradle wrapper if it is missing).
3. Run on a device or emulator, or choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**.

Debug output: `app/build/outputs/apk/debug/app-debug.apk`

## Project layout
- `MainActivity.kt`: interface, editing behavior, find/replace, library
- `CodeEditText.kt`: editor view with its own line-number gutter
- `Luau.kt`: lexer, problem checker, indentation engine, formatter
- `Suggest.kt`: completion engine
- `Pal.kt`: colors

No third-party libraries are used.
