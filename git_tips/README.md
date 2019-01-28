# Git技巧

## Git最快速克隆一个仓库 - shallow repository

```
$ git clone --depth 1 git@github.com:gongpengjun/GPJDataDrivenTableView.git
```

```
$ git log --oneline
7585d7a (grafted, HEAD -> master, origin/master, origin/HEAD) add unavailable reason
```

### 将shallow repository转成正常的仓库

```
$ git fetch --unshallow
```

```
$ git log --oneline
7585d7a (HEAD -> master, origin/master, origin/HEAD) add unavailable reason
25e8edb (tag: v0.6.2) change GPJTableViewData's interface method to property
...
7c3db54 initial commit
```