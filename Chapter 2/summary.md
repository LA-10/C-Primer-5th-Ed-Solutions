# Chapter 2: Variables and Basic Types — Comprehensive Summary

---

## Overview

Types are fundamental in C++ programming. They define the meaning of data, the storage requirements, and the operations that can be performed on them. This chapter explores:

- Primitive built-in types
- Variables and their initialization
- Compound types (references, pointers)
- The `const` qualifier
- Techniques for dealing with complex types
- Defining custom data structures (classes)

---

## 2.1 Primitive Built-in Types

### Categories of Arithmetic Types

- **Integral types:** Include boolean (`bool`), character types (`char`, `wchar_t`, `char16_t`, `char32_t`), and various integer types (`short`, `int`, `long`, `long long`).
- **Floating-point types:** Include `float`, `double`, and `long double`.

### Size Guarantees and Representations

- The C++ standard guarantees minimum sizes (e.g., `char` is at least 8 bits, `int` at least 16 bits).
- Actual sizes may be larger depending on the machine.
- Floating-point types usually correspond to 32-bit (`float`), 64-bit (`double`), or 96/128-bit (`long double`) representations.
- Boolean type `bool` represents `true` and `false`.

### Character Types and Unicode Support

- `char` is the basic character type.
- `wchar_t`, `char16_t`, and `char32_t` support extended character sets and Unicode.

### Type Conversions

- Automatic conversions occur between arithmetic types.
- Assigning floating-point to integral types truncates the fractional part.
- Assigning out-of-range values to unsigned types results in modulo arithmetic.
- Assigning out-of-range values to signed types leads to undefined behavior.
- Mixing signed and unsigned types can cause unexpected results.

### Advice on Choosing Types

- Use `unsigned` types when values cannot be negative.
- Use `int` for integer arithmetic; `long long` if larger sizes are needed.
- Use `double` for floating-point computations; `float` often lacks precision.
- Avoid arithmetic with `char` or `bool` directly.

---

## 2.2 Variables

### Variable Definitions and Initialization

- Variables have types that determine their size, layout, and operations.
- A variable definition specifies the type and can include an initializer.
- **Initialization** happens at creation and differs from assignment.
- Four forms of initialization exist, including **list initialization** (using `{}`), which prevents narrowing conversions.
- Variables without explicit initializers may have undefined values, especially local built-in types.

### Scope and Identifiers

- **Scope** defines where a name is valid.
- Most scopes are delimited by `{}` (blocks).
- Variables can shadow outer-scope variables (nested scopes).
- Identifiers consist of letters, digits, and underscores, and are case-sensitive.
- Some names are reserved and cannot be used.

### Separate Compilation and Declarations

- C++ supports separate compilation with **declarations** (introducing a name) and **definitions** (allocating storage).
- `extern` keyword declares a variable without defining it.
- Variables must be defined exactly once but can be declared multiple times.

---

## 2.3 Compound Types

### References

- A **reference** is an alias to an existing object.
- Must be initialized at definition.
- Cannot be rebound to refer to another object.
- Syntax: `int &ref = var;`

### Pointers

- A **pointer** holds the address of an object.
- Can be dereferenced to access the object.
- Pointers can be to pointers (multiple indirection levels).
- Must be initialized; uninitialized pointers cause undefined behavior.
- `nullptr` represents a null pointer.
- Mixing pointers and references differs in usage and capabilities.

### Compound Type Declarations

- Base type followed by declarators, each modifying the base type.
- Pointer or reference modifiers (`*`, `&`) apply to each declarator individually.
- Example: `int *p1, p2;` — `p1` is a pointer to int; `p2` is int.

---

## 2.4 The `const` Qualifier

### Basics

- Defines objects whose values cannot change after initialization.
- Must be initialized at definition.
- Used to prevent accidental modification.

### References to const

- Can bind to const or non-const objects, or to literals.
- Cannot modify the underlying object through a `const` reference.

### Pointers and const

- **Pointer to const:** pointer points to a constant object (cannot modify the object).
- **Const pointer:** pointer itself is constant (cannot change the address it holds).
- Both can be combined.

### Top-level vs. Low-level `const`

- **Top-level const:** applies to the object itself (e.g., const pointer).
- **Low-level const:** applies to the pointed-to or referenced type.

### `constexpr` and Constant Expressions

- `constexpr` variables are constant expressions evaluated at compile time.
- Functions can be declared `constexpr` to be usable in constant expressions.
- Helps with compile-time computation and optimization.

---

## 2.5 Dealing with Types

### Type Aliases

- Use `typedef` or `using` to create synonyms for types, improving readability.
- Aliases can simplify complex type declarations.

### The `auto` Type Specifier

- Compiler deduces the type from the initializer.
- Must have an initializer.
- Ignores top-level `const` but preserves low-level `const`.
- Can deduce pointers, references, and compound types correctly.

### The `decltype` Type Specifier

- Deduces the type of an expression without evaluating it.
- Preserves top-level `const` and references.
- Useful to declare variables with the same type as expressions without initializing them.

---

## 2.6 Defining Our Own Data Structures

### Classes and Structs

- Classes define new types grouping data and operations.
- `struct` keyword creates a class with all members public by default.
- Example: `Sales_data` struct groups ISBN, units sold, and revenue.
- Data members can have in-class initializers.
- Classes enable encapsulation and abstraction.

### Using Classes

- Objects of class types store their own copies of data members.
- Operations on objects can be user-defined (input/output, addition).
- Classes are usually defined in header files to enable reuse and separate compilation.
- Header guards prevent multiple inclusions of the same header.

### Header Guards

- Use `#ifndef`, `#define`, and `#endif` preprocessor directives to prevent multiple inclusions.
- Example:

```cpp
#ifndef SALES_DATA_H
#define SALES_DATA_H

#include <string>

struct Sales_data {
    std::string bookNo;
    unsigned units_sold = 0;
    double revenue = 0.0;
};

#endif
```

---

## Key Concepts and Terminology

- **Static typing:** Types are checked at compile time.
- **Initialization vs. assignment:** Initialization sets the initial value; assignment changes the value afterward.
- **Undefined behavior:** Using uninitialized variables or invalid conversions can cause unpredictable results.
- **Scope and lifetime:** Variables exist within scopes; names are visible only within their scope.
- **Type modifiers:** `const`, pointers, references modify base types.
- **Constant expressions:** Expressions evaluable at compile time (`constexpr`).

---
