## Background

When transmuting to a mutable const, an ICE occurs. It should error, but not crash.

## Test

```rust
//@ check-fail

const IMMUT_MUT_REF: &mut u16 = unsafe { std::mem::transmute(&13) };

fn main() {}
```

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/ice-mutable-const
./x test tests/ui/consts/const-mut-refs/mut_ref_in_final.rs
```

## Failing Test

tests/ui/consts/const-mut-refs/mut_ref_in_final.rs
