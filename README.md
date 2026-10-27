# z80-string-utils

A lightweight collection of string utility functions written in Z80 assembly, focused on simplicity, speed, and memory efficiency.

Developed and tested using [ASM Editor](https://asm-editor.specy.app), an online Z80 assembler and emulator.

## Functions

| Function  | Description                                                 |
| --------- | ----------------------------------------------------------- |
| `_strlen` | Returns the length of a null-terminated string.             |
| `_strcpy` | Copies a null-terminated string to another memory location. |
| `_streq`  | Checks whether two strings are identical.                   |
| `_strcat` | Appends one string to another.                              |
| `_strchr` | Finds the first occurrence of a character in a string.      |

## Usage

In ASM Editor, add `functions.z80` to your project and include it by filename.

```asm
        .org 0x8000

start:
        ld hl, message
        call _strlen            ; A = 5
        halt


        .org 0x9000

message: .asciz "Hello"

#include "functions.z80"
```

The memory addresses `0x8000` and `0x9000` are used for testing in ASM Editor's emulator and should not be assumed safe on other Z80 systems, including the TI-84 Plus.

Each function includes documentation describing its inputs, outputs, and clobbered registers.

## Limitations

- Strings must be null-terminated (`0x00`).
- `_strlen` and `_strchr` return 8-bit values (0–255).

## Testing

The `tests/` directory contains five tests for each function.

To run a test in ASM Editor, add the test file and `functions.z80` to the same project and execute the test.

At the final "halt", register `A` contains the number of failed tests.

- `A = 0`: All tests passed.
- `A > 0`: Number of failed tests.
