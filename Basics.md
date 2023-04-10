## Commands

Below are some basic Unix commands and their descriptions.

cd /			 - Change to root directory

cd ~			 - Change to home directory

ls 			 - List the contents of the working directory.

pwd 			 - Print the Working Directory.

wc filename		 - Print word count of a file to the command line.

wc -l filename 		 - Adding the -l option to wc will print the number of lines.

head -n filename	 - Print the first n lines of a file. If -n not used, default is 10.

tail -n filename 	 - Print the last n lines of a file. If -n not used, default is 10.

less filename 		 - Scroll through large text file.

touch filename 		 - Easy way to create and empty file.

cat filename 		 - Cat is the concatenate command. When used with only one file argument,
 the contents of the file are printed to the terminal.

cat filename1 filename2  - Concatenate file2 to file1. If more than 2 files provided, concatenate to 
the first first in order of the arguments passed.

rm filename 		 - Remove/delete files or directories. Use -r option for directories.

rmdir Directoryname 	 - Remove/delete EMPTY directories.

### Output redirection and appending

'>' 			 - Output redirection. E.g 'cat file1.txt > file2.txt' redirects the output of 
'cat file1.txt' into another file called 'file2.txt'. CAUTION: If output redirection is used on an
existing file, the contents of the file will be replaced. See append below.

'>>' 			 - Append the output of a command. E.g. 'cat file1.txt >> file2.txt' redirects
the output of 'cat file1.txt' into 'file2.txt' while retaining the original contents of 'file2.txt'. 
