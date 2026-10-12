# Free Sample — Flutter: Your First Widget Tree

> **Difficulty:** Beginner · **Time:** ~20 minutes · **Level:** The first step of the Flutter/Dart track.
> **Outcome:** you will build (and run) a small screen made purely of nested widgets, and understand why a UI is a tree.

---

## 1. Why this lesson exists

Flutter's superpower is that **everything is a widget** — layout, styling, padding, even the text itself. The paid track turns this into a production chat dashboard (WebSockets, state, animations). This free lesson gives you the one idea everything else builds on: **the widget tree**.

## 2. Install & create (5 minutes)

```bash
flutter create first_app
cd first_app
```

## 3. Write a tiny widget tree

Replace the contents of `lib/main.dart`:

```dart
import 'package:flutter/material.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text('Project Success Sample')),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              const Text('Your first widget tree'),
              const SizedBox(height: 12),
              ElevatedButton(
                onPressed: () {},
                child: const Text('A button'),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

## 4. What you just built

```
MaterialApp          ← the app (theme, routes)
 └─ Scaffold         ← the page skeleton (app bar + body)
     ├─ AppBar       ← the top bar
     └─ Center       ← centers its child
         └─ Column   ← stacks children vertically
             ├─ Text
             ├─ SizedBox      ← spacing
             └─ ElevatedButton
```

A widget tree is exactly that: **parent widgets wrap child widgets**. `Column` *is* its children — the tree *is* the layout.

## 5. Run it (2 minutes)

```bash
flutter run              # any connected device/emulator or Chrome
# or build web:
flutter build web
```

Tap the button (it does nothing yet — that's state, the next step).

## 6. Why this is the whole game

- UI = data-shaped trees (this is the mental model for everything: navigation, theming, state).
- Widgets are **immutable descriptions**; Flutter rebuilds the parts that change.
- The paid track adds **stateless → stateful → Riverpod** to make trees react to data.

---

## 🚧 Where the paid curriculum begins (the gate)

| This free step | The paid next step (Flutter track) |
|---|---|
| `StatelessWidget` | **StatefulWidget**, `setState`, and the widget lifecycle |
| One static screen | **Navigation** (Navigator, GoRouter), theming, responsive layouts |
| A dead button | **Riverpod state**, async providers, and the AI chat build |
| No data | `dio` HTTP, JSON serialization, **flutter_secure_storage** |
| No polish | Animations (Hero, Lottie, CustomPainter), dark mode, glassmorphism |
| No release | Testing, Firebase, method channels, profiling, ASO, App Store + Play Store |

The full 154-chapter Flutter track and its **Senior Dev Insights** are inside the curriculum → **[UPGRADE.md](../UPGRADE.md)**.

---

> **Try this now:** change `Column` to `Row` (and tweak `mainAxisAlignment`) to feel how the same data re-lays-out instantly. That instant feedback loop is the Flutter habit.