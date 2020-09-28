# Linux Tutorial

Unix  is a family of multitasking, multiuser computer operating systems that derive from the original AT&T Unix, development starting in the 1970s at the Bell Labs research center by Ken Thompson, Dennis Ritchie, and others.

Linux is a family of open source Unix-like operating systems based on the Linux kernel, an operating system kernel first released on September 17, 1991, by Linus Torvalds. Linux is typically packaged in a Linux distribution.

**In simpler words:**
Linux is nothing but a UNIX clone which is written Linus Torvalds from scratch with the help of some hackers across the globe. Unix and Unix-like operating systems are a family of computer operating systems that derive from the original Unix System from Bell Labs which can be traced back to 1965. Linux is the most popular variant and there comes in a number of different distributions.

## Basic commands Overview:
When working with linux we will wok on a  terminal. In order to acomplish something we will need to use some basic commnads:

## Managing files and dirs
| Command | Description |
| --- | --- |
| `pwd   `   | Print working directory|
| `ls  `   | Lists files in Directory|
| `ls -l `   | Lists files in Directory with permission information|
| `ls -a`   | Lists all files including those hidden|
| `cd `   | Change Directory|
| ` echo ` | Prints messege in terminal|
| `touch `   | Create an empty file|
| `mkdir`   | Create new Directory|
| `rmdir `   | Remove empty Directory|
| ` cp   ` | Coppy file |
| ` mv`   | Move file (also renames files) |
| ` chmod  ` | Change permissions of a file |

<br>
<br>


## Operating with file content 

| Command | Description |
| --- | --- |
| `file `  file-name| prints tpye of given file |
| `cat `   file-name| Show contents of files|
| `wc`     file-name | Counts the amount of characters, words, and lines in a file|
| `head`   file-name| Show the first 10 lines of a file |
| `tail`   file-name | Show the last 10 lines of a file |
| `grep `  file-name | Find pattern in file|
| `cut `   file-name| Extracts a given number of characters or columns from a file|
| `grep ` 'pattern'  file-name| Extracts patterns from file |

<br>
<br>


## ADDITIONAL COMMANDS:

| Command | Description |
| --- | --- |
| `date` | Prints the current date|
| `Who`  |  Prints the list of users currently logged into the computer|
| `man` command | Shows the manual page of the given command (press "q" to quit)|
| `uptime` | Shows how long the computer has been running |
| `free`   file-name | Shows the amount of unused memory on the current system |


### SIGNALS:
Singals are tokens that allows us to control the behaviour of a program
###### SPECIAL SIGNALS :
kill is a specila signal, in has to be run from another therminal, therefore
you need the Process Identifier (PID) to be able to stop the process:
To find the PID you can use the `ps` comand 
<br>
<br>

### SIGNALS + PROCESSES:

| Command | Description |
| --- | --- |
| `ps`   | Lists the processes executing in the current terminal for the current user|
| `ps ax`   | Lists all processes currently executing for all users|
| `ps e`   | Shows the environment for the processes listed|
| `kill PID`   | Sends the SIGTERM signal to the process identified by PID (run this from another terminal)|
| `ctrl + c`| Termiantes a process properly|
| `ctrl + z`| Stop a process|
| `fg`   | causes a job that was stopped or in the background to return to the foreground|
| `bg ` |causes a job that was stopped to go to the background|
| `jobs `   |lists the jobs currently running or stopped|
| `top`   |shows the processes currently using the most CPU time (press "q" to quit)|

<br>
<br>

### Chmod options: 
<ul>
  <li> chmod -x : Make file executable </li>
  <li> chmod -r : Make file readable </li>
  <li> chmod -w : Make file writable  </li>
   <li> chmod -rwx : All of the above  </li>
</ul>
