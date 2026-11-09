# B8A1: Problem Solving with TypeScript & OOP

This repository contains the complete submission for **Assignment 1 (B8A1)**, demonstrating practical implementations of core TypeScript features—including union and primitive types, optional/default parameters, readonly tuples, interfaces, type narrowing, generics, asynchronous Promises, and Object-Oriented Programming (OOP) concepts, alongside two in-depth technical blog posts.

---

## Repository Structure

```text
├── solutions.ts             # All 8 TypeScript problem solutions
├── type-vs-interface.md     # Blog Post 1: Type Aliases vs Interfaces
├── type-narrowing.md        # Blog Post 2: Type Narrowing Techniques
└── README.md                # Assignment overview and blog links
```

---

## Solutions Overview (`solutions.ts`)

All required coding solutions are cleanly implemented in [`solutions.ts`](./solutions.ts) with explicit parameter and return types, zero use of `any`, and strict type safety:

1. **`multiplyValue`**: Accepts a number and an optional multiplier (defaulting to `2`), properly handling `0`.
2. **`processInput`**: Uses runtime type narrowing (`typeof`) on `string | number | boolean` union input to format strings (trimmed and lowercased), multiply numbers by 10, and return `"Active"` or `"Inactive"` for booleans.
3. **`formatCoordinate`**: Accepts a `readonly` tuple `[latitude, longitude, locationName]` (`[number, number, string]`) and returns the exact formatted coordinate string without mutating the input.
4. **`concatenateArrays`**: A generic function `<T>` utilizing rest parameters (`...arrays: T[][]`) to flatten multiple arrays of identical types into a single ordered array.
5. **`getPopularCourses`**: Defines the `Course` interface and filters courses by publication status and minimum student count without mutating the original array.
6. **`pluckValues`**: Employs generics with a `keyof` constraint (`<T, K extends keyof T>`) to extract values of a specified property key into an array of type `T[K][]`.
7. **`Employee` & `Manager`**: Demonstrates OOP encapsulation and inheritance using `protected` and `private` access modifiers, a `super()` constructor call, and formatted details/role methods.
8. **`validateAgeAsync`**: An async function returning `Promise<string>` that resolves with `"Access Granted"` after a 1-second delay for ages $\ge 18$, and rejects immediately with an `Error` instance for ages $< 18$.

---

## Technical Blog Posts

Both blog posts satisfy the 150–300 words requirement, featuring clear structure (Title, Introduction, Body with Code Examples, and Conclusion):

1. **[Type Aliases vs Interfaces in TypeScript](./type-vs-interface.md)**
   * Explores the fundamental differences between `type` and `interface`, including declaration merging, union/primitive type support, and architectural recommendations for when to use each.
2. **[A Practical Guide to Type Narrowing in TypeScript](./type-narrowing.md)**
   * Explains how TypeScript narrows broad types into specific types during runtime, with practical code examples demonstrating the `typeof`, `instanceof`, and `in` operator type guards.

---

## Verification & Compilation

Compile the TypeScript solutions using the TypeScript compiler:

```bash
npx tsc
```
