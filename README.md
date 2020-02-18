# Git & GitHub Masterclass - Summary
---
**Course:** https://www.udemy.com/course/git-and-github-masterclass/
**Author:** William Anderson
**Date Created &nbsp;:** 02/13/2020
**Date Last Rev:** 02/18/2020 

**TODO:**
Left off @ 4:15 Video #10

The following notes were written for use on the Windows 10 Platform, using the Git Bash Shell under `git version 2.23.0.windows.1`

## Git Basics
### git init
To initalize a directory as a git repository, type the command -
 `git init`
 This action only has to happen once, when a new directory is to be established as a repository.

### git add
Next, to do what is known as staging a file, type the command -
`git add [FILE_NAME]`
This should be done for each file in the directory to stage. Staging a file saves the current state of the file, so that when a commit happens, it is that state of the file that is commited.

### git commit
Finally, to commit the staged changes, use the command -
`git commit -m ["MESSAGE_GOES_HERE"]`
Always commit your changes with a descriptive message.
Once the files are commited, a new version now exists inside the repository.

### git diff
To see any differences between the local file and the currently staged/current version of the file, type the command - 
`git diff [FILE_NAME]`
By default, the currently staged file, if different from the local file, will be compared against. If there is no staged file, the local file will be compared against the current version in the repository. 

### git diff using IDs
To compare against different versions in the repository, you need the ID of the version to compare against. The commit ID is hashed *(SHA-1)*, and as such, will be a large hexidecimal value. 

`git diff [FIRST_SEVEN_OF_ID] -p`

This will show the differences between that version and the current version. 
**NOTE:** 
diff is simply showing the difference (*B - A*) between the two files. It is not tracing the revision chain and accounting for possible differences that exist between them, but are not reflected in either.

## Git Configurations
### git config --global [user<span></span>.name | user.email]
One of the first things to do when using git is to configure the global user<span></span>.name and user.email variables. These correspond to the name and email of the author of the commit.

To view the current git configuration, type the command - 
`git command --list`

If the variables are set, they should appear in the list, if not, set user<span></span>.name and user.email with the commands -
`git config --global user.name ["NAME_GOES_HERE"]`
`git config --global user.name [EMAIL_GOES_HERE]`

### git config --global core.editor
To configue the default editor that git uses, which is particularly useful for writing longform revisions, type the command -
`git config --global core.editor ["EDITOR_CODE -- wait"]`

The editor code is the associated shortcode for popular corresponding text editors, for example, this command sets the default git text editor to [Visual Studio Code](https://code.visualstudio.com/).
`git config --global core.editor "code --wait"`

By default, git uses the shell envrionment variable `VISUAL` or `EDITOR`, and if neither of those are set, falls back to `vi`.
