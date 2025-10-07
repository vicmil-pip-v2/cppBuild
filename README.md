# cppBuild

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-windows%20%7C%20linux-lightgrey)
![Status](https://img.shields.io/badge/status-active-success)
![Made with ❤️ for C++](https://img.shields.io/badge/made%20with-%E2%9D%A4-red)

**cppBuild** is a Python-based build system for C++ projects. It allows you to define, merge, and execute build setups without requiring external tools like CMake. The system is designed to be simple, flexible, and compatible with multi-library projects.

---

## 📘 Description

`cppBuild` wraps the build process of C++ projects in Python. You can define compiler paths, source files, optimization flags, include paths, libraries, and output files in a structured manner. Multiple build setups can be merged for handling complex dependencies.

---

## 🧩 Distributed via **vicmil-pip**

This library is officially distributed through **[vicmil-pip](https://github.com/vicmil-pip-v2/vicmil-pip)** — a cross-platform C++ package manager inspired by Python’s `pip`.

To install **cppBuild**:

```bash
python3 vicmil-pip.py install cppBuild
```

After installation, include it in your project like so:

```python
from vicmil_pip.lib.cppBuild import *
```

That’s it — no manual setup or global installs required!

---

## 🚀 Features

- Define build parameters in a **structured order** for safe compilation.
- Merge multiple build setups to combine libraries seamlessly.
- Cross-platform support (Windows, Linux, Browser via Emscripten).
- Python-driven, no external dependencies needed.
- Automatically handles include paths, library paths, macros, and compiler flags.
- Convert files into `.cpp`/`.hpp` pairs for embedding large assets in C++ projects.
- Optional browser compilation with Emscripten, including asynchronous execution support.

---

## 🧩 Build Parameters

The `BuildSetup` class organizes compiler arguments in the following order:

| Parameter                         | Type      | Description                                                                |
| --------------------------------- | --------- | -------------------------------------------------------------------------- |
| `n1_compiler_path`                | str       | Compiler executable path (default `g++` or `em++` if `browser_flag=True`). |
| `n2_cpp_files`                    | List[str] | Paths to C++ source files.                                                 |
| `n3_optimization_level`           | List[str] | Optimization flags, including C++ standard (e.g., `-std=c++11`).           |
| `n4_macros`                       | List[str] | Preprocessor macros (`-D` automatically added).                            |
| `n5_additional_compiler_settings` | List[str] | Extra compiler flags.                                                      |
| `n6_include_paths`                | List[str] | Include directories (`-I` automatically added).                            |
| `n7_library_paths`                | List[str] | Library directories (`-L` automatically added).                            |
| `n8_library_files`                | List[str] | Library names (`-l` automatically added).                                  |
| `n9_output_file`                  | str       | Output executable or HTML file path.                                       |
| `browser_flag`                    | bool      | If true, uses Emscripten for browser builds.                               |

---

## 🛠 Usage

### 1. Create a build setup

```python
from vicmil_pip.lib.cppBuild import BuildSetup

build = BuildSetup(browser=False)
build.add_default_parameters(
    cpp_file_paths=["src/main.cpp", "src/utils.cpp"],
    output_dir="bin",
    O2_optimization=True
)
```

---

### 2. Merge other build setups

```python
build.add_vicmil_pip_package("someLibrary")
```

---

### 3. Build the project

```python
build.build()
```

This automatically constructs the compiler command in the correct order and executes it.

---

### 4. Run the compiled program

```python
build.run()
# or
build.build_and_run()
```

For browser builds, this will serve the `.html` file locally.

---

### 5. Convert files into C++ source/header

```python
from vicmil_pip.lib.cppBuild  import convert_file_to_cpp

convert_file_to_cpp("assets/image.png", "src/generated")
```

This creates `.cpp` and `.hpp` files that store the file data as a byte array, safely accessible from C++.

---

## 📦 Dependencies

- Python 3.x
- Standard Python libraries (`os`, `sys`, `importlib`, `pathlib`, `platform`)
- Optional: **vicmil-pip** packages for library-specific build setups

---

## 🧰 Notes

- Works cross-platform (Windows/Linux) and supports browser builds using Emscripten.
- Automatically handles missing directories, DLL copying, and default compiler paths.
- Ideal for rapid prototyping and integrating multiple C++ libraries in a single build system.

---

## ⚖️ License

Distributed under the **MIT License**. See `LICENSE` for details.

---

**Author:** [02vicmil](https://github.com/02vicmil)
**Version:** 1.0.0

```

```
