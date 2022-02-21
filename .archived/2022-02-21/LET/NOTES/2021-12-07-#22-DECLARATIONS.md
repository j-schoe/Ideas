# Declarations

As in mutable properties and events.
Where e.g. the getter is public but the setter private.

## Declaring Access

```
let MyValue :Mutable(Int32) { get = public, set = private } = 0

type Mutable = trait {
  
  this(Element)
  type Element
  
  assoc let get :AccessModifier def public
  assoc let set :AccessModifier def public
  
  @get fun Get() :Element
  @set fun Set(:Element) :Unit
  
  @get and set) fun GetAndSet(:Element) :Element
  @(get and set) fun CompareAndSet(:Element, :Elemenet) :Element
  
}
```

## Overloading Access

```
let MyValue :Mutable(Int32) { get, private set }

type Mutable = trait {
  
  this(Element)
  type Element
  
  __overloadableAccess fun get :Element
  __overloadableAccess fun set(:Element) :Unit
  
  __overloadableAccess(get, set) fun get_and_set(:Element) :Element
  __overloadableAccess(get, set) fun compare_and_set(:Element, :Element) :Element
  
}
```

## Parallel Assignment

```
let MyValue.[get, private set] = Mutable(Int32)(0)
```

