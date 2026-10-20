# TinyC Compiler

A compiler front end for **TinyC**, a small subset of C, written in Java.
Built in the *Programming 2* course at Saarland University (summer 2024).

## What it does

- **Parsing to an AST:** the course-provided parser calls my `ASTFactory`
  implementation, which builds a typed abstract syntax tree of expressions,
  statements, types, function definitions and global declarations.
- **Semantic analysis:** checks that variables and functions are declared before
  use, rejects duplicate declarations and `void` variables, tracks nested scopes (global, function, block) and reports errors through
  the diagnostics module.
- **MIPS code generation:** started, not finished. `CodeGenerator` emits globals
  and function labels; control flow and local variables are not implemented yet.

## Project structure

```
src/tinycc/
  implementation/   my code: AST classes, ASTFactory, semantic analysis, code generation
    expression/     binary, unary, call and primary expressions
    statement/      block, if, while, return, declaration, ... statements
    type/           int/char/void base types, pointers, function types
  parser/           lexer and parser (course framework)
  diagnostic/       error reporting (course framework)
  driver/           command-line entry point (course framework)
  mipsasmgen/       MIPS assembly builder (course framework)
  logic/            formula classes for verification (course framework)
```

## Running

The driver depends on the course's Z3 and MARS libraries, which are not included
here. With `com.microsoft.z3.jar` in `libs/` and the sources compiled to `bin/`:

```bash
scripts/tinycc <file.c>
```

## Tech

Java, compiler construction (parsing, ASTs, scopes and declaration checks), MIPS assembly
