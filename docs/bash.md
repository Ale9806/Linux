# Bash Scripting 

## Introduction to BASH

In a Unix like operating system, such as Linux, a shell takes input from you in the form of commands, processes it, and then gives an output. It is the interface through which a user works on the programs, commands, and scripts. A shell is accessed by a terminal which runs it.

In order to visualize the shells you have available in your Linux distribrution type:

```bash
user@desktop:~$ cat ~/../../etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
/usr/bin/tmux
/usr/bin/screen
```

In this tutorial we will use the born again shell (bash). In order to see the path of your shell run the following command:

```bash
user@desktop:~$ which bash
/bin/bash
```

In order to run a program with bash we will have to add this path in every script  we creat (take in mind that the file has to end in .sh) :

```bash
user@desktop:~$ nano filename.sh 

#! /bin/bash             # Add line
echo "HELLO BASH LINUX"  # Add line
```

<br>

## File Permission 

You can check the permission of files and directories with `ls -l` 

```bash
alex@LAPTOP-B501IEC8:~$ ls -l
total 0
-rw-r--r-- 1 alex alex  162 Sep 23 23:57 01-What-is-Unix.md
drwxrwxrwx 1 alex alex 4096 Sep 24 16:50 BMSIS
....
```
The left column of this table contains a series of individual characters and dashes. The first hyphen (-) signifies that each of the entries in this list are files. If any of them were directories then instead of a hyphen there would be a d. Excluding the first hyphen we have the following string: rw-rw-r--. This string reflects the permissions that are set up for this file. There are three permissions that we can grant: 
<ul>
<li>`r` Read file</li>
<li>`w` Write file</li>
<li>`x` Execute file</li>
</ul>

 These three permissions can be granted on three different levels of access which correspond to each of the three sets of rwx in the permissions string: 

<ol>
<li>Owner of file</li>
<li>Group</li>
<li>Everyone else </li>
</ol>

Levels of permmision:

| Character | Meaning |
| --- | --- |
|u	|The owner of the file|
|g	|The group that the file belongs to|
|o	|Everyone else|
|a	|Everyone above|

Option: 

| Character | Meaning |
| --- | --- |
|+ |Add permission|
|-	|Remove permission|
|=	|Set permission|

Permission:

| Character | Meaning |
| --- | --- |
|r  |Read a file|
|w	|Write to or edit a file|
|x	|Execute a file|

### Example:
If we want to make a file executable for the owner  of this file (us). We can combine u, +, and x in order make the file  executable. 

```bash
user@desktop:~$ chmod u+x [file]
```

<br>


## Basic arithmetic 
The Bash programming language can do very basic arithmetic, we have two options:

### expr
The expr command can be used to evaluate Bash expressions. An expression is just a valid string of Bash code that, when run, produces a result. The arithmetic operators that you’re already familiar with for addition (+), subtraction (-), and multiplication (*) work like you would expect them to. 

```bash
user@desktop:~$ nano math.sh
#!/usr/bin/env bash
# File: math.sh
expr 5 + 2
expr 5 - 2
expr 5 \* 2
expr 5 / 2

user@desktop:~$ bash math.sh
7
3
10
2
```
 Notice that when doing multiplication you need to escape the star character, otherwise Bash thinks you’re trying to create a regular expression! The division operator (/) does not work as you might expect it to since 5 / 2 = 2.5. Bash does integer division, which means that the result of dividing one number by another is always rounded down to the nearest integer.

### Bench Calculator 
If you want to do more complex math, for example math with fractions and numbers with decimals then us echo and the **b**ench **c**alculator program called `bc`.

```bash
user@desktop:~$ nano math2.sh
#!/usr/bin/env bash
# File: math.sh
echo "22 / 7" | bc -l
echo "4.2 * 9.15" | bc -l
echo "(6.5 / 0.5) + (6 * 2.2)" | bc -l

user@desktop:~$ bash math2.sh
3.14285714285714285714
38.430
26.20000000000000000000
```

<br>

## Variables
In Bash you can store data in variables. Previously we have discussed environmental variables that are set by your operating system. You can also create your own variables. Make sure you follow these rules when you’re naming variables:

* Every character should be lowercase.
* The variable name should start with a letter.
* The name should only contain alphanumeric characters and underscores.
* Words in the name should be separated by underscores.

You can assign data to a variable using the equals sign (=). The data you store in a variable can either be a string or a number. No spaces on either side of the equals sign are allowed.

```bash
a=5
```
In order to print the data in a variable, we can use echo. When you want to retrieve the value of a variable you must use the dollar sign ($) before the name of the variable.

```bash
user@desktop:~$ a=5
user@desktop:~$ echo $a
5
```
You can modify the value of a variable using arithmetic operators by using the `let` command:

```bash
user@desktop:~$ let a=$a+1
user@desktop:~$ echo $a
6
```

Occasionally you might want to run a command like you would on the command line and store the result of that command in a variable. We can do this by wrapping the command in a dollar sign and parentheses ($( )) around a command. This syntax is called command substitution. The command is executed and then gets replaced by the string that resulted from running the command. For example if we wanted to store the number of lines in math.sh

```bash
user@desktop:~$ math_lines=$(cat math.sh | wc -l)
user@desktop:~$ echo $math_lines
7
```

Variable names with a dollar sign can also be used inside other strings in order to insert the value of the variable into the string:


```bash
user@desktop:~$ echo "The file math.sh has $math_lines lines"
The file math.sh has 6 lines
```

When writing a Bash script, the first argument to your script is stored in $1, the second argument is stored in $2, etc, etc. An array of all of the arguments passed to your script is stored in $@, and we’ll discuss how to handle arrays later on

```bash
user@desktop:~$ nano free.sh
echo  "First variable $1 , second variable $2 , List of variables $@"

user@desktop:~$  bash free.sh blue red
First variable blue , second variable red , List of variables blue red
```

## User Input
You can ask the users to type in a string on the command line by temporarily stopping the execution of your program using the `read` command.

```bash
user@desktop:~$ nano read_example.sh

echo "Type in a string and then press Enter:"
read response
echo "You entered: $response"

user@desktop:~$ bash read_example.sh
Type in a string and then press Enter
Hello world
You entered: Hello world
```

<br>

## Arrays
Arrays in Bash are ordered lists of values. You can create a list from scratch by assigning it to a variable name. Lists are created with parentheses () with a space separating each element in the list. Let’s make a list of the plagues of Egypt:

```bash
user@desktop:~$  plagues=(blood frogs lice flies sickness boils hail locusts darkness death)
```

To retrieve the array you need to use parameter expansion, which involves the dollar sign and curly brackets (${ }). The positions of the elements in the array are numbered starting from zero. To get the first element of this array use ${plagues[0]} like so

```bash
user@desktop:~$  echo ${plagues[0]}

blood
```

To get all of the elements of plagues use a star (*) between the square brackets:

```bash
user@desktop:~$  echo ${plagues[*]}

blood frogs lice flies sickness boils hail locusts darkness death
```

Other useful things:

You can find the length of an array using the pound sign (#)

```bash
user@desktop:~$ echo ${#plagues[*]}

10
```

You can use the plus-equals operator (+=) to add an array onto the end of an array array:

```bash
user@desktop:~$  dwarfs=(grumpy sleepy sneezy doc) # Command
user@desktop:~$ echo ${dwarfs[*]}                  # Command
grumpy sleepy sneezy doc                           # Output
user@desktop:~$ dwarfs+=(bashful dopey happy)      # Command
user@desktop:~$ echo ${dwarfs[*]}                  # Output
grumpy sleepy sneezy doc bashful dopey happy       # Command
```
<br>
<br>

## Conditional Expressions
Conditional execution allows you to control the circumstances where certain programs are executed based on whether those programs succeed or fail, but you can also construct conditional expressions which are logical statements that are either equivalent to true or false. Conditional expressions either compare two values, or they ask a question about one value. Conditional expressions are always between double brackets ([[ ]]), and they either use logical flags or logical operators.

|Logical Flag|	Meaning	|Usage|
| - | -- | -- |
|-gt| Greater Than|	[[ $planets -gt 8 ]]|
|-ge|	Greater Than or Equal To|	[[ $votes -ge 270 ]]|
|-eq|	Equal|	[[ $fingers -eq 10 ]]|
|-ne|	Not Equal|	[[ $pages -ne 0 ]]|
|-le|	Less Than or Equal To|	[[ $candles -le 9 ]]|
|-lt|	Less Than|	[[ $wives -lt 2 ]]|
|-e|	A File Exists|	[[ -e $taxes_2016 ]]|
|-d|	A Directory Exists|	[[ -d $photos ]]|
|-z|	Length of String is Zero|	[[ -z $name ]]|
|-n	|Length of String is Non-Zero|	[[ -n $name ]]|

**Example:**
```bash
[[ 3 -gt 4 ]]
flase
```
In addition to logical flags there are also logical operators. One of the most useful logical operators is the regex match operator =~. The regex match operator compares a string to a regular expression and if the string is a match for the regex then the expression is equivalent to true, otherwise it’s equivalent to false. Let’s test this operator a couple different ways:

```bash
[[ rhythms =~ [aeiou] ]] && echo t || echo f
my_name=sean
[[ $my_name =~ ^s.+n$ ]] && echo t || echo f

## f
## t
```
Here’s a table of some of the useful logical operators in case you need to reference how they’re used later:


|Logical Operator	|Meaning|	Usage|
|--|--|--|
|=~|	Matches Regular Expression|	[[ $consonants =~ [aeiou] ]]|
|=|	String Equal To	|[[ $password = "pegasus" ]]|
|!=|	String Not Equal To|	[[ $fruit != "banana" ]]|
|!|	Not	|[[ ! "apple" =~ ^b ]]|

<br>
<br>

## IF and Else
Conditional expressions are powerful because you can use them to control how a Bash program that you’re writing is executed. One of the fundamental constructs in Bash programming is the IF statement. Code written inside of an IF statement is only executed if a certain condition is true, otherwise the code is skipped. Let’s write a small program with an IF statement:

```bash
#!/usr/bin/env bash
# File: condexif.sh

if [[ $1 -gt 3 ]] && [[ $1 -lt 7 ]]
then
  echo "$1 is between 3 and 7"
elif [[ $1 =~ "Jeff" ]] || [[ $1 =~ "Roger" ]] || [[ $1 =~ "Brian" ]]
then
  echo "$1 works in the Data Science Lab"
else
  echo "You entered: $1, not what I was looking for."
fi
```
**Notes:**

* It is important to put the if evaluation  inside brackets and leave space among  the expresison.

* After the if condition it is important to specify the behavior with the keyword **then**

* In order to close the loop write **if**

* Conditional execution uses two operators: AND (&&) and OR (||) which you can use to control what command get executed based on their exit status.

<br>
<br>

## Braces
Bash has a very handy tool for creating strings out of sequences called brace expansion. Brace expansion uses the curly brackets and two periods ({ .. }) to create a sequence of letters or numbers. For example to create a string with all of the numbers between zero and nine you could do the following:

```bash
user@desktop:~$  echo {0..9}

0 1 2 3 4 5 6 7 8 9
```

You can put strings on either side of the curly brackets and they’ll be “pasted” onto the corresponding end of the sequence:
```bash
user@desktop:~$ echo a{0..4}
user@desktop:~$ echo b{0..4}c

a0 a1 a2 a3 a4
b0c b1c b2c b3c b4c
```

You can also combine sequences so that two or more sequences are pasted together:

```bash
user@desktop:~$  echo {1..3}{A..C}

1A 1B 1C 2A 2B 2C 3A 3B 3C
```
If you want to use variables in order to define a sequence you need to use the eval command in order to create the sequence:
```bash
user@desktop:~$  start=4
user@desktop:~$  end=9
user@desktop:~$  echo {$start..$end}
{4..9}
user@desktop:~$  eval echo {$start..$end}
4 5 6 7 8 9
```

You can combine sequences with a comma between brackets ({,}):
```bash
user@desktop:~$ echo {{1..3},{a..c}}
1 2 3 a b c
```

<br>
<br>

## For loop
FOR loops iterate through every element of a sequence that you specify. Let’s take a look at a small example FOR loop:

```bash
#!/usr/bin/env bash
# File: forloop.sh

echo "Before Loop"

for i in {1..3}
do
    echo "i is equal to $i"
done

echo "After Loop"

```
**Notes:**

* After giving the breace to iterate, specify the bahavior after **do**
* The closing keyword for for loop is not rof, but **done**


## While loop
The WHILE loop begins first with the while keyword followed by a conditional expression. As long as the conditional expression is equivalent to true when an iteration of the loop begins, then the code within the WHILE loop will continue to be executed.

```bash
#!/usr/bin/env bash
# File: whileloop.sh

count=3

while [[ $count -gt 0 ]]
do
  echo "count is equal to $count"
  let count=$count-1
done
```

## Functions 
A function is a small piece of code that has a name. Writing functions allows us to re-use the same code multiple times across programs. Functions have the the following syntax:

```bash
function [name of function] {
  # code here
}
```