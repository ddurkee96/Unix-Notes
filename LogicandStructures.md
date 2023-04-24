# Logic, Structures, Loops, and more...

In this file are notes concerning if/and logic, structures like arrays and loops, and functions in Unix.

# AND/OR logic

'&&' represents the 'and' symbol in Unix.

In an expression on a line in a program, the program directly to the right of '&&' will only run if the exit status of the program on the left of '&&' is successful - i.e. if the exit status is 0.

Exit status

1 : unsuccessful/false

0 : successfultrue

Consider the following example:

```
expr 1+3=4 && echo 'yes'
```

First, the command on the left of '&&' is evaluated to '0' or 'true', and as a result the program on the right of '&&' is evaluated. In this example, 'yes' is printed to the terminal. If the program on the left had read, for example '1+3=2', then the exit status would evaluate to '1' or 'false', and the program on the right of '&&' would not execute.

'||' represents the 'or' symbol in Unix

In contrast to the and symbol, the program to the right of '||' only executes if the exit status of the program on the left is something other than '0' (fails).

## Conditional Expressions

Conditional expressions, represented inside of double brackets '[[]]', are often used in conjunction with and/or logic. The conditional expression is evaluated, and has an exit status associated with it.

```
[[ -e <file> ]] && echo t || echo f
```

The code above uses the -e logical flag to test if 'file' exists, and returns 't' if it does, and 'f' if it does not according to the and/or logic. Can also use the -d logical flag for directories.

Below is a table that summarizes logical operators that are used in conditional expressions.

| logical operator | description                         |
| ---------------- | ----------------------------------- |
| -gt              | greater than                        |
| -ge              | greater than or equal to            |
| -eq              | equal to                            |
| -lt              | less than                           |
| -le              | less than or equal to               |
| -ne              | not equal to                        |
| -z               | length of string is 0               |
| -n               | length of string is not 0           |
| =~               | regular expression logical operator |

The regex logical operator is used, for example, in the following way to identify vowels:

```
[[ rhythms =~ [aeiou] ]]
```

Adding an exclamation mark '!' before a conditional expression (still inside of the double brackets) will invert the value pf the conditional expression.
