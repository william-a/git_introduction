# Git & GitHub Masterclass - Summary
---
**Course:** https://www.udemy.com/course/git-and-github-masterclass/

**Author:** William Anderson

**Date Created :** 02/13/2020

**Date Last Rev:** 02/18/2020 

**TODO:** On Wed./Thurs. pickup at git status, finalize section about bringing it all together, then start on branches and merging.

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

## Git - Local & Remote
This guide is written under the assumption that the user is also using GitHub in conjunction with Git. If not, please follow the directions of the chosen repository. The changes to these commands should be minimal except where obvious.


### git remote
`git remote` is a command to create, view, and delete connections to other repos. It allows for simple aliasing of otherwise verbose URLs. To add a remote, type the command -

 `git remote add [REMOTE_NAME] [URL]`

To remove a remote, type the command - 

`git remote rm [REMOTE_NAME]`

To rename a remote, type the command -

 `git remote rename [REMOTE_OLD_NAME] [REMOTE_NEW_NAME]`


#### **E.g.:**
---

Assume a GitHub profile name of  `your_name_here` and a repo of `your_repo_here`. To add a remote to the current .git directory, type the command -

`git remote add orggin https://github.com/your_name_here/your_repo_here.git`

To fix the misspelling of orggin to origin, type the commands -

`git remote rm orggin`
`git remote add origin https://github.com/your_name_here/your_repo_here.git`

or more simply - 

`git remote rename orggin origin`

---

To show the remote connections to this repository, type the command - 

`git remote`

To inspect a remote, type the command - 

`git remote show [REMOTE_NAME]`

The output will contain a list of branches associated with the remote and also the endpoints for fetching and pushing.

Remoting is the stage that comes before pushing *(if a remote is not associated with the repo)*, which is the final step in publishing local changes to remote.

### git push
`git push` is used to commit the changes from local to remote. This assumes that remote has been set up previously by `git remote`. Having done so, type the command - 

`git push`

This will upload the local state of the branch to the remote repo specified by the remote name. To be more specific, type the command -

`git push [REMOTE_NAME] [BRANCH_NAME]`

This specificity allows for more fine control over different remotes and branches.

### git pull
`git pull` is the counterpart to `git push`. Where `git push` commits changes from local to remote, `git pull` returns commited changes from remote to local. To use `git pull`, type the command -

`git pull`

With no arguments, the default behavior is equivalent to that of `git fetch origin HEAD` and `git merge HEAD` where `HEAD` is ref pointing to the current branch.

However, similar to that of `git push` for more specificity, type the command -
`git pull [REMOTE_NAME] [BRANCH_NAME]`

This will download the current state of remote/branch and merge it with your local/branch.

### git status
`git status` is a simple command to view which files are staged, unstaged, or untracked. `git status` does not show any information based on commit history, for that, use `git log`
