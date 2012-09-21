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

git config --global
Stored in ~/.gitconfig or c:\Users\<name>\.gitconfig

### Repo Level

git config
Stored in .git/config in each repo

### How to configure

git config --global --list
git config --global user.name "UserNameHere"
git config --global user.email "email@host.com"
git config --global core.editor vim
git config --global help.autocorrect 1 // Fixes dodgy typing
git config --global color.ui auto
git config --global core.autocrlf input


      Windows -- true
      Mac / Linux -- input 

### Using

git add -u // Stage all modified files.

### What's Changed?

git diff sha..sha
git diff HEAD~1..HEAD // 1 commit back from the head
git diff HEAD~1..     // 1 commit back from the head
git diff --cached

### Adding Files

git add -A  // Add all untracking files
git add -U  // Stage all modified files

git commit -am "" // adds modified files at the same time.

### Committing Specific Files

git add <filename> // git status will show the file as tracked
git commit -m "description"

### Undoing Changes

### By File

git checkout <filename> // pulls the file from the HEAD version

### All

git reset --hard // Reset the working copy back to the head
git reset --soft HEAD~1 // Reset the working copy back to a sha
git reset --hard HEAD~1 // Discard the changes made in the commit

### Remove files -> Remove stay files from your working copy.

git clean -n // what would I clean?
git clean -f // Perform the action

### Showing Changes

git log --oneline | wc -l // How many commits made?
git log --online --graph  // Adds a graph down the left hand side
git log branch
git shortlog // Lists the authors in the changes and the commit messages
git shortlog -sne // numerical order decrease e email address

git show HEAD
git show <SHA>

### Showing Remotes

git remote
git remote -v // verbose

### Removing Remotes

git remote rm <name>

### Showing Branches

git branch
git branch -r // show remote branches

### Showing Tags (Stable points in the codebase)

git tag
git tag -v <tagname> // verify signed tag

### Adding a remote branch
You can add a remote branch (mutiple remotes) when someone sends a pull request to examine their changes.

git remote add <origin> <location>

### Getting Changes

git fetch // pull down the changes from a remote repo.  Does not incorporate changes
git fetch <remote>

git pull // short cut for git fetch, git merge
git pull <remotebranch> <localbranch> // If tracking has not been set.  Cloning does this automatically.

### Merging Changes

git merge <remote> // merge changes from remote branch into local branch

### Associate a branch with a remote branch
git branch --set-upstream master origin/master

### Adding Tags
Friendly name for a sha1 hash.

git tag <name> //unsigned tag
git tag v1.0

git tag -a message // with annotation

git tag -s v1.0 // automatically requires a message.  Passphrase required for signing key.

### Pushing Tags
By default git does not push tags

git push --tags

### Branches
Branches are labels on the sha commits

git branch <feature name> 
git branch <feature name> <sha>

git checkout -b <name> // Create and switch branch

git branch -d <name> // delete branch
git branch -D <name> // Force

### Recovering Branches
Commits are around for 30 days by default.

git reflog // Use this to locate the sha
git branch <name> sha

### Alias 

git config --global alias.lga "log --graph --oneline --all --decorate"

### Stashing
Store changes but do not apply.

git stash
git stash list
git stash apply 
git stash pop // apply the last stash

git stash drop // drop reference to a stash
git stash branch <x> // Create branch from stash, check it out and apply.

### Merging
git merge <branch to pull changes from>

git mergetool

(don't forget the working copy will contain .orig files, so simply delete them)

### Rebasing
Replay changes onto a branch.

go the branch to rebase from:

git rebase <targetbranchname>

If you can conficts when merging.  
  git mergetool // resolve the conflict
  git rebase --continue

### Cherry Pick Branch
git cherry-pick <sha> // select a single commit and apply it.

### Remote Branches
git push origin <branchname> // Push creating a new remote branch
git push origin <branchname>:<branchname> // Create new remote branch from remote branch

git push origin :<branchname> // Delete the remove branch

