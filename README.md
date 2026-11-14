# 🛡️ Dex2cPlus — Native DEX-to-C++17 JNI Protection Suite

[](https://github.com/iAmINCoder/Dex2cPlus)

[](https://github.com/iAmINCoder/Dex2cPlus)
[](https://developer.android.com)
[](https://isocpp.org)
[](https://llvm.org)
[](https://developer.android.com/ndk)
[License Apache 2.0](https://www.google.com/search?q=https://github.com/iAmINCoder/Dex2cPlus/blob/main/LICENSE)
[Developer Telegram](https://www.google.com/search?q=https://t.me/INCoderDev)
[](https://t.me/INCoderX)

> **Dex2cPlus** is a high-performance, on-device Android DEX-to-C++17 bytecode transpiler and native `.so` protection suite architected by **[@INCoderDev](https://www.google.com/search?q=https://t.me/INCoderDev)** ([iAmINCoder/Dex2cPlus](https://github.com/iAmINCoder/Dex2cPlus)). It converts Dalvik bytecode methods from single-DEX and multi-DEX APKs into obfuscated C++17 JNI functions, compiles them on-device across up to 4 CPU architectures using **LLVM Clang + LLD**, patches the DEX files with `native` method modifiers, and repackages the APK via a zero-recompression **C++ `FastZipModifier`** engine.

## ⚡ Live Pipeline Overview

[](https://github.com/iAmINCoder/Dex2cPlus)

| Stage | Engine Module | Input | Output | Core Technology |
| :--- | :--- | :--- | :--- | :--- |
| **Stage 1** | `ApkDexManager` | Target `.apk` | Parsed `DexClassItem` Tree | Smali / Dexlib2 (`classes.dex` .. `classesN.dex`) |
| **Stage 2** | `Dex2CTranslator` | Selected DEX Classes | Obfuscated C++17 JNI Sources | Dalvik AST Transpiler + `RegisterNatives` |
| **Stage 3** | `DexRewriterEngine` | Original `.dex` Files | Patched `ACC_NATIVE` `.dex` | Custom `Loader` Class + `<clinit>` Injection |
| **Stage 4** | `NdkCompiler` | Generated `.cpp` Units | Stripped `lib<name>.so` ELF | On-Device Android NDK Sysroot + LLVM Clang/LLD |
| **Stage 5** | `FastZipModifier` | Cached APK + `.dex` + `.so` | Protected Output Bundle | Native C++17 Central Directory ZIP Modifier |

## ✨ Core Features & UI/UX Architecture

- **🔍 Dual-Mode Tree Explorer with Shimmer Skeleton Loader**: Browse APK contents in either hierarchical **Package Tree** mode or multi-DEX **`.dex` File Tree** mode with instant `Search...` filtering, recursive package/class check counters, and synchronized `ShimmerFrameLayout` skeleton loading animations.
- **🛡️ C++17 JNI Bytecode Transpiler (`Dex2CTranslator`)**: Translates Dalvik instructions—including arithmetic ops, control-flow branches, `try`/`catch` exception tables, static/virtual/direct invocations, field accesses, and multidimensional arrays—into self-contained C++17 JNI routines.
- **🔒 Dynamic `RegisterNatives` (`JNI_OnLoad`)**: Hides exported `Java_pkg_Class_method` symbols from the ELF `.dynsym` table by registering native function pointers dynamically inside `JNI_OnLoad`.
- **🧬 JNI Environment & String Encryption**: Obfuscates class descriptors, method names, and type signatures in generated C++ sources and decrypts native metadata at runtime.
- **🎛️ Granular Method Filter Controls**: Independently toggle translation for `Synthetic`, `Bridge`, `Static`, `Virtual`, `Private`, `Synchronized`, and `Varargs` methods directly from Settings.
- **⚙️ On-Device Multi-ABI NDK Toolchain (`NdkCompiler`)**: Supports one-tap online download or local archive installation of `mini_ndk.zip`, compiling in parallel across `arm64-v8a`, `armeabi-v7a`, `x86`, and `x86_64`.
- **🚀 Zero-Recompression C++ ZIP Engine (`fast_zip_modifier.cpp`)**: Replaces modified `.dex` entries and injects `lib/<abi>/lib<name>.so` directly at the binary ZIP central directory level without re-compressing unchanged APK resources.
- **💻 Live Glow Build Terminal (`GlowConsoleTextView`)**: Real-time compilation console with status indicators, stage progress tracking, one-tap log copy, and instant build cancellation.
- **🎨 Adaptive Material 3 DayNight UI**: Seamless status/navigation bar integration with **Light Theme**, **Dark Theme** (Graphite/Charcoal), and **System Default** modes.

## 📂 Project Structure

```text
Dex2cPlus/
├── app/
│   ├── build.gradle.kts                  # compileSdk 36, minSdk 21, NDK 29.0.14033849, Java 17
│   └── src/main/
│       ├── AndroidManifest.xml           # Permissions, activities & storage configuration
│       ├── cpp/
│       │   ├── CMakeLists.txt            # Native C++17 build script for libdex2cplus.so
│       │   ├── dex2c_helper.cpp          # Native ABI detection & JNI helpers
│       │   ├── fast_zip_modifier.cpp     # High-speed C++ ZIP central directory engine
│       │   └── telegram_profile_dialog.cpp # Runtime byte decryptor for profile metadata
│       ├── java/com/dex2c/plus/
│       │   ├── MainActivity.java         # APK selector, dual-mode tree explorer & shimmer UI
│       │   ├── ConsoleLogger.java        # Thread-safe live terminal logger
│       │   ├── StorageHelper.java        # Storage permissions & /storage/emulated/0/Dex2cPlus
│       │   ├── engine/
│       │   │   ├── ApkDexManager.java    # Multi-DEX parser & class hierarchy builder
│       │   │   ├── Dex2CTranslator.java  # Dalvik bytecode to C++17 JNI transpiler
│       │   │   ├── DexRewriterEngine.java # Native modifier patcher & Loader class injector
│       │   │   ├── FastZipModifier.java  # JNI bridge for native C++ ZIP modification
│       │   │   └── NdkCompiler.java      # On-device Mini-NDK manager & parallel Clang driver
│       │   ├── model/
│       │   │   ├── DexClassItem.java     # Class node model & selection state
│       │   │   └── ProjectState.java     # Persistent configuration & preferences manager
│       │   └── ui/
│       │       ├── BuildActivity.java    # Protection pipeline executor & terminal screen
│       │       ├── ClassAdapter.java     # High-speed flattened tree RecyclerView adapter
│       │       ├── FileManagerDialog.java # Built-in storage browser for APK & NDK files
│       │       ├── GlowConsoleTextView.java # Custom glowing terminal text view
│       │       ├── SettingsActivity.java # Theme, NDK, ABI, library & method filter settings
│       │       ├── ShimmerFrameLayout.java # Specular shimmer skeleton animation container
│       │       ├── TelegramProfileDialog.java # Circular profile dialog with 2s shimmer loader
│       │       ├── AcknowledgementActivity.java # Official credits & open-source attributions
│       │       └── UiAnimator.java       # Tactile press & window decor animations
│       └── res/                          # Adaptive Light/Dark colors, vector drawables & layouts
├── build.gradle.kts
└── settings.gradle.kts
```

## ⚙️ Settings & Protection Options

| Option Name | Default | Functionality |
| :--- | :--- | :--- |
| **Theme Preference** | `System Default` | Choose between **Light**, **Dark**, or **System Default** appearance. |
| **Manage Native code support** | `mini_ndk` | Install or uninstall the on-device NDK sysroot + LLVM Clang toolchain (Online or Local `.zip`). |
| **Parallel Build** | `ON` | Compiles C++ translation units across multiple threads for faster multi-ABI builds. |
| **Custom Library Name** | `native-lib` | Sets the compiled shared library name (`lib<name>.so`). |
| **Custom Loader Class** | `Loader` | Sets the injected DEX loader class name responsible for loading the native library. |
| **ABI Architectures** | `arm64-v8a`, `armeabi-v7a`, `x86`, `x86_64` | Configures target CPU architectures for native `.so` compilation. |
| **Method Types Filter** | All `ON` | Selects which method modifiers (`Synthetic`, `Bridge`, `Static`, `Virtual`, `Private`, `Synchronized`, `Varargs`) are translated. |
| **RegisterNatives** | `ON` | Binds JNI methods dynamically inside `JNI_OnLoad` instead of exporting symbol names. |
| **Env Encryption** | `ON` | Encrypts JNI class, method, and field lookup strings in generated C++ code. |
| **Rewrite DEX** | `ON` | Patches translated methods to `native` and outputs the protected package to `/storage/emulated/0/Dex2cPlus/`. |

## 🚀 Build & Installation Guide

1. **Clone the Repository**
   ```bash
   git clone https://github.com/iAmINCoder/Dex2cPlus.git
   cd Dex2cPlus
   ```

2. **Build Requirements**
   - **Android SDK**: `compileSdk = 36`, `minSdk = 21`, `targetSdk = 34`
   - **Android NDK**: `29.0.14033849`
   - **CMake**: `4.1.2`
   - **Java Toolchain**: JDK 17

3. **Assemble APK via Gradle**
   ```bash
   ./gradlew assembleDebug
   ```

4. **Protecting an APK on Android**
   - Open **Dex2cPlus** and grant storage permission.
   - Navigate to **3-Dot Menu ➔ Settings ➔ Manage Native code support** and install the NDK toolchain.
   - Tap the **APK Icon** in the top header and pick your target `.apk` file.
   - Filter classes via `Search...` or switch between **Package Tree** and **`.dex` Tree** modes to select classes for native conversion.
   - Tap the floating **Build** button at the bottom-right to run the protection pipeline and save the output in `/storage/emulated/0/Dex2cPlus/`.

## 🤝 Credits & Official Links

| Role / Component | Official Link |
| :--- | :--- |
| **Core Engine & Android Architect** | **[@INCoderDev](https://www.google.com/search?q=https://t.me/INCoderDev)** • **[GitHub (`iAmINCoder/Dex2cPlus`)](https://github.com/iAmINCoder/Dex2cPlus)** |
| **Official Telegram Channel** | **[@INCoderX](https://t.me/INCoderX)** |
| **DEX Bytecode Framework** | **[Smali & Dexlib2](https://github.com/google/smali)** |
| **Native Compiler Toolchain** | **[LLVM Clang & LLD](https://llvm.org)** • **[Android NDK](https://developer.android.com/ndk)** |
| **UI & Material Components** | **[AndroidX & Material Design 3](https://m3.material.io)** |
