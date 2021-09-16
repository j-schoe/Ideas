# Stateful Objects

## Declaration

```
type MyMutable = trait {
  
  this[T]
  type T
  
  state let Set :Boolean default False
  
  fun Get() :T
    prologue(this is Set)
  
  fun Set(:T) :Unit
    epilogue(this is Set)
  
  fun Exchange(:T) :T
    prologue(this is Set)
  
  fun Clear() :Unit
    epilogue(this is not Set)
  
}
```

## Usage

```
let mut :MyMutable[String] = TODO()
Assert(mut is not Set)

mut.Set("Hello")
Assert(mut is Set)

mut.Clear()
Assert(mut is not Set)
```

