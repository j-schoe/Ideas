# Bootstrapping

## Booleans

```
type Ink.Boolean = trait {
  (@Ink.Build.Optimization.ForceInline)
  (@Ink.Build.Optimization.CompilerIntrinsic)
  this

  permits Ink.False.type
  permits Ink.True.type

  protected fun Select {
    generic type A
    takes let WhenFalse :A
    takes let WhenTrue  :A
    returns A
  }
}

let Ink.False = object {
  extends Ink.Boolean {
    Select = (let it, _) -> it
  }
}

let Ink.True = object {
  extends Ink.Boolean {
    Select = (_, let it) -> it
  }
}

let Ink.Boolean.Operators = extension {
  for Ink.Boolean

  fun this.(Ink.Symbols.Operators.Prefix.Not) {
    returns Ink.Boolean
    apply {
      return this.Select(Ink.False, Ink.True)
    }
  }

  fun this.(Ink.Symbols.Operators.Infix.And) {
    takes let Operand :lazy Ink.Boolean
    returns Ink.Boolean
    apply {
      return this.Select(Operand, Ink.False as lazy)
    }
  }

  fun this.(Ink.Symbols.Operators.Infix.Or) {
    takes let Operand :lazy Ink.Boolean
    returns Ink.Boolean
    apply {
      return this.Select(Ink.True as lazy, Operand)
    }
  }
}
```





