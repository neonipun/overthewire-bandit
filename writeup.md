# Walkthrough/Write-ups

Back to [Index](./README.md##Index).

All solved levels with their corresponding username and password are [here](./pwds.csv).

To know more about any command used in Linux, a quick ```  man <command> ``` will give its manual page. Otherwise, a quick search on the inter webs should help!


**SSH Information**     
Host: bandit.labs.overthewire.org   
Port: 2220


----------------------------------------------
## [bandit0](https://overthewire.org/wargames/bandit/bandit0.html)

https://overthewire.org/wargames/bandit/bandit0.html
> "The goal of this level is for you to log into the g    ame using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1."

Here the ``` ssh ``` command shold be used to login as the user ``` bandit0 ``` into the specified host and port, followed by the corresponding password.

```
ssh 
```

Back to [Index](./README.md##Index).

----------------------------------------------

## [bandit1](https://overthewire.org/wargames/bandit/bandit1.html)

Login with ``` ssh bandit0@bandit.labs.overthewire.org -p 2220 ```

Perform a the ``` cat ``` command on the file ``` readme ```, the file contains the password to the next level. To check out all files or dirctories present in the current working directory use ``` ls ```. 

```
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```

```cat``` is one of the most frequently used Linux command that is short for concatenate, and is used to view a single or multiple file contents.

Back to [Index](./README.md##Index).

----------------------------------------------
## [bandit2](https://overthewire.org/wargames/bandit/bandit2.html)

Login with ``` ssh bandit1@bandit.labs.overthewire.org -p 2220 ```

It's always a good idea to do an ```ls``` once you login to a machine, to see what you can deal with. Doing so gives us a single file '-'.
```
bandit1@bandit:~$ bandit1@bandit:~$ ls
-
bandit1@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit2 bandit1 33 Oct 16  2018 -
```
Your first instict might be to do a ```cat -```, but doing so only makes the shell wait for user input.

As recommended [here](https://overthewire.org/wargames/bandit/bandit2.html), a quick Google search of ['dashed filename'](https://www.google.com/search?q=dashed+filename) gives you a lot to read and know about file naming conventions and stdin/stdout in Unix and Linux.

The main takeaway would be that the dash '-' specifies an option to be set to a linux command in the bash shell, but doesn't have any special meaning to the Unix/Linux kernel. This makes it okay to name a file with just '-', or even start with it. Also, '-' for ``` cat ``` is taken as a stdin/stdout, making it wait for user input. (https://unix.stackexchange.com/questions/16357/usage-of-dash-in-place-of-a-filename)

To work around this, using the absolute or relative path to '-' will work.
```
bandit1@bandit:~$ bandit1@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```

Back to [Index](./README.md##Index).

----------------------------------------------

## [bandit3](https://overthewire.org/wargames/bandit/bandit3.html)

Login with ``` ssh bandit2@bandit.labs.overthewire.org -p 2220 ```

Doing an ``` ls ``` shows that the filename has spaces in it. To deal with passing it as a command parameter, it needs to be enclosed within quotes - " ".

i.e. ``` cat "spaces in this filename" ```.

```
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit3 bandit2 33 Oct 16  2018 spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename" 
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
bandit2@bandit:~$
```

Back to [Index](./README.md##Index).

----------------------------------------------

## [bandit4](https://overthewire.org/wargames/bandit/bandit4.html)

Login with ``` ssh bandit3@bandit.labs.overthewire.org -p 2220 ```

To view the hidden files in a directory the ``` -a ``` option for ``` ls ``` should be used, and to obtain the password for the next level, i.e. bandit5, a ``` cat ``` on that hidden file would do it.

Before that, we need to change into the ```inhere``` directory using the ``` cd ``` command.

```
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden
bandit3@bandit:~/inhere$ cat .hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

Here ```.``` represents the current directory and ```..``` represents the parent directory.
Back to [Index](./README.md##Index).

----------------------------------------------

## [bandit5](https://overthewire.org/wargames/bandit/bandit5.html)

Login with ``` ssh bandit4@bandit.labs.overthewire.org -p 2220 ```

``` cd ``` into ``` inhere ``` and check what it contains.
```
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file0
```

You could manually ``` cat ``` each file to see which ones gives readable text, but that wouldn't be efficient nor something you would want to do if you have 100s of files to search from.

Now would be a good time to learn about the ``` file ``` command. This command shows what the given file's file type is.
```
bandit4@bandit:~/inhere$ file ./-file00
./-file00: data
bandit4@bandit:~/inhere$ file ./-file01
./-file01: data
```

Now again, doing it for each and every file is very inefficient. 
Here the Linux wildcard character asterisk (*) would be usefule to use. It matches one or more occurrences of any character, including no character. So, using it to match all file names to check with ``` file ``` would help.
```
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

This shows that ``` -file07 ``` is ASCII text, which is human readable. A ``` cat ``` on it would give us the password to bandit5.
```
bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```

Back to [Index](./README.md##Index).

----------------------------------------------

