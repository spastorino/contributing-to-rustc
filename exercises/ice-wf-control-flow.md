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

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/ice-wf-control-flow
./x test tests/ui
```

## Failing Test

tests/ui/wf/ice-wf-missing-span-in-error-130012.rs
