# CPP

日本語版: [README.ja.md](README.ja.md)

This repository is the top-level collection for the 42 C++ Piscine modules `00` through `09`. Each module is kept as a Git submodule and contains several small C++98 exercises with its own README, Makefiles, source files, and headers.

The exercises cover the progression from basic C++ syntax and classes to inheritance, polymorphism, exceptions, templates, STL containers, parsing, and sorting.

## Modules

| Module | Topics | README |
| --- | --- | --- |
| `00` | Basic syntax, standard I/O, classes, static members | [00/README.md](00/README.md) |
| `01` | Memory allocation, references, pointers, file I/O | [01/README.md](01/README.md) |
| `02` | Orthodox Canonical Form, fixed-point numbers, operator overloads | [02/README.md](02/README.md) |
| `03` | Inheritance and multiple inheritance | [03/README.md](03/README.md) |
| `04` | Polymorphism, abstract classes, deep copies, interfaces | [04/README.md](04/README.md) |
| `05` | Exceptions, validation rules, forms, factories | [05/README.md](05/README.md) |
| `06` | C++ casts, scalar conversion, serialization, runtime type identification | [06/README.md](06/README.md) |
| `07` | Function templates, iteration templates, templated arrays | [07/README.md](07/README.md) |
| `08` | Templated containers, iterators, algorithms, stack adaptation | [08/README.md](08/README.md) |
| `09` | STL containers, file parsing, RPN evaluation, merge-insertion sort | [09/README.md](09/README.md) |

## Prerequisites

- A C++ compiler available as `c++`
- `make`
- `git` with submodule support
- A Unix-like shell

The exercise Makefiles compile with:

```sh
c++ -Wall -Wextra -Werror -pedantic -std=c++98
```

## Installation

Clone this repository with its module submodules:

```sh
git clone --recurse-submodules <repository-url>
cd CPP
```

If you already cloned the repository without submodules, initialize them with:

```sh
git submodule update --init --recursive
```

The submodule remotes are listed in [.gitmodules](.gitmodules).

## Build

There is no top-level Makefile. Build each exercise from the repository root with `make -C`:

```sh
make -C 00/ex00
make -C 01/ex04
make -C 09/ex02
```

Each exercise Makefile supports the usual targets:

```sh
make
make clean
make fclean
make re
```

Run those commands inside an exercise directory, or pass the directory with `make -C`.

## Usage

Each exercise builds its own executable. See the module README for exact commands and arguments. Examples:

```sh
./00/ex00/megaphone "hello world"
```

```sh
cd 01/ex04
./file_replace filename s1 s2
```

```sh
cd 09/ex01
./RPN "8 9 * 9 - 9 - 9 - 4 - 1 +"
```

Some exercises expect to be run from their own directory because they read local files or create local output files.

## Testing

There is no repository-wide test runner. Use each exercise's `main.cpp` and Makefile as the local check:

```sh
make -C 00/ex00 re
make -C 06/ex00 re
make -C 09/ex02 re
```

## Project Structure

```text
.
├── 00/ ... 09/      # C++ Piscine modules, stored as Git submodules
├── .gitmodules      # Submodule paths and remote URLs
├── README.md        # English top-level guide
└── README.ja.md     # Japanese top-level guide
```

Inside each module, exercises are organized as `ex00`, `ex01`, and so on. Most exercises contain a `Makefile`, `src/` implementation files, and `include/` headers.

## Notes

- This root repository is an index for the ten module repositories.
- Build and runtime details live in each module README.
- Generated object files and executables can be removed with `make clean` or `make fclean` in the corresponding exercise directory.
