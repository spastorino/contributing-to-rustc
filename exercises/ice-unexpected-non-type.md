## Background

If a function does not exist on a type, it should emit an error, but not ICE.

## Test

```rust
//@ check-fail


fn x<T: Copy>() {
    T::try_from();
}

fn main() {}
```

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/ice-unexpected-non-type
./x test tests/ui
```
