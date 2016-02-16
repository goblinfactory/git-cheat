# git-cheat
my personal git cheatsheet - lazy (not git pro) dev take on using git

### Difference between my file and master
See the diff between a local file in a local branch and the latest version in master. (Do `git checkout master`, `git pull`, to make sure you have latest master, then `git checkout {yourbranch}` before doing a diff. 
```
git diff master {path to your file}
git diff master Utils/Demo.cs
```

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
### Abort merge with conflicts
How to abort a merge, if there are conflicts. (Only works if there are conflicts.)
```
git merge --abort
```

### Preview merge before merging
? Im not convinced, (not tested yet) but dont think either of these will show you in advance that your merge will create conflicts? 
If that's the case then best to create a new test-branch from your current branch and do an experimental merge from master.
```
git log ..otherbranch  // two dots = list of changes that will be merged 
git log ...otherbranch // three dots = diff
```

### Undo git add for specific file
Before a local commit.
```
$ git reset <file>
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
```
```
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

### See 'ahead' + 'behind'
See how many commits ahead and behind you are on a branch. (prints out {a} {b}) a=ahead, b=behind 
```
$ git rev-list --left-right --count master...my-branch
```
```
42      58
```
### Some links I need to try out
Storing here for emergency access
- http://stackoverflow.com/questions/1670970/how-to-cherry-pick-multiple-commits
- https://gist.github.com/hofmannsven/6814451
- http://railsware.com/blog/2014/08/11/git-housekeeping-tutorial-clean-up-outdated-branches-in-local-and-remote-repositories/
- http://sethrobertson.github.io/GitFixUm/fixup.html
- http://www.gitguys.com/topics/git-diff/
