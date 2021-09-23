---
layout: post
title:  "mdBook"
date:   2021-09-22 21:59:57 -0400
---

# Get Latest Version of Rust

Make sure you have the latest version of Rust and Cargo installed. 

You can check your current version of Rust by running `rustc --version`.
Yyou can update your version of Rust by running `rustup update`.

# Command Line Tool

## Install mdBook 

You can uninstall mdBook by running `cargo install mdbook`.
Run `mdbook help` in your terminal to verify that it works. 

## Initialize mdBook

Initialize mdbook by running `mdbook init`.
`--theme` argument might be used to specify a custom theme.
`path/to/book` argument can be used to specify a target directory.

Upon successful initializing of the book, the following files will be set up for you:

book-test/
├── book 
└── src 
    ├── chapter_1.md
    └── SUMMARY.md

`src` is were you write your book in markdown. 
`book` is where your book is rendered. 
`SUMMARY.md` is the skeleton of your book.


## Render mdBook 

Render your book by running `mdbook build`.
`--open` `(-o)` argument opens the rendered book in your default web browser after building it.
`--dest-dir` `(-d)` argument allows you to change the output directory for your book.
`path/to/book` argument can be used to specify a target directory.

### Render mdBook on every file change

Rendered mdbook on every file change by running `mdbook watch`.
You can use it once and it will watch your files and trigger a build automatically whenever you modify a file.
`--open` `(-o)` argument opens the rendered book in your default web browser after building it.
`--dest-dir` `(-d)` argument allows you to change the output directory for your book.
`path/to/book` argument can be used to specify a target directory.

## Preview mdBook after every file change

Preview your mdBook with hot reloading of the webpage whenever a file changes by running `mdbook serve`. 
It allows for you to see the result of your work instantly after every file change.
The contents are displayed on `localhost:3000` (unless otherwise configured) and runs a websocket server on `localhost:3001` which triggers the reloads.
`--open` `(-o)` argument opens the rendered book in your default web browser after building it.
`--dest-dir` `(-d)` argument allows you to change the output directory for your book.
`path/to/book` argument can be used to specify a target directory.

# Format

## `SUMMARY.md`

`SUMMARY.md` is the skeleton of the book. It has a strict formatting for parcing.

**Title** This is pretty self-explanatory. It is a good practive to give a title to your book, and sometimes a `# Summary` but it is not mandatory.

**Prefix Chapter** Non-numbered chapters are useful for forewords, introductions, etc. 

There are however some constraints:
* You can not nest prefix chapters, they should all be on the root level
* You can not add prefix chapters once you have added numbered chapters.

`[Title of prefix element](relative/path/to/markdown.md)`

**Numbered Chapter** These are the main content of the book, they will be numbered and can be nested, resulting in a nice hierarchy (chapters, sub-chapters, etc.)
You can either use `-` or `*` to indicate a numbered chapter.

`- [Title of the Chapter](relative/path/to/markdown.md)`

**Suffix Chapter** These are non-numbered chapters after the numbered chapters. They are the same as prefix chapters but come after the numbered chapters instead of before.


All other elements are unsupported and will be ignored at best or result in an error.

---

Adapted from [documentation](https://rust-lang.github.io/mdBook/index.html).