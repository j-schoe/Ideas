# Flow Control

## Branching

### If

```
let result1 = if condition then action1
```

* `condition` is of type `Boolean`
* `action1` is of type `A`
* `result1` is of type `Option(A)`

Equivalent to the javascript code:
`const result1 = condition && action1`

### Else

```
let result2 = result1 else action2
```

* `result1` is of type `Option(A)`
* `action2` is of type `A`
* `result2` is of type `A`

Equivlent to the javascript code:
`const result2 = result1 || action2`

### Combined

```
let result = if condition then action1 else action2
```

### Variation

```
if condition then
  action1
else
  action2
```

```
if (condition) then {
  action1
}
else {
  action2
}
```

```
if condition
then
  action1
else
  action2
```

### Alternatives

* Without `if`
``` 
x == 7 then
  action1
else
  action2
```

* Without `then`

