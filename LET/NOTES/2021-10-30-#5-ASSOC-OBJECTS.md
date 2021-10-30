# Associated Objects

Objects whose are statically associated with other objects.

## Example: Link

```
type Link = trait {
    assoc let Marshal  :Marshal
    assoc let Resolver :Resolver
}

type LinkCrudExtension = extension {
    for Link {
        fun Create {
            using let Marshal  :Marshal  default this.Marshal
            using let Resolver :Resolver default this.Resovlver
            takes let Object   :Marshal.MarshalledType
            returns Boolean
            body default {
                return Resolver.Create(this, Object)
            }
        }
        fun Retrieve {
            using let Marshal  :Marshal  default this.Marshal
            using let Resolver :Resolver default this.Resolver
            returns Marshal.MarshalledType
            body default {
                return Resolver.Resolve(this)
            }
        }
        fun Update {
            using let Marshal  :Marshal  default this.Marshal
            using let Resolver :Resolver default this.Resovlver
            takes let Object   :Marshal.MarshalledType
            returns Marshal.MarshalledType?
            body default {
                return Resolver.Update(this, Object)
            }
        }
        fun Dispose {
            using let Marshal  :Marshal  default this.Marshal
            using let Resolver :Resolver default this.Resovlver
            returns Boolean
            body default {
                return Resolver.Dispose(this)
            }
        }
    }
}
```

Usage
```
Assert(URL <: Link)

let json = URL("http://json.example/example.json").With(Marshal = JsonObject).Retrieve()
```

## Example: String

```
type String = primitive {

    /** The unicode version associated with the string. */
    assoc let Unicode :Unicode

    /** The UTF-8 bytes of the string. */
    let Bytes :Bytes

    ...

    fun ToLower {
        using let Unicode :Unicode default this.Unicode
    }

    ...
}
```

Usage?

```
let str = "Hello World".With(Unicode = Unicode.14)
```

