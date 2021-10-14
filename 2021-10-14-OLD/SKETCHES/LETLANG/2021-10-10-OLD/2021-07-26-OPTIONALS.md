# Optionals in let Lang

> Pseudocode ahead!

```
T?` === Option(T)

t :T
Some(t) :T?
None    :T?
```


## Nestes Optionals

### Encapsulation

```
t :T
Some(Some(t)) :T??
Some(t) !== t
```
### Layers of None

```
t :T
t :T?
t :T??
t !== None
Some(t)    === t
Some(None) !== None

None             === None$0
Some(None)       === None$1
Some(Some(None)) === None$2

T?  === T or None$0.type
T?? === T or None$0.type or None$1.type
```









