# Workflow
## Empty Directory
```
Commands:
  $ mkdir my-repos
  $ cd my-repos
  
Changed Files:
  ~/my-repos/
  <directory>

Commits:
  <none>
```
## Initialization
```
Commands:
  $ pit init .

Changed Files:
  ~/my-repos/.pitlock
  <like the .git directory, just as a single file>
  <no tracked files>

  ~/my-repos/.pitmessage
  <empty>

  ~/my-repos/.pitsettings
  <contains configuration>

Commits:
  #0-Sign GenesisCommit {
    Unique      <random-string>
    Controllers <list-of-dids>
  }
  #0-Anch AnchorCommit {
    Parent #0-Sign
    <anchor data>
  }
```
## Create First File
```
Commands:
  $ echo "Hello World" > text.txt

Changed Files:
  ~/my-repos/text.txt
  "Hello World"

Commits:
  <none>
```
## Track First File
```
Commands:
  $ pit add .

Changed Files:
  ~/my-repos/.pitlock
  <tracked text.txt>

Commits:
  <none>
```
## Prepare First Commit
```
Commands:
  $ echo "Added text.txt" > .pitmessage

Changed Files:
  ~/my-repos/.pitmessage
  "Added text.txt"

Commits:
  <none>
```
## First Commit
```
Commands:
  $ pit commit

Changed Files:
  ~/my-repos/.pitlock
  <something prolly changed>
  
  ~/my-repos/.pitmessage
  <empty again>

Commits:
  #1-Sign SignedCommit {
    Parent    #0-Anch
    TreeType  "unixfsv1"
    TreeRoot  <cid-of-root-directory>
    <...>
  }
  #1-Anch AnchorCommit {
    Parent #1-Sign
    <anchor data>
  }
```


