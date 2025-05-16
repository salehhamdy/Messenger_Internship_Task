
# Messenger Internship Task

A lightweight **Messenger** prototype built with **Kotlin** and **Jetpack Compose** as part of an internship assessment.

---

## ✨ Features

| Module | Highlights |
| ------ | ---------- |
| **Landing** | Displays the list of conversations with dummy / persisted data |
| **Chat** | Single-chat screen with sent & received bubbles, timestamps, and auto-scroll |
| **Local Storage** | Offline-first using **Room** ( `MessengerEntity`, `MessengerDao`, `MessengerDatabase` ) |
| **Navigation** | Single-activity architecture powered by **Navigation-Compose** |
| **MVVM + State** | ViewModels expose immutable `State` classes consumed by Composables |
| **Theming** | Material 3 light & dark, typography & color token files |
| **Localization** | English (default) & Arabic (`values-ar/strings.xml`) |

---

## 🗂 Project Structure (package-by-feature)

```text
com.linkdev.messengerinternshiptask
│
├── data.database
│   ├── entity        // Room entities (MessengerEntity)
│   ├── dao           // Room DAO (MessengerDao)
│   └── MessengerDatabase.kt
│
├── navigation        // NavGraph destinations (Chat, MessengerLanding)
│
├── ui
│   └── components
│       ├── chat      // Chat screen & message bubbles
│       └── landing   // Landing screen & actions
│
├── theme             // Color.kt, Type.kt, Theme.kt
├── utils             // Constants & Extensions
└── MainActivity.kt   // Single-activity Compose host
```

> **Tip:** every folder is _self-contained_—UI, ViewModel, and state live together for easy refactorability.

---

## 🛠️ Tech Stack

- **Kotlin 1.9** & Kotlin Coroutines
- **Jetpack Compose BOM** (Material 3, Navigation-Compose)
- **Room 2.6** for local persistence
- **AndroidX Lifecycle** ViewModel + StateFlow
- Gradle Kotlin DSL (AGP `8.x`)

---

## 🚀 Getting Started

### Prerequisites

- **Android Studio Iguana** (or newer)
- **JDK 17**
- Android SDK 33+

### Clone & Open

```bash
git clone https://github.com/<your-org>/messenger-internship-task.git
cd messenger-internship-task
```

1. **File → Open** the project in Android Studio.
2. Let Gradle sync & download dependencies.
3. Select an emulator / device and press ▶️ Run.

---

## 🏗️ Build Commands

| Task | Command |
| ---- | ------- |
| Assemble Debug APK | `./gradlew assembleDebug` |
| Assemble Release APK | `./gradlew assembleRelease` |
| Run Unit Tests | `./gradlew test` |
| Run Android Instrumented Tests | `./gradlew connectedAndroidTest` |

Generated APKs are output to `app/build/outputs/apk/`.

---

## 📐 Architecture Overview

```
                                    +----------------+
                                    |   MainActivity |
                                    +-------+--------+
                                            |
                            Navigation-Compose (NavHost)
                                            |
              +-----------------------------+-----------------------------+
              |                                                           |
       +------+------+                                           +--------+--------+
       | LandingViewModel |                               |    ChatViewModel     |
       +---------+--------+                               +--------+-------------+
                 |                                                   |
         StateFlow<MessengerLandingState>                 StateFlow<MessengerState>
                 |                                                   |
           Composables                                        Composables
```

- **Single-source of truth:** each screen owns its own immutable `State` data class.
- **Unidirectional data flow:** UI → ViewModel → Repository / DAO.

---

## 🌐 Localization

All user-facing strings live in `res/values/strings.xml` (English) and `res/values-ar/strings.xml` (Arabic). From Compose, simply use `stringResource(R.string.your_key)`.

---

## 📝 Contributing

PRs are welcome! For major changes, please open an issue first to discuss what you would like to change.

```bash
# Create a feature branch
git checkout -b feature/amazing-feature

# Commit your changes
git commit -m "feat: add amazing feature"

git push origin feature/amazing-feature
```

---

## 📄 License

Distributed under the **MIT License**. See `LICENSE` for more information.
