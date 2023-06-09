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
