## Background

When implementing a foreign trait for an unknown type, `fn_arg_names` is called on an non-fn item.

## Test

```rust
//@ check-fail

use std::ops::Index;

impl<T, F, Idx> Index<Idx> for Map<T, Output> {}

fn main() {}
```

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/ice-no-fn_arg_names
./x test tests/ui/resolve/dont-compute-arg-names-for-non-fn.rs
```

## Failing Test

tests/ui/resolve/dont-compute-arg-names-for-non-fn.rs
