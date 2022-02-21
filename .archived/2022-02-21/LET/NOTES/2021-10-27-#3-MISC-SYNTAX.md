# Misc. Syntax

## Scope Annotations

```
fun Foo(let Strings: Iterable(String)): String = {
    let s: String? = Strings.ForEach {
        let str ->
        if (str.Bytes.Count > 3) {
            return@ForEach str
        }
        else {
            return@Foo str
        }
    }
    return (s? ++ "...") else "N/A"
}
```

```
fun Bar(): Unit = {
  super@ParentType.Bar()
}
```

## Also Match As

```
let jane = Person {
  Firstname = "Jane"
  Lastname  = "Doe"
}

jane apply {
  let p & Person { let Fn = Firstname, let Ln = Lastname }
}
```

Alternative:
```
let p also Person { let Firstname, let Lastname } 
```

