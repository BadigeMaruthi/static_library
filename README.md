
# 🔗 Static Linking 

## 📌 Overview

Static linking combines required library code with an application during linking.

This project contains:

* `sum()` → Addition
* `sub()` → Subtraction
* `libcal.a` → Static library
* `a.out` → Statically linked executable
* `b.out` → Dynamically linked executable

## 📂 Project Structure

```text
static/
├── calc.h
├── main.c
├── sum.c
├── sub.c
├── sum.o
├── sub.o
├── libcal.a
├── a.out
└── b.out

---
🧩 Complete Workflow
        sum.c                 sub.c
          │                     │
       gcc -c                gcc -c
          ↓                     ↓
        sum.o                 sub.o
          │                     │
          └─────────┬───────────┘
                    ↓
                 ar -rcs
                    ↓
                libcal.a
                    │
                    +
                  main.c
                    │
              gcc -static
                    ↓
                  a.out
                    ↓
                 ./a.out
                    ↓
          Addition = 15
          Subtraction = 5
# ⚖️ a.out vs b.out

| Feature             | `a.out`                       | `b.out`                        |
| ------------------- | ----------------------------- | ------------------------------ |
| Command             | `gcc -static main.c libcal.a` | `gcc main.c libcal.a -o b.out` |
| `libcal.a`          | Used                          | Used                           |
| Application library | Static                        | Static                         |
| System libraries    | Static                        | Dynamic                        |
| `ldd`               | Not a dynamic executable      | Shows dependencies             |
| `file`              | Statically linked             | Dynamically linked             |
| `.so` dependency    | Normally none                 | Yes                            |
| Output              | Same                          | Same                           |


Key Difference
-----------------------------------------------------------
a.out
 ↓
gcc -static
 ↓
Statically linked
 ↓
ldd → not a dynamic executable

b.out
 ↓
gcc without -static
 ↓
Dynamically linked
 ↓
ldd → shows shared libraries

# 🌍 Applications

Static linking can be useful for:

* Embedded Linux systems
* Standalone utilities
* Recovery/rescue environments
* Controlled deployment environments
* Low-level system utilities
* Specialized system software

# 📚 Command Full Forms

| Command/Option | Meaning                   |
| -------------- | ------------------------- |
| `gcc`          | GNU Compiler Collection   |
| `cc`           | C Compiler command        |
| `ar`           | Archiver                  |
| `ldd`          | List Dynamic Dependencies |
| `-c`           | Compile only              |
| `-o`           | Specify output file       |
| `-static`      | Static linking            |
| `-r`           | Replace / Insert          |
| `-s`           | Create symbol index       |
| `-v`           | Verbose                   |
| `-t`           | Table of contents         |
| `.c`           | C source file             |
| `.o`           | Object file               |
| `.a`           | Static library            |
| `.so`          | Shared object library     |


# 🏁 Project Outcome
Through this project, I practiced:

* C compilation
* Object file generation
* Static library creation
* `ar` utility
* Symbol indexing
* Static linking
* GCC `-static`
* `ldd` analysis
* `file` command
* `a.out` vs `b.out`
* Static vs dynamic linking
* Linux build workflow
