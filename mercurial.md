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

### Show Revision ID and Author of last commit
```bash
vbe$ hg log --limit 1 --template "{rev} (by {author} )"
4381
```
