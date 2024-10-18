## Background

Generics found in an associated type in a trait bound requires it to be
in the trait parameters. The following test should fail because of this,
but instead ICEs.

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
./x test tests/ui/wf/ice-wf-missing-span-in-error-130012.rs
```

## Failing Test

tests/ui/wf/ice-wf-missing-span-in-error-130012.rs
