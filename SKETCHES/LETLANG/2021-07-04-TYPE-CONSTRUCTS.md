# Type Constructs

## Tuples

```
// Tuples as product of types?
type MyTuple = Int * Int * String
type MyTuple = (Int ** 2) * String

// Tuples as tuple of types?
type MyTuple = (Int, Int, String)

// Tuples as pattern!
type MyTuple = (:Int, :Int, :String)
```

Usage

```
let t: MyTuple = (17, -3, "Hello")
t.0
t.1
t.2
```

## Named Tuples

```
// As patterns!
type MyNamedTuple = (let X: Int, let Y: Int, let D: String)
```

Usage

```
let t: MyNamedTuple = (17, -3, D = "Hello")
t.0
t.Y
t.2
```

## Records

```
type MyRecord = record {
  let X: Int
  let Y: Int
  let D: String
}
```

Usage

```
let t: MyRecord = new {
  X = 17
  Y = -3
  D = "Hello"
}
t.X
t.Y
t.D
```

## Traits

```
type MyTrait = trait {
  let X: Int
  let Y: Int
  let D: String
}
```

Usage

```
let t = object {
  extends MyTrait {
    X = 17
    Y = -3
  }
  override let D = "Hello"
  let D2 = "World"
}
t.D
t.D2
// X and Y are unaccessible

let t2: MyTrait = t
t2.X
t2.Y
t2.D
// D2 is unaccessible
```
