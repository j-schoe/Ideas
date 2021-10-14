# Let Parser

```
fun Main(let Env: Ink.Launch.Envrionment): Unit {
  let x = 7 + 3
  Env.IO.WriteLine("The Result Is " ++ x)
}
```

```
Function {
    Name = Symbol "Main"
    Takes = {
        #0 = NameAndTypePattern {
            Name = Symbol "Env"
            Type = Dot {
                Receiver = Dot {
                    Receiver =  Symbol "Ink"
                    Symbol = Symbol "Launch"
                }
                Symbol = Symbol "Envrionment"
            }
        }
    }
    Returns = Type {
        Symbol "Unit"
    }
    Body = {
        #0 = Assignment {
            Pattern = NamedAndTypePattern {
                
            }
            Value = Infix {
                Name = Symbol "+"
                L = Literal "7"
                R = Literal "3"
            }
        }
        #1 = Application {
            Receiver = Dot {
                Reciever = Dot {
                    Reciver = Symbol "Env"
                    Sybmol = Symbol "IO"
                }
                Symbol = Symbol "WriteLine"
            }
            Takes = {
                #0 = Literal "\"Hello World\""
            }
        }
    }
}
```

