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
