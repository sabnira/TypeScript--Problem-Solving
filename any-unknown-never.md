# `any`, `unknown`, and `never` in TypeScript

## Introduction

TypeScript has some special types that work differently from normal types like string, number, and boolean. Three important ones are `any`, `unknown`, and `never`. Understanding how they work helps us write safer code and avoid unexpected errors, especially when working with data whose type is not clear.

## How They Work

In TypeScript's type system, `unknown` and `any` can both accept values of any type, but they do not behave the same way. `unknown` is a type-safe top type. We can store any value in it, but we must check its type before using it.

```ts
let value: unknown = "Hello";

if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

Here, TypeScript allows `toUpperCase()` only after confirming that value is a string. This process is called type narrowing.

On the other hand, `any` basically turns off type checking for that value. We can access properties or call methods without checking them first.

```ts
let value: any = "Hello";
value.toFixed(); // No TypeScript error, but fails at runtime
```

This can hide bugs because TypeScript cannot warn us about incorrect operations.

`never` is different from both. It represents a value that never occurs. A function that always throws an error can have a `never` return type.

```ts
function throwError(message: string): never {
  throw new Error(message);
}
```

In the type hierarchy, `never` is the bottom type: it can be assigned to other types, but no normal value can be assigned to it. `unknown` is at the top because every value can be assigned to it.

## Conclusion

I prefer `unknown` over `any` when the type of a value is not clear because it keeps TypeScript's safety checks active. We should use `any` only when we intentionally need to skip type checking, such as during gradual migration or when dealing with an untyped library. Using the right type makes code easier to maintain and helps catch mistakes earlier.