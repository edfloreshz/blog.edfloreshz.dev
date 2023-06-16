---
title: "Functions In Rust"
tags: ["rust", "basics"]
type: "blank"
author: "Eduardo Flores"
cover: /images/articles/rust/functions/header.png
publishdate: 2020-10-12
---

In this article, we'll be discussing what functions are and when to use them in Rust.

As some of us already know, functions are "self-contained" modules of code that accomplish a specific task. Generally, functions are used to encapsulate certain pieces of repetitive code that can later be used by other functions to execute said code without having to write it all over again.

Functions should be small, this is the first and the most important rule related to functions, you should keep them as short as possible. A shorter function will do less and as a consequence, it will be more easily understood and managed. You might be wondering: "How short should my functions be?", unfortunately, there is no magic number here. In general, if you end up with a method longer than 10-15 lines of code you should take a look over it and see why it is so long. Functions should also **do one thing**, this will make it easier for you and others to manage your code and understand where a certain bug might be appearing, also, try using descriptive names.

> If you want to learn more about how to write good code, I recommend you read [Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882) by Robert C. Martin.

## Functions in Rust

Rust code uses **snake_case **as the conventional style for function and variable names. In snake_case, all letters are lowercase, and underscores are used to separate words.

```rust
fn main() {
    println!("Hello, world!");
    another_function();
}

fn another_function() {
    println!("Another function.");
}
```

The curly brackets tell the compiler where the function body begins and ends. Note that we defined `another_function` after the main function in the source code; we could have defined it before as well. Rust doesn’t care where you define your functions, only that they’re defined somewhere. This is not the case with other languages like C/C++, where you need to define functions before the function that will call them.

## Function Parameters

If you've worked with functions before, you already know what parameters are for, but for those who haven't, a parameter is simply data being sent to a function. As you may have already realized, functions are not in the same scope as the function that calls them, this means that they don't have access to the same data. In order for the function to work, we need to send them the required data.

As an example, imagine a function `add` that takes two parameters, two numbers to add.

```rust
fn add( x: u32, y: u32) -> u32 {
    x + y
}
```

Functions are declared using the `fn` keyword. Its arguments are type annotated, just like variables, and, if the function returns a value, the return type must be specified after an arrow `->`.

If you come from another language, you might be wondering where the `return` statement and the `;` are. With Rust, the final expression in the function will be used as the return value. Alternatively, the `return` statement can be used to return a value earlier from within the function, even from inside loops or if statements.

Take a look at `x + y`, this is what's called an expression, expressions evaluate to a resulting value, in this case, the sum of `x` and `y`. For instance, this function will return the resulting value of that expression.

Function definitions and variable declarations are statements; statements do not return values, therefore, you can’t assign a let statement to another variable:

```rust
let x = (let y = 6);
```

This will result in an error:

```bash
error: expected expression, found statement (`let`)
 --> src/main.rs:2:14
  |
1 |     let x = (let y = 6);
  |              ^^^
  |
  = note: variable declaration using `let` is a statement
```

## Returning Values

In Rust, the return value of the function is synonymous with the value of the final expression in the block of the body of a function. You can return early from a function by using the return keyword and specifying a value, but most functions return the last expression implicitly.

If we place a semicolon at the end of the final line containing `x + y`, changing it from an expression to a statement, we’ll get an error:

```bash
error[E0308]: mismatched types
 --> src/main.rs:7:24
  |
7 | fn add(x: u32, y: u32) -> u32 {
  |    ----                   ^^^ expected `u32 `, found `()`
  |    |
  |    implicitly returns `()` as its body has no tail or `return` expression
8 |     x + y;
  |          - help: consider removing this semicolon

error: aborting due to previous error
```

The main error message, “mismatched types,” reveals the core issue with this code. The definition of the function `add` says that it will return an `i32`, but statements don’t evaluate to a value, which is expressed by (), an empty tuple. Therefore, nothing is returned, which contradicts the function definition and results in an error. In this output, Rust provides a message to possibly help rectify this issue: it suggests removing the semicolon, which would fix the error.

## What's next?

There is a lot more to learn about functions, this is just a quick introduction, we will explore functions in more detail in a later article.

In the next article, we'll talk about [Control Flow](/articles/controlflow), it will allow us to express the way that execution components (statements, expressions, and declarations) are wired together to effect a computation.

If you enjoyed this article, consider sharing it so more people can benefit from it! Also, feel free to [@me](https://twitter.com/edfloreshz) on Twitter or send me a [message](https://t.me/edfloreshz).
