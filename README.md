# Git & GitHub - An Introduction
**Author:** William Anderson

**Date Created :** 02/13/2020

**Date Last Rev:** 02/28/2020 

---
<!--  ✅🔲  -->
### **Working Objective List:**
####  **Week of 03/01/2020**
- [ ] Git - Git Bash Shell - 🔲
- [X] Git - Global Configurations - ✅✅✅
- [X] Git - Repository Initialization  - ✅✅
- [X] Git - Basics: - ✅✅✅✅
- [X] Git - Basic Workflow: ✅✅✅
- [ ] Git - Intermediary - 🔲🔲🔲🔲
- [ ] Git - Workflow - Intermediary Case: 🔲
- [ ] Git - Advanced - 🔲🔲🔲🔲🔲
- [ ] Git - Workflow - Advanced Case: 🔲
- [ ] Git - Bringing It All Together - 🔲🔲🔲🔲🔲



The following notes were written for use on the Windows 10 Platform, using the Git Bash Shell under:

`git version 2.23.0.windows.1`

## Git - Git Bash Shell

"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."

## Git - Global Configurations
Before using Git, it's important to first configure some personalized settings. A little time here can save a lot of frustration, not only for you, but also your collaborators. Some of the most important configurations are as follows:

### git config --list
If you ever want to check your current configuration settings, type the command -

```
git config --list
```

This will show you the current configuration relative to the directory you're in. If the directory does not contain a `.git` sub-directory, then it will show you your global Git settings. If you are in a directory with a `.git` sub-directory, then it will also show any settings specific to that repo, such as the location of `remote.origin.url`.

### git config --global [user<span></span>.name | user.email]

Probably the most important global settings, `user.name` and `user.email` is your identity to your collaborators. This information is immutably baked into commits and is important for being able to trace commit history through a single collaborator, as well as contact them. To set these global variables, type the command -

```
git config --global user.name ["NAME_GOES_HERE"]
git config --global user.email [EMAIL_GOES_HERE]
```

If you want to mask the global setting for an individual project, remove the `--global` argument when in that project's directory and it will create a local value for it. This masking is also supported for various other global settings.

### git config --global core.editor
Commonly, you will need to use a text editor with Git. It is particularly necessary when writing larger bodies of text for version management, such as a commit's changelog. To configure the default editor that Git uses, type the command -

```
git config --global core.editor ["EDITOR_CODE" | "EDITOR_PATH"]
```

Whereby the editor code is the associated shortcode for the text editor of your choice.
For a listing of popular text editor codes, visit [Associating text editors with Git](https://help.github.com/en/github/using-git/associating-text-editors-with-git).

## Git - Repositories
Once some basic configurations are set, you're ready to begin using Git. However, before you can use it, you must first have a `.git` directory in the project folder you want Git to manage. There are two ways of doing this, one is `git init` and the other is `git clone`.

### git init
If you have an existing project that you want Git to manage, navigate to the project directory and type the command - 

```
git init
```

`git init` does a number of actions, such as set environment variables and sets `HEAD` to the newly created master branch. `git init` is the appropriate command to use to manage a project that is not yet under the management of Git. This action only has to be done once, at the start of the project or when Git is to be used to manage an already existing **local** project.

### git clone
`git clone` is like `git init`, but for an already existing project under the supervision of Git. Typically, this project is hosted on a platform like GitHub or BitBucket. `git clone` will get the individual who uses it a *working copy*. This copy contains all of the associated files for the project, as well as any configuration settings that are not specific to a local machine. To clone an existing repo, navigate to the directory to clone the repo under, and type the command -

```
git clone [REPO_URL]
```

Much like `git init`, `git clone` is typically a one time action used to initially setup a project to manage.

## Git - Basics: 
Git has a simplistic working schema. `add`, `commit`, and `push` compose most the vast majority of actions you will need to perform. This initial section will cover the workflow under the guise of a single-user. Later sections will expand upon this and encompass the scope of the development process.

### git add
By default, Git does not automatically track all files in the directory it supervises. If you want to track the history of a file, you have to add that file. To add a file for Git to track, type the command -

```
git add [FILE_NAME]
```

You have to add each file you want to track. If you want to track all files, you can type the command -

```
git add .
```

`git add` works by tracking the state of the file at the time of its addition. That is to say, it only sees what the file looks like up to that point, and no further. Any modifications made to the file after the `git add` command is issued will not be tracked. 

### git commit
After adding the files, they are indexed as a set of changes to be made, but haven't yet been "saved". To "save" the current state of the project and generate a referenceable object, you need to commit those changes. To do so, type the command - 

```
git commit
```
By default, this command will open the text editor associated with Git and prompt you to supply a commit message. You should always supply a meaningful commit message. If you find yourself having to write very verbose commit messages, let that be an indicator that your commits encompass too many changes between them. However, if you wish to skip the step of having to type your message in a text editor, you can type the command -

```
git commit -m "[MESSAGE_GOES_HERE]"
```

This will allow you to commit with a message attached through the terminal without going through the intermediary text editor. For small changes, this is quick and effective.

### git push
`git push` is used to upload your local repo to a remote repo. For the purposes of this tutorial, that remote repo is GitHub. However, because it is typical to only ever reference remote by a local variable, this method is typically the same, regardless of the chosen remote repo. To "push" the commit history to a remote repo, type the command -

```
git push [REMOTE_NAME] [BRANCH_NAME]
```

For the vast majority of use cases, `[REMOTE]` will be `origin`. The only exception is if you want to push changes to multiple repositories and have manually configured multiple remotes, shown by the command, `git remote`.

With that sequence of `add`, `commit`, and `push`, the vast majority of your Git workflow is complete.

## Git - Basic Workflow:

### Example #1 - First Time Git Repo: 
```
# Make a project directory
mkdir my_project_directory

# Go to that directory
cd my_project_directory

# Init the directory as a git repo
git init

# Create the README.md file
echo Hello World > README.md

# Stage README.md
git add README.md

# Commit the changes
git commit -m "Init Repo & Created README.md"
```

### Example #2 - Committing Changes To Local & Remote Repos [remote@ origin/master]:
```
git add hello_worlds.c
git commit -m "Changed hello_world.c to hello_worlds.c"
git push origin master

# ...more changes are made

git add hello_worlds.c
git commit -m "Added support for multiple worlds to hello_worlds.c"
git push origin master
```

### Example #3 - Clone A Repo
```
cd my_project_folder
git clone https://www.github.com/github_user_name/github_repo_name
```




# PICK UP HERE

### git reset

If `git add` stages your files, then `git reset` will un-stage them for you. There is quite a bit more going on under the hood with `git reset`, such as the ability to operate on the multiple management mechanisms Git (Commit Tree, Staging Index, Working Directory), but for the purposes of this simple use case, think of it as your un-staging tool.

To un-stage a file at the current commit, type the command -

```
git reset [FILE_NAME]
```
Similarly to add, you can un-stage all files by typing the command -
```
git reset
```
---

### 1.3.5. git diff
To see any differences between the local file and the currently staged/current version of the file, type the command - 

`git diff [FILE_NAME]`

By default, the currently staged file, if different from the local file, will be compared against. If there is no staged file, the local file will be compared against the current version in the repository. 

### 1.3.6. git diff using IDs
To compare against different versions in the repository, you need the ID of the version to compare against. The commit ID is hashed *(SHA-1)*, and as such, will be a large hexadecimal value. 

`git diff [FIRST_SEVEN_OF_ID] -p`

This will show the differences between that version and the current version. 
**NOTE:** 
diff is simply showing the difference (*B - A*) between the two files. It is not tracing the revision chain and accounting for possible differences that exist between them, but are not reflected in either.

## 1.4. Git - Local & Remote
This guide is written under the assumption that the user is also using GitHub in conjunction with Git. If not, please follow the directions of the chosen repository. The changes to these commands should be minimal except where obvious.


### 1.4.1. git remote
`git remote` is a command to create, view, and delete connections to other repos. It allows for simple aliasing of otherwise verbose URLs. To add a remote, type the command -

 `git remote add [REMOTE_NAME] [URL]`

To remove a remote, type the command - 

`git remote rm [REMOTE_NAME]`

To rename a remote, type the command -

 `git remote rename [REMOTE_OLD_NAME] [REMOTE_NEW_NAME]`


#### 1.4.1.1. **E.g.:**
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

### 1.4.2. git push
`git push` is used to commit the changes from local to remote. This assumes that remote has been set up previously by `git remote`. Having done so, type the command - 

`git push`

This will upload the local state of the branch to the remote repo specified by the remote name. To be more specific, type the command -

`git push [REMOTE_NAME] [BRANCH_NAME]`

This specificity allows for more fine control over different remotes and branches.


### 1.4.3. git fetch
`git fetch` is used to update the history of a local repo to the state of a remote repo. To synchronize local to remote, type the command - 

`git fetch origin`

After fetching, local will now be informed as to its current state relative to remote. This step is typically done before a `git pull`. `git fetch` is not a merge, it is asks "What's been going on?"

### 1.4.4. git pull
`git pull` is the counterpart to `git push`. Where `git push` commits changes from local to remote, `git pull` returns committed changes from remote to local. To use `git pull`, type the command -

`git pull`

With no arguments, the default behavior is equivalent to that of `git fetch origin HEAD` and `git merge HEAD` where `HEAD` is ref pointing to the current branch.

However, similar to that of `git push` for more specificity, type the command -
`git pull [REMOTE_NAME] [BRANCH_NAME]`

This will download the current state of remote/branch and merge it with your local/branch.

### 1.4.5. git status
`git status` is a simple command to view which files are staged, un-staged, or un-tracked. `git status` does not show any information based on commit history, for that, use `git log`

## 1.5. Git - Putting It All Together #1

### 1.5.1. Ex # 1 - Creating a local repo
This command sequence will create a local repo
``` git
> mkdir my_new_folder
> cd my_new_folder
> git init
```

### 1.5.2. Ex # 2 - Adding a remote
```
> git remote add origin https://github.com/my_user_name/my_repo.git
```

### 1.5.3. Ex # 3 - Pushing local changes to remote
```
# After making the changes to be committed
> git add README.md
> git commit -m "Created README.md
> git push origin master
```

### 1.5.4. Ex # 4 - Change the remote repo
```
> git remote -v
> git remote rm origin
# To verify removal of old origin
> git remote -v
> git remote add origin https://github.com/my_user_name/my_repo.git
```



### 1.5.5. BRANCH NOTES
Currently, only experienced with the Master branch.

Branches solve the problem, how can we safely and stably add new code.

We could create another branch, such as `test` to deploy and test new changes to code before pushing them into the master branch, where they would be "live".

Another example could be a `dev` branch, where new features are developed before being sent to a `test` branch.

One thing branches allow for is a hierarchy for code changes to fall through, with each stage covering a different requirement.

The idea of branching extends further, and within each branch. For example, in the `dev` branch we may yet have even more branches, which tackle a specific function within a development process. Such as a branch for adding a very specific feature, or a branch for solving a particular bug. Then, once completed, these changes can be finalized and **MERGED** into the dev branch.

So, putting it all together. in the [master,test,dev] branch framework. Master typically only receives merges from test, test may have a few branches itself, but mostly it also only receives merges from dev. dev would be a branch that has multiple sub-branches where different features and bugs are being tackled.

Typically, smaller sub-branches, like feature or bug-fixing branches are deleted after being merged into their parent branch.

GitHub branches are known as pull requests

