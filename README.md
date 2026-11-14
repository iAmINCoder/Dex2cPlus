Dex2cPlus

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=24&pause=1000&color=00BFFF&center=true&vCenter=true&width=600&lines=Dex2cPlus;DEX+to+C%2B%2B17+JNI+Protection;Native+Android+Protection+Suite" alt="Dex2cPlus" />
</p><p align="center">
  <a href="https://github.com/iAmINCoder/Dex2cPlus">GitHub Repository</a> |
  <a href="https://t.me/INCoderDev">Developer</a> |
  <a href="https://t.me/INCoderX">Telegram Channel</a>
</p>Dex2cPlus is an on-device Android DEX-to-C++17 JNI transpiler and native protection suite. It converts selected Dalvik bytecode methods into native C++17 functions, compiles them into shared libraries, patches DEX files, and rebuilds the APK.

Features

- DEX and Multi-DEX APK parsing.
- Dalvik bytecode to C++17 JNI translation.
- Dynamic JNI "RegisterNatives" support.
- Runtime encryption of JNI metadata.
- Multi-ABI compilation.
- On-device LLVM Clang and LLD toolchain.
- Native DEX rewriting and Loader injection.
- Zero-recompression APK modification.
- Live build console and progress tracking.
- Material 3 Light and Dark themes.
- Configurable method filters and build settings.

Supported Architectures

- arm64-v8a
- armeabi-v7a
- x86
- x86_64

Requirements

- Android SDK 36
- Android NDK 29.0.14033849
- CMake 4.1.2
- JDK 17

Build

git clone https://github.com/iAmINCoder/Dex2cPlus.git
cd Dex2cPlus
./gradlew assembleDebug

Usage

1. Install and open Dex2cPlus.
2. Install the Mini NDK toolchain from Settings.
3. Select your target APK.
4. Browse and select classes or methods.
5. Configure protection settings.
6. Start the build process.
7. Find the protected APK in "/storage/emulated/0/Dex2cPlus/".

Developer

INCoderDev

GitHub: https://github.com/iAmINCoder/Dex2cPlus

Telegram: https://t.me/INCoderDev

Channel: https://t.me/INCoderX

License

Apache License 2.0
