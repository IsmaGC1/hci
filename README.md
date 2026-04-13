# Human-Computer Interfaces

## Environment setting-up for raylib on Windows and macOS (OS X)

This guide describes simple setups to compile and run raylib programs:

1. **Windows (Terminal): MSYS2 UCRT64**
2. **Windows (IDE): Visual Studio Code (recommended) or Visual Studio**
3. **macOS / OS X (Terminal): Homebrew + pkg-config**

---

## 1) Windows (Terminal): MSYS2 UCRT64

### Why this option?
- Unix-like terminal
- GCC toolchain
- Easy package install with `pacman`
- raylib package available

### Install & Setup
Open **MSYS2 UCRT64** terminal:

```bash
pacman -Syu
pacman -Syu
pacman -S --needed mingw-w64-ucrt-x86_64-toolchain
pacman -S mingw-w64-ucrt-x86_64-raylib
```

### Compile & Run
```bash
g++ main.cpp -o app.exe -lraylib -lopengl32 -lgdi32 -lwinmm
./app.exe
```

---

# 🟦 2) Windows (IDE): Visual Studio Code (RECOMMENDED)

### Why this option?
- Very friendly for students
- Integrated editor + terminal
- Easy debugging
- Works with MSYS2 toolchain

---

## Step 1. Install tools

Install:

- **Visual Studio Code**
- Extension: **C/C++ (Microsoft)**

---

## Step 2. Use MSYS2 compiler inside VS Code

Open VS Code terminal and select:

👉 **MSYS2 UCRT64 terminal**

Or configure VS Code to use:

```bash
C:\msys64\ucrt64\bin
```

in PATH.

---

## Step 3. Create project folder

```
raylib-project/
├── main.cpp
```

---

## Step 4. Example program

```cpp
#include "raylib.h"

int main()
{
    InitWindow(800, 600, "raylib VSCode");
    SetTargetFPS(60);

    while (!WindowShouldClose())
    {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText("Hello from VS Code!", 250, 280, 20, BLACK);
        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

---

## Step 5. Compile inside VS Code terminal

```bash
g++ main.cpp -o app.exe -lraylib -lopengl32 -lgdi32 -lwinmm
```

Run:

```bash
./app.exe
```

---

## Optional: Build Task (recommended for class)

Create `.vscode/tasks.json`:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "build raylib",
      "type": "shell",
      "command": "g++",
      "args": [
        "main.cpp",
        "-o",
        "app.exe",
        "-lraylib",
        "-lopengl32",
        "-lgdi32",
        "-lwinmm"
      ],
      "group": "build"
    }
  ]
}
```

Now students can press:

👉 **Ctrl + Shift + B**

---

# 🟦 Alternative IDE: Visual Studio (MSVC)

### Option (more advanced)
Use **vcpkg**:

```bash
vcpkg install raylib
```

Then integrate:

```bash
vcpkg integrate install
```

Create a Visual Studio project and link raylib.

👉 This option is more complex; recommended only for advanced students.

---

# 🟦 3) macOS / OS X (Terminal)

### Install tools

```bash
xcode-select --install
brew install raylib
```

Verify:

```bash
pkg-config --modversion raylib
```

---

## Compile & Run

```bash
clang++ -std=c++17 main.cpp -o app $(pkg-config --cflags --libs raylib)
./app
```

---

# 🟦 4) Troubleshooting

## Windows
- Ensure MSYS2 UCRT64 terminal is used
- Ensure raylib installed with pacman

## macOS
- Use pkg-config
- Ensure raylib installed via brew

---

# 🟦 Final recommendation

Use an GenAI such as ChatGPT, Gemini or deepseek for troubleshooting. 
