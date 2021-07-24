# Framework

## Target

* Compilation from LetLang to Wasm
* Interop from LetLang to Wasm
* Interop from Wasm to LetLang
* Wasm Library

## Ink

Ink is to LetLang what .NET is to C#.
But:
* Less monolithic!
* More modular!
* Based on dependency injection!
* No static magic!

## Modularity

~/src/main/let/module.let
```
module {
  from    "http://my-company.example/my-module/dist/main"
  name    "My.Module"
  vendor  "My.Company"
  version "0.0.1"

  dependency {
    from    "http://ink.example/interface/crypto/dist/main"
    name    "Interface.Ink.Crypto"
    vendor  "Ink-Foundation"
    version "1.0.0"
    integrity { ... }
  }

  dependency {
    from "http://ink.example/interface/launch/dist/main"
    at ILaunch
  }

  provides {
    service ILaunch.App
    with My.Project.CLI.Main
  }
}
```

## Ink URLs

```
ink+https://example.com/foo
 => https://example.com/foo/dist/main
```
```
ink+ftp://example.net/bar!test
 => ftp://example.net/bar/dist/test
```

## Pit SCM

A git-like SCM based on ceramic.
`pit://<stream-id>/foo/bar.txt`

> TO BE CONTINUED!
