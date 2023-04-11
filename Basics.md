# Unix Basics

## Commands, Output, Command Customization, Makefile, and more

### Basic Commands

Below are some basic Unix commands and their descriptions.

| Command                 | Description                                                                                                                  |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| cd /                    | Change to root directory                                                                                                     |
| cd ~                    | Change to home directory                                                                                                     |
| ls                      | List the contents of the working directory.                                                                                  |
| pwd                     | Print the Working Directory.                                                                                                 |
| wc filename             | Print word count of a file to the command line.                                                                              |
| wc -l filename          | Adding the -l option to wc will print the number of lines.                                                                   |
| head -n filename        | Print the first n lines of a file. If -n not used, default is 10.                                                            |
| tail -n filename        | Print the last n lines of a file. If -n not used, default is 10.                                                             |
| less filename           | Scroll through large text file.                                                                                              |
| touch filename          | Easy way to create and empty file.                                                                                           |
| cat filename            | Cat is the concatenate command. When used with only one file argument, the contents of the file are printed to the terminal. |
| cat filename1 filename2 | Concatenate file2 to file1. If more than 2 files provided, concatenate to the first first in order of the arguments passed.  |
| rm filename             | Remove/delete files or directories. Use -r option for directories.                                                           |
| rmdir Directoryname     | Remove/delete EMPTY directories.                                                                                             |

### Searching: grep and awk

The 'grep' command is used to print lines that contain a specified string of characters that can also contain regular expressions. It is a powerful command to quickly search through text files and parse data files.

In my research, for example, I often run DFT-based molecular dynamics simulations in the software package called VASP (Vienna **ab **initio simulation package). One of the output files contains thermodynamic information including the pressure of the system at each trajectory in the simulation. To quickly obtain this information from the data file, I often use 'grep' in the following way:

'grep 'total pressure' OUTCAR > pressures.csv'

This command searches for lines, in a file named OUTCAR, which contain the string 'total pressure', and redirects the output to a file called 'pressures.csv'.

The 'awk' command is used to re-format files into output. One can provide a pattern/keyword to the argument of awk and print the lines in a file that match the pattern. Awk is powerful because one can use arithmetic, if/else logic, for/while loops, etc. and also split lines by a delimiter to print specific columns in a file.

awk options 'selection_criteria {action}' in > out

Example: awk '{print}' file

Prints file line-by-line.

awk '/match/ {print}' file

Print the lines with a pattern/keyword in place of match.

### Output redirection and appending

| Symbol | Description                                                                                                                                                                                                                                                |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| >      | Output redirection. E.g 'cat file1.txt > file2.txt' redirects the output of 'cat file1.txt' into another file called 'file2.txt'. CAUTION: If output redirection is used on an existing file, the contents of the file will be replaced. See append below. |
| >>     | Append the output of a command. E.g. 'cat file1.txt >> file2.txt' redirects the output of 'cat file1.txt' into 'file2.txt' while retaining the original contents of 'file2.txt'.                                                                           |

### Customization using alias

Use the \*alias command to create a shorter name for a command. To do this, one must make edits to the bash profile:

```
nano ~/.bash_profile

--------------------
alias edbp='nano ~/.bash_profile'

```

The above shows an example of opening the bash profile inside of the text editor *nano, and setting the shortcut command *edbp. The result is that instead of using the command 'nano ~/.bash_profile' to open up and edit the bash profile, one can simply use the shortcut 'edbp' directly on the command line.

Before one can use the shortcut, however, one must run the following command on the command line when new aliases are created:

```
source ~/.bash_profile
```

### Make and makefile

Makefile is a file that "describes the relationship between different files and programs." It can be used to generate files or documents automatically, for example.

The makefile is run using the command 'make' on the command line.

General format in makefile:

```
[target]: [dependencies]
  [commands]
```

Must have the tab underneath 'target' to start setting commands. Below is a simple example of a makefile that creates a README.md file, and also has a target called 'clean' which will remove the README file whenever the command 'make clean' is run.

```
readme.md:
  echo "Creating a README file" >> README.md

clean:
  rm README.md

```
