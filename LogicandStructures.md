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

# Arrays

Arrays are created with parentheses (), where the elements are separated by a sapce. In UNIX, the first element in an array starts from 0 - the 'zeroth' element of the array. To call an element in an array, use curly braces. See example code below.

```
my_arr=(1 2 3 4)

echo ${my_arr[0]}

-----------------

1
```

To print **all elements in an array**, use the asterik symbol \* as shown below.

```
echo ${my_arr[*]}

-----------------

1 2 3 4

```

To print **a range of elements of an array**, see following example.

```
your_arr=({1..10})

echo ${your_arr[*]:3:10}

----------------
4 5 6 7 8 9 10
```

In the first line of code above, I used **brace expansion** to create a sequence of numbers from 1 to 10, and store these numbers as elements in an array. More description on using brace expansion is given in subsection below.

Next, I can specify the range of elements in the array that I'd like to echo. In this case, I specified to print the values of the elements starting at element 3 in the array, and ending at and including element 10 in the array.

To print **length of array**, include a pound symbol '#' as shown below:

```
echo ${#your_arr[*]}

---------------

10
```

## Brace Expansion

Use curly braces {..} to create a string sequence:

```
echo {0..9}
echo {a..e}
echo {A..Z}

----------------
0 1 2 3 4 5 6 7 8 9

a b c d e

A B C D E
```

One can put strings on either side to paste on to every 'element' in the sequence:

```
echo a{0..3}
------------
a0 a1 a2 a3
```

or combine multiple sequences together:

```
echo {0..3}{a..c}
-----------------
0a 1a 2a 3a 0b 1b 2b 3b 0c 1c 2c 3c

```
