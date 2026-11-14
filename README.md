Dex2cPlus

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=34&duration=2500&pause=900&color=38BDF8&center=true&vCenter=true&width=650&height=65&lines=Dex2cPlus;DEX+%E2%86%92+C%2B%2B17+%E2%86%92+JNI;Native+Android+Protection" alt="Dex2cPlus Animated Title" />
</p><p align="center">
  <strong>Advanced Native Android Protection Suite</strong>
  <br/>
  Transform Dalvik bytecode into optimized C++17 JNI libraries.
</p><p align="center">
  <a href="https://github.com/iAmINCoder/Dex2cPlus">
    <img src="https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github" />
  </a>
  <img src="https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=cplusplus" />
  <img src="https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" />
  <img src="https://img.shields.io/badge/License-Apache%202.0-blue?style=for-the-badge" />
</p>---

Overview

Dex2cPlus is an on-device DEX-to-C++17 transpiler and JNI protection framework designed to transform selected Android bytecode methods into native shared libraries.

It combines DEX analysis, native code generation, runtime JNI registration, multi-ABI compilation, and optimized APK modification into a unified workflow.

Architecture

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=0:0F172A,100:0369A1&height=3" width="100%" />
</p>flowchart TD
    A["Android APK"] --> B["DEX Parser"]
    B --> C["Class & Method Selection"]
    C --> D["C++17 JNI Translator"]
    D --> E["DEX Native Patcher"]
    D --> F["LLVM Clang / LLD"]
    F --> G["Native Shared Libraries"]
    E --> H["APK Rebuilder"]
    G --> H
    H --> I["Protected APK"]
    
    style A fill:#172554,stroke:#38BDF8,color:#fff
    style D fill:#164E63,stroke:#22D3EE,color:#fff
    style F fill:#312E81,stroke:#818CF8,color:#fff
    style I fill:#14532D,stroke:#4ADE80,color:#fff

Core Capabilities

<table>
<tr>
<td width="50%" valign="top">DEX Analysis

- Multi-DEX parsing
- Package and class explorer
- Recursive class selection
- Method filtering
- Search and navigation

</td>
<td width="50%" valign="top">Native Translation

- Dalvik to C++17
- JNI function generation
- Control-flow translation
- Exception handling
- Field and method access

</td>
</tr>
<tr>
<td width="50%" valign="top">Native Protection

- Dynamic RegisterNatives
- JNI metadata encryption
- Native DEX rewriting
- Loader injection
- Configurable native libraries

</td>
<td width="50%" valign="top">Build Engine

- LLVM Clang and LLD
- Parallel compilation
- Multi-ABI support
- On-device Mini NDK
- Zero-recompression ZIP engine

</td>
</tr>
</table>Supported Architectures

<p align="center">
  <img src="https://img.shields.io/badge/ARM64-arm64--v8a-2563EB?style=flat-square" />
  <img src="https://img.shields.io/badge/ARM32-armeabi--v7a-2563EB?style=flat-square" />
  <img src="https://img.shields.io/badge/x86-x86-0891B2?style=flat-square" />
  <img src="https://img.shields.io/badge/x64-x86__64-0891B2?style=flat-square" />
</p>Technology Stack

<p align="center">
  <img src="https://skillicons.dev/icons?i=java,cpp,androidstudio,gradle,cmake,llvm,github" />
</p>- Java 17
- C++17
- Android SDK 36
- Android NDK 29.0.14033849
- CMake 4.1.2
- LLVM Clang and LLD
- Smali and Dexlib2
- Material Design 3

Build From Source

git clone https://github.com/iAmINCoder/Dex2cPlus.git

cd Dex2cPlus

./gradlew assembleDebug

Workflow

<p align="center">
  <img src="https://img.shields.io/badge/01-Select%20APK-0F172A?style=for-the-badge" />
  <img src="https://img.shields.io/badge/02-Analyze%20DEX-164E63?style=for-the-badge" />
  <img src="https://img.shields.io/badge/03-Select%20Methods-1E3A8A?style=for-the-badge" />
  <img src="https://img.shields.io/badge/04-Compile%20Native-312E81?style=for-the-badge" />
  <img src="https://img.shields.io/badge/05-Protected%20APK-14532D?style=for-the-badge" />
</p>1. Install the application and Mini NDK toolchain.
2. Select the target APK.
3. Browse packages, DEX files, classes, and methods.
4. Configure ABI and protection settings.
5. Start native compilation.
6. Export the protected APK.

Output: "/storage/emulated/0/Dex2cPlus/"

Developer

<p align="center">
  <a href="https://github.com/iAmINCoder">
    <img src="https://img.shields.io/badge/Developer-INCoderDev-0F172A?style=for-the-badge&logo=github" />
  </a>
  <a href="https://t.me/INCoderDev">
    <img src="https://img.shields.io/badge/Telegram-Developer-0088CC?style=for-the-badge&logo=telegram" />
  </a>
  <a href="https://t.me/INCoderX">
    <img src="https://img.shields.io/badge/Telegram-Official%20Channel-0088CC?style=for-the-badge&logo=telegram" />
  </a>
</p>---

<p align="center">
  <strong>Dex2cPlus</strong>
  <br/>
  Native Code. Advanced Protection. Android.
  <br/><br/>
  <sub>Licensed under Apache License 2.0</sub>
</p>
