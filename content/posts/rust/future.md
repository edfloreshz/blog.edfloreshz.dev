---
title: "Should we trust Rust with the future of systems programming?"
tags: ["rust", "industry"]
author: "Eduardo Flores"
cover: /images/articles/career/future/header.png
date: 2020-08-30
description: "Should we trust Rust with the future of systems programming?"
---

That's a pretty daring question considering Rust has been around for a fairly short amount of time and in that time has become the most loved language for 5 years in a row, according to the Stack Overflow [Developer Surveys](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-languages-loved).

It is very clear that developers love working with Rust, many big companies have been adopting it to fix many of the memory issues C and C++ have caused by taking advantage of Rust's memory safety capabilities. Microsoft recently started rewriting [core components](https://msrc-blog.microsoft.com/2019/11/07/using-rust-in-windows/) of Windows in Rust and the folks in charge of Linux have been talking about integrating Rust to the [kernel](https://lore.kernel.org/lkml/CAKwvOdmuYc8rW_H4aQG4DsJzho=F+djd68fp7mzmBp3-wY--Uw@mail.gmail.com/T/). That's a big step for Rust.

But the question remains... should we trust Rust with the future of systems programming?

## Rust is still a young language

As much as it costs to admit, Rust is still a young language compared to C, which has been around for over 48 years and still is the preferred language for **systems programming**, every major operating system in the world is written in C/C++, as well as their drivers, utilities and built-in software.

But is Rust up to the challenge? Many developers have been rewriting software written in C with Rust, demonstrating that it is not only capable of competing with it but also of generating faster, more reliable software by taking advantage of Rust's modern features.

Here's a small [list](https://zaiste.net/posts/shell-commands-rust/) of projects to check out:

1.  [bat](https://zaiste.net/posts/shell-commands-rust/#bat) -> is a `cat` clone with syntax highlighting.
2.  [exa](https://zaiste.net/posts/shell-commands-rust/#exa) -> is a modern replacement for `ls`.
3.  [starship](https://zaiste.net/posts/shell-commands-rust/#starship) -> is a minimal, blazing-fast, and infinitely customizable prompt for any shell.
4.  [ripgrep](https://zaiste.net/posts/shell-commands-rust/#ripgrep) -> is an extremely fast alternative to `grep`

## Operating systems written in Rust

While having programs rewritten in Rust is pretty cool, being able to write low-level components is a must-have for a language that intends to become #1 for systems programming, things such as the kernel and drivers. There are no immediate plans to rewrite current operating systems in Rust, but there is a project created by [Jeremy Soller](https://twitter.com/jeremy_soller), System76 Principal Engineer called [RedoxOS](https://www.redox-os.org/).

> Redox is a Unix-like Operating System written in Rust, aiming to bring the innovations of Rust to a modern microkernel and full set of applications.

Redox aims to demonstrate Rust's systems programming capabilities to a full extent, having written not only the kernel in Rust but also every piece of software that it ships with it. One of those is [relibc](https://gitlab.redox-os.org/redox-os/relibc/-/blob/master/README.md), a portable POSIX C standard library compatible with Redox and Linux. Redox isn't currently going to replace your existing OS, but it's a fun thing to try.

Rust still has a long way to go before it can compete with a language like C, but the future is looking very promising.

## Rust is still missing some features

While Rust has come a long way but it still lacks many of the features that C/C++ programmers take for granted, just to name a few:

**Compile-time code/type generation and verification** -> Rust does have a procedural macro system that can be used to accomplish these things but it's not remotely the same.

**Static Analysis** -> There may be more tools available for C++ but the quality of the static analysis built right into Rust's type system blows all of them away, no tool can reliably prevent dangling references or data races in C++. As far as only using safe Rust, static analysis is in a way better shape than C++ because it has nothing as powerful as the borrow checker.

**Sanitizers** -> Due to the type system, safe Rust code has much less need for sanitizers, when it comes to unsafe code, C++ has the advantage as it has more tools available.

There's also safe transmutation (safely cast "plain old data" types to and from raw bytes), safe support for C style unions, and fallible allocation (fail gracefully from allocation failure, rather than panic) as stated by Microsoft.

## Conclusion

As many missing features Rust has, its safe to say that, in time, Rust may become the language of choice for systems programming. Rust has an amazing community of developers that work hard every day to bring new features to the language, especially now that Microsoft supports Rust into becoming a better and more useful language.

> We at Microsoft will be able to help in these endeavors to shape the future of the language to improve its usefulness [...].

If you enjoyed this article, consider sharing it so more people can benefit from it! Also, feel free to [@me](https://twitter.com/edfloreshz) on Twitter.
