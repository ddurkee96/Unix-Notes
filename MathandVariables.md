## Arithmetic in Unix

Basic arithmetic symbols in bash:

Can use the command 'expr' to do basic arithmetic:

```
expr 5 \* 2     # Multiplication - outputs '10'
expr 5 / 2      # Integer division - outputs '2'
expr 5 % 2      # Modulo division - outputs the remainder of the integer divison '1'
expr 5 + 2      # Addition
expr 5 - 2      # Subtraction
```

Note that Bash does integer division, and rounds _down_.

Also note the the spaces between the digits in each expression and the mathematical operators.

To do more sophisticated arithmetic using floating numbers, one uses the **bench calculator**:

```
bc -l
```

The -l flag defines the standard math library.

Typically, one can pass a mathematical expression as an argument to the **echo** command, and pipe that in to the bench calculator.

```
echo '6.2 * 3.14' | bc -l
```

Note that the spaces between each number on either side of the mathematical operator are not important when doing math this way.

## Variables in Unix

Values can be assigned to variables directly on the command line or in bash scripts:

```
my_var=1
```

Note from the above example that when assigning variable values, there are no spaces between the variable name, equal sign, and value.

The dollar sign '$' is inserted before a variable name to retrieve the value of that variable:

```
echo $my_var              # Outputs 1
```

### Variable assignment with arithmetic operators

Use the 'let' program to modify the value of a variable using arithmetic operators:

```
let my_var=$my_var+1      # Value of my_var changed from 1 to 2
```

As before, space are not allowed when assigning values to variables using 'let'.

### Command substitution

One can execute a command, and assign the output to a variable using '$(place commands here)

```
math_lines=$(cat math.sh | wc -l)
```

In the above example, a script file named 'math.sh' is concatenated, and the output piped into the word count command 'wc -l' which, with the inclusion of the -l flag, counts the number of lines in the file. Thus, the number of lines in the 'math.sh' script is stored into the variable 'math_lines'.
