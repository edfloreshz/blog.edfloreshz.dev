---
title: How to get started with Rust?
tags: [rust, basics]
layout: post
url: articles/getstarted
author: Eduardo Flores
publishdate: 2020-09-16T00:00:00.000Z
summary: This is the first in a series of articles to help developers understand Rust better
cover: { image: images/articles/rust/getstarted/header.png, relative: false }
twittercover:
  { image: images/articles/rust/getstarted/cover.png, relative: false }
---

This is the first in a series of articles to help developers understand **Rust** better, I will be covering most of what you can find in [The Rust Book](https://doc.rust-lang.org/book/), in a more synthesized and concise way. I will start with the basics and build my way up to more complex topics.

#### Disclaimer

This course is intended for people who have a basic understanding of programming languages, preferably those who have written code before, this doesn't mean you can't follow along if you have no experience, just that it will be harder to understand some concepts.

Don't get discouraged if you fail to understand the concepts presented in these articles, I'd like to encourage you to ask questions, if you need assistance you can send me a [message](https://t.me/edfloreshz).

# Try Rust

If you're not comfortable installing Rust, you can [try](https://play.rust-lang.org/) Rust in the browser!

# Installing Rust

If you use Windows, you can download the installer [here](https://www.rust-lang.org/tools/install).

Install Rust by pasting this in your terminal if you're on a UNIX based system

    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

You will be presented with the following

```
Welcome to Rust!

This will download and install the official compiler for the Rust
programming language, and its package manager, Cargo.

Rustup metadata and toolchains will be installed into the Rustup
home directory, located at:

  /home/username/.rustup

This can be modified with the RUSTUP_HOME environment variable.

The Cargo home directory located at:

  /home/username/.cargo

This can be modified with the CARGO_HOME environment variable.

The cargo, rustc, rustup, and other commands will be added to
Cargo's bin directory, located at:

  /home/username/.cargo/bin

This path will then be added to your PATH environment variable by
modifying the profile files located at:

  /home/username/.profile
  /home/username/.zprofile
  /home/username/.bash_profile

You can uninstall at any time with rustup self uninstall and
these changes will be reverted.

Current installation options:


   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable (default)
               profile: default
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation

```

Type your desired method of installation and let the installer do its thing. Once it's done, open a new instance of your terminal and type `rustc`, you should see something like this

    Usage: rustc [OPTIONS] INPUT

    Options:
        -h, --help          Display this message
            --cfg SPEC      Configure the compilation environment
        -L [KIND=]PATH      Add a directory to the library search path. [...]

# What just happened?

You just installed Rust, the installer doesn't only install the compiler, it comes with a set of tools that will help you out in your journey as a [Rustacean](https://www.rustaceans.org/), I'll explain what they all do.

- **rustc** -> This is the Rust compiler, it takes the code you've written and turns it into machine code, making it understandable by your machine and therefore, executable.
- **rustup** -> This tool manages Rust, it can update and remove the tools or personalize your preferences.
- **cargo** -> Cargo is Rust's package manager, it manages dependencies for projects and can help you create new projects from scratch.
- **clippy** -> Clippy is a collection of lints to catch common mistakes and improve your code. Linters are static code analysis tools used to flag various kinds of programming errors.
- **rust-docs** -> Is a tool used to generate documentation for your code, this saves you a lot of time.
- **rust-std** -> This is the Rust Standard Library, a collection of crates you have available when writing your programs. Every Rust program is called a `crate`.
- **rustfmt** -> A tool for formatting Rust code according to style guidelines. This one is pretty cool.

# Managing Rust

There are various things **rustup ** can do for you, such as update `rustup update` and uninstall Rust `rustup self uninstall`. We will discuss more this tool in a future article.

# Write Your First Program

Let's get coding! Start by making a directory for your files.

```bash
mkdir ~/developer
cd ~/developer
mkdir hello_world
cd hello_world
```

Inside that directory, create a file by either `touch main.rs` and opening it or using your preferred text editor.

```bash
vim main.rs
nano main.rs
emacs main.rs
```

And write the following:

    fn main() {
        println!("Hello, world");
    }

`fn` is the keyword for defining new functions and `main` is the name for that function, also the entry point for our program. `println!` is a macro, not a function, we will learn more about macros in a future article but for now, know that `println!` will print "Hello, world" to the terminal.

# Compiling And Executing

It's time to run our program, save your file and exit your text editor, we will use `rustc` to make a binary of our file.

```bash
rustc main.rs
```

You will notice a new file with the name `main` was created, this is our binary file, to run it type:

```bash
./main
```

You should see `Hello, world` on your screen.

Congratulations! You've successfully written, compiled, and ran your first Rust program.

# Conclusion

Rust's main objective is to create a language that empowers everyone
to build reliable and efficient software, in the next articles, we will learn how to make use of Rust's best features, such as `cargo`, you can check the next [article](/articles/cargo).

If you enjoyed this article, consider sharing it so more people can benefit from it! Also, feel free to [@me](https://twitter.com/edfloreshz) on Twitter.
