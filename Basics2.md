# Unix Basics 2

## Functions, Source, Environmental/PATH variables, and more

This page will cover some more basic Unix concepts that did not quite fit into the other notebooks.
It will cover things like how to write functions, using the **source** command to use function definitions in bash scripts as command line prompts, what environmental variables are, shebangs, and more.
Thus, this will in some sense cover some remaining miscellaneous but important concepts to know for Unix.

## Writing functions

The following code snippet outlines the basic syntax for writing a function, usually inside of a bash script:

```
function [name of function] {
  #code here
}
```

General utilities/properties for functions:

- One can pass arguments to a bash script which will be used inside of a function - i.e $1, $2, $@.
- One must explicitly define local variables when writing functions, otherwise they are **global** variables by default.
  This is a very important thing to remember particularly if you have global and local variables with the same name.

Use the **source** command to use function definitions in bash scripts as command line commands.

### Source

For example, suppose one defines a function inside of a bash script 'ntmy.sh'.

```
#!/usr/bin/env bash
# File: ntmy.sh

function [ntmy] {
  echo "Nice to meet you $1"
}
```

Instead of writing commands in the shell script after we have defined it, we can use the **source** command to be able to access
the ntmy function from the command line:

```
source ntmy.sh

ntmy Dylan
ntmy Balthazar
---------------
## Nice to meet you Dylan
## Nice to meet you Balthazar
```

### Permissions in Unix

Associated with each file is a string of characters that define the read, write, and execute permissions for that file. The syntax looks like the following:

```
-rw-rw-r
```

We see that there are three segments in the above format. Each segment prescribes permissions for:

1. the owner of the file
2. the group that the file belongs to
3. everyone besides the owner and the group

The **chmod** command allows one to modify the permissions on a file:

```
chmod <arg1> <arg2>
```

arg1: a string, e.g. 'u+x', composed of three parts together in the following way:

1. specify set of users

- u : owner
- g : group
- o : everyone else
- a : all

2. add, remove, or set permission

- (+) : add
- (-) : remove
- (=) : set

3. specify what permission to change

- r : read
- w : write/edit
- x : execute

### Shebang

The 'shebang' begins with "#!" followed by the path to a program which executes the code in file.
For example, one will typically see the following shebang at the beginning of a Bash script in order to use Bash:

```
#!/usr/bin/env
```

### Environmental Variables

Environmental variables are variables that Bash creates, in which data about your current computing environment is stored. Thsese variables use all capital letters

For example:

```
echo $HOME
echo $PWD
```

#### $PATH

The PATH variable contains a sequence of paths separated by colons. When the shell starts, it searches these paths for executable files, and
makes these executable commands available in our shell. We can make our scripts available by adding a directory to the PATH variable. Bash scripts
that are in the directory that are executable can be used as commands.

To modify an environmental variable, use the **export** keyword:

```
export PATH=~/
```
