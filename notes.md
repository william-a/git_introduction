# Git & GitHub Masterclass - Notes
---
**Course:** https://www.udemy.com/course/git-and-github-masterclass/
**Author:** William Anderson
**Date Start:** 02/13/2020
**Date End:** 00/00/2020 

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
`git commit -m "MESSAGE GOES HERE"`
Always commit your changes with a descriptive message.
Once the files are commited, a new version now exists inside the repository.

### git diff
To see any changes that have been made since the last stage or commit, type the command -
`git diff [FILE_NAME]`
By default, the currently staged file, if different from the current version's commited file, will be compared against. If there is no staged file, the current commited version of the file we be compared against. 
