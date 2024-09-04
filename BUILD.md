# Building Nanosaur

## Quick Start: Using build.py (Automated Build Script)

The `build.py` script offers a streamlined method to create a game executable from a fresh repository clone. This script is compatible with macOS, Windows, and Linux, provided your system meets these prerequisites:

- Python 3
- CMake
- A suitable C++ compiler

Follow these steps to build Nanosaur:

1. Clone the repository with submodules:
   ```
   git clone --recurse-submodules https://github.com/jorio/Nanosaur
   ```

2. Navigate to the project directory:
   ```
   cd Nanosaur
   ```

3. Run the build script:
   ```
   python3 build.py
   ```

4. Once the build process completes:
   - Locate the zipped Nanosaur build in the "Build" directory
   - Unpack the zip file
   - Launch the game by running the Nanosaur executable

This automated process simplifies the build workflow, allowing you to go from a fresh clone to a playable game with minimal manual intervention.

## Manual Build Instructions

If you prefer to build the game manually, follow the platform-specific instructions below.

### macOS Manual Build

1. **Prerequisites:**
   - Xcode 12 or later
   - CMake 3.16 or later (Homebrew installation recommended)

2. **Clone the repository:**
   ```
   git clone --recurse-submodules https://github.com/jorio/Nanosaur
   cd Nanosaur
   ```

3. **Set up SDL2:**
   - Download [SDL2-2.30.2.dmg](https://libsdl.org/release/SDL2-2.30.2.dmg)
   - Mount the DMG and copy `SDL2.framework` to the `extern` folder in your project directory

4. **Generate Xcode project:**
   ```
   cmake -G Xcode -S . -B build
   ```

5. **Build the game:**
   - Open `build/Nanosaur.xcodeproj` in Xcode and build from there, or
   - Use the command line:
     ```
     cmake --build build --config RelWithDebInfo
     ```

6. **Run the game:**
   The built application will be located at `build/RelWithDebInfo/Nanosaur.app`

### Windows Manual Build

1. **Prerequisites:**
   - Visual Studio 2022 with C++ toolchain
   - CMake 3.16 or later

2. **Clone the repository:**
   ```
   git clone --recurse-submodules https://github.com/jorio/Nanosaur
   cd Nanosaur
   ```

3. **Set up SDL2:**
   - Download [SDL2-devel-2.30.2-VC.zip](https://libsdl.org/release/SDL2-devel-2.30.2-VC.zip)
   - Extract and copy the `SDL2-2.30.2` folder to the `extern` directory in your project

4. **Generate Visual Studio solution:**
   ```
   cmake -G "Visual Studio 17 2022" -A x64 -S . -B build
   ```

5. **Build the game:**
   - Open `build/Nanosaur.sln` in Visual Studio and build from there, or
   - Use the command line:
     ```
     cmake --build build --config Release
     ```

6. **Run the game:**
   The built executable will be located at `build/Release/Nanosaur.exe`

### Linux Manual Build

1. **Prerequisites:**
   Install the following packages using your distribution's package manager:
   - C++20 compatible compiler
   - CMake 3.16 or later
   - SDL2 development library (e.g., `libsdl2-dev` on Ubuntu, `sdl2` on Arch, `SDL-devel` on Fedora)
   - OpenGL development libraries (e.g., `libgl1-mesa-dev` on Ubuntu)

2. **Clone the repository:**
   ```
   git clone --recurse-submodules https://github.com/jorio/Nanosaur
   cd Nanosaur
   ```

3. **Build the game:**
   ```
   cmake -S . -B build -DCMAKE_BUILD_TYPE=RelWithDebInfo
   cmake --build build
   ```
   
   Note: To enable runtime sanitizers, add `-DSANITIZE=1` to the first `cmake` command.

4. **Run the game:**
   The built executable will be located at `build/Nanosaur`

Enjoy playing Nanosaur!
