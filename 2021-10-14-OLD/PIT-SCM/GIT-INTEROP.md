# Git-Interop?

```
$ pit init .
$ pit import git https://github.com/j-schoe/Ideas.git

$ echo "Hello World" > text.txt
$ echo "Added text.txt" > .pitmessage
$ pit add .
$ pit commit

$ pit export git --git-push https://github.com/j-schoe/Ideas.git
```

## ~/.pitparents?file-svn=1
```
<cid-of-parent-commit>
<cid-of-imported-git-commit>
```

## ~/.pitparents?file-svn=2
```
<cid-of-parent-commit>
<cid-of-exported-git-commit>
```
