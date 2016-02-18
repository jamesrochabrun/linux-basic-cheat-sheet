Linux Cheat sheet basic commnads

Lists
(ls) - Shows list of files 
(ls -l) - shows list of files in more detail
(ls -a) - Shows list of files including dot files (hide files)
(ls /directory) - shows files inside a directory.
(ls -l /directory) - Shows long list of the files in a directory
(clear) - clears the bash(shell/terminal)


Moving around the file system

(pwd) - print working directory, shows where are we e.g /home/user/desktop/directory
(cd directory) - change directory 
(cd  /directory1/directory2/) change directory inside a directory
(cd ~) - change to home
(cd ..) - change one directory up
(cd ../..) - change more than one directory up


Reading files

(less file.txt) - prints out what’s inside a file
(q) - exit the file printed with less
(cat) - prints out multiple file e.g. cat file1.txt/ file2.txt -similar to less-


Edit files

(nano file.txt)- creates a new file or acces to a file called file.txt
(pico file.txt) - text editor for UNIX
(control x) - exit the text editor

Renaming/moving   files/directories

(mv file1.txt  file2.txt) - rename file1 in to file2
(mv directory/filename . ) - moves the file “filename” in the directory in our current directory (dont forget to use a dot or a tilda~)
dont forget that works relative to the path where you are, for example if you are in desktop and want to move a file in other folder in your same tree level, yo can mv file.txt folder/


Copying and deleting  files/directories

(cp -r currentdirectoryname copydirectorname) - copies a directory and gives it a name to the copy.
(rm file.txt ) - removes a existent file
(rm -r directory) - removes a directory
Creating directories

(mkdir -p directory1/directory2) - creates a directory2 inside a directory1
(mkdir -p newdirectory) - creates a new directory in our current location


Creating users

(whoami) - shows current user
(sudo adduser newusername) - creates a new user
(#useradd -m newusername) - creates a new user in UNIX
(#passwd newusername) - sets a password for the new user
(su newusrename) - switch user 
(exit) - returns to the last user

File permissions


                                                                   Who?

User 				Group 				Other 

                                                             permissions

Read 				Write 				Exceute

U 				G 				O
rwx                                       rwx                                          rwx


(chmod) - changes permission of a file or a directory
(chmod O + W    file.txt)  - + gives acces to Others to Write in a file called file.txt
(chmod  -x file.txt) - - delete acces to ALL (user, group, others) to execute a file.txt)

  Changing permissions with octal numbers     r = 4          w = 2          x = 1             4+3+1 =7

(chmod 777 file.txt) - gives 100% acces to ALL to read write and excute a file.txt
(chmod 501 file.txt)- gives read and write permission to user, any permission to group, and execute permission to others.

(chown) - Changes file ownerships, sending files and their permissions  to other users
(sudo chown otheruser file.txt) - We need sudo, this “sends” a file called file.txt and its permissions to other user.
(sudo chown otheruser:othergroup file.txt) - this change the ownership of a file called file.txt to otheruser and othergroup
(sudo) - runs a command as a super user.
Processes

(top) - let the user see the processes that are currently executing in real time (updating)
(Q) - quits 
(?) - show options
(ps) - show all the processes 
(ps aux) - show all the processes in detail “we can see the process id)
  

Pausing and resuming

(ctrl + Z) - pauses a process e.g if we are editing a file with nano .
[1] + stopped nano file.txt --->  output that shows the job id , the current job , the status, the process and the file 
(fg) - return the recently paused process
(fg 1) -  return the job [1] 
(jobs) - shows a list of all the paused processes
(programname  &) - runs a program in the backend


Killing a process

(ctrl + c) - kills the process
(kill 1234 ) - e.g kills a process with an id of 1234 in other terminal
(kill - 9  1234) - e.g. kills a process with an id 1234  IMMEDIATELY!
(kill - kill  1234) - e.g. kills a process with an id 1234  IMMEDIATELY!
(kill -stop  1234) - stops a process with an id 1234 in other terminal.

Enviroment variables

($) - sets the variable e.g $newvariable 
(env) - shows all the variables in the enviroment (shell)
(variable = “this is a variable”) - creating a variable call variable and setting a value.
(echo) - returns a echo of a variable oranyting.
(echo $variable) - returns “this is a variable”
(ps1) - prompt , can be modified as a variable e.g. ps1 = newprompt 
(bash) - creates a new shell inside the shell (a new session inside the current session)
(exit) - return to the last session
(export variable = “this is a variable”) - makes this variable available to other shell/session
(echo $PATH) - return directories
(which echo) - shows the location of a program e.g echo 
(which top) - shows the location of a program e.g. top
(export PATH=/home/username/bin:$PATH) - updates the path 



Find and Grep files/directories

(find) - locate by name
(grep) - locate by pattern
(find . -name “file”) - find (dot) in current directory a file called file
(find directoryA directoryB -name “file”) - find in directoryA and B a file called file
(find / -name “file”) - find a a file called file in every directory
(grep “is” file) - find the kewyword “is” i a file called file
(grep -n “is” file) - find the line where the keyword “is” is in a file called file
(grep -i “is” file) - i unlocks cas sensitive
(grep -v “is” file) - find everything in a file called file , that doesn’t contain the keyword “is”


Redirections

(grep “is”  file.txt > newfile.txt) - this  puts everything with the keyword “is” from a file called file.txt , in a new file called newfile.txt 
(grep “is”  file.txt >> newfile.txt) - this  puts everything with the keyword “is” from a file called file.txt , in a new file called newfile.txt WITHOUT OVERWRITE ON IT
(find / -name “filename” 2> /dev/null)  - this send all the list of errors asociates to a search using find to a directory called /dev/null where everything disapear, and we can find a file called “filename” withou displaying the whole list of errors.

Pipes

A | B | C … Pipes the input of A and sends it as an output to B which takes it as an input to display an output to C , C takes that output and uses it as an input to output something. we can use as many pipes that we want.
The standard input is the keyword
The standard output is the terminal

e.g.

(ps aux  |   grep bash) - this shows all the procces and sends the data as an input to grep bash, then grep bash takes this data and search for a process with the keyowrd “bash”
(sort) - sorts the lines of standard inputs and sends it to standards outputs.
(ps aux | grep bash | sort) - this repeats the (ps aux |  grep bash ) command but shows the data sorted.
(ps aux | grep bash | sort > newfile.txt) - this uses pipes and redirection to take the data of the command and send it to a file called newfile.txt






Installing software with the package manager


APT , advanced packaging tool (Linux)

Steps :

(sudo apt-get update) - this updates your packages 
(apt - cache search git ) - this searches for a package called git
(sudo apt-get install git ) - this installs a package called git
(sudo apt-get upgrade) - this upgrades the packages
(sudo apt-get remove git) - this removes a package called git 







