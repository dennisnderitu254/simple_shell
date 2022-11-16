Create a Simple Shell in C - Code Explanation 

0. Betty would be proud


1. Simple shell 0.1

Your Shell should:
Display a prompt and wait for the user to type a command. A command line always ends with a new line.
The prompt is displayed again each time a command has been executed.
The command lines are simple, no semicolons, no pipes, no redirections, or any other advanced features.
The command lines are made only of one word. No arguments will be passed to programs.
If an executable cannot be found, print an error message and display the prompt again.
Handle errors.
You have to handle the “end of file” condition (Ctrl+D)
File - shell_loop.c 
hsh - main shell loop
find_builtin - finds a builtin command
find_cmd - finds a command in PATH
Fork_cmd - forks an executable thread to run the command

2. Simple shell 0.2

Simple shell 0.1 +
Handle command lines with arguments
Parsing - where a string of commands – usually a program – is separated into more easily processed components, which are analyzed for correct syntax and then attached to tags that define each component. The computer can then process each program chunk and transform it into machine language
File - parser.c
is_cmd - determines if a file is an executable command
dup_chars - duplicates characters
find_path - finds this cmd in the PATH string 


3. Simple shell 0.3

Simple shell 0.2 +
Handle the PATH
fork must not be called if the command doesn’t exist
File - parser.c
find_path - finds this cmd in the PATH string 

 
4. Simple shell 0.4
 
Simple shell 0.3 +
Implement the exit built-in, that exits the shell
Usage: exit
You don’t have to handle any argument to the built-in exit
File - builtin.c
_myexit - exits the shell
 
5. Simple shell 1.0

Simple shell 0.4 +
Implement the env built-in, that prints the current environment
File - environ.c
_myenv  - prints the current environment
_getenv - gets the value of an environ variable
_mysetenv - Initialize a new environment variable, or modify an existing one
_myunsetenv - Remove an environment variable
Populate_env_list - populates env linked list
 
File - getenv.c
get_environ - returns the string array copy of our environ
_unsetenv - Remove an environment variable
_setenv - Initializes a new environment variable, or modify an existing one
 
 
6. Simple shell 0.1.1
 
Simple shell 0.1 +
Write your own getline function
Use a buffer to read many chars at once and call the least possible the read system call
You will need to use static variables
You are not allowed to use getline
You don’t have to:
be able to move the cursor
A buffer is a computer's memory, that acts as a temporary holding place for data that is being sent to or received from an external device like a keyboard, hard disk, printer, etc
 
File - getLine.c
input_buf - buffers chained commands
get_input - gets a line minus the newline
read_buf - reads a buffer
_getline - gets the next line of input from STDIN (standard input)
signinHandler - blocks ctrl-C
 
 
7. Simple shell 0.2.1

Simple shell 0.2 +
You are not allowed to use strtok


8. Simple shell 0.4.1

Simple shell 0.4 +
handle arguments for the built-in exit
Usage: exit status, where status is an integer used to exit the shell
File exits.c
_strncpy - copies a string
_strncat - concatenates two strings
_strchr - locates a character in a string

9. setenv, unsetenv

Simple shell 1.0 +
Implement the setenv and unsetenv builtin commands
setenv
Initialize a new environment variable, or modify an existing one
Command syntax: setenv VARIABLE VALUE
Should print something on stderr on failure
unsetenv
Remove an environment variable
Command syntax: unsetenv VARIABLE
Should print something on stderr on failure
File - environ.c
_myenv  - prints the current environment
_getenv - gets the value of an environ variable
_mysetenv - Initialize a new environment variable, or modify an existing one
_myunsetenv - Remove an environment variable
Populate_env_list - populates env linked list
 
File - getenv.c
get_environ - returns the string array copy of our environ
_unsetenv - Remove an environment variable
_setenv - Initializes a new environment variable, or modify an existing one
 


10. cd

Simple shell 1.0 +
Implement the builtin command cd:
Changes the current directory of the process.
Command syntax: cd [DIRECTORY]
If no argument is given to cd the command must be interpreted like cd $HOME
You have to handle the command cd -
You have to update the environment variable PWD when you change directory
man chdir, man getcwd
File - builtin.c

_mycd - changes the current directory of the process

 

11. ;

Simple shell 1.0 +
Handle the commands separator ;  
 
This enables the entry of two commands as the ; serves to separate the commands for execution.
File - getline.c
 

12. && and ||

Simple shell 1.0 +
Handle the && and || shell logical operators
 

13. alias

Simple shell 1.0 +
Implement the alias builtin command
Usage: alias [name[='value'] ...]
alias: Prints a list of all aliases, one per line, in the form name='value'
alias name [name2 ...]: Prints the aliases name, name2, etc 1 per line, in the form name='value'
alias name='value' [...]: Defines an alias for each name whose value is given. If name is already an alias, replaces its value with value 
File - builtin.c


14. Variables

Simple shell 1.0 +
Handle variables replacement
Handle the $? variable
Handle the $$ variable
 

 
 
 
15. Comments
 
Simple shell 1.0 +
Handle comments (#)
 
 
16. File as input
 
Simple shell 1.0 +
Usage: simple_shell [filename]
Your shell can take a file as a command line argument
The file contains all the commands that your shell should run before exiting
The file should contain one command per line
In this mode, the shell should not print a prompt and should not read from stdin
