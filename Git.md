# Git and Github: the basics

Here, we describe Git and Github and go over the basic commands and utilities that they allow.

**Git** is a command line program which keeps track of changes made to code or text documents you create.

**Github** is a website which provides remote Git repositories, and can help sync changes to code files.

Git and Github are powerful tools for tracking changes to code files in collaborative projects. For
example, each user in a collaboration can create their own branches of code files, and merge file
changes to a main once all collaborators agree on a change.

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
