# Ink Strings

```
/// A sequence of Unicode symbols.
/// Independent of language and
/// Unicode version.
let Ink.Text.String = class {
  
  /// The content of the string
  /// as UTF-8 bytes.
  let Bytes: Bytes
  
  /// The content of the string
  /// as Unicode scalars.
  let Scalars = object {
    extends Immutable.Sequence[VarNat]
    ...
  }
  
}
```
```
let Ink.Text.GraphemeString = class {
  
  let GraphemeClusters: Immutable.Sequence[String]
  
  let Unicode: Unicode
  
  let Locale: Locale
  
}
```


