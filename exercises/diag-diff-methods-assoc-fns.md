## Background

```rust
trait Other {
    fn bar<const M: u8>() {}
}
impl Other for () {
    fn bar<T>() {}
    //~^ error: method `bar` has an incompatible generic parameter for trait
}
```

Make that be `associated function` for associated functions and `method` for methods.

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/diag-diff-methods-assoc-fns
./x test tests/ui
```
