# Let Schemas & RPC

## Message

```
@Conforms("https://example.org/person.json", JsonSchema)
@Conforms("https://example.org/person.jsonld", JsonLD)
@Conforms("https://example.org/person.proto", ProtoIDL)
type Person = record {

  @SerializedName("id")
  @SerializedToken(4)
  @SerializeAs(UUID.Stringify)
  let Identifier :UUID

  @SerializedName("fn")
  @SerializedToken(1)
  let Firstname :String

  @SerializedName("ln")
  @SerializedToken(2)
  let Lastname :String

  @SerializedName("bd")
  @SerializedToken(3)
  @SerializeAs(TimeFormat.ISO8601)
  let Birthdate :Date? = None

  unique(Identifier)
  unique(Firstname, Lastname)

}
```

## Service

```
type PersonDB = trait {

  fun Add(let Person :Person, let Override :Boolean = True) :Boolean

  fun Get(let ID :UUID) :Person?

}

@Conforms("https://example.org/person-db.json", OpenRPC)
PersonDB

@SerializedName("pdb_Add")
PersonDB::Add
@SerializedName("per")
PersonDB::Add::Person
@SerializedName("ovr")
PersonDB::Add::Override

@SerializedName("pdb_Get")
PersonDB::Get
@SerializedName("id")
@SerializeAs(UUID.Stringify)
PersonDB::Get::ID
```

## Client

```
fun Main(let Env :Environment) = {

  let pdb :PersonDB = JRPC.Client("/dns/example.org/tcp/80/http")

  let uid = UUID.Random(Env.OS.Misc.RNG)

  pdb.Add(new {
    Identifier = uid
    Firstname  = "Jane"
    Lastname   = "Doe"
  })

  pdb.Get(uid)?.Firstname? apply Env.IO.WriteLine

}
```

## Server

```
fun Main(let Env : Environment) = {

  let pdb = object {
    extends PersonDB

    private let db = Mutable.HashTable[Person].Create()

    override fun Add(let Person :Person, let Override :Boolean) :Boolean = {
      return db.Add(Person, Override)
    }

    override fun Get(let ID :UUID) :Person? = {
      return db.Find(new {
        Identifier = ID
      })
    }
  }

  JRPC.Server("/tcp/80/http", pdb)

}
```
