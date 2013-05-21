Git
===

Configuration
----------------

### System Level

```bash
git config --system
```

Stored in /etc/gitconfig or Program Files\Git\etcgitconfig

### User Level

```bash
git config --global
```
Stored in ~/.gitconfig or c:\Users\<name>\.gitconfig

### Repo Level

```bash
git config
```

Stored in .git/config in each repo

### How to configure

```bash
git config --global --list
```

```bash
git config --global user.name "UserNameHere"
```

```bash
git config --global user.email "email@host.com"
```

```bash
git config --global core.editor "subl -w"
```

```bash
git config --global help.autocorrect 1
```
Fixes dodgy typing

```bash
git config --global color.ui auto
```

```bash
git config --global core.autocrlf input
```

- Windows     = true
- Mac / Linux = input

### Using

```bash
git add -u
```

Stage all modified files.

### What's Changed?

```bash
git diff sha..sha
```

```bash
git diff HEAD~1..HEAD
```
1 commit back from the head

```bash
git diff HEAD~1..
```
1 commit back from the head

```bash
git diff --cached
```

### Adding Files

```bash
git add -A
```
Add all untracking files

```bash
git add -U
```
Stage all modified files

```bash
git commit -am ""
```
adds modified files at the same time

### Committing Specific Files

```bash
git add <filename>
git commit -m "description"
```
git status will show the file as tracked

### Undoing Changes

### By File

```bash
git checkout <filename>
```
pulls the file from the HEAD version

### All

```bash
git reset --hard
```
Reset the working copy back to the head

```bash
git reset --soft HEAD~1
```
Reset the working copy back to a sha

```bash
git reset --hard HEAD~1
```
Discard the changes made in the commit

Amend the last commit message

```bash
git commit --amend
```

### By Commit
```bash
git reset --hard SHA
```

To remove from github
```bash
git push [remote] +[branch]
```

### Remove files -> Remove stay files from your working copy.

```bash
git clean -n
```
What would I clean?

```bash
git clean -f
```
Perform the action

### Showing Changes

```bash
git log --oneline | wc -l
```
How many commits made?

```bash
git log --online --graph
```
Adds a graph down the left hand side

```bash
git log branch
```

```bash
git shortlog

```
Lists the authors in the changes and the commit messages

```bash
git shortlog -sne
```
numerical order decrease e email address

```bash
git show HEAD
```

```bash
git show <SHA>
```

### Showing Remotes

```bash
git remote
```

```bash
git remote -v
```
verbose

### Removing Remotes

```bash
git remote rm <name>
```

### Showing Branches

```bash
git branch
```

```bash
git branch -r
```
show remote branches

### Showing Tags (Stable points in the codebase)

```bash
git tag
```

```bash
git tag -v <tagname>
```
verify signed tag

### Adding a remote branch
You can add a remote branch (mutiple remotes) when someone sends a pull request to examine their changes.

```bash
git remote add <origin> <location>
```

### Getting Changes

```bash
git fetch
```
Pull down the changes from a remote repo.  Does not incorporate changes

```bash
git fetch <remote>
```

```bash
git pull
```
Short cut for git fetch, git merge

```bash
git pull <remotebranch> <localbranch>
```
If tracking has not been set.  Cloning does this automatically

### Merging Changes
```bash
git merge <remote>
```
merge changes from remote branch into local branch

### Associate a branch with a remote branch
```bash
git branch --set-upstream master origin/master
```
### Adding Tags
Friendly name for a sha1 hash.
```bash
git tag <name>
```
unsigned tag

```bash
git tag v1.0
```

```bash
git tag -a message
```
with annotation

```bash
git tag -s v1.0
```
Automatically requires a message.  Passphrase required for signing key.

### Pushing Tags
By default git does not push tags

```bash
git push --tags
```
### Branches
Branches are labels on the sha commits

```bash
git branch <feature name>
```

```bash
git branch <feature name> <sha>
```

```bash
git checkout -b <name>
```
Create and switch branch

```bash
git branch -d <name>
```
delete branch

```bash
git branch -D <name>
```
Force

### Recovering Branches
Commits are around for 30 days by default.

```bash
git reflog
```
Use this to locate the sha

```bash
git branch <name> sha
```
### Alias

```bash
git config --global alias.lga "log --graph --oneline --all --decorate"
```

### Stashing
Store changes but do not apply.

```bash
git stash
```

```bash
git stash list
```

```bash
git stash apply
```

```bash
git stash pop
```
apply the last stash

```bash
git stash drop
```
drop reference to a stash

```bash
git stash branch <x>
```
Create branch from stash, check it out and apply

### Merging

```bash
git merge <branch to pull changes from>
```

```bash
git mergetool
```
(don't forget the working copy will contain .orig files, so simply delete them)

### Rebasing
Replay changes onto a branch.

go the branch to rebase from:

```bash
git rebase <targetbranchname>
```
If you can conficts when merging.

```bash
git mergetool
```
Resolve the conflict

```bash
git rebase --continue
```

Squash mutiple commits into a single commit

```bash
git rebase -i
```

```bash
git rebase -i HEAD~n
```

* 1 pick c196b54 Feature8
* 2 squash 7787a9c Feature7
* 3 squash f771621 Master in the house

You must have root commit to go back to.

```bash
git cherry-pick <sha>
```
select a single commit and apply it.

### Remote Branches
```bash
git push origin <branchname>
```
Push creating a new remote branch

```bash
git push origin <branchname>:<branchname>
```
Create new remote branch from remote branch

```bash
git push origin :<branchname>
```
Delete the remove branch

### Configuring Merge Tool
http://www.andymcintosh.com/?p=33
