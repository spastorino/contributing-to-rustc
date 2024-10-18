## Background

Given a function with anonymous arguments like `fn foo_with_qualified_path(<Bar as T>::Baz);`,

instead of suggesting:

```
fn foo_with_qualified_path(_: <Bar as T>::Baz);
                           ~~~~~~~~~~~~~~~~~~
```

suggest:

```
fn foo_with_qualified_path(_: <Bar as T>::Baz);
                           ++
```

## Branch

```
# Go to previously cloned exercises repo
cd contributing-to-rustc-exercises
git checkout exercises/diag-more-acc-span
./x test tests/ui
```

## Failing Test

tests/ui/anon-params/anon-params-denied-2018.rs
