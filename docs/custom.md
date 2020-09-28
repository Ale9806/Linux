# Customizing Bash
## Basic information:
The home directory is a special directory that is represented by a tilde (~). Your home directory contains your personal files, like your photos, documents,the contents of your desktop, and more imporantly, hidden files that allow us to add speciall functionality to Linux. When you first open up your shell you usually start off in your home directory.

Hidden files can be created with "." at the begenning, .ignore for example. In linux we can visualize hidden files with `ls -a`

```
user@desktop:~$  ls -a
.bash_profile    .config   .linuxbrew   .bashrc  .git    
.ssh             .nano     .bash_history
```

## History
We can acces and edit the content of .bash-history with `nano .bash_history` or we can use the `history` command to see the same content. The content of this file is all the commands we have run. 

## Profile
The ~/.bash_profile is a list of Unix commands that are run every time we open our terminal, usually with a different command on every line. 
 
## Setting alias commands

One of the most common commands used in a ~/.bash_profile is the alias command, which creates a shorter name for a command. Let’s take a look at a ~/.bash_profile:

```bash 
user@desktop:~$ nano .bash_profile # Command

alias docs='cd ~/Documents'        # Line added
alias edbp='nano ~/.bash_profile'  # Line added

```
We add an allias by: `alias [alias_name]="code"`

In order to make the changes to our ~/.bash_profile take effect we need to run `source ~/.bash_profile` in the console:
```bash 
user@desktop:~$ source ~/.bash_profile # Command
user@desktop:~$ docs                   # Command
user@desktop:~/Documents$              # New promt (output of docs)
```

## Environmental Variables
The PATH variable contains a sequence of paths on our computer separated by colons. When the shell starts it searches these paths for executable files, and then makes those executable commands available in our shell. One approach to making our scripts available is to add a directory to the PATH. Bash scripts in the directory that are executable can be used as commands. We need to modify PATH every time we start a shell, so we can ammend our ~/.bash_profileso that our directory for executable scripts is always in the PATH. To modify an environmental variable we need to use the export keyword.

First let’s create a new directory called Commands in our Codedirectory where we can keep our executable scripts. Then we’ll add a line to our ~/.bash_profile so that Commands is added to the PATH.

```bash
user@desktop:~$ mkdir Commands
user@desktop:~$ echo "hello world" > Commands/first.sh
user@desktop:~$ nano ~/.bash_profile

export PATH=~/Code/Commands:$PATH
source ~/.bash_profile
```