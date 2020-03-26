# Walkthrough/Write-ups

Back to [Index](./README.md##Index).

All solved levels with their corresponding username and password are [here](./pwds.csv).

To know more about any command used in Linux, a quick ```  man <command> ``` will give its manual page. Otherwise, a quick search on the inter webs should help!


**SSH Information**     
Host: bandit.labs.overthewire.org   
Port: 2220


----------------------------------------------
## bandit0
https://overthewire.org/wargames/bandit/bandit0.html

"The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1."

Here the ``` ssh ``` command shold be used to login as the user ``` bandit0 ``` into the specified host and port, followed by the corresponding password.

```
ssh 
```

Back to [Index](./README.md##Index).

----------------------------------------------

## bandit1

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
## bandit2

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

As recommended [here](https://overthewire.org/wargames/bandit/bandit2.html), a quick Google search of ['dashed filename'](https://www.google.com/search?q=dashed+filename) gives you a lot to read and know about file naming conventions in Unix and Linux.

The main takeaway would be that the dash '-' specifies an option to be set to a linux command in the bash shell, but doesn't have any special meaning to the Unix/Linux kernel. This makes it okay to name a file with '-'. Also, '-' for ``` cat ``` is taken as a stdin/stdout, making it wait for user input. (https://unix.stackexchange.com/questions/16357/usage-of-dash-in-place-of-a-filename)

To work around this, using the absolute or relative path to '-' will work.
```
bandit1@bandit:~$ bandit1@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```

Back to [Index](./README.md##Index).

----------------------------------------------

## bandit3

Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test

Test testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test

Back to [Index](./README.md##Index).

----------------------------------------------

## bandit4

Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test

Test testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test

Back to [Index](./README.md##Index).

----------------------------------------------

## bandit5
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test

Test testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test
Test testTest testTest testTest testTest testTest testTest testTest testTest test

Back to [Index](./README.md##Index).

----------------------------------------------

