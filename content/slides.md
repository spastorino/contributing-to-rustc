class: center
name: title
count: false

![Rust logo](content/rust-logo-blk.svg)

# Contributing to the Rust Compiler Workshop

.grey[Santiago Pastorino & Jack Huey]<br>
.grey[.smaller[Compiler & types team and Futurewei Rust team]]

[![Slides repo](content/qr.jpg)](https://github.com/spastorino/contributing-to-rustc)

https://github.com/spastorino/contributing-to-rustc

???

Ask them to copy the link, get the qr code
Introduce ourselves

---

# Objectives

- Give you the motivation, tools and willingness to become a contributor

???

This is a hands on workshop.
Where you would learn by doing.

---

# How did we get started?

- We all start somewhere, doing simple things and over time we become contributors

???

Share our experience about how and why did we get into the compiler

---

# Getting started

.center[[![Rustc Dev Guide](content/rustc-dev-guide.png)](https://rustc-dev-guide.rust-lang.org/)]

.center[https://rustc-dev-guide.rust-lang.org/]

???

You would find everything you need in the Rustc Dev Guide

---

# Prerequisites and requirements

- Laptop capable of building a compiler
- Intermediate-level Rust language experience
    - We're not going to teach Rust - we will guide on compiler internals though
- Rust development environment
    - Text editor or IDE
    - Git (and basic Git knowledge)
- Clone the workshop compiler repo (https://github.com/spastorino/contributing-to-rustc.git) and build/test
    - Useful guide: https://rustc-dev-guide.rust-lang.org/building/how-to-build-and-run.html (1.1, 1.2, 1.3)

---

# Quickstart

Guide: https://rustc-dev-guide.rust-lang.org/building/prerequisites.html

```
# clone the repo
git clone https://github.com/spastorino/contributing-to-rustc-exercises.git
cd contributing-to-rustc-exercises

# no need to ./x setup as the repo already includes a config.toml

# run all ui tests as a way to check that everything works
./x test tests/ui
```

???

x.py is the build tool for the rust repository. It can build docs, run tests, and compile the compiler and standard library.

---

# Editor

Most popular IDE for rustc development is VS Code

https://rustc-dev-guide.rust-lang.org/building/suggested.html#configuring-rust-analyzer-for-rustc

???

There are instructions to set up rust-analyzer for vscode
Use whatever you feel more comfortable with

---

# Overview of the compiler

.center[[![Overview](https://raw.githubusercontent.com/rust-lang/rustc-dev-guide/444fb28c880a24f9b36f1f6d658688c4041a60f8/src/overview/img/high-level-overview.svg)](https://rustc-dev-guide.rust-lang.org/overview.html)]

???

Don't worry too much about this

---

# Working on an issue

- Confirm/investigate the issue
    - playground: https://play.rust-lang.org/
    - godbolt: https://rust.godbolt.org/
    - bisect-rustc
    - add a test: https://rustc-dev-guide.rust-lang.org/tests/adding.html

???

Learn by doing is a great way
Hack and read as you go
Live demo (playground, godbolt, add test)

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

# Exercises

- ICE: internal compiler error
    - A unexpected bug in the compiler
- Diagnostics
- Features

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
