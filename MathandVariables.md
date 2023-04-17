## Arithmetic in Unix

Basic arithmetic symbols in bash:

Can use the command 'expr' to do basic arithmetic on the command line:

```
expr 5 \* 2     # Multiplication - outputs '10'
expr 5 / 2      # Integer division - outputs '2'
expr 5 % 2      # Modulo division - outputs the remainder of the integer divison '1'
expr 5 + 2      # Addition
expr 5 - 2      # Subtraction
```

Note that Bash does integer division, and rounds _down_ Note the the spaces between the digits in each expression.

To do more sophisticated arithmetic using floating numbers, one uses the **bench calculator**:

```
bc -l
```

The -l flag defines the standard math library.

Typically, one can pass a mathematical expression as an argument to the **echo** command, and pipe that in to the bench calculator.

```
echo '6.2 * 3.14' | bc -l
```

Note that the spaces between each number on either side of the mathematical symbol are not important when doing math this way.
