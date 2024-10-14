## Background

When there is a trait with no impls with a function containing an RPITIT, we
encounter an ICE. The error suggests that the expectation of a defining use,
which doesn't exist (and cannot because there is no method body).

## Test

```rust
//@ check-pass

trait T0 {}

trait T1 {
    type A: Send;
}

trait T2 {
    fn foo() -> impl T1<A = ((), impl T0)>;
}

fn main() {}
```