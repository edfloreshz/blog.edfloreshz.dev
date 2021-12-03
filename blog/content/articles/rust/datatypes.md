---
title: "Data Types In Rust"
tags: ["rust", "basics"]
layout: "post"
url: "articles/datatypes"
author: "Eduardo Flores"
publishdate: 2020-09-25
summary: In this article, we'll be discussing the various data types in Rust
cover: { image: images/articles/rust/datatypes/header.png, relative: false }
twittercover:
  { image: images/articles/rust/datatypes/cover.png, relative: false }
---

In this article, we'll be discussing the various data types in Rust.

Rust differs from languages like Python or JavaScript in many ways, Rust is what's known as a strongly typed language, this means that every variable must have a predefined data type bound to it at compile-time, in weakly typed languages, you don't have to explicitly define them because it makes conversions between unrelated types implicitly. Of course, this comes at a cost, while weakly typed languages have many advantages, speed isn't one of them.

> **Compile time** is the time at which the source code is converted into executable code.

Every value in Rust is of a certain _data type_, this tells Rust what kind of data is being used and how to manage it. There are two types of data in Rust, **scalar** and **compound**.

The compiler can usually infer what data type we want to use based on the value we assign to it and how we use it. In cases when many types are possible, such as when we convert text to a numeric type, we must add a type annotation:

```rust
let guess: u32 = "42".parse().expect("Not a number!");
```

Type annotations are added by using `:` followed by the data type, in this case `u32`, after the variable name. If we don’t add the type annotation here, we'll get a compiler error:

```bash
error[E0282]: type annotations needed
 --> src/main.rs:2:9
  |
2 |     let guess = "42".parse().expect("Not a number!");
  |         ^^^^^ consider giving `guess` a type
```

# Scalar Types

A **scalar** type represents a single value. Rust has four primary scalar types: integers, floating-point numbers, Booleans, and characters. You might recognize these from other languages.

## Integer Types

An integer is a number without a fractional component. Integers can be divided into two types: **signed** and **unsigned**.

A signed integer is an integer that can be both positive and negative. This is as opposed to an unsigned integer, which can only be positive. Integers are represented as bytes, one byte is equivalent to 8 bits, which is the basic unit of information in computing.

In Rust, we have the following data types:

| Length  | Signed | Unsigned |
| ------- | ------ | -------- |
| 8-bit   | `i8`   | `u8`     |
| 16-bit  | `i16`  | `u16`    |
| 32-bit  | `i32`  | `u32`    |
| 64-bit  | `i64`  | `u64`    |
| 128-bit | `i128` | `u128`   |

Each number represents the number of bits that can be allocated in that data type, for instance, when we declare a variable with `u8`, we are saying that our variable will not have negative numbers and can store up to 8 bits of information.

Each signed variant can store numbers from `-(2^(n - 1)) to 2^(n - 1) - 1` inclusive, where `n` is the number of bits that variant uses. So an i8 can store numbers from `-(2^7) to 2^7 - 1`, which equals `-128` to `127`. Unsigned variants can store numbers from `0` to `2^(n) - 1`, so a `u8` can store numbers from `0` to `2^(8) - 1`, which equals `0` to `255`.

| Length | From      | To       |
| ------ | --------- | -------- |
| i8     | `-128`    | `127`    |
| u8     | `0`       | `255`    |
| i16    | `-32,768` | `32,767` |
| u16    | `0`       | `65,535` |

You can calculate the remaining ranges using [Wolfram Alpha](https://www.wolframalpha.com/), just replace `n` in the equation with the number of bytes that the remaining data types can store.

Additionally, the `isize` and `usize` types depend on the kind of computer your program is running on: 64 bits if you’re on a 64-bit architecture and 32 bits if you’re on a 32-bit architecture.

#### Integer Literals

You can write integer literals in any of the forms shown in the next table. Note that all number literals except the byte literal allow a type suffix, such as 57u8, and \_ as a visual separator, such as 1_000.

| Number literals | Example       |
| --------------- | ------------- |
| Decimal         | `98_222`      |
| Hex             | `0xff`        |
| Octal           | `0o77`        |
| Binary          | `0b1111_0000` |
| Byte `u8 only`  | `b'A'`        |

#### Integer Overflow

Let’s say you have a variable of type `u8` that can hold values between `0` and `255`. If you try to change the variable to a value outside of that range, such as `256`, **integer overflow** will occur. An integer overflow occurs when an arithmetic operation attempts to create a numeric value that is outside of the range that can be represented with a given number of digits.

When you're debugging your app, this will cause it to `panic` and exit, but if this code is compiled as `-- release`, _two’s complement wrapping_ will occur. This means that values greater than the maximum value the type can hold “wrap around” to the minimum of the values the type can hold. In the case of a `u8`, 256 becomes 0, 257 becomes 1, and so on.

## Floating-Point Types

Rust also has two primitive types for floating-point numbers, which are numbers with decimal points, `f32` and `f64`. Here's how you declare a variable of type floating-point.

```rust
fn main() {
    let x = 2.0; // Rust can infer this is of type f64 when we use a decimal point.
    let y: f32 = 3.0; // We need to specify it as f32 because f64 is the default.
}
```

## The Boolean Type

The boolean type, as in most programming languages, has only two possible values, `true` and `false`. Booleans are one byte in size. The Boolean type in Rust is specified using `bool`.

```rust
fn main() {
    let t = true;
    let f: bool = false; // with explicit type annotation
}
```

You can also declare boolean types by using logical operators.

```rust
fn main() {
    let yes = true || true;
    let no = true && false;

    println!("{} and {}", yes, no); // true and false
}
```

## The Character Type

Rust doesn't only work with numbers, it has letters too!

```rust
fn main() {
    let c = 'z';
    let z = 'ℤ';
    let heart_eyed_cat = '😻';
}
```

Rust’s char type is the language’s most primitive alphabetic type, are four bytes in size, and represent a Unicode Scalar Value, which means it can represent a lot more than just ASCII. Accented letters; Chinese, Japanese, and Korean characters; emoji; and zero-width spaces are all valid char values in Rust.

Note that `char` literals are specified with single quotes, as opposed to `string` literals, which use double-quotes.

## Numeric Operations

Rust supports the basic mathematical operations you’d expect for all of the number types: addition, subtraction, multiplication, division, and remainder.

The following example shows how to use all of them:

```rust
fn main() {
    // addition
    let sum = 5 + 10;
    // subtraction
    let difference = 95.5 - 4.3;
    // multiplication
    let product = 4 * 30;
    // division
    let quotient = 56.7 / 32.2;
    // remainder
    let remainder = 43 % 5;
}

```

# Compound Types

Compound types can group multiple values into one type. Rust has two primitive compound types: **tuples** and **arrays**.

## The Tuple Type

A tuple is a general way of grouping together a number of values with a variety of types into one compound type. Tuples have a fixed length: once declared, they cannot grow or shrink in size.

We create a tuple by writing a comma-separated list of values inside parentheses. Each position in the tuple has a type, and the types of the different values in the tuple don’t have to be the same.

```rust
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```

To get the individual values out of a tuple, we can use pattern matching to destructure a tuple value, like this:

```rust
fn main() {
    let tup = (500, 6.4, 1);
    let (x, y, z) = tup;
    println!("The value of y is: {}", y);  // 6.4
}
```

This program first creates a tuple and binds it to the variable `tup`. It then uses a pattern with `let` to take `tup` and turn it into three separate variables, `x`, `y`, and `z`. This is called destructuring because it breaks the single tuple into three parts. Finally, the program prints the value of `y`, which is `6.4`.

In addition to destructuring through pattern matching, we can access a tuple element directly by using a period `.` followed by the index of the value we want to access. For example:

```rust
fn main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);
    let five_hundred = x.0; // 500
    let six_point_four = x.1; // 6.4
    let one = x.2; // 1
}

```

## The Array Type

Another way to have a collection of multiple values is with an array. Unlike a tuple, every element of an array must have the same type.

In Rust, the values going into an array are written as a comma-separated list inside square brackets:

```rust
fn main() {
    let a = [1, 2, 3, 4, 5];
    let months = ["January", "February", "March", "April", "May", "June", "July",
              "August", "September", "October", "November", "December"];
}
```

Arrays are useful when you want your data allocated on the **stack** rather than the **heap** (you can learn more about this [here](https://gribblelab.org/CBootCamp/7_Memory_Stack_vs_Heap.html)) or when you want to ensure you always have a fixed number of elements.

You would write an array’s type by using square brackets, and within the brackets include the type of each element, a semicolon, and then the number of elements in the array, like so:

```rust
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

Here, `i32` is the type of each element. After the semicolon, the number `5` indicates the array contains five elements.

#### Accessing Array Elements

An array is a single chunk of memory allocated on the stack. You can access elements of an array using indexing, like this:

```rust
fn main() {
    let a = [1, 2, 3, 4, 5];

    let first = a[0]; // 1
    let second = a[1]; // 2
}
```

In this example, the variable named `first` will get the value 1, because that is the value at index `[0]` in the array. The variable named `second` will get the value `2` from index `[1]` in the array.

#### Invalid Array Element Access

What happens if you try to access an element of an array that is past the end of the array? Say you change the example to the following code, which will compile but exit with an error when it runs:

```rust
fn main() {
    let a = [1, 2, 3, 4, 5];
    let index = 10;

    let element = a[index];

    println!("The value of element is: {}", element);
}
```

Running this code using cargo run produces the following result:

```bash
$ cargo run
   Compiling arrays v0.1.0 (file:///projects/arrays)
    Finished dev [unoptimized + debuginfo] target(s) in 0.31s
     Running `target/debug/arrays`
thread 'main' panicked at 'index out of bounds: the len is 5 but the index is 10', src/main.rs:5:19
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace.
```

The compilation didn’t produce any errors, but the program resulted in a runtime error and didn’t exit successfully. When you attempt to access an element using indexing, Rust will check that the index you’ve specified is less than the array length. If the index is greater than or equal to the array length, Rust will panic.

This is the first example of Rust’s safety principles in action. In many low-level languages, this kind of check is not done, and when you provide an incorrect index, invalid memory can be accessed. Rust protects you against this kind of error by immediately exiting instead of allowing the memory access and continuing.

# What's next?

In the next article, we'll talk about [functions](/articles/functions) to provide better modularity for your application.

If you enjoyed this article, consider sharing it so more people can benefit from it! Also, feel free to [@me](https://twitter.com/edfloreshz) on Twitter or send me a [message](https://t.me/edfloreshz).
