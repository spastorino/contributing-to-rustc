## Background

When calling a c-variadic function with the wrong number of arguments, an
error should be emitted instead of an ICE.

## Test

```rust
//@ check-fail

#![feature(c_variadic)]
unsafe extern "C" fn test_va_copy(_: u64, mut ap: ...) {}
pub fn main() {
    unsafe {
        test_va_copy();
    }
}
```

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/ice-variadic-mismatch
./x test tests/ui
```
