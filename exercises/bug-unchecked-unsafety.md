## Background

When accessing the fields of a `union`, an unsafe block must be used. However,
when destructing a union in a function argument, no error is emitted.

## Test

```rust
//@ check-fail

union U {
    a: &'static i32,
    b: usize,
}
fn fun(U { a }: U) {
    dbg!(*a);
}
fn main() {
    fun(U { b: 0 });
    let closure = |U { a }| {
        dbg!(*a);
    };
    closure(U { b: 0 });
}
```

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/bug-unchecked-unsafety
./x test tests/ui
```
git 