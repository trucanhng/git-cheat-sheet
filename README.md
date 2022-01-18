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
