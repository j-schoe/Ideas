# External (Static) Resources In Let

## Example

```
let pref = <https://example.org/>

let personJson =
  <[pref:person.json]>
  as JsonSchema
  at <cid:...>

let personProto =
  <[pref:person.proto]>
  as ProtoIDL
  at <cid:...>

type Person = record {
  ...
  conforms personJson
  conforms personProto
}
```

## Syntax

```
// URI Literal
<some+uri:/>

// CURIE Literal
let variable = <some+uri:/>
<[variable:some-extension]>

// Marshall Annotation
<some+uri:/> as Marshaller

// Integrity Annotation
<some+uri:/> at <cid:-some-cid->
<some+uri:/> at CID"-some-cid-"
<some+uri:/> at ETag"some-etag"
```

## Typing

```
let res1 :StaticResource[Nothing] = <some+uri:/>
let res2 :StaticResource[Interface] = res1 as JsonSchema
```

## Housekeeping

```
let <https://example.com/> at <cid:1234567890>
let <https://example.org/> at <cid:0987654321>
```

## Attic

Store the desired versions of the resources in the
local project.

```
~/src/...
~/dist/...
~/attic/index.jsonld
~/attic/blocks/...
```


