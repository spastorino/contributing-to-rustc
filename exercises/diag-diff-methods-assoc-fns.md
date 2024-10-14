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
