# Functions

```
fun Foo(): Int32 {
  WriteLine("Hello World")
  return 42
}
```

## Verbose Declaration

```
fun Bar {
  takes let {0, X}: Int
  takes let {1, Y}: Int
  takes let {2, D}: String = ""
  returns Int
  body {
    WriteLine("Computing the squared magnitude of " ++ D)
    return X**2 + Y**2
  }
}
```

