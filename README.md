# 📘 C++ Documentation with Doxygen and Class Diagrams

This project uses **Doxygen** to generate C++ documentation and **Graphviz** to render class and collaboration diagrams.

---

## 🛠 Requirements

- [Doxygen](https://www.doxygen.nl/download.html)
- [Graphviz](https://graphviz.org/download/)

---

## ✅ Installation

### Windows

1. Download and install **Doxygen**.
2. Download and install **Graphviz**.
   - Make sure `dot.exe` is in your system's `PATH`.
   - Default path: `C:\Program Files\Graphviz\bin`

---

## 📝 Configuration (Doxyfile)

Save the following configuration as a file named `Doxyfile` in your project root:

```ini
INPUT = ./src ./include
FILE_PATTERNS = *.cpp *.h *.c *.hpp
RECURSIVE = YES

EXTRACT_ALL = YES
EXTRACT_PRIVATE = YES
EXTRACT_STATIC = YES

HAVE_DOT = YES
DOT_PATH = C:\Program Files\Graphviz\bin

CALL_GRAPH = YES
CALLER_GRAPH = YES
INLINE_INFO = YES
SHOW_USED_FILES = YES

GENERATE_HTML = YES
GENERATE_LATEX = NO

DOT_GRAPH_MAX_NODES  = 50
UML_LOOK             = YES
CLASS_GRAPH          = YES
COLLABORATION_GRAPH  = YES
CALL_GRAPH           = YES
CALLER_GRAPH         = YES
INCLUDE_GRAPH        = YES
INCLUDED_BY_GRAPH    = YES
