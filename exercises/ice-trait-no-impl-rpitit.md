## Background

When there is a trait with no impls with a function containing an RPITIT, we
encounter an ICE. The error suggests that the expectation of a defining use,
which doesn't exist (and cannot because there is no method body).

## Test

```rust
//@ check-fail

trait Fun {
    type Assoc;
}

trait Trait: for<'v> Fun<Assoc = &'v ()> {}

impl<F: for<'v> Fun<Assoc = &'v ()>> Trait for F {}

fn main() {}
```
