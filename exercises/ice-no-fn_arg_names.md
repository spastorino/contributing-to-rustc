## Background

When implementing a foreign trait for an unknown type, `fn_arg_names` is called on an non-fn item.

## Test

```rust
//@ check-fail

use std::ops::Index;

impl<T, F, Idx> Index<Idx> for Map<T, Output> {}

fn main() {}
```
