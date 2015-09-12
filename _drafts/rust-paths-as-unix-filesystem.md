---
layout: post
title: "The Rust Module System as a UNIX Filesystem"
---

A lot of people have a hard time understanding [Rust][rust]'s module system.
It can feel like there's a lot going on
with `mod`, `use`, `extern crate`, `foo::bar`, and `::foo::bar`
all playing a role.
But like many problems, it's easy once you have the right mental model.
I hope the following explanation will be that mental model for you.

(If you aren't familiar with the Rust syntax I mentioned above,
you should start with the Rust book's [section on modules][rust-modules]
and come back to this post later.
If you aren't familiar with Rust at all,
[the Rust book][rust-book] is for you!)

[rust]: https://www.rust-lang.org/
[rust-book]: https://doc.rust-lang.org/stable/book/
[rust-modules]: https://doc.rust-lang.org/stable/book/crates-and-modules.html


### Early hints

The key insight to understanding Rust's module system for me
was hinted at first in the Rust documentation.
The book has this to say:

> Well, by default, `use` declarations are absolute paths, starting from your
> crate root. `self` makes that path relative to your current place in the
> hierarchy instead.[^1]

[^1]: [The Rust Programming Language: Crates and Modules][rust-book-modules]

Absolute and relative paths in a hierarchy? Sounds like a filesystem.
Reading on:

> There’s one more special form of `use`: you can `use super::` to reach one
> level up the tree from your current location. Some people like to think of
> `self` as `.` and `super` as `..`, from many shells' display for the current
> directory and the parent directory.

Yep, definitely a filesystem. But the book stops here, and I want to stretch
this analogy much further.


### Basics

Let's start with a basic Rust program with a submodule:

``` rust
// lib.rs

/// This module has a doc comment.
mod {
    fn generic<T: Copy>(t: T) -> T {
        t.clone() // This should work.
    }

    fn maths(x: i32, y: i64) -> i64 {
        let z: i64 = x as i64 * y + 20 & 0x0F;
        z + 0o77 / 0b1001
    }

    fn strings() -> &'static str {
        "this is a string"
    }

    fn map<X, Y>(option: Option<X>, transformer: ...) -> Option<Y> {
        match option {
            Some(x) => Some(transformer(x)), // (closure syntax for now)
            None => None,
        }
    }
}
```

### Notes

* The current scope is the current working directory (cwd).
* The crate root, or `::`, is `/`.
* `mod foo { ... }` is `mkdir foo; cd foo; ...; cd ..;`.
* Every item (`fn`, `type`, `const`, `static`, `struct`, `enum`, etc.)
  creates a different kind of file in the current working directory.
* `use foo::bar` is `ln -s /foo/bar bar`.
* `use foo::bar as quux` is `ln -s /foo/bar quux`.
* `use self::foo::bar` is `ln -s ./foo/bar bar`.
* `use super::foo::bar` is `ln -s ../foo/bar bar`.
* `extern crate foo;` is `mkdir foo; mount /dev/foo foo`.
* What about `pub` and visibility?
