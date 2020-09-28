# Make files 

Makefile (makefile) define a set of tasks to be executed. You may have used make to compile a program from source code. Most open source projects use make to compile a final executable binary, which can then be installed using make install.

## structure

The simple makefile has the following general format:

```
[target]: [dependencies...]
  [commands...]
```

**Exmple**:

```
user@desktop:~$ nano makefile

journal.txt:
  touch journal.txt
```

In this example, journal.txt is the target, and returns  a file which is created as the result of the command(s). It’s very important to note that any commands under a target must be indented with a Tab. If we don’t use Tabs to indent the commands then make will fail. 

Let’s use the make command with the target we want to be “made” as the only argument:

```
user@desktop:~$ ls               # command
makefile                         # ouput
user@desktop:~$ make journal.txt # command
touch journal.txt                # ouput
user@desktop:~$ ls               # command
makefile                         # ouput
journal.txt                      # ouput

```


Let’s update our makefile to include a readme.txt that is built automatically. First, let’s add a a dependencie:

```bash
user@desktop:~$  nano makefile    # command

journal.txt:
  touch journal.txt
  
readme.txt: toc.txt
  echo "This journal contains the following number of entries:" > readme.txt
  wc -l toc.txt | egrep -o "[0-9]+" >> readme.txt
```

Now that we have added a new target lets build it

```
user@desktop:~$  make readme.txt                                            # command
echo "This journal contains the following number of entries:" > readme.txt  # output
wc -l toc.txt | egrep -o "[0-9]+" >> readme.txt                             # output
user@desktop:~$  cat readme.txt                                             # command
1                                                                           # output 
```