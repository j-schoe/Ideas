# Example Module

* `https://example.com/example-project/`
  * `src/main/let/`
    * `module.let`
    * `Main.let`
    * `Prompter.let`
  * `src/test/let/`
    * `module.let`
    * `Prompter.test.let`
  * `dist/`
    * `module.jsonld`
    * `main.wasm`
    * `test.wasm`


## src/main/let/module.let
```
module {
  from    "ink+https://example.com/example-project"
  name    "Example-Project"
  vendor  "Example-Company"
  version "1.0.0"

  dependency {
    from    "ink+https://ink.example/stdlib"
    name    "Ink-Stdlib"
    vendor  "Ink-Foundation"
    version "1.0"
  }

  dependency {
    from    "ink+https://ink.example/launch"
    name    "Ink-Launch"
    vendor  "Ink-Foudation"
    version "1.0"
  }

  provides {
    service Ink.Launch.App
    with ExampleProject.Main
  }
}
```

## src/main/let/Main.let
```
at ExampleProject {

  import Ink.Launch.App
  import Ink.Launch.Environment

  export let Main = object {
    extends App

    override fun Main(let Env: Environment): Unit {
      let p = new Prompter {
        Write = Env.IO.WriteLine
        Read  = Env.IO.ReadLine
      }
      let name = p.Prompt("name")
      Env.IO.WriteLine("Hello " ++ name ++ ". o/")
      let rawAge = p.Prompt("age")
      try {
        Nat32.Parse(rawAge)
        Env.IO.WriteLine("Wow! That old!?")
      }
      catch { ->
        Env.IO.WriteLine("You entered a wrong age :'(")
      }
      Env.Exit(0)
    }
  }

}
```

## src/main/let/Prompter.let
```
at ExampleProject {

  export let Prompter = class {
    protected fun Write(let Text: String): Unit
    protected fun Read(): String

    fun Promt(let What: String): String {
      this.Write("Please enter your " ++ What ++ ":")
      return this.Read()
    }
  }

}
```

## src/test/let/module.let
```
module {
  from    "ink+https://example.com/example-project!test"
  name    "Example-Project-Tests"
  vendor  "Example-Company"
  version "1.0.0"

  dependency {
    from "ink+https://example.com/example-project"
  }
  dependency {
    fron "ink+https://ink.example/testlet"
  }
}
```

## src/test/let/Prompter.test.let
```
test {
  import ExampleProject.Prompter

  that "prompter returns right value" {
    run {
      let v = "Hello"
      let p = new Prompter {
        Write = _  -> {}
        Read  = () -> v
      }
      let m = p.Prompt("foo")
      Assert(m === v)
    }
  }
}
```

## dist/module.jsonld
```json
{
  "@context": "https://ink.example/ink-module.jsonld",
  "id": "ink+https://example.com/example-project",
  "dependencies": [{
    "id": "ink+https://ink.example/stdlib",
    "name": "Ink-Stdlib",
    "vendor": "Ink-Foundation",
    "version": "1.0",
    "integrity": [...]
  }, {
    "id": "ink+https://ink.example/launch",
    "name": "Ink-Launch",
    "vendor": "Ink-Foundation",
    "version": "1.0",
    "integrity": [...]
  }],
  ...
}
```

