# Syntax: Comments

## Line Comments
~~~
// Hello
~~~

## Block Comments
~~~
/*
 * /* Hello
 *
 */
~~~

## Nest Comments
~~~
/^
 ^ /^ Hello ^/
 ^
 ^/
~~~

## Doc Comments
~~~
/**
 * Does *something*.
 */
~~~
OR
~~~
/^^
 ^ Does *something*.
 ^/
~~~
OR
~~~
/// Does *something*.
~~~

## Doc Comment Markup
* Markup?
* Wiki?
* Something else?

~~~
/**
 * Greets the given name.
 *
 * # Parameter [Name]
 *   The name to greet.
 *
 * # Throws [ArgumentException]
 *   If [Name] is empty.
 */
fun Greet(let Name :String) :Unit
~~~

> Do I wanna reinvent the wheel?



