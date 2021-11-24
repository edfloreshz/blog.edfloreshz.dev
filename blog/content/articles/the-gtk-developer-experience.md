---
title: The GTK Developer Experience
tags: [rust, gtk, development]
layout: post
url: articles/the-gtk-developer-experience
author: Eduardo Flores
publishdate: 2021-11-24T00:00:00.000Z
summary: "In this article, we'll be discussing what the experience of getting into GTK is like."
cover:
  {
    image: images/articles/the-gtk-developer-experience/header.png,
    relative: false,
  }
twittercover:
  {
    image: images/articles/the-gtk-developer-experience/cover.png,
    relative: false,
  }
---

## What is GTK?

**GTK** is a cross-platform graphical user interface toolkit, which is used to build graphical applications, primarily for the desktop.

Offers a complete set of UI elements, GTK is suitable for projects ranging from small one-off tools to complete application suites.

GTK stands for GIMP Tool Kit, as it was originally created to implement the user interface for [GIMP](https://www.gimp.org/), a free image manipulation tool. It is also used in the [GNOME](https://www.gnome.org/) project, which is one of the most popular desktop environments.

[GTK](https://www.gtk.org/) can be used with many languages, including _C, JavaScript, Perl, Python, Vala and Rust_, thanks to language bindings or wrappers.

## Why I chose to learn GTK with Rust?

As you can see, I had quite a few choices regarding the language I would use for my projects, and I decided to go with [**Rust**](https://www.rust-lang.org/).

Besides all of the advantages of using Rust, which I will not cover in this article, one of the main reasons I chose it is that I already have a good understanding of the language.

I was also motivated by the fact that [**System76**](https://system76.com) is using Rust for their new **COSMIC** desktop environment.

![cosmic](https://64.media.tumblr.com/d9910d084e7f02234b790767a3d152a2/29eaab1056480fec-6b/s1280x1920/65926a981c3e080bca38bacdb9311f586eaf53ad.png)

## The experience of getting into GTK.

Ever since I found out about UI toolkits, GTK was the one that caught my eye and for a very long time I wanted to get more in-depth with this toolkit, so this has been my experience…

> Just a heads up, this is not me ranting, I’ll try to be constructive and propose solutions to all the problems exposed in this blog post.

## What is the problem?

Trying to learn GTK has been a confusing experience, as someone who has never had a encounter with GTK code before, my first instinct was to find some code examples and start from there. I did find some, but I had to really look for them, I haven’t been able to find relevant tutorials, as most of them stay on the basics, a single window with a button.

This is something that should be taken into consideration, GTK is huge and if we want to attract more developers, having code examples, in many languages, would be a good place to start.

The gtk-demo app would be key to this objective, right now only C code examples are being presented, having other languages there might help.

## The API Reference

The API Reference is very informative, there’s lots and lots of information about the toolkit there, but I feel like code examples would be helpful if included.

There’s a LOT of new concepts one has to learn in order to understand why GTK behaves the way it does.

To everyone in my position, take a look at [this](https://discourse.gnome.org/t/useful-documentation-for-gtk/29)

## Using gtk-rs

I’m using the [gtk-rs](https://gtk-rs.org) project and Julian Hofer is writing a book titled [GUI development with Rust and GTK 4](https://gtk-rs.org/gtk4-rs/stable/latest/book/) which has been helpful and is still in early stages.

![gtk-rs-logo](https://raw.githubusercontent.com/edfloreshz/blog/main/blog/static/images/articles/the-gtk-developer-experience/gtk-rs-logo.png)

Using Rust is another important factor as to why I haven’t been able to find much information, both GTK4 and Rust bindings are fairly new to the GTK family.

## Considering Relm 4

Relm 4 is an idiomatic GUI library inspired by Elm and based on gtk4-rs.

Relm4 is a new version of relm that's built from scratch and is compatible with GTK4 and libadwaita.
