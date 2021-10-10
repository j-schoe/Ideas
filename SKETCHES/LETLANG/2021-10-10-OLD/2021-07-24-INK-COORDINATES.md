# Ink Coordinates

1 Package <---> n Modules

```
~/projects/example/
  src/
    main/...
    test/...
    whatever/...
  dist/
    main.wasm
    test.wasm
    whatever.wasm
```

## Absolute URLs

* The binaries of the main module:
```
file:///~/projects/example/dist/main.wasm
```

* The sources of the test module:
```
file:///~/projects/example/src/main/
```

## Coordinate URLs?

```
ink+<url>[#[<module>]]
```
* `<module>` defaults to `main`.
Examples:
```
ink+https://example.com/foo
ink+ftp://ftp.example.net/bar#test
```

## Package URLs?


