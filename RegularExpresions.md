# Regular Expressions

Regular expressions are strings that define patterns to search for in text files. Being able to define regular expressions is a powerful and important method in Unix for parsing files. One often uses the 'grep' and 'awk' commands in Unix to search for and print specific strings in files.

### Metacharacters

Metacharacters are characters that can be used to represent other characters. These are very important for creating regular expression patterns.

| Metacharacter | Description                                                         |
| ------------- | ------------------------------------------------------------------- |
| .             | can represent any character                                         |
| \w            | all "word" characters - letters, numbers, underscores               |
| \d            | all "number" characters - the set of digits [0-9]                   |
| \s            | all "space" characters                                              |
| $             | follows a character to match that character at the end of a line    |
| ^             | precedes a character to match that character at the start of a line |
| \n            | newline character                                                   |

One can use the uppercase version (\W, \D, \S ) of the above to represent the \*\*inverse sets. The \W metacharacter would thus represent everything besides word characters.

### Quantifiers

Quantifiers are characters that specify the quantity of the preceding character set to search for. For example, the regular expression '\d+' searches for one or more number characters.

| Quantifier | Description                                                                            |
| ---------- | -------------------------------------------------------------------------------------- |
| +          | one or more of preceding expression                                                    |
| \*         | zero or more of preceding expression                                                   |
| {n}        | specify exact number (replace n with an integer) of occurances of preceding expression |
| ?          | zero or one of preceding expression                                                    |
| &#124;     | either the previous or the following expression                                        |

### Character sets

Character sets can be specified by square brackets, and character groups can be specified by parantheses. Brackets match any of the specified characters and charcter ranges contained inside, whereas character groups match exactly what is contained inside. See below for examples.

| Characters | Description                                                                                                                      |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------- |
| ( )        | create a capturing group. (a-z0-9) will capture occurances of 'a-z0-9' exactly, it does not capture the range                    |
| [ ]        | create a character set. [a-z0-9] will capture occurances of a character between a-z in the alphabet, OR a number between 0 and 9 |
| ^          | matches the compliment of a set - [^aeiou] will match consonants instead of vowels                                               |
