# Git Cheat Sheet
---
---
### Installation
##### Windows
https://git-scm.com/download/win
##### MacOS
https://git-scm.com/download/mac
##### Linux/Unix
https://git-scm.com/download/linux

---
### Git GUI Clients
##### Windows
https://git-scm.com/download/gui/windows
##### MacOS
https://git-scm.com/download/gui/mac
##### Linux
https://git-scm.com/download/gui/linux
##### Android
https://git-scm.com/download/gui/android
##### iOS
https://git-scm.com/download/gui/ios

---
### Configuration
Set the name that you want Git to use for all of your Git work
```
$ git config --global user.name "<your-name>"
```

Retrieve your Git user name
```
$ git config user.name
```

Set the email address that you want Git to use for all of your Git work
```
$ git config --global user.email <your-email-address>
```

Retrieve your Git email address
```
$ git config user.email
```

Set the default text editor to create and edit commit and tag messages
```
$ git config --global core.editor <text-editor-name>
```
[List of commands for specific text editors.](https://git-scm.com/book/en/v2/Appendix-C%3A-Git-Commands-Setup-and-Config)

Retrieve the text editor used by Git
```
$ git config core.editor
```

---
### Repository Initialization
Start a new Git repository for your project (make sure you are in the top-level folder containing your project)
```
$ git init
```
Once the command is executed, a `.git` directory is created (run `ls -a` to check it out).

---
### Adding and Committing
Show the working directory status
```
$ git status
```

Take a snapshot of the content of your working directory to prepare for the next commit. In other words, add the changes that have been made since your last commit to the index or staging area
+ Stage one or multiple new or modified files
  ```
   $ git add <file1_name> <file2_name> ...
  ```
+ Stage all changes at once
  ```
   $ git add .
  ```

Record the snapshot taken with `git add` to the Git repository
+ Commit message passed to the command
  ```
   $ git commit -m "<commit-message>"
  ```
+ Commit message entered in the default text editor (default text editor can be configured using `git config`)
  ```
   $ git commit
  ```

Redo the previous commit, either to include additional files or to fix the commit message. If you want to add additional files, run `git add` to stage them first.
```
$ git commit --amend
```

Print commit logs
+ In complete details
  ```
   $ git log
  ```
+ In one-line format
  ```
   $ git log --oneline
  ```

---
### Branching and Merging
List the existing branches in your repository.  The `*` in front of the branch name indicates the branch you are currently on.
```
$ git branch
```

Create a new branch (but not switching to that branch)
```
$ git branch <branch-name>
```

Delete a branch.  Note that you cannot delete the branch you are currently on.
```
$ git branch -d <branch-name>
```

Force delete a branch regardless of its merged status or whether it points to a valid commit
```
$ git branch -D <branch-name>
```

Rename the branch that you are currently on
```
$ git branch -m <new-branch-name>
```

Force rename the branch even the new branch name already exists
```
$ git branch -M <new-branch-name>
```

Switch to another branch
```
$ git switch <branch-name>
```

Another way of switching branches
```
$ git checkout <branch-name>
```

Create a new branch and switch to it at the same time
```
$ git switch -c <branch-name>
```

Merge the changes from one branch into another branch.  The receiving branch is the branch that you are currently on (HEAD points to this branch reference).  So before merging, make sure you run either `git switch` or `git checkout` to switch to the branch into which you want to incorporate the changes.
```
$ git merge <branch-name>
```

---
### Rebasing
Rebase the branch you are currently on (branch-1) onto the specified branch (branch-2):  create a new commit for each branch-1's commit, and apply these commits at the tip of branch-2 (the commit history is re-written).
```
$ git rebase <branch-2-name>
```

Clean up the commit history in interactive rebase mode
```
$ git rebase -i
```

---
### Tagging
List existing tags
```
$ git tag
```

Create a lightweight tag for the most recent commit
```
$ git tag <tag-name>
```

Create an annotated tag for the most recent commit
```
$ git tag -a <tag-name>
```

Tag the specified commit
```
$ git tag <tag-name> <commit-hash>
```
```
$ git tag -a <tag-name> <commit-hash>
```

Display the meta data of a tag
```
$ git show <tag-name>
```

---
### Comparing Changes
Show changes between two branches
```
$ git diff <branch-1>..<branch-2>
```

Show changes between two commits
```
$ git diff <commit-hash-1>..<commit-hash-2>
```

Show all unstaged changes (show the content differences between the working directory and the index)
```
$ git diff
```

Show all staged changes (show the content differences between the last commit and the index)
```
$ git diff --staged
```
or
```
$ git diff --cached
```

Show staged changes within a file
```
$ git diff --staged <file-name>
```

Show all unstaged and staged changes since the last commit
```
$ git diff HEAD
```

Show unstaged and staged changes within a file
```
$ git diff HEAD <file-name>
```

---
### Stashing
Save all the uncommitted changes (both unstaged and staged) and revert the working directory to where it was before these changes were made
```
$ git stash
```
or
```
$ git stash save
```

Remove the most recently created stash from the stash list and apply it on top of the current working directory
```
$ git stash pop
```

Apply the most recently created stash on top of the current working directory, but without removing the stash from the stash list.  This command is useful if you want to apply the same stash to multiple branches.
```
$ git stash apply
```

Apply a specific stash with the given stash name on top of the current working directory.  Stashes are named following the useful reflog (reference log) syntax with stash@{0} specifying the most recently created stash, stash@{1} specifying the stash created before stash@{0}, and so on.
```
$ git stash apply <stash-name>
```

Show the stash list
```
$ git stash list
```

Delete a stash
```
$ git stash drop <stash-name>
```

Remove all stashes
```
$ git stash clear
```

---
### Restoring, Resetting, and Reverting
Restore a file's content to what it looked like in the last commit (all changes made to this file since the last commit are discarded)
```
$ git restore <file-name>
```

Restore a file's content to what it looked like in the specified commit.  You can reference a commit by using its hash or using the HEAD reference.
```
$ git restore --source <commit-hash> <file-name>
```

Reset the repository to a specific commit.  All commits made after the specified commit are removed, but the changes in those commits are still in your working directory.
```
$ git reset <commit-hash>
```

Reset the repository to a specific commit.  All commits made after the specified commit and the changes in those commits are removed.
```
$ git reset --hard <commit-hash>
```

Reset the repository to what it looked in the specified commit (same as `git reset`), but by creating a new commit that records the reverting (the tip of the branch is moved forwards) instead of by removing unwanted commits (the tip of the branch is moved backwards) (different from `git reset`).
```
$ git revert <commit-hash>
```

---
### Working With Remotes
Clone a remote repository hosted on a Git repo hosting platform such as Github
```
$ git clone <remote-repo-url>
```

List all existing remotes associated with your local repository
```
$ git remote -v
```

Add a new remote for your local repository: <remote-name> is the label you give to this remote.
```
$ git remote add <remote-name> <remote-url>
```

Rename a remote
```
$ git remote rename <old-name> <new-name>
```

Remove a remote
```
$ git remote remove <remote-name>
```

Push your work in a branch up to a remote

+ Push to the same remote branch
  ```
   $ git push <remote-name> <branch-name>
  ```
+ Push to a different remote branch
  ```
   $ git push <remote-name> <local-branch-name>:<remote-branch-name>
  ```

Set the upstream of a local branch (establish a connection between your local branch and the remote's branch of the same name so that whenever you want to push your changes in the local branch up to the remote's, you only need to run `git push`.
```
$ git push -u <remote-name> <branch-name>
```

List all remote branches
```
$ git branch -r
```

Get changes from a remote repository without incorporating those changes into the working directory

+ From the default `origin` remote
  ```
   $ git fetch
  ```
+ From any remote
  ```
   $ git fetch <remote-name>
  ```
+ From a specific branch
  ```
   $ git fetch <remote-name> <remote-branch-name>
  ```

Get changes from a remote repository and incorporating those changes into the working directory.  Make sure you are on the branch into which you want the changes to be merged.
```
$ git pull <remote-name> <remote-branch-name>
```

---
