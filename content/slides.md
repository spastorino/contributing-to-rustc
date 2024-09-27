class: center
name: title
count: false

# Contributing to the Rust Compiler Workshop

Santiago Pastorino & Jack Huey

---

# About us

Santiago: Compiler team contributor, Types team member, Project Director for the Rust Foundation and Futurewei Rust team member
Jack: Compiler team member, Types team lead, Council member and Futurewei Rust team member

---

# Objectives

Give you the motivation, tools and willingness to become a contributor

???

This is a hands on workshop.
Where you would learn by doing.

---

# How did we get started?

We all start somewhere, doing simple things and over time we become contributors

???

Share our experience about how and why did we get into the compiler

---

# Getting started

[![Rustc Dev Guide](content/rustc-dev-guide.png)](https://rustc-dev-guide.rust-lang.org/)

???

You would find everything you need in the Rustc Dev Guide

---

# Quickstart

[Prerequisites](https://rustc-dev-guide.rust-lang.org/building/prerequisites.html)

```
# clone the repo
git clone https://github.com/rust-lang/rust.git
# or shallow clone (not recommended but faster on a slow internet)
# git clone --depth 1 https://github.com/rust-lang/rust.git
cd rust

# create configuration with good defaults (choose b: compiler)
./x setup

# build the compiler, standard library and a few tools
./x build

# create toolchain with rustup
rustup toolchain link rustc-stage1 build/host/stage1

# compile a file to test everything is working
rustc +rustc-stage1 testfile.rs

# test all ui tests
./x test tests/ui
```

???

x.py is the build tool for the rust repository. It can build docs, run tests, and compile the compiler and standard library.

---

# Editor

- Vscode, vim, neovim, whatever you like
- [rust-analyzer and set it up](https://rustc-dev-guide.rust-lang.org/building/suggested.html#configuring-rust-analyzer-for-rustc)

???

Use whatever you feel more comfortable with

---

# Overview of the compiler

[![Overview](https://raw.githubusercontent.com/rust-lang/rustc-dev-guide/444fb28c880a24f9b36f1f6d658688c4041a60f8/src/overview/img/high-level-overview.svg)](https://rustc-dev-guide.rust-lang.org/overview.html)

---

# Working on an issue

- Confirm/investigate the issue
    - [playground](https://play.rust-lang.org/)
    - [godbolt](https://rust.godbolt.org/)
    - bisect-rustc
- Investigate/explore concepts
    - Try to guess, read relevant parts of the guide go back, investigate
    - Check nightly rustc documentation if needed
    - Read issues and pull requests
    - Search for error messages, failures and things to jump to relevant parts of the code
- Debug
- [Add a test](https://rustc-dev-guide.rust-lang.org/tests/adding.html) if needed

???

Learn by doing is a great way
Hack and read as you go

---

# Debugging

- [`RUST_BACKTRACE=1` & `-Z flags`](https://rustc-dev-guide.rust-lang.org/compiler-debugging.html#getting-a-backtrace)
    - \# enable printing more info
       -Z verbose-internals
    - \# Get backtrace on the point the compiler emits an error
      `-Z treat-err-as-bug`
    - \# Turn delayed bugs into normal errors
      `-Z eagerly-emit-delayed-bugs`
    - \# Track where errors were created
      `-Z track-diagnostics`
    - [`#[rustc_*]` TEST attributes](https://rustc-dev-guide.rust-lang.org/compiler-debugging.html#rustc_-test-attributes)
- [Tracing](https://rustc-dev-guide.rust-lang.org/tracing.html)
    - `RUSTC_LOG=rustc_borrowck[do_mir_borrowck]`
    - `RUSTC_LOG=rustc_ast_lowering,rustc_hir_typeck`

---

## Exercises

### Features
 
Silly stuff like pineapple on pizza or similar style of lint
#70645 https://github.com/rust-lang/rust/pull/70645
 
Tracking Issue for Rust 2024: Make unsafe_op_in_unsafe_fn warn-by-default
#123916 https://github.com/rust-lang/rust/pull/112038 (Extremely easy)
 
Tracking Issue for RFC 3325: unsafe attributes
#123757 https://github.com/rust-lang/rust/pull/124214

Tracking Issue for RFC 3484: Unsafe Extern Blocks
#123743 https://github.com/rust-lang/rust/issues/123743
 
Add automatic applicable lint to Unsafe extern blocks so items can be automatic upgrade to be unsafe
 
Tracking Issue for #![feature(offset_of)]
#106655 https://github.com/rust-lang/rust/issues/106655 impl https://github.com/rust-lang/rust/pull/106934
 
### ICEs

ICE "tried to get type of this RPITIT with no definition" for complex return position impl trait
#130422 https://github.com/rust-lang/rust/issues/130422 fix https://github.com/rust-lang/rust/pull/130440

Avoid crashing on variadic functions when producing arg-mismatch errors #130437 (warning: requires debug assertions to repro)
https://github.com/rust-lang/rust/issues/130400 fix https://github.com/rust-lang/rust/pull/130437

const: don't ICE when encountering a mutable ref to immutable memory #130394 
https://github.com/rust-lang/rust/issues/130392 fix https://github.com/rust-lang/rust/pull/130394

ICE: does not have a "fn_arg_names"'
#130015 https://github.com/rust-lang/rust/issues/130015 fix https://github.com/rust-lang/rust/pull/130033

ICE: control flow ensures we have a BindingObligation or WhereClauseInExpr here
#130012 https://github.com/rust-lang/rust/issues/130012 fix https://github.com/rust-lang/rust/pull/130137

Unsoundness: Patterns in function parameters are not checked for union access
#130528 https://github.com/rust-lang/rust/issues/130528 fix https://github.com/rust-lang/rust/pull/130531

ICE: expected lifetime parameter, but found another generic parameter
#129850 https://github.com/rust-lang/rust/issues/129850 fix https://github.com/rust-lang/rust/pull/130412

ICE: associated type missing default
#129216 https://github.com/rust-lang/rust/issues/129216 fix https://github.com/rust-lang/rust/pull/129250

### Diagnostics

Point at explicit 'static obligations on a trait #129070 https://github.com/rust-lang/rust/pull/129070

Differentiate between methods and associated functions in diagnostics #128910 https://github.com/rust-lang/rust/pull/128910

More accurate suggestion for -> Box<dyn Trait> or -> impl Trait #127987  https://github.com/rust-lang/rust/pull/127987

More accurate span for anonymous argument suggestion #127889 https://github.com/rust-lang/rust/pull/127889

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

# Thanks

Twitter/Github: spastorino, jackh726
Email: spastorino@gmail.com, jackh726@gmail.com
