&lt;div align=&quot;center&quot;&gt;

&lt;img src=&quot;assets/header_banner.svg&quot; alt=&quot;Dex2cPlus Official Animated Banner&quot; width=&quot;100%&quot; /&gt;

<br/>

&lt;a href=&quot;https://github.com/iAmINCoder/Dex2cPlus&quot;&gt;
  &lt;img src=&quot;https://readme-typing-svg.demolab.com?font=JetBrains+Mono&amp;weight=700&amp;size=22&amp;duration=3200&amp;pause=900&amp;color=689BF6&amp;center=true&amp;vCenter=true&amp;width=780&amp;lines=Dex2cPlus+%E2%80%94+Native+DEX+to+C%2B%2B17+JNI+Protection+Suite;Multi-DEX+Smali+%26+Dexlib2+Bytecode+Transpilation+Engine;On-Device+LLVM+Clang+%2B+LLD+Multi-ABI+(.so)+Compiler;RegisterNatives+%2B+JNI+Env+Encryption+%2B+C%2B%2B+FastZipModifier&quot; alt=&quot;Dex2cPlus Typing Animation&quot; /&gt;
&lt;/a&gt;

&lt;p align=&quot;center&quot;&gt;
  &lt;a href=&quot;https://github.com/iAmINCoder/Dex2cPlus&quot;&gt;
    &lt;img src=&quot;https://img.shields.io/badge/GitHub-iAmINCoder%2FDex2cPlus-181717?style=for-the-badge&amp;logo=github&amp;logoColor=white&quot; alt=&quot;GitHub Repository&quot; /&gt;
  &lt;/a&gt;
  &lt;a href=&quot;https://developer.android.com&quot;&gt;
    &lt;img src=&quot;https://img.shields.io/badge/Android-API%2021%E2%80%9336-3DDC84?style=for-the-badge&amp;logo=android&amp;logoColor=white&quot; alt=&quot;Android API 21-36&quot; /&gt;
  &lt;/a&gt;
  &lt;a href=&quot;https://isocpp.org&quot;&gt;
    &lt;img src=&quot;https://img.shields.io/badge/Engine-C%2B%2B17%20JNI-00599C?style=for-the-badge&amp;logo=cplusplus&amp;logoColor=white&quot; alt=&quot;C++17 JNI&quot; /&gt;
  &lt;/a&gt;
  &lt;a href=&quot;https://llvm.org&quot;&gt;
    &lt;img src=&quot;https://img.shields.io/badge/Toolchain-LLVM%20Clang%20%2B%20LLD-262D3A?style=for-the-badge&amp;logo=llvm&amp;logoColor=2DD4BF&quot; alt=&quot;LLVM Clang &amp; LLD&quot; /&gt;
  &lt;/a&gt;
  &lt;a href=&quot;https://www.google.com/search?q=https://t.me/INCoderDev&quot;&gt;
    &lt;img src=&quot;https://img.shields.io/badge/Architect-%40INCoderDev-26A5E4?style=for-the-badge&amp;logo=telegram&amp;logoColor=white&quot; alt=&quot;Telegram @INCoderDev&quot; /&gt;
  &lt;/a&gt;
  &lt;a href=&quot;https://t.me/INCoderX&quot;&gt;
    &lt;img src=&quot;https://img.shields.io/badge/Channel-%40INCoderX-059669?style=for-the-badge&amp;logo=telegram&amp;logoColor=white&quot; alt=&quot;Telegram Channel @INCoderX&quot; /&gt;
  &lt;/a&gt;
&lt;/p&gt;

&lt;/div&gt;

## Overview

**Dex2cPlus** is a native Android application and DEX-to-C++17 bytecode protection suite architected by **[@INCoderDev](https://www.google.com/search?q=https://t.me/INCoderDev)** ([GitHub: iAmINCoder/Dex2cPlus](https://github.com/iAmINCoder/Dex2cPlus)). It parses single-DEX and multi-DEX Android packages (`classes.dex`, `classes2.dex`, `classesN.dex`) directly on-device using **Smali / Dexlib2**, translates selected Java/Kotlin methods into obfuscated **C++17 JNI source code**, compiles stripped native shared libraries (`.so`) across up to four CPU architectures using an on-device **Android NDK + LLVM Clang/LLD** toolchain, rewrites DEX bytecode to `native` modifiers with automatic `System.loadLibrary` injection, and repackages the target APK using a zero-recompression **C++ `FastZipModifier`** engine.

&lt;div align=&quot;center&quot;&gt;
  &lt;img src=&quot;assets/pipeline_animation.svg&quot; alt=&quot;Dex2cPlus Native Compilation Pipeline&quot; width=&quot;100%&quot; /&gt;
&lt;/div&gt;

## Key Features & Capabilities

| Feature Module | Technical Implementation | Highlights |
| :--- | :--- | :--- |
| **Dual-Mode Class & DEX Tree Explorer** | `MainActivity` + `ClassAdapter` + `ShimmerFrameLayout` | Switch seamlessly between hierarchical **Package Tree** mode and multi-DEX **`.dex` File Tree** mode with real-time search (`Search...`), recursive selection counters, and synchronized shimmer skeleton loading animations. |
| **DEX-to-C++17 JNI Transpiler** | `Dex2CTranslator` | Converts Dalvik bytecode instructions (arithmetic, branching, `try`/`catch` exception handlers, field/method invocations, arrays, and object casts) into standalone C++17 JNI functions. |
| **Dynamic `RegisterNatives` Binding** | `Dex2CTranslator` (`JNI_OnLoad`) | Eliminates exported `Java_pkg_Class_method` symbol names from the `.so` dynamic symbol table by binding method pointers inside `JNI_OnLoad` via `env->RegisterNatives(...)`. |
| **JNI Environment & String Obfuscation** | `Dex2CTranslator` + `telegram_profile_dialog.cpp` | Obfuscates class descriptors, method names, and signatures at rest and resolves `jclass`, `jmethodID`, and `jfieldID` references dynamically at runtime. |
| **Selective Method Filter Engine** | `SettingsActivity` + `ProjectState` | Granular control over which method categories are translated: `Synthetic`, `Bridge`, `Static`, `Virtual`, `Private`, `Synchronized`, and `Varargs`. |
| **Automated DEX Bytecode Rewriter** | `DexRewriterEngine` | Converts translated methods to `ACC_NATIVE`, strips their Dalvik code items, injects a custom native loader class (default `Loader`), and patches `<clinit>` to load the compiled `.so` library automatically. |
| **On-Device Multi-ABI NDK Compiler** | `NdkCompiler` | Compiles generated C++17 sources directly on Android using LLVM `clang++` and `ld.lld` with parallel worker threads across `arm64-v8a`, `armeabi-v7a`, `x86`, and `x86_64`. |
| **Native C++ `FastZipModifier` Engine** | `fast_zip_modifier.cpp` + `FastZipModifier` | High-speed C++ ZIP central directory parser and in-place append/replacement engine that injects rewritten `.dex` files and `lib/<abi>/lib<name>.so` binaries without re-compressing unchanged APK entries. |
| **Glow Build Terminal & Live Console** | `BuildActivity` + `GlowConsoleTextView` | Real-time build progress tracker with macOS-style status lights, stage indicators, one-tap log copy, and instant process cancellation. |

## Architecture & Source Structure

```text
Dex2cPlus/
├── app/
│   ├── build.gradle.kts                  # Android SDK 36, NDK 29.0.14033849, CMake 4.1.2, Java 17
│   └── src/main/
│       ├── AndroidManifest.xml           # App permissions, activities & storage declarations
│       ├── cpp/
│       │   ├── CMakeLists.txt            # Native library (libdex2cplus.so) build configuration
│       │   ├── dex2c_helper.cpp          # JNI ABI detection & native runtime helpers
│       │   ├── fast_zip_modifier.cpp     # High-speed C++ ZIP/APK central directory modifier
│       │   └── telegram_profile_dialog.cpp # Multi-layer runtime byte decryptor for profile metadata
│       ├── java/com/dex2c/plus/
│       │   ├── MainActivity.java         # APK picker, dual-mode tree explorer & synchronized shimmer UI
│       │   ├── ConsoleLogger.java        # Thread-safe build console event dispatcher
│       │   ├── StorageHelper.java        # Scoped & full-storage permission + workspace directory manager
│       │   ├── engine/
│       │   │   ├── ApkDexManager.java    # Multi-DEX APK parser & class metadata extractor
│       │   │   ├── Dex2CTranslator.java  # Core Dalvik bytecode to C++17 JNI transpiler
│       │   │   ├── DexRewriterEngine.java # Dexlib2 native modifier rewriter & loader injector
│       │   │   ├── FastZipModifier.java  # JNI bridge to native C++ FastZipModifier
│       │   │   └── NdkCompiler.java      # On-device Mini-NDK installer & parallel Clang/LLD driver
│       │   ├── model/
│       │   │   ├── DexClassItem.java     # DEX class model with method/protection counters
│       │   │   └── ProjectState.java     # Persistent compiler settings, ABI targets & filter state
│       │   └── ui/
│       │       ├── BuildActivity.java    # End-to-end protection pipeline runner & live terminal
│       │       ├── ClassAdapter.java     # Flattened high-performance tree adapter for 50k+ classes
│       │       ├── FileManagerDialog.java # In-built APK & NDK archive browser
│       │       ├── GlowConsoleTextView.java # Custom glowing terminal log view
│       │       ├── SettingsActivity.java # Toolchain, ABI, method filter & theme configuration
│       │       ├── ShimmerFrameLayout.java # Hardware-accelerated specular shimmer container
│       │       ├── TelegramProfileDialog.java # Circular profile dialog with 2s shimmer loader
│       │       ├── AcknowledgementActivity.java # Open-source & architect credits screen
│       │       └── UiAnimator.java       # Seamless system bar & tactile press animations
│       └── res/                          # Adaptive Light/Dark Material 3 themes, vectors & layouts
└── assets/
    ├── header_banner.svg                 # Animated SVG hero banner
    └── pipeline_animation.svg            # Animated SVG compilation pipeline diagram
```

## Configuration & Settings Reference

| Setting Option | Default Value | Description |
| :--- | :--- | :--- |
| **Theme Preference** | `System Default` | Switch between **Light Theme**, **Dark Theme** (Graphite/Charcoal), or **System Default**. |
| **Manage Native Code Support** | `mini_ndk` | Install the Android NDK sysroot + Clang toolchain either **Online** or from a local `.zip` / `.tar.xz` archive. |
| **Parallel Build** | `Enabled` | Compiles C++ translation units concurrently across CPU cores for faster multi-ABI `.so` generation. |
| **Custom Library Name** | `native-lib` | Customizes the output shared library filename (`lib<name>.so`) loaded by the protected DEX. |
| **Custom Loader Class** | `Loader` | Specifies the injected helper class name that invokes `System.loadLibrary("<name>")`. |
| **ABI Targets** | `arm64-v8a`, `armeabi-v7a`, `x86`, `x86_64` | Select one or more target device architectures to package into the output bundle. |
| **Method Types Filter** | All `Enabled` | Toggle protection for `Synthetic`, `Bridge`, `Static`, `Virtual`, `Private`, `Synchronized`, and `Varargs` methods. |
| **RegisterNatives (`JNI_OnLoad`)** | `Enabled` | Binds native methods dynamically in `JNI_OnLoad` to hide exported JNI symbol names. |
| **JNI Env & String Encryption** | `Enabled` | Encrypts class, method, and field signatures inside the generated C++ translation unit. |
| **Rewrite DEX & Repackage APK** | `Enabled` | Rewrites protected methods to `native` and outputs a ready-to-sign protected APK inside `/storage/emulated/0/Dex2cPlus/`. |

## How to Build & Run

1. **Clone the Repository**
   ```bash
   git clone https://github.com/iAmINCoder/Dex2cPlus.git
   cd Dex2cPlus
   ```

2. **Requirements**
   - **Android Studio**: Ladybug / Meerkat or newer
   - **Android SDK**: `compileSdk = 36`, `minSdk = 21`, `targetSdk = 34`
   - **Android NDK**: `29.0.14033849` & **CMake**: `4.1.2`
   - **JDK**: Java 17

3. **Compile Debug / Release APK**
   ```bash
   ./gradlew assembleDebug
   ```

4. **On-Device Workflow**
   - Launch **Dex2cPlus** and grant storage access so protected outputs can be saved to `/storage/emulated/0/Dex2cPlus/`.
   - Open **Settings ➔ Manage Native code support** and install the `mini_ndk` toolchain (via one-tap Online Download or Local Archive Picker).
   - Tap the **APK Picker** icon in the top header to select any target `.apk` file.
   - Use the `Search...` filter bar or toggle between **Package Tree** and **`.dex` Tree** mode to select the classes or packages you want to protect.
   - Tap the floating **Build** button at the bottom-right to transpile, compile native `.so` libraries, rewrite DEX files, and generate the output archive in `/storage/emulated/0/Dex2cPlus/`.

## Credits & Official Community

| Component / Role | Attribution & Official Link |
| :--- | :--- |
| **Core Engine & Android Architect** | **[@INCoderDev](https://www.google.com/search?q=https://t.me/INCoderDev)** — [GitHub Repository (`iAmINCoder/Dex2cPlus`)](https://github.com/iAmINCoder/Dex2cPlus) |
| **Official Telegram Community** | **[@INCoderX](https://t.me/INCoderX)** — Official updates, releases, and discussion channel |
| **DEX Bytecode Parsing & Rewriting** | [Smali / Dexlib2 (`com.android.tools.smali:smali-dexlib2`)](https://github.com/google/smali) |
| **Native Compilation Toolchain** | [LLVM Clang & LLD](https://llvm.org) + [Android NDK](https://developer.android.com/ndk) |
| **UI Foundation** | [AndroidX & Material Design 3](https://m3.material.io) |
