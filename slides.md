---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Typescript Generics
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# Typescript

Creating Types from Types

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Creating Types from Types

"Creating Types from Types" in TypeScript means using existing types to create new types. This can make your code more organized and reusable.
The simplest form of this idea is Generics.

## What is Generics?

Generics in typescript allow you to create reusable, flexible components, such as functions, classes, and interfaces, that work with various data types. You can think of generics as placeholders for types that you can specify when you use these components.

### Basic Idea of Generics

1. **Placeholder for Types**: Generics let you define a component without specifying exact types. Instead, you use placeholders (like T, U, etc.) that will be replaced with actual types when you use the component.

2. **Reusable Code**: By using generics, you can write functions or classes that work with any data type, making your code more reusable and flexible.

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/features/slide-scope-style
-->

<style>
h1{
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

h2{

  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

h3{
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---

## Example:

Let's say you want to create a function that returns the first element of an array. Without generics, you'd have to write a specific function for each type of array:

```ts
function getFirstNumber(arr: number[]): number {
  return arr[0];
}

function getFirstString(arr: string[]): string {
  return arr[0];
}
```

With generics, you can write a single function that works for any type of array:

```ts
function getFirst<T>(arr: T[]): T {
  return arr[0];
}
```

In this example, T is a placeholder for any type. When you call getFirst, TypeScript replaces T with the type of elements in the array:

```ts
let num = getFirst([1, 2, 3]); // num is of type number
let str = getFirst(["a", "b", "c"]); // str is of type string
```

<style>
 h2{
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

## How Generics Work

1. **Definition**: You define a generic type by placing it inside angle brackets `(<T>)` next to the function name, class name, or interface name.

```ts
function getFirst<T>

class Box<T>

interface Pair<T>
```

2. **Usage**: When you call the function or create an instance of the class, you specify the actual type to replace the generic placeholder.

```ts
let firstNumber = getFirst<number>([1, 2, 3]); // `T` is replaced by `number`
console.log(firstNumber); // Output: 1

let firstString = getFirst<string>(["a", "b", "c"]); // `T` is replaced by `string`
console.log(firstString); // Output: 'a'
```

<style>
h2{
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

## More Examples:

**Generic Classes**

```ts
class Box<T> {
  contents: T;

  constructor(contents: T) {
    this.contents = contents;
  }

  getContents(): T {
    return this.contents;
  }
}

let numberBox = new Box<number>(123);
let stringBox = new Box<string>("Hello");
```

**Generic Interfaces**

```ts
interface Pair<T, U> {
  first: T;
  second: U;
}
```

<style>
 h2{
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

```ts
let pair: Pair<number, string> = { first: 1, second: "one" };
```

## Benefits of Generics

1. **Type Safety**: Generics help catch type errors at compile time, ensuring that your code is more robust and less error-prone.

2. **Flexibility**: You can create more versatile and reusable components that work with various data types without rewriting code.

3. **Readability**: Using generics makes your code more readable and easier to understand, as it clearly shows the intention of handling different data types.

<style>
 h2{
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

## When not to use Generics.

While generics are a powerful feature in TypeScript, there are situations where they might not be the best choice. Here are some scenarios when not to use generics:

1. **Simplicity**: If your function or class is straightforward and works with a single, specific type, using generics might add unnecessary complexity.

2. **Fixed Types**: When you know that your code will only ever work with one type, using generics can be overkill.

3. **Overuse Leading to Complexity**: Overusing generics can make the code harder to read and understand, especially for new developers or those unfamiliar with TypeScript.

4. **Library or Framework Constraints**: Some libraries or frameworks might not fully support TypeScript generics, leading to integration issues or increased complexity when trying to make the two work together.

<style>
 h2{
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

## Conclusion.

In summary, use generics when they make your code more flexible, reusable, and type-safe. Avoid them when they add unnecessary complexity or when dealing with specific types that don’t benefit from being generic. The key is to strike a balance between flexibility and simplicity to maintain clean and readable code.

## Thanks!

<style>
h2{
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>
