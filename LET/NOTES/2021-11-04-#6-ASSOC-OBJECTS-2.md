# Associated Objects (2)

## Direct

```
type String = primitive {
    assoc let Unicode :Unicode
    assoc let Locale  :Locale
    ...
}

let str { Locale = "de-DE" } = "Hallo"
```

# Indirect

```
type String = primitive {...}

type String.AssocUnicodeAnnotation = trait {
    extends RuntimeAnnotation {
        Target = Use(String)
    }
    let Unicode :Unicode
    new(Unicode)
}

type String.AssocLocaleAnnotation = trait {
    extends RuntimeAnnotation {
        Target = Use(String)
    }
    let Locale :Locale
    new(Locale)
}

let str :(@AssocLocale("de-DE")) String = "Hallo"
```
