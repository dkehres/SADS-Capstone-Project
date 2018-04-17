Basic functionality

The current version of the SADS tool includes nine different functions that can be called from the CLI. The first four of these functions are specific to Dynamical Systems, whereas the last five commands are more generic string manipulation commands.  These functions include: 


-Shift Maximality

-Cutting Times

-Word Count

-Star Product

-Concatenation

-Insertion

-Substitution

-Compare

-Alphabet Definition and Derivation


The syntax, as well as example input/output for these functions are detailed below.

Shift Maximality 
results will be either 1 (is shift maximal) or -1 (is not shift maximal)


Syntax: 
sm(expression) 
sm expression

Where “expression” is a sequence of alphanumeric characters or another command. 

	Example: Input: sm(“101011”)	 Output: -1


Cutting Times

Syntax: 
ct(expression)
ct expression

Where “expression is a sequence of alphanumeric characters or another command

	Example: Input: ct(“101011”)	Output: 1,2,6

Word Count 
returns how many subwords of a certain length are in the main string

Syntax: wc(expression, integer)
Where “expression” is a sequence of alphanumeric characters or another command and “integer” is a whole number that is less than or equal to the length in digits of “expression”

	Example: Input: wc(“101011”, 2)		Output: {01=2, 10=2, 11=1}

Star Product 
creates a new string based on predefined rules

Syntax: sp(expression, expression)
Where “expression” is a sequence of alphanumeric characters or another command
	
	Example: Input: sp(“101011”, “101011”)		Output: 101011110101101010111101011010101111010111101011

Concatenation 
adds the second string on to the the end of the first string

Syntax: 
concat(expression, expression)
Where “expression” is a sequence of alphanumeric characters or another command

	Example: Input: concat(“101011”, “101”)		Output: 101011101

Insertion
insert after an index

Syntax:
insert(expression, expression, index)

Where “expression” is a sequence of alphanumeric characters or another command and “index” is 

	Example: Input: insert(“101011”, “111”, 2)		Output: 101111011

Substitution 
substitute characters of a string with different characters

Syntax:
sub(expression, “string”->”string”)
sub(expression, “string”->”string”,“string”->”string”)
sub(expression, “string”->”string”,“string”->”string”, integer)

Where “expression” is a sequence of 1’s and 0’s contained within double quotes and “string” is a sequence of alphanumeric characters. Integer defines the number of times to perform the substitution if less than or equal to 100. If it is greater, it defines the number of characters to generate.

	Example: Input: sub(“101”, “1”->”0”,”0”->”1”)		Output: 010
		Input: sub(“10”, “1”->”1a”,”a”->”b”, 3)	Output: 1abb0

Compare 
compare two strings and gives the position in which they differ

Syntax:
cmp(string, string)
Where “string” is a sequence of alphanumeric characters.

	Example: Input: cmp(“101011”, “010”)		Output: 1 2 3 4 5 6

Alphabet Definition
define an alphabet to be used for derivation

Syntax:
def({string, string, ...})
def({string, string, ...}, r(int, int, ...), r(int, int, ...), ...)

Where “string” is a sequence of alphanumeric characters.

First is the set of characters contained in the alphabet, after that are the optional rules for deriving higher levels of the alphabet using der().  The number of rules must match the number of characters.

	Example: Input: def({“0”, “1”}, r(0, 1), r(1, 0))		Output: {“0”, “1”}


Alphabet Derivation
generate an alphabet from a given alphabet

Syntax:
der(def(...), level)
der(variable, level)
Where “string” is a sequence of alphanumeric characters.
And “level” is an integer specifying which level should be returned (greater than 1)
And “variable” is a stored alphabet.

If a stored alphabet is used, then it will always take the value of the highest-level alphabet after generation (e.g. if a level 1 alphabet is used to generate a level 10 one, the level 10 will be stored in the variable; but if that level 10 alphabet is used to generate a level 2, then the variable will retain the level 10 alphabet, even if the der() returns the level 2 version).

	Example: Input: der(def({“0”, “1”}, r(0, 1), r(1, 0)), 2)		Output: {“01”, “10”}



Things to remember:
Strings need to be in double quotes: “101011”
Integers are left as is: 1
Expression can be either a string, or another command/function
Some nested commands only work with certain others, all of them work with star product

Variable assignment
Allows for the local storage of a string that is accessible later in the execution of the program.  This string could be used for anything from a command parameter to the definition of an alphabet.  

Syntax:
variable_name := “string”
Where “string” is a sequence of alphanumeric characters.

	Example: x := “101011”



Checking variable assignment
To check the value of a variable assignment, simply use the print command with the variable name.

Syntax: 
print variable_name 
Where “variable_name” is the string used during variable assignment (see above)

	Example: Input: print x 	Output: 101011  

Nested Commands

All regular commands can have other commands run on them
sp(sp(expression, expression), expression)
sp(sp(“101011”, “101”), “010”)

wc(sp(expression, expression), integer)
wc(sp(“101011”, “101”), 3)
Console Commands

/help
Prints out a list of all console commands and a short help string for each

/exit
Quits the application.

/clear
Clears all text in the output window.

/exec <file path>
Executes a batch of several sequential commands.  To automatically insert a file path into the command line, use Ctrl + I, or Edit > Insert File Path... from the menu bar.

Batch files should be written in text format (.txt).  Below is an example.

/debug
Toggles developer debug mode on and off.  Not recommended for normal use.

Executable version with documentation coming soon...
