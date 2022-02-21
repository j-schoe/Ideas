# Ink Files API

```
Ink.Files.EntryHandle      <:  Ink.Handle
Ink.Files.FileHandle       <:  Ink.Files.EntryHandle
Ink.Files.DirectoryHandle  <:  Ink.Files.EntryHandle
Ink.Files.FileSystemHandle
Ink.Files.FileSystemProvider
```
 
## FileSystemProvider

Specifies a kind of a filesystem.

```
::IsCaseSensitive  :Boolean
::IsCasePreserving :Boolean
::CanFilesAndDirectoriesHaveSameName :Boolean
::IsNameLegal(:String) :Boolean
::IsPathLegal(:String) :Boolean
```
