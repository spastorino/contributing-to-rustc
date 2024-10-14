## Background

```rust=
extern "C" {
    static FOO: i32;
    fn bar();
}
```

A machine applicable lint to automatically convert with `cargo fix`, `extern "C"` into `unsafe extern "C"` already exist.
Implemented in https://github.com/rust-lang/rust/pull/124482/commits/1afc7d716cfb7858863754217566b785bac179a4

Now use that as inspiration to add a machine applicable lint to extern items, `static Foo` and `fn bar` in this example.

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/feat-machine-applicable-lint
```
