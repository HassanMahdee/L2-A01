# A Practical Guide to Type Narrowing in TypeScript

## Introduction
TypeScript frequently encounters values typed with broad unions, such as `string | number` or custom union objects. **Type Narrowing** is the process where TypeScript analyzes runtime control flow checks and refines a broad type into a more specific, predictable type within conditional branches.

## Practical Narrowing Techniques

### 1. The `typeof` Guard
The `typeof` operator inspects primitive values at runtime (`"string"`, `"number"`, `"boolean"`, `"symbol"`, `"undefined"`, `"object"`):

```typescript
function formatInput(input: string | number): string {
  if (typeof input === "string") {
    return input.trim().toLowerCase(); // Narrowed to string
  }
  return input.toFixed(2); // Narrowed to number
}
```

### 2. The `instanceof` Guard
For object instances created from classes or constructors, `instanceof` verifies prototype chains:

```typescript
function getTimestamp(value: Date | string): number {
  if (value instanceof Date) {
    return value.getTime(); // Narrowed to Date
  }
  return new Date(value).getTime(); // Narrowed to string
}
```

### 3. The `in` Operator Guard
When discriminating between distinct object types that share no class constructor, the `in` operator checks for the existence of unique property keys:

```typescript
interface Admin {
  id: number;
  permissions: string[];
}

interface Member {
  id: number;
  joinDate: string;
}

function processUser(user: Admin | Member) {
  if ("permissions" in user) {
    console.log(user.permissions.length); // Narrowed to Admin
  } else {
    console.log(user.joinDate); // Narrowed to Member
  }
}
```

## Conclusion
Type narrowing bridges the gap between static type checking and dynamic JavaScript execution. Leveraging `typeof`, `instanceof`, and the `in` operator produces clean, defensive, and bug-free code.

