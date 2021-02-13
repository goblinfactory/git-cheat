# git-cheat
my personal git cheatsheet and favourites - lazy (not git pro) dev take on using git

### refresh a forked project from upstream master

For when I forked a project a long time ago, but now need to work on it. I can either delete and re-fork, or I can ...

```sh
git remote add upstream https://github.com/{github-username}/{dudes-cool-project}.git
git fetch upstream
git checkout master
git merge upstream/master
```

### update master without switching branch

If I am busy working on a branch and want to `git pull master` without switching branches so that I can easily merge a small change in master with `git merge master`. 

```sh
git fetch origin master:master
```

### pull in latest from remote origin

If I have forked someone's repo and want to merge in latest changes. Recipe is `git fetch --all {my-origin-name} {remote-branch}`

1. create a remote origin for the repo I forked from, for example; (hint, F7 in conemu shows command history)
2. pull the remote branch you want to update
3. merge in the changes

```sh
git remote add origin-proto https://github.com/AsynkronIT/protoactor-dotnet.git
git pull origin-proto dev
git checkout {mybranch}
git merge dev
```

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

### remove untracked files
```
$ git clean -f -n  \\ preview (using -n) to see what would be deleted
$ git clean -f     \\ to delete them.
```
sometimes if I need to undo all my changes I use `git checkout .` followed by `git clean -f -n` then `git clean -f`

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
### Accidentally pushed to master
This is a contentious item, how to undo someone's push to master, discussions around editing 'history'. If your team is small, and no-one else has pushed or pulled from master or cloned, then this was the simplest hack for me, where `AB12CD34` is the hash of the commit immediately prior the wrong commit. This makes `AB12CD34` the new head. 
```
git push origin+AB12CD34:master
```

### Preview merge before merging
? Im not convinced, (not tested yet) but dont think either of these will show you in advance that your merge will create conflicts? 
If that's the case then best to create a new test-branch from your current branch and do an experimental merge from master.
```
git log ..otherbranch  // two dots = list of changes that will be merged 
git log ...otherbranch // three dots = diff
```

### Resolve a merge conflict using 'theirs' or 'our' file

```
git checkout --theirs PATH/FILE
or
git checkout --ours PATH/FILE
```

see more : https://easyengine.io/tutorials/git/git-resolve-merge-conflicts/

### Undo git add for specific file
Before a local commit.
```
$ git reset <file>
```

### Push new local branch to origin

```
git push -u origin {my-branch-name}
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
# Some non GIT cheats

### wget clone website for offline

Shortcut below will start at url (foo) and recurse, converting all links to relative (e.g. CSS stylesheets), adding approp extensions, and downloading CSS stylesheets and images.

```
wget -mkEpnp http://example.org
```


### Some links I need to try out
Storing here for emergency access
- http://stackoverflow.com/questions/1670970/how-to-cherry-pick-multiple-commits
- https://gist.github.com/hofmannsven/6814451
- http://railsware.com/blog/2014/08/11/git-housekeeping-tutorial-clean-up-outdated-branches-in-local-and-remote-repositories/
- http://sethrobertson.github.io/GitFixUm/fixup.html
- http://www.gitguys.com/topics/git-diff/

### non GIT emergency links

- https://ardalis.com/configure-visual-studio-to-name-private-fields-with-underscore/
