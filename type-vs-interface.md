# Understanding Type Aliases vs Interfaces in TypeScript

## Introduction
TypeScript provides two primary mechanisms to define custom data shapes: `type` aliases and `interface`. While they frequently seem interchangeable in everyday development, each serves distinct architectural purposes within the type system.

## Key Differences and Capabilities
An `interface` is primarily designed to define the contracts of object shapes and classes. One unique feature of interfaces is **declaration merging**. If you define the same interface twice, TypeScript automatically merges their declarations into a single definition:

```typescript
interface User {
  id: number;
}
interface User {
  name: string; // Merged with id
}
```

In contrast, a `type` alias cannot be reopened or merged. However, `type` is far more versatile because it can represent primitive types, union types, intersection types, and tuples directly:

```typescript
type Status = "pending" | "approved" | "rejected";
type Coordinate = readonly [number, number];
```

Interfaces support inheritance using the `extends` keyword, whereas types compose shapes via intersection (`&`).

```typescript
interface Admin extends User {
  role: string;
}

type AdminType = User & { role: string };
```

## When to Choose Which
Choose `interface` when authoring public libraries, object-oriented models, or domain entities where declaration merging and inheritance are desirable. Choose `type` aliases when working with unions, tuples, function signatures, mapped types, or complex conditional type transformations.

## Conclusion
Both `type` and `interface` are fundamental building blocks in TypeScript. Prefer `interface` for modeling object structures and class implementations, and rely on `type` when you need expressive flexibility and union compositions.

