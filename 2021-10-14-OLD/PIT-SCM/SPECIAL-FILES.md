# Special Files

## ~/.pitlock

Contains information of the current working copy.
Like the ".git" folder in git.
(The actual blocks are not stored locally.)

## ~/.pitsettings

General settings for repository.
Could contain things like:
* Which Filesystem? (UFSv1/v2?)
* Which Network? (clay, mainnet?)
* Which Anchor Chain? (ethereum?)
* Which Anchor Service?

## ~/.pitmessage

Contains the message for the next commit.

## ~/.pitparents

Contains the URLs of all merged commits.
Such as:
```
pit://<sid>?commit-cid=<cid>
pit://<sid>?commit-cid=<cid>
ipld:<git-cid>
```

## ~/.pitbranches

Contains the URLs of all repositories
whose are considered branches of this repository.
Such as:
```
MAIN  pit://<other-sid>
DEV   pit://<own-sid>
```

## ~/.pitmodules

Like ".gitmodules". Maybe a different syntax?
Such as:
```
./sub-project-1   pit://<sid>
./sub-project-2   pit://<sid>
./some-indi-file  ceramic://<sid>
```

## ~/**/.pitignore

Like ".gitignore" or ".npmignore".

## ~/**/(directory)/.pitkeep

Indicates that an empty directory should be kept.


