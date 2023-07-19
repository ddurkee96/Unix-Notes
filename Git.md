# Git and Github basics

Here, we describe Git and Github and go over the basic commands and utilities that they allow.

**Git** is a command line program which keeps track of changes made to code or text documents you create.

**Github** is a website which provides remote Git repositories, and can help sync changes to code files.

Git and Github are powerful tools for tracking changes to code files in collaborative projects. For
example, each user in a collaboration can create their own branches of code files, and merge file
changes to a main once all collaborators agree on a change.

## Git

```
git -- version
```

Use above command to check your version of git.

One needs to set up two environmental variables, but only need to do this once.

```
git config --global user.name "myName"
git config --global user.email myemail@gmail.com
```

### Creating a Git repository

To create a local Git repository,

1. Create a directory and cd into that directory.
2. run the command 'git init' on the command line to start tracking files inside that directory with Git.

### List of Git commands

| Command                       | Description                                                                                                                                                                                  |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| git status                    | Gives information about the status of the Git repository (commits, files to be committed, etc.)                                                                                              |
| git add file1 file2 ...       | Lets Git know that you want to track these files. The file is now 'staged'.                                                                                                                  |
| git rm --cached file          | Unstage (un-track) file                                                                                                                                                                      |
| git commit -m "short message" | Commit creation of files that have been added with "git add". Makes a milestone to indicate changes to repo. Must type brief message with notes about changes to the file since last commit. |
| git add -A                    | Stages all files in the directory                                                                                                                                                            |
| git help cmd                  | View manual for a command                                                                                                                                                                    |
| git log                       | View list of Git commands                                                                                                                                                                    |
| git diff file                 | Show differences between unstaged changes to a file compared to the last commit                                                                                                              |
| git checkout file             | Remove all changes made to a file since the last commit                                                                                                                                      |

### Ignoring files

.gitignore is a special file in which each line specifies files or groups of files to ignore.
For example, if one wants to ignore all jpg files, one can append the following to the .gitignore file:

```
echo "*.jpg" > .gitignore
```

### Branching

Branching allows one to work on and update files through a copy of a repository, without changing the 'master' copy directly.
Git can merge branches and changes together later.

| Command                | Description                                |
| ---------------------- | ------------------------------------------ |
| git branch             | list available branches in the repo        |
| git branch new-branch  | Create a new branch with name 'new-branch' |
| git branch -d branch   | Delete branch 'branch'                     |
| git checkout branch    | Switch to a different branch               |
| git checkout -b branch | Create new branch and switch to it         |

To merge two branches together, use the following commands. Usually, branch1 will be the 'master' branch.

```
git checkout branch1
git merge branch2
```

## Github

Below is a list of commands that are useful for communicating between local and online repos.

| Command                       | Description                                                                                                    |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------- |
| git remote                    | Lets one see which remote (on Github) repositories the local repo is connected to                              |
| git remote add origin URL.git | Add a Github remote repository to your local repository w/ name 'origin'                                       |
| git push -u origin master     | When setting up a remote repo, the first Git push looks like this. -u sets 'origin' as the default remote repo |
| git push                      | After first push, only need to use this command to update the online repo with changes made on the local repo  |

### Pull requests

Pulls requests are a request to 'git merge' facilitated by Github. To make a pull request:

1. Click 'new pull request' on the Github repository. 'base' is the branch that changes are being merged into.
   'compare' is the branch that has the changes.
2. Once merge is complete on the online repo, now we can update the local repo with the 'git pull' command.

### Forking

Forking creates a copy of a remote repo. This is useful if you identify a repository belonging to another Github user which you would like to have a local
copy.

To clone to a local repo,

1. Copy the URL of your forked repo
2. Use the command "git clone URL" (replace URL with the actual URL) to make a local clone of the online repo

The command "git remote -v" lists the origin of the online repo from the local repo.
The command "git show" shows commits in the repo.
