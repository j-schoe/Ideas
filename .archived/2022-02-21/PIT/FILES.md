# Files

## Variant 1

Generic File Syntax:
* Linebreak separated list of _entries_
  * No blank linkes between entries (only at the end of the file)
  * Whitespaces before the linebreak will be ignored
* Each _entry_ consists of multiple _elements_, separated by whitespaces
  * More than one whitespace will be ignored

### ~/.pitparents
```
pit+ipld:abcdefghijklmnopq pit+ceramic://abcdefghijklmnopq
pit+ipld:jklmnopqrstuvwxyz pit+ceramic://jklmnopqrstuvwxyz
git+ipld:0123456789abcdefg git+https://pit.example/example.git
```

Syntax:
* Generic File Syntax
* The first element is the mandatory URL to the commit
* The second element is the optional URL to the repository


### ~/.pitbranches
```
HEAD pit+ceramic://abcdefghjijklmnopq
SELF pit+ceramic://abcdefghjijklmnopq
main pit+ceramic://abcdefghjijklmnopq
feature/x000 pit+ceramic://789456123789456123
feature/x012 pit+ceramic://123456789123456789
```

Syntax:
* Generic File Syntax
* The first element is the mandatory name of the branch
* The second element is the optional URL to the repository


## Variant 2

Generally using an existing syntax; such as JSON, YAML, etc.

### ~/.pitparents
```yaml
- commit: pit+ipld:abcdefghijklmnopq
  repos:  pit+ceramic://abcdefghijklmnopq
- commit: pit+ipld:jklmnopqrstuvwxyz pit+ceramic://jklmnopqrstuvwxyz
  repos:  git+ipld:0123456789abcdefg git+https://pit.example/example.git
```

### ~/.pitbranches
```yaml
- name:  HEAD
  repos: pit+ceramic://abcdefghjijklmnopq
- name:  SELF
  repos: pit+ceramic://abcdefghjijklmnopq
- name:  main
  repos: pit+ceramic://abcdefghjijklmnopq
- name:  feature/x000
  repos: pit+ceramic://789456123789456123
- name:  feature/x012
  repos: pit+ceramic://123456789123456789
```

