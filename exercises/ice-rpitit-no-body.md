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

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/ice-rpitit-no-body
./x test tests/ui
```

## Failing Test

tests/ui/impl-trait/opaque-hidden-inferred-rpitit.rs
