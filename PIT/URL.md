# Pit URL

## Repository level (dynamic) URL

* `"pit+" <Ceramic-URL> [<Path>] [<Query>] [<Fragment>]`

```
pit+ceramic://bzyahcewbtj4x7ip5legnfznufuopl4sg4knzc2cof6duas4b3q2fy6swua/foo/bar.html?commit=hl:f12e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855#fragment
\_________/   \_________________________________________________________/\___________/\____________________________________________________________________________/\_______/
S C H E M A      A U T H O R I T Y   ( R E P O S - S T R E A M - I D )      P A T H                                   Q U E R Y                                      H A S H
```

## Commit level (static) URL

* `"pit+" <IPLD-CID-URL> [<Path>] [<Query>] [<Fragment>]`
* `"pit+" <Hashlink-URL> [<Path>] [<Query>] [<Fragment>]`

```
 pit+ipld:boejmdgtzp6q72wim2ls3ili46xzenyu3sfue4l4hibfydxbulr5fnia/foo/bar.html?file=hl:f12e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855#fragment
 \_______/\______________________________________________________/\___________/\__________________________________________________________________________/\_______/
S C H E M A      A U T H O R I T Y   ( C O M M I T - C I D )         P A T H                                  Q U E R Y                                     H A S H
```

## Query Parameters

### References

* Commit Reference
  * `?commit=<Reference>`
* File Reference
  * `?file=<Reference>`
  * `?hl=<Multihash>[:<Metadata>]`

The _reference_ is a URL encoding the hash-value of the referencee.
* Encoded as a CID: `=ipld:<CID>`
* Encoded as a Hashlink: `=hl:<Multihash>[:<Metadata>]`


## Alternative: The Pit:// URL

```
pit://<Ceramic-Stream-ID>[...]
pit://<Domain-Name>[...]
```

Where the domain is resolved via the URL-RR, which must be a Pit-Repository-URL.

## Issues

**How to refer to the repository (not a file)?**
* A Pit-URL without a path and without a file reference.
* A Pit-URL without a file reference and with the path of an included Pit-Module.
* &rarr; Pit-Repository-URL &sub; Pit-URL
