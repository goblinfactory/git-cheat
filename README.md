# git-cheat
my personal git cheatsheet - lazy (not git pro) dev take on using git

See what's waiting to be pushed (what was the last commit?)
```
$ git log -1
```

Undo last commit (keep the changes) 
```
$ git reset HEAD~1
```
http://stackoverflow.com/questions/927358/how-do-you-undo-the-last-commit

Delete a remote branch. (i.e. push [nothing] to : <something>)
```
git push origin :<branchName>
```
