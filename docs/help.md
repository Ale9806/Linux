# Self help

## MAN (Manuals)
Each of the commands that we’ve discussed so far are thoroughly documented, and you can view their documentation using the `man`command, where the first argument to man is the command you’re curious about. Example : `man ls` or `man cat`

**Controls:**
<ul>
<li> `Up arrow`: Move up </li> 
<li> `Down arrow`: Move down </li> 
<li> `/ [word/phrase]  + Enter`: Start search of [word/phrase] </li> 
<li> `Shift + n`: search for the next occurrence of the word </li> 
<li> `q`: quit </li> 
</ul>
Let’s take a look at the documentation for ls:

## Apropos

The `man` command works wonderfully when you know which command you want to look up, but what if you’ve forgotten the name of the command you’re looking for? You can use `apropos [word/phrase]` to search all of the available commands and their descriptions.  

Example let’s pretend that I forgot the name of my favorite command line text editor. You could type apropos editor into the command line which will print a list of results:

```terminal
user@desktop:~$ apropos editor
vim  (1)             -Vi Improved, a programers text editor
nano (1)             -Restriceted modefor Nano's Another editor
```