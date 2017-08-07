# Stuff about Mercurial & Tortoise
This page contains stuff about Mercurial & Tortoise i don't want to forget.
It may be useful for others...

## TortoiseHG & Filters
TortoiseHG supports filtering the list of shown branches.
You can specify the list of branches by using filter expressions:
* branch("development") -> display development-branch only
* branch("integration") -> display integration-branch only
* branch("development") or branch("feature/MY-AWESOME_FEATUREBRANCH") -> display development- and feature-branch at the same time

## Mercurial log output
### Show last commit only
```bash
vbe$ hg log --limit 1
changeset:   4381:3b078d825776
branch:      feature/change_color
tag:         tip
user:        Volker Benders
date:        Tue Jul 11 15:51:53 2017 +0200
summary:     Changed color to make the design guys happy.
```

### Show only Revision ID of last commit
```bash
vbe$ hg log --limit 1 --template "{rev} "
4381
```

### Show all commits to a branch
```bash
vbe$ hg log --only-branch "feature/RuleTheWorld"
changeset:   3401:3e00fbf6e81a
branch:      feature/RuleTheWorld
parent:      3391:d366ae39c5bb
user:        Linus Torvalds
date:        Wed Mar 14 16:08:34 1994 +0100
summary:     give birth to linux 1.0

changeset:   3391:d366ae39c5bb
branch:      feature/RuleTheWorld
parent:      3389:0ab4b23b1383
user:        Linus Torvaldds awesome mother
date:        Wed Dec 28 13:27:45 1969 +0100
summary:     give birth to linus benedict

<snip>
```
