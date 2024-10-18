## Background

```rust
trait Other {
    fn bar<const M: u8>() {}
}
impl Other for () {
    fn bar<T>() {}
    //~^ error: method `bar` has an incompatible generic parameter for trait
}
```

Make that be `associated function` for associated functions and `method` for methods.

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/diag-diff-methods-assoc-fns
./x test tests/ui
```

## Failing Tests

tests/ui/async-await/in-trait/generics-mismatch.rs
tests/ui/const-generics/defaults/mismatched_ty_const_in_trait_impl.rs
tests/ui/error-codes/E0049.rs
tests/ui/error-codes/E0195.rs
tests/ui/generic-associated-types/gat-trait-path-missing-lifetime.rs
tests/ui/impl-trait/in-trait/trait-more-generics-than-impl.rs
tests/ui/rfcs/rfc-2632-const-trait-impl/const-drop.rs#precise
tests/ui/rfcs/rfc-2632-const-trait-impl/const-drop.rs#stock
tests/ui/rfcs/rfc-2632-const-trait-impl/specialization/default-keyword.rs
tests/ui/rfcs/rfc-2632-const-trait-impl/specialization/const-default-bound-non-const-specialized-bound.rs
tests/ui/rfcs/rfc-2632-const-trait-impl/specialization/issue-95186-specialize-on-tilde-const.rs
tests/ui/rfcs/rfc-2632-const-trait-impl/specialization/issue-95187-same-trait-bound-different-constness.rs
tests/ui/rfcs/rfc-2632-const-trait-impl/specializing-constness-2.rs
tests/ui/rfcs/rfc-2632-const-trait-impl/specialization/const-default-const-specialized.rs
tests/ui/rfcs/rfc-2632-const-trait-impl/specialization/non-const-default-const-specialized.rs
tests/ui/specialization/const_trait_impl.rs
tests/ui/typeck/issue-36708.rs
