class: center
name: title
count: false

![Rust logo](content/rust-logo-blk.svg)

# Contributing to the Rust Compiler Workshop

.grey[Santiago Pastorino & Jack Huey]<br>
.grey[.smaller[Compiler & types team and Futurewei Rust team]]

[![Slides repo](content/qr.jpg)](https://github.com/spastorino/contributing-to-rustc)

https://santiagopastorino.com/contributing-to-rustc<br>
https://github.com/spastorino/contributing-to-rustc

???

- Welcome
- Copy the link
- Introduce ourselves

---

# Objectives

- Give you the motivation, tools and willingness to become a contributor

???

- Get excited about contributing
- This is a hands on workshop
- Where you would learn by doing
- It takes a LOT of time to really learn the compiler and probably nobody understands it all

---

# How did we get started?

- We all start somewhere, doing simple things and over time we become contributors

???

Share our experience about how and why did we get into the compiler

---

# Prerequisites and requirements

- Laptop capable of building a compiler
- Intermediate-level Rust language experience
    - We're not going to teach Rust - we will guide on compiler internals though
- Rust development environment
    - Text editor or IDE
    - Git (and basic Git knowledge)
- Clone the workshop compiler repo (https://github.com/spastorino/contributing-to-rustc-exercises.git) and build/test
    - Useful guide: https://rustc-dev-guide.rust-lang.org/building/how-to-build-and-run.html (1.1, 1.2, 1.3)

???

- Did you get a message with these instructions?
- Did you all do this already?
- Don't worry if you didn't

---

# Editor

Most popular IDE for rustc development is VS Code

https://rustc-dev-guide.rust-lang.org/building/suggested.html#configuring-rust-analyzer-for-rustc

???

- There are instructions to set up rust-analyzer for vscode
- Use whatever you feel more comfortable with

---

# Quickstart

Guide: https://rustc-dev-guide.rust-lang.org/building/prerequisites.html

```
# clone the repo, there's no need to do ./x setup as the repo already
# includes a config.toml and run all ui tests as a way to check that
# everything works
git clone https://github.com/spastorino/contributing-to-rustc-exercises.git
cd contributing-to-rustc-exercises
./x test tests/ui
```

???

- x.py is the build tool for the rust repository
- It can build docs, run tests, and compile the compiler and standard library.

---

# Rustc Dev Guide

.center[[![Rustc Dev Guide](content/rustc-dev-guide.png)](https://rustc-dev-guide.rust-lang.org/)]

.center[https://rustc-dev-guide.rust-lang.org/]

???

- You would find everything you need in the Rustc Dev Guide
- Take one minute to open the guide and navigate it together

---

# Overview of the compiler

.center[[![Overview](content/high-level-overview.svg)](https://rustc-dev-guide.rust-lang.org/overview.html)]

???

- Don't worry too much about this

---

# Working on an issue

- Confirm/investigate the issue
    - playground: https://play.rust-lang.org/
    - godbolt: https://rust.godbolt.org/
    - bisect-rustc
    - add a test: https://rustc-dev-guide.rust-lang.org/tests/adding.html

???

- Learn by doing is a great way to learn
- Hack and read as you go
- Live demo (playground, godbolt, add test)

---

# Working on an issue

- Confirm/investigate the issue
    - playground: https://play.rust-lang.org/
    - godbolt: https://rust.godbolt.org/
    - bisect-rustc
    - add a test: https://rustc-dev-guide.rust-lang.org/tests/adding.html
- Investigate/explore concepts
    - Try to guess, read relevant parts of the guide go back, investigate
    - nightly rustc documentation: https://doc.rust-lang.org/nightly/nightly-rustc/rustdoc/index.html
    - Read issues and pull requests
    - Search for error messages, failures and things to jump to relevant parts of the code
- Debug

---

# Debugging

```
# Enable printing more info
# Probably not needed
//@ compile-flags: -Z verbose-internals
# Get backtrace on the point the compiler emits an error
# Useful when there is an ICE (internal compiler error)
//@ compile-flags: -z treat-err-as-bug
# When something unexpected happens, we sometimes
# *assume* that compilation will later fail
//@ compile-flags: -Z eagerly-emit-delayed-bugs
# Track where errors were created
//@ compile-flags: -Z track-diagnostics
```

https://rustc-dev-guide.rust-lang.org/compiler-debugging.html

---

# Tracing

A better "log" crate

Examples:

```
RUSTC_LOG=rustc_borrowck[do_mir_borrowck]
RUSTC_LOG=rustc_ast_lowering,rustc_hir_typeck
```

???

Can filter by crate, method, argument, etc.

---

class: medium

# Exercises

- ICEs: Internal Compiler Error
  - [const: don't ICE when encountering a mutable ref to immutable memory](https://github.com/spastorino/contributing-to-rustc/blob/main/exercises/ice-mutable-const.md)
  - [ICE "tried to get type of this RPITIT with no definition" for complex return position impl trait](https://github.com/spastorino/contributing-to-rustc/blob/main/exercises/ice-rpitit-no-body.md)
  - [ICE: does not have a "fn_arg_names"](https://github.com/spastorino/contributing-to-rustc/blob/main/exercises/ice-no-fn_arg_names.md)
  - [ICE: control flow ensures we have a BindingObligation or WhereClauseInExpr here](https://github.com/spastorino/contributing-to-rustc/blob/main/exercises/ice-trait-no-impl-rpitit.md)
- Diagnostics
  - [More accurate span for anonymous argument suggestion](https://github.com/spastorino/contributing-to-rustc/blob/main/exercises/diag-more-acc-span.md)
  - [Differentiate between methods and associated functions in diagnostics](https://github.com/spastorino/contributing-to-rustc/blob/main/exercises/diag-diff-methods-assoc-fns.md)
- Features
  - [Pineapple on pizza not allowed](https://github.com/spastorino/contributing-to-rustc/blob/main/exercises/feat-pinneaple-pizza.md)

???

ICE: can happen from panics, for example
Diagnostics: We value good diagnostics
Features: Only small things here

---

# What's next for me?

- Join Zulip discussions https://rust-lang.zulipchat.com/
- Keep contributing and learning
    - Find e-easy and/or e-mentor issues
    - Read issues and pull requests
    - Search in your area of interest, try to focus
    - Contribute documentation, triage/prioritization, project management, etc

???

How do I learn?

- Do whatever you feel more comfortable with to learn
- Read PRs
- Project management
  - Ensure features keep moving
  - Help teams keep track of and document decisions

---

class: center
name: title
count: false

![Rust logo](content/rust-logo-blk.svg)

# Thanks

.grey[Twitter/Github: spastorino, jackh726]<br/>
.grey[Email: spastorino@gmail.com, jackh726@gmail.com]
