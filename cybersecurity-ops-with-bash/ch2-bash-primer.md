# CH2 Bash Primer

## Outputting Information

Bash provides the ability to output information to the screen. Some example commands include:

- **`echo`**: Simply echoes text to the screen.
- **`printf`**: Provides additional formatting options for output.

## Variables

Variables in Bash usually hold strings unless declared as other types.

- To assign a value to a variable, use the syntax: `MYVAR="textforvalue"`.
- You can use quotes to enclose whitespace within a variable's value.
- Double quotes (`"`) will print the values of variables within the string, while single quotes (`'`) will treat the string literally.

You can run a subshell using the following syntax:

$(command)

## Positional Parameters

positional parameters store in dollar sign followed by a number format  
$# many parameters  
$0 file name  
$1 first param  
$2 second param  
$3 etc, etc

## Input

input is received in bash using read command  
read command obtains user input from stdin and stores it in specified variable

## Conditionals

return value of zero equals success, nonzero considered error
can use \[\[ command to test
