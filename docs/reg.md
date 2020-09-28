# Regular expressions
A regular expression (regex or regexp) is a sequence of characters that define a search pattern. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings.The concept arose in the 1950s when the American mathematician Stephen Cole Kleene formalized the description of a regular language. The concept came into common use with Unix text-processing utilities.

Regular expressions are used in search engines, search and replace dialogs of word processors and text editors, in text processing utilities. Many programming languages provide regex capabilities either built-in or via libraries.

## GREP
The ability to search through files and folders can greatly improve your productivity using Unix.

One of the most popular tools for searching through text files is `grep`. The simplest use of grep requires two arguments: a string or character you are looking for and the text file to search.

`grep "[string/character]" [file]`


## EGREP

Regular expressions aren’t just limited to searching with characters and strings, the real power of regular expressions come from using metacharacters.  To take full advantage of all of the metacharacters we should use grep’s cousin `egrep`, which just extends grep’s capabilities. 

`egrep "[regular expression]" [file]`

## FIND

If you want to find the location of a file or group of files you can use the `find` command. `find [Directory to start at] [argument]` this command has a specific structure where the first argument is the directory where you want to begin the search ( . for current directory, .. for parent director with respect to current directort), and all directories contained within that directory will also be searched. The first argument is then followed by a flag that describes the method you want to use to search. For instance the  -name flag.

```
alex@LAPTOP-B501IEC8:/home$ find . -name "states.txt"
./alex/states.txt
```

## Metacharacters 
 `Metacharacters` are characters that can be used to represent one ocurrance of any other characters.

| Metacharacter | Meaning |
| --- | --- |
| `.`   |Any Character|
|`^`	|Beginning of String |
|`$`	|End of String |
|`\n`	|Newline |


## Quantifiers 

Besides metacharacters that can represent one character, there are also metacharacters called `quantifiers` which allow you to specify the number of times a particular regular expression should appear in a string.

**Example:**
One of the most basic quantifiers is "+"  which represents one or more occurrences of the preceeding expression. The regular expression “s+as” means: one or more “s” followed by “as”. Let’s see if any of the state names match this expression

| Metacharacter | Meaning |
| --- | --- |
|`+`	|One or More of Previous  Character|
|`*`	|Zero or More of Previous Character |
|`?`	|Zero or One of Previous Character|
|`|`	|Either the Previous or the Following Character |
|`{6}`	|Exactly 6 of Previous Character |
|`{4, 6}`	|Between 4 and 6 or Previous Character|
|`{4, }`	|More than 4 of Previous Character|

**Note:** it is important to know the differnece between  * and "*", the first means all (wildcard) and the second one is a metachacaracter 

##  Sets
In addition to quantifiers there are also regular expressions for describing sets of characters.

| Metacharacter | Meaning |
| --- | --- |
| `\w`   |A word (letters, numbers, underscores)|
|`\W`	|Not a Word|
|`\d`	|A Digit (Numbers)|
|`\D`	|Not a Digit |
|`\s`	|Whitespace |
|`\S`	|Not Whitespace |
|`[def]`	|A Set of Characters |
|`[^def]`	|Negation of Set |
|`[e-q]`	|A Range of Characters |

## Wrap up
We can us methcaracters to match a single character, quintifiers to match many characters and together we can build sets to match specifc patterns 

## Practical examples:
Given a file states.txt with all the sates of the Us we will aply some basic search:

## Character search example
We wish to find all the states that start with "Miss"
```
user@desktop:~$  grep "^Miss" states.txt
Mississippi
Missouri
```
## Quintifier search example 
If we apply "s+as" we will get back all the states that have a pattern of One or more appearance of "s" followed by "as" [sas,ssas,sssas,...)
```
user@desktop:~$  egrep "s+as" states.txt

Arkansas
Kansas
```
If we apply "s*as" we will get back all the states that have a pattern of zero or more appearance of "s" followed by "as" [as,sas,ssas,sssas,...)
```
user@desktop:~$  egrep "s*as" states.txt

Alaska
Arkansas
Kansas
Massachusetts
Nebraska
Texas
Wahington
```
## Sets search exmaple

Take note that the regular expression "s{2}" is equivalent to the regular expression "ss","s{3}" to "sss" and we can combine them "s{2,3}[ae]" to get ["ssa","sssa","sse","ssse"] matches 

```
user@desktop:~$  egrep "s{2,3}[ae]" states.txt

Massachusetts
Tennesss       # matched sss due of typo in Tennessee
```

