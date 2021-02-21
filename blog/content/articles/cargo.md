---
title: "Let's Talk About Cargo For Rust Projects"
layout: "article"
url: "blog/articles/cargo"
author: "Eduardo Flores"
publishdate: 2020-09-17
summary: We are now going to discuss how can we use Cargo, one of the tools we talked about that comes with Rust
---

In the last article, we talked about the basics to get started with Rust, we even wrote our first, very simple program. We are now going to discuss how can we use Cargo, one of the tools we talked about that comes with Rust.

**Cargo** is Rust's package manager, with it, you can add dependencies to your projects, for instance, let's say you need to generate random numbers, well, there's a [crate](https://crates.io/crates/rand) for that.

[crates.io](crates.io) is a website where you can explore every available crate for your projects, it gives you access to documentation, statistics, and many more things. We'll discuss more on how can we add a crate to our project later.

# Hello Cargo

In the last article, we created a file called `main.rs`, wrote the main function with some very basic functionality, and used `rustc` to compile and then ran it. Now, we are going to focus on using the `rand` crate to make a random number generator, our main focus here will be using `cargo` to make all of this easier.

To start a new project, navigate to your projects directory and type:

```
cargo new randgen
```

We'll see that there's now a new directory called `randgen` in our projects folder. When we enter, we will see a file called `Cargo.toml`, which is our project's configuration file, it looks something like this:

```toml
[package]
name = "randgen"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
edition = "2018"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

And the `src` directory, where all of our source files will live.

Let's open `src/main.rs` and see what's in there:

```rust
fn main() {
    println!("Hello, world!");
}
```

Looks familiar?

### Dependencies

We are now going to include the `rand` crate to our file:

```rust
use rand::Rng;

fn main() {
    println!("Hello, world!");
}
```

When we want to include a dependency in one of our files, we need to use the `use` keyword, followed by our crate's name and subsequent modules, in this case, the `Rng` trait, we separate them by using a `::`.

> We'll talk about traits in a future article.

### Create a random number

We haven't talked about variables yet, we'll cover the basic here and go more in-depth in a later article.

Let's make a variable to store our random number:

```rust
use rand::Rng;

fn main() {
    let random = rand::thread_rng().gen_range(1, 101);
    println!("The random number is {}!", random);
}
```

We use the `let` keyword to create new variables, followed by their name, then we use `=` to assign a value to them. In this case, we're assigning the value that `rand::thread_rng().gen_range(1, 101)` generates. Both `thread_rng()` and `gen_range()` are functions, which return a value.

`thread_rng()` returns a lazily-initialized thread-local random number generator, which then calls `gen_range()`, a function that returns a random value that is in the range that was passed to the function as a parameter, in this case, `1, 100`.

We then pass this variable to `println!` and we use a syntax we haven't seen before:

```rust
println!("The random number is {}!", random);
```

That `{}` you see inside the text we're printing is a placeholder for a value to fill in, in this case, the `random` variable. When we run this, we might encounter something like this:

```text
The random number is 12!
```

We don't know exactly what number will be displayed, given that it is a random number.

### Running the program

Try running your program, but this time use Cargo to run it.

```bashtoml
cargo run
```

Whoops! What did we miss?

You should've encountered something like this:

```bash
error[E0432]: unresolved import `rand`
 --> src/main.rs:1:5
  |
1 | use rand::Rng;
  |     ^^^^ use of undeclared crate or module `rand`

error[E0433]: failed to resolve: use of undeclared crate or module `rand`
 --> src/main.rs:4:18
  |
4 |     let random = rand::thread_rng().gen_range(1, 101);
  |                  ^^^^ use of undeclared crate or module `rand`

error: aborting due to 2 previous errors
```

Remember that `Cargo.toml` configuration file we talked about at the beginning? That file manages what dependencies are loaded into your project, so we need to specify we want the [`rand`](https://crates.io/crates/rand) crate in out project. Open it, look for `[dependencies]` and add `rand = "0.7.3"` below, the version number might change, be sure to use the one that fits your needs.

The file should look something like this now:

```toml
[package]
name = "randgen"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
edition = "2018"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
rand = "0.7.3"
```

Try running the project now and you should see something like this now:

```toml
$ cargo run
   Compiling cfg-if v0.1.10
   Compiling ppv-lite86 v0.2.9
   Compiling libc v0.2.77
   Compiling getrandom v0.1.15
   Compiling rand_core v0.5.1
   Compiling rand_chacha v0.2.2
   Compiling rand v0.7.3
   Compiling randgen v0.1.0 (/home/eduardo/Developer/Projects/randgen)
    Finished dev [unoptimized + debuginfo] target(s) in 1.92s
     Running `target/debug/randgen`
The random number is 22!

```

Congratulations! This is your second program in Rust and you made use of an external crate and Cargo.

# Cargo tips and tricks

We only used one Cargo command in this article, but there are a lot more!

`cargo` -> will list all of the available commands for you.

`cargo build` -> will build your project, this includes downloading dependencies and compiling it, it will not run it.

`cargo check` -> will check for syntax errors in your code, it will not compile nor run it. This is handy when you don't want to wait for your program to compile in order to check for errors.

`cargo init` -> will create a new cargo package in an existing directory.

`cargo install` -> can be used to install a Rust binary, such as [gitui](https://github.com/extrawurst/gitui), which is a terminal-ui for git written entirely in Rust by [Stephan Dilly](https://twitter.com/Extrawurst).

`cargo uninstall` -> will uninstall a Rust binary.

If you'd like to get a more in-depth look at Cargo you can check out the [Cargo Guide](https://doc.rust-lang.org/cargo/guide/).

# What's next?

In the next article, we'll talk about [variables and mutability](https://edfloreshz.blog/variables-and-mutability).

If you enjoyed this article, consider sharing it so more people can benefit from it! Also, feel free to [@me](https://twitter.com/edfloreshz) on Twitter or send me a [message](https://t.me/edfloreshz).
