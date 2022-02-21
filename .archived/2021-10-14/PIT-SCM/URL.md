# Pit URL

```
pit://<stream-id>[<path>][<query>][<fragment>]
```

## Query Parameters

| Parameter    |
|:-------------|
| `commit_cid` |
| `commit_svn` |
| `file_cid`   |
| `file_svn`   |

SVN...Serial Version Number

File at the first version of the repository:
```
pit://.../foo/text.txt?commit-svn=1
```

File at the first version of itself:
```
pit://.../foo/text.txt?file-svn=1
```

## DNS Link

```
pit://example.com/foo/text.txt
```

DNS:
```
_pit.example.com. IN URI "pit://<sid>"
```

