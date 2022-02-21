# Named Parameters in Application, Construction & Deconstruction

Let lang is called let lang because of the inflationary usage of
the keyword let. The keyword is used to introduce a new name to
the current context aka. binding.

`let NewName = oldName`

## Possibilities

### Plain

| Operation       | Example                                                   | Issue?            |
|:----------------|:----------------------------------------------------------|:------------------|
| Application:    | `Foo(7, Bar = 28)`                                        |                   |
| Construction:   | `let p = Person { Firstname = "Jane", Lastname = "Doe" }` |                   |
| Deconstruction: | `p apply { let fn = Firstname -> fn }`                    | Weird assignment. |
| Yielding:       | `yield Result = "N/A"`                                    |                   |

### Dot Prefix

| Operation       | Example                                                     | Issue?               |
|:----------------|:------------------------------------------------------------|:---------------------|
| Application:    | `Foo(7, .Bar = 28)`                                         |                      |
| Construction:   | `let p = Person { .Firstname = "Jane", .Lastname = "Doe" }` |                      |
| Deconstruction: | `p apply { let fn = .Firstname -> fn }`                     |                      |
| Yielding:       | `yield .Result = "N/A"`                                     | Navigation operator! |

### Keyword Prefix

| Operation       | Example                                                             | Issue? |
|:----------------|:--------------------------------------------------------------------|:-------|
| Application:    | `Foo(7, with Bar = 28)`                                             |        |
| Construction:   | `let p = Person { with Firstname = "Jane", with Lastname = "Doe" }` |        |
| Deconstruction: | `p apply { let fn = with Firstname -> fn }`                         |        |
| Yielding:       | `yield with Result = "N/A"`                                         |        |

Issue: with operator:
`p with { with Firstname = "John" }`

Or instead:
`p { with Firstname = "John" }`

## Alternatives

### As

`p apply { Firstname as let fn -> fn }`

