---
title: "Variables And Mutability In Rust"
tags: ["rust", "basics"]
layout: "post"
url: "articles/varmut"
author: "Eduardo Flores"
publishdate: 2020-09-18
summary: We are now going to go further and start talking about variables and mutability.
---

![Header](46GVcAL8q.png)

In the last article, we talked about how to use Cargo for Rust projects and highlighted some of its most common commands. We are now going to go further and start talking about variables and mutability.

One of Rust's main features is that variables are immutable by default, which means that values cannot change once set. This might seem odd at first, mainly because we sometimes need to change values in order to make our program work, but fear not, you can still make them mutable!

I will try to solve most of the questions you may have about this, let's dive right in!

# Variables

By definition, a variable is a value that can change, if you've been taught programming before or learned by yourself, this might sound familiar.

Rust takes a different approach when it comes to variables, instead of assuming that values will change throughout the lifespan of the program, it assumes that they won't and lets you, the programmer, decide which values will change. This lets you write your code in a way that takes advantage of the safety guarantees Rust offers.

When a variable is immutable, once a value is bound to a name, you cannot change that value. Let's see an example:

```rust
fn main() {
    let x = 5;
    println!("The value is: {}", x);
    x = 6;
    println!("The value is: {}", x);
}
```

Save and run the program using `cargo run`.You should receive an error message:

```bash
$ cargo run
   Compiling variables v0.1.0 (file:///projects/variables)
error[E0384]: cannot assign twice to immutable variable `x`
 --> src/main.rs:4:5
  |
2 |     let x = 5;
  |         -
  |         |
  |         first assignment to `x`
  |         help: make this binding mutable: `mut x`
3 |     println!("The value of x is: {}", x);
4 |     x = 6;
  |     ^^^^^ cannot assign twice to immutable variable

error: aborting due to previous error

For more information about this error, try `rustc --explain E0384`.
error: could not compile `variables`.

To learn more, run the command again with --verbose.
```

Look closely for `error[E0384]: cannot assign twice to immutable variable 'x'`, this might've already given you a clue of what's going on, but I'll go through the error message and explain what's going on in detail.

What this error is basically telling us is that we tried to change an immutable variable and since this is not allowed the compiler will yell at us, it might appear like a simple thing to complain about, but the Rust compiler is very strict and for good reason, the error messages only mean your program isn’t safely doing what you want it to do yet.

The Rust compiler not only checks for errors, but it also tries to give you suggestions on how to solve them, check for lines like this:

```
help: make this binding mutable: 'mut x'
```

Also, look for error codes in your compiler output, it might give you a better clue of what's going on. For example, `error[E0384]` is something you can look up and get help with, try either using `rustc --explain E0384` or find the error code in the [Rust Compiler Error Index](https://doc.rust-lang.org/error-index.html).

Okay! Let's fix our program, taking all of the previous suggestions into account, you might've realized by now that we are missing a keyword in our variable definition, `mut`, this keyword will make our variables **mutable**:

```rust
fn main() {
    let mut x = 5;
    println!("The value of x is: {}", x);
    x = 6;
    println!("The value of x is: {}", x);
}
```

Therefore, you are now allowed to reassign the value for our `x` variable.

# Differences between variables and constants

By now, if you have used constants before you might've thought

> "Immutable variables are basically constants then?"

Well, not exactly, first, you aren’t allowed to use mut with constants, they aren't just immutable by default, they are immutable forever.

You declare constants with the `const` keyword and you must always annotate the data type, like so:

```rust
const MAX_POINTS: u32 = 100_000;
// Rust’s naming convention for constants is to use all uppercase with underscores between words, and underscores can be inserted in numeric literals to improve readability
```

Constants can be declared in any scope, including the global scope, which makes them useful for values that many parts of code need to know about.

# Shadowing

There is a concept in Rust that most of you might be unfamiliar with, it's called **shadowing**, it allows you to declare a new variable with the same name as a previous variable. This is useful in cases where you want to take a previous value of a variable and assign it to itself with some modification, here's an example:

```rust
fn main() {
    let x = 5;
    let x = x + 1;
    let x = x * 2;

    println!("The value of x is: {}", x);
}

```

As you can see, this program first binds `x` to a value of `5`. Then it shadows `x` by repeating `let x =`, taking the original value, and adding `1` so the value of `x` is then `6`. Then, the third let statement also shadows `x`, multiplying the previous value by `2` to give `x` a final value of `12`. When we run this program, it will output the following:

```bash
$ cargo run
   Compiling variables v0.1.0 (file:///projects/variables)
    Finished dev [unoptimized + debuginfo] target(s) in 0.31s
     Running `target/debug/variables`
The value of x is: 12
```

Shadowing is different from marking a variable as `mut` because we’ll get a compile-time error if we accidentally try to reassign to this variable without using the `let` keyword. By using `let`, we can perform a few transformations on a value but have the variable be **immutable** after those transformations have been completed. By using shadowing, we are also able to reuse the same name as the previous variable.

# What's next?

In the next article, we'll talk about [data types](/articles/datatypes).

If you enjoyed this article, consider sharing it so more people can benefit from it! Also, feel free to [@me](https://twitter.com/edfloreshz) on Twitter or send me a [message](https://t.me/edfloreshz).
