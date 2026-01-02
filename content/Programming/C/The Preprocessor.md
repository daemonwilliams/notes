#systems
The **C Preprocessor** is a text substitution tool that processes your source code *before* the actual compilation begins. All preprocessor directives start with `#`.

---
#### 1. File Inclusion (`#include`)
Literally copy-pastes the contents of the specified file into the current file.
- `#include <stdio.h>`: Search standard system paths.
- `#include "myheader.h"`: Search the current directory first.

#### 2. Macro Substitution (`#define`)
Replaces occurrences of a token with specific text.
- **Constants:** `#define PI 3.14159`
- **Function-like Macros:**
    ```c
    #define SQUARE(x) ((x) * (x))
    ```
- **Warning:** Macros are unaware of types and syntax. Always wrap arguments in parentheses to avoid operator precedence issues.
- *Side Effects:* `SQUARE(i++)` will increment `i` twice!
#### 3. Conditional Compilation (`#ifdef`)
Compiles blocks of code only if certain conditions are met. Used heavily for:
- **Cross-platform code:** `#ifdef _WIN32 ... #endif`
- **Debugging:** `#ifdef DEBUG ... #endif`

---
#### Header Guards
To prevent a header file from being included multiple times (which causes "redefinition" errors), use **Header Guards**:

```c
#ifndef MY_HEADER_H
#define MY_HEADER_H

struct MyStruct { int x; };

#endif
```
*Modern Alternative:* `#pragma once` (Supported by most compilers).

---
