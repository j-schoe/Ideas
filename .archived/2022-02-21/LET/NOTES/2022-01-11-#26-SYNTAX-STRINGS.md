# Syntax: Strings

## Regular Line Strings

~~~
let Message = "Hello World \\o/"
~~~

## Regular Block Strings

~~~
let Message =
  """
  Hello
  World
  """
~~~
ALTERNATIVE
~~~
let Message =
  /"Hello
   "World
   "/
~~~

> Linebreak at the end?

## Raw Line Strings

~~~
let Message = `Hello World \o/`
~~~

## Raw Block Strings

~~~
let Message =
  ```
  Hello
  World
  ```
~~~
ALTERNATIVE
~~~
let Message =
  /`Hello
   `World
   `/
~~~

## Interpolation

* Only for regular strings.
* The brackets are mandatory.

~~~
let Message1 = "Hello ${name}."
let Message2 =
  """
  Hello ${name}.
  """
let Message3 = /"Hello ${name}."/
~~~

## Escaping

Typical Escapes:
* `\\`
* `\"`
* `\n`
* `\r`
* `\t`
* `\0` (special)
* etc.

Unicode Escapes:
* `\u{20}`
* `\U{20}`

Escaped Linebreak:
~~~
"""
Hello\
World
"""
~~~

Keep Trailing Whitespaces
~~~
"""
Hello     \s
World
"""
~~~
