# git-cheat
my personal git cheatsheet - lazy (not git pro) dev take on using git

### What's in the queue 
waiting to be pushed (what was the last commit?)
```
$ git log -1
```

### Undo last commit 
(keep the changes) http://stackoverflow.com/questions/927358/how-do-you-undo-the-last-commit
```
$ git reset HEAD~1
```

### Delete a remote branch
(i.e. push [nothing] to : [branchname] )
```
git push origin :<branchName>
```

### Show the origin 
details of where the branch comes from;
```
git remote show origin

* remote origin
  Fetch URL: https://github.com/Snowcode/2014LaClusaz.git
  Push  URL: https://github.com/Snowcode/2014LaClusaz.git
  HEAD branch: master
  Remote branch:
    master tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (local out of date)
```
