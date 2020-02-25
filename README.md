# Git & GitHub Masterclass - Summary
---
**Course:** https://www.udemy.com/course/git-and-github-masterclass/

**Author:** William Anderson

**Date Created :** 02/13/2020

**Date Last Rev:** 02/25/2020 

**TODO: Wed/Thurs -** 
* Streamline the push/pull/status section (add fetch, etc..) +++
* Finish bringing it all together #1 - +++
* Watch branch section ++
* (Watch merge section) ++
* (Start on bringing it all together #2) +

The following notes were written for use on the Windows 10 Platform, using the Git Bash Shell under:

`git version 2.23.0.windows.1`

## Git - Git Bash Shell
### TODO

## Git - Configuration
Before using Git, it's important to first configure some personalized settings. A little time here can save a lot of frustration, not only for you, but also your collaborators. Some of the most important configurations are as follows:

### git config --global [user<span></span>.name | user.email]

Probably the most important global setting, `user.name` and `user.email` give information as to who gave a commit and how to contact them. To view the current git configuration, type the command - 

`git config --list`

This will show a combination of global and local configurations for the current directory. Different directories may have different configurations, such as a different `remote.origin.url` for different repositories, commonly called repos. To configure the global `user.name` and `user.email`, type the command -

`git config --global user.name ["NAME_GOES_HERE"]`

`git config --global user.email [EMAIL_GOES_HERE]`

### git config --global core.editor
Commonly, you will need to use a text editor with Git. It is particularly necessary when writing larger bodies of text for version management, such as a commit's changelog. To configure the default editor that git uses, type the command -

`git config --global core.editor ["EDITOR_CODE -- wait"]`

Whereby the editor code is the associated shortcode for the text editor of your choice.
For a listing of popular text editor codes, visit [Associating text editors with Git](https://help.github.com/en/github/using-git/associating-text-editors-with-git).

## Git - Basic Commands
Once some basic configurations are set, you're ready to begin using Git. However, before you can use it, you must first have a `.git` directory in the project folder you want Git to manage. There are two ways of doing this, one is `git init` and the other is `git clone`.

### git init
If you have an existing project that you want Git to manage, or you are the individual in your collaboratory group that is tasked with initially setting up the repo, navigate to the directory you want Git to manage, then, type the command - 

`git init`

`git init` does a number of actions, such as set environment variables and sets `HEAD` to the newly created master branch. `git init` is the appropriate command to use to manage a project that is not yet under the management of Git. This action only has to be done once, at the start of the project or when Git is to be used to manage an already existing **local** project.

### git clone
`git clone` is like `git init`, but for an already existing project in some centralized repo. Typically, this project is hosted on a platform like GitHub or BitBucket. `git clone` will give the individual who uses it a *working copy*. This copy contains all of the associated files for the project, as well as any configuration settings that are not specific to a local machine. To clone an existing repo, navigate to the directory to clone the repo under, and type the command -

`git clone [REPO_URL]`

Much like `git init`, `git clone` is typically a one time action used to initially setup a project to manage.

---

***PICK BACK HERE UP CHANGING THE VOICE TO YOU-IMPERATIVE***

---

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


### git fetch
`git fetch` is used to update the history of a local repo to the state of a remote repo. To syncronize local to remote, type the command - 

`git fetch origin`

After fetching, local will now be informed as to its current state relative to remote. This step is typically done before a `git pull`. `git fetch` is not a merge, it is asks "What's been going on?"

### git pull
`git pull` is the counterpart to `git push`. Where `git push` commits changes from local to remote, `git pull` returns commited changes from remote to local. To use `git pull`, type the command -

`git pull`

With no arguments, the default behavior is equivalent to that of `git fetch origin HEAD` and `git merge HEAD` where `HEAD` is ref pointing to the current branch.

However, similar to that of `git push` for more specificity, type the command -
`git pull [REMOTE_NAME] [BRANCH_NAME]`

This will download the current state of remote/branch and merge it with your local/branch.

### git status
`git status` is a simple command to view which files are staged, unstaged, or untracked. `git status` does not show any information based on commit history, for that, use `git log`

## Git - Putting It All Together #1

### Ex # 1 - Creating a local repo
This command sequence will create a local repo
> `mkdir my_new_folder`
> 
> `cd my_new_folder`
> 
> `git init`

### Ex # 2 - Adding a remote
> `git remote add origin https://github.com/my_user_name/my_repo.git`
> 
### Ex # 3 - Pushing local changes to remote
> `# After making the changes to be committed`
> 
> `git add README.md`
> 
> `git commit -m "Created README.md`
> 
> `git push origin master` 

### Ex # 4 - Change the remote repo
> `git remote -v`
> 
> `git remote rm origin`
> 
> `# To verify removal of old origin`
> 
> `git remote -v` 
> 
> `git remote add origin https://github.com/my_user_name/my_repo.git`



### BRANCH NOTES
Currently, only experienced with the Master branch.

Branches solve the problem, how can we safely and stably add new code.

We could create another branch, such as `test` to deploy and test new changes to code before pushing them into the master branch, where they would be "live".

Another example could be a `dev` branch, where new features are developed before being sent to a `test` branch.

One thing branches allow for is a hierarchy for code changes to fall through, with each stage covering a different requirement.

The idea of branching extends further, and within each branch. For example, in the `dev` branch we may yet have even more branches, which tackle a specific function within a development process. Such as a branch for adding a very specific feature, or a branch for solving a particular bug. Then, once completed, these changes can be finalized and **MERGED** into the dev branch.

So, putting it all together. in the [master,test,dev] branch framework. Master typically only receives merges from test, test may have a few branches itself, but mostly it also only receives merges from dev. dev would be a branch that has multiple sub-branches where different features and bugs are being tackled.

Typically, smaller sub-branches, like feature or bug-fixing branches are deleted after being merged into their parent branch.

GitHub branches are known as pull requests

