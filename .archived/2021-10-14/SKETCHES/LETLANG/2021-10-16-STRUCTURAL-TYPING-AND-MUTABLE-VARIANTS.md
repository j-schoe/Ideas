# Thoughts on structural typing and mutable variants

Declaring a collection type with im-/mutable variants.
```
/**
 * A simple fixed-sized list of strings.
 */
type StringList = trait {

  let Length: VarNat

  fun GetAt(let Index: in until Length): String

  companion {
    type Immutable = trait {
      extends StringList
    }

    type Mutable = trait {
      extends StringList

      fun SetAt(let Index: in until Length, let Element: String): String
    }
  }

}
```

Usage
```
let myList1: StringList.Mutable = ???
let myList2: StringList = myList1
```

Sugar
```
let myList3 = mutable StringList = ???
let myList4 = immutable StringList = ???
```

Declaring Sugar?
```
type mutable(righthand type Container: having { type Mutable }) = Container.Mutable

type immutable(righthand type Container: having { type Immutable }) = Container.Immutable
```

TODO: Type parameters!?
``` 
/** for types with type-parameter */
type mutable(righthand type Container: Parameterized(let Param) and having { type Mutable <: Parameterized(typeOf(Param)) }) = Container.Mutable(Param)

/** for types without type-parameter */
type mutable(righthand type Container: having { type Mutable }) = Container.Mutable
```

