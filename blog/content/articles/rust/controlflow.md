---
title: "Control Flow In Rust"
tags: ["rust", "basics"]
layout: "post"
url: "articles/controlflow/"
author: "Eduardo Flores"
publishdate: 2020-10-20
summary: In this article, we'll be discussing what control flow is and how we can use it in Rust
cover: { image: images/articles/rust/controlflow/header.png, relative: false }
twittercover:
  { image: images/articles/rust/controlflow/cover.png, relative: false }
---

In this article, we'll be discussing what control flow is and how we can use it in Rust.

Deciding whether or not to run some code depending on a condition and deciding to run some code repeatedly while a condition is true are basic building blocks in most programming languages.

The most common constructs that let you control the flow of execution of Rust code are `if` expressions and `loops`.

# `if` Expressions

`if` expressions are one of the most useful features of programming languages, it allows us to provide a condition and execute code if that condition is met.

> An `if` expression allows you to branch your code depending on conditions. You provide a condition and then state, “If this condition is met, run this block of code. If the condition is not met, do not run this block of code.” - The Rust Book

All if expressions start with the keyword `if`, which is followed by a condition.

```rust
fn main() {
    let number = 3;
    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```

After the condition, there should be curly brackets `{}` that will contain the code to execute in case the given condition is met.

Optionally, we can also include an `else` expression, which we chose to do here, to give the program an alternative block of code to execute should the condition evaluate to false. If you don’t provide an `else` expression and the condition is false, the program will just skip the if block and move on to the next bit of code.

It’s also worth noting that the condition in this code must be a `bool`. If the condition isn’t a `bool`, we’ll get an error.

In order to write a valid condition, you can use `==`, `!=`, `>`, `<`, `>=`, `<=`. It's also valid to evaluate the result of an operation.

```rust
if 1 + 1 == 2 {
    println!("1 + 1 is 2");
}
```

### Handling Multiple Conditions with `else if`

You can have multiple conditions by combining if and else in an else if expression.

```rust
fn main() {
    let number = 6;

    if number % 4 == 0 {
        println!("number is divisible by 4");
    } else if number % 3 == 0 {
        println!("number is divisible by 3");
    } else if number % 2 == 0 {
        println!("number is divisible by 2");
    } else {
        println!("number is not divisible by 4, 3, or 2");
    }
}
```

Using too many else if expressions can clutter your code, so if you have more than one, you might want to refactor your code. In a later article, we'll talk about a powerful Rust branching construct called `match` for these cases.

### Using `if` in a `let` Statement

Because if is an expression, we can use it on the right side of a let statement:

```rust
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };

    println!("The value of number is: {}", number);
}
```

This is useful when we don't want to create a variable and then assign the value inside the conditional blocks, we can do it all in one single expression.

# Repetition with Loops

It’s often useful to execute a block of code more than once. For this task, Rust provides several loops. A loop runs through the code inside the loop body to the end and then starts immediately back at the beginning.

Rust has three kinds of loops: `loop`, `while`, and `for`. Let’s try each one.

### Repeating Code with `loop`

The `loop` keyword tells Rust to execute a block of code over and over again forever or until you explicitly tell it to stop. This is equivalent to using `while true` in C.

```rust
fn main() {
    loop {
        println!("again!");
    }
}
```

When we run this program, we’ll see `again!` printed over and over continuously until we stop the program manually. Fortunately, Rust provides another, more reliable way to break out of a loop. You can place the `break` keyword within the loop to tell the program when to stop executing the loop. This can be placed inside a conditional block.

```rust

fn main() {
    let mut number = 3;
    loop {
        if number == 5 {
            break
        } else {
            number += 1;
        }
    }
}
```

Once `number` reaches the value 5, the break keyword will break out of the loop.

### Returning Values from Loops

One of the uses of a `loop` is to retry an operation you know might fail, such as checking whether a thread has completed its job. However, you might need to pass the result of that operation to the rest of your code. To do this, you can add the value you want to be returned after the break expression you use to stop the loop; that value will be returned out of the loop so you can use it.

```rust
fn main() {
    let mut counter = 0;
    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2;
        }
    };

    println!("The result is {}", result);
}
```

Before the loop, we declare a variable named `counter` and initialize it to 0. Then we declare a variable named `result` to hold the value returned from the `loop`. On every iteration of the `loop`, we add 1 to the `counter` variable, and then check whether the `counter` is equal to 10. When it is, we use the `break` keyword with the value `counter * 2`. After the `loop`, we use a semicolon to end the statement that assigns the value to `result`. Finally, we print the value in `result`, which in this case is 20.

### Conditional Loops with while

It’s often useful for a program to evaluate a condition within a `loop`. While the condition is true, the `loop` runs. When the condition ceases to be true, the program calls `break`, stopping the loop. This loop type could also be implemented using a combination of `loop`, `if`, `else`, and `break`. However, this pattern is so common that Rust has a built-in language construct for it, called a `while` loop.

```rust
fn main() {
    let mut number = 3;
    while number != 0 {
        println!("{}!", number);

        number -= 1;
    }
    println!("LIFTOFF!!!");
}
```

This construct eliminates a lot of nesting that would be necessary if you used `loop`, `if`, `else`, and `break`, and it’s clearer. While a condition holds true, the code runs; otherwise, it exits the loop.

### Looping Through a Collection with for

You could use the while construct to loop over the elements of a collection, such as an array.

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];
    let mut index = 0;
    while index < 5 {
        println!("the value is: {}", a[index]);
        index += 1;
    }
}
```

Here, the code counts up through the elements in the array. It starts at index 0, and then loops until it reaches the final index in the array (that is, when index < 5 is no longer true). Running this code will print every element in the array.

But this approach is error-prone; we could cause the program to panic if the index length is incorrect. It’s also slow because the compiler adds runtime code to perform the conditional check on every element on every iteration through the loop.

As a more concise alternative, you can use a for loop and execute some code for each item in a collection.

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];

    for element in a.iter() {
        println!("the value is: {}", element);
    }
}
```

We’ve now increased the safety of the code and eliminated the chance of bugs that might result from going beyond the end of the array or not going far enough and missing some items.

For example, if you changed the definition of the `a` array to have four elements but forgot to update the condition to `while index < 4`, the code would panic. Using the `for` loop, you wouldn’t need to remember to change any other code if you changed the number of values in the array.

### Summary

The safety and conciseness of for loops make them the most commonly used loop construct in Rust.

Even in situations in which you want to run some code a certain number of times, as in a countdown, most Rustaceans would use a `for` loop. The way to do that would be to use a `Range`, which is a type provided by the standard library that generates all numbers in sequence starting from one number and ending before another number.

Here’s what the countdown would look like using a `for` loop and another method we’ve not yet talked about, `rev`, to reverse the range.

```rust
fn main() {
    for number in (1..4).rev() {
        println!("{}!", number);
    }
    println!("LIFTOFF!!!");
}
```

# What's next?

This was just a quick introduction to control flow, we will explore more about this in a later article.

In the next article, we'll talk about [Understanding Ownership](https://blog.edfloreshz.dev/articles/understanding-ownership-in-rust). Rust is a very unique programming language and ownership is one of the reasons why.

If you enjoyed this article, consider sharing it so more people can benefit from it! Also, feel free to [@me](https://twitter.com/edfloreshz) on Twitter or send me a message.
