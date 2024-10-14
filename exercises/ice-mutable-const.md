## Background

When transmuting to a mutable const, an ICE occurs. It should error, but not crash.

## Test

```rust
//@ check-fail

const IMMUT_MUT_REF: &mut u16 = unsafe { std::mem::transmute(&13) };

fn main() {}
```
