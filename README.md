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
