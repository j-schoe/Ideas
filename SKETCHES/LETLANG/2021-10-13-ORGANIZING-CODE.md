# Organizing Code

## Namespaces

Generic Syntax: `at ⟪namespace⟫ ⟪declaration⟫`

Where `namespace` is a dot separated list of symbols.
Such as `Foo`, `Foo.Bar` or `Foo.Bar.Baz`.

And `declarations` is any sort of declaration.
Such as a `let`, a `fun`, a `type` or even
another `at` or a block of declarations.

### E.g.
```
at Foo let X = 17
```
Which can also be written as:
```
let Foo.X = 17
```

### Chained namespace declarations

Within the `declaration` part of an `at`
all members whose are declared in the same
namespace are accessible without having to
prefix them.

```
let Foo.X = 17

at Foo
at Bar
let Y = X + 3
```
Instead of:
```
let Y = Foo.X + 3
```

### At blocks

```
at Foo.Bar {
  let X = 17
  let Y = -3
}
```

### Issues

Only the first declaration after an `at`
is added the specified namespace!

*This might lead to confusing code?*

```

at Foo {
  at Bar
  let X = 7   // Foo.Bar.X
  let Y = 3   // Foo.Y
}

```

## Regions

Regions are purly there to group members
in the source code! They don't affect the code generated!

Regions can be named or not and may have doc-code
attached to them.

```
region "something something x something constant" {
  let X = 7
}
let Y = X - 3
```

```
/**
 * something something another x constant
 */
region {
  let X = 7
}
```
