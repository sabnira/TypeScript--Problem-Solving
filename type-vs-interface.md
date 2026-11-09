# Type Aliases vs. Interfaces in TypeScript

## Introduction

In TypeScript, both `type` and `interface` are used to describe the structure of data. At first, they may look almost the same because both can define object properties. However, there are some differences between them. In this blog, I will explain how they work and when to use each one.

## Main Differences

An interface is mainly used to describe the shape of an object. It can also extend another interface, so we can reuse properties without writing them again.

```ts
interface User {
  name: string;
  age: number;
}

interface Admin extends User {
  role: string;
}
```

Here, Admin gets the name and age properties from User and adds a new role property.

A type alias can also describe an object, but it can do more than that. For example, we can use it for union types, tuples, and primitive types.

```ts
type Status = "success" | "error" | "loading";

type Coordinate = [number, number];
```

Another difference is that interfaces support declaration merging. This means we can declare the same interface more than once, and TypeScript combines the properties. Type aliases do not support this.

## Conclusion

I would use interface when I am describing an object and may need to extend it later. I would use type when I need unions, tuples, or other type combinations. Both are useful, so the choice depends on what I am trying to build.
