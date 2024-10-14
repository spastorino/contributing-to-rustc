## Background

- Do not allow types named `Pizza` that contains in its generics types `Pineapple`. `Pizza<Pinneaple>`
- Learn about `TyKind` and in particular `TyKind::Path`
- Register late lint, for that look at `compiler/rustc_lint/src/lib.rs` 
- Can just finding such types and `panic!` when you find them.
- Extra points to use the linting infrastructure

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/feat-pinneaple-pizza
```
