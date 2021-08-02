# Branching & Matching

## if else

```
let a :String? = reader.IsOpen then reader.ReadLine()
let b :String = a else "<EOF>"
```

Or combined

```
let b :String =
  reader.IsOpen
  then
    reader.ReadLine()
  else
    "<EOF>"
```

Definition
```
infix operator fun then {
  generic type A
  takes lefthand  let Condition :Boolean
  takes righthand let Action    :-> A
  returns A?
}

infix operator fun else {
  generic type A
  takes lefthand  let Option :A?
  takes righthand let Action :-> A
}
```

## Patterns

Type Matching
```
let x :Any = 7 to Int32
x is String then {
  WriteLine(x.ToLower)
}
else x is Int32 then {
  WriteLine(abs(x))
}
```

Pattern Matching
```
let x :Any = 7 to String
x matches let y :String then {
  WriteLine(y.ToLower)
}
```

Tuples
```
let x :Any = (7 to Int32, 7 to String)
x matches (let a :String, let b :String) then {
  WriteLine(a.ToLower ++ " " ++ b.ToUpper)
}
```

Records
```
let x :Any = new Person {
  Firstname = "Jane"
  Lastname  = "Doe"
}
x matches Person { let Firstname, let Lastname as Surname } then {
  WriteLine("Hello " ++  Surname ++ ", " ++ Firstname)
}
```






