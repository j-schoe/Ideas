# Immutable Properties vs. Constants

An immutable property is basically a constant which may be overridden.

So, are members overridable by default or not!?

```
type Person = record {
  
  open let Firstname :String
  open let Lastname  :String
  open let Birthdate :Date? = None
  
  closed get Age(using Clock): VarInt? = this.Birthdate then { (Clock.Now() - it).Days.Total }
  
}
```

## Options

### Constant, Default, Abstract

```
let Constant :VarInt = 7
let Default  :VarInt default 7
let Abstract :VarInt
```

Same for functions:
```
fun Constant() :VarInt = 7
fun Default() :VarInt default 7
fun Abstract(): VarInt
```

But what with verbose functions?
(Their syntax is anyways... experimental)
```
fun Constant {
  returns Int32
  apply = {
    return 7
  }
}

fun Default {
  returns Int32
  apply default {
    return 7
  }
}
```

### Open By Default

Means, since properties are just abstract constants; every function of a record, which is not declared clsoed, is included in its value!?

### Freedom Of Bound Type

```
type MyRec = record {
  let Foo: VarInt = 7
  let Bar = 7
}
```

A constant can only be overridden with a subtype of its declared type.
The type of `MyRec::Bar` is the type of 7, which just allowes 7!
So it can only be overridden with 7. Its de facto not overridable!

How are functions defined?


## Conclusion

For the time being:
Everything is open, except declared as `final`!

