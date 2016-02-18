Linux Cheat sheet basic commnads

Show Lists

Shows list of files 
```
ls     
```
Shows list of files in a longer version
```
ls -l  
```
Shows list of all files (including dot files)
```
ls -a    
```
Shows files inside a directory
```
ls /directory    
```
Shows long list of the files inside a directory
```
ls -l /directory   
```
Clears the bash(shell/terminal)
```
clear  
```


Moving around the file system

pwd                           Print working directory, shows where are we e.g /home/user/desktop/directory<br>
cd directory                  Change to a directory called "directory"<br>
cd  /directoryA/directoryB/   Change to a directory called directoryA inside a directory called directory<br>
cd ~                          Change to the root directory<br>
cd ..                         Change to a directory in one superior level<br>
cd ../..                      Change more than one directory level <br>


Reading files

less file.txt                 Prints out what’s inside a file<br>
q                             Exit/escape from a file open with less<br>
cat                           Prints out multiple files e.g. cat file1.txt/ file2.txt <br>


Edit files

nano file.txt                 Creates a new file called file.txt, or acces to a existing file called file.txt<br>
pico file.txt                 text editor for UNIX<br>
control +  x                  Exit/escape the text editor<br>


Renaming/moving   files/directories

mv oldname.txt  newname.txt   This changes the name of oldname.txt to newname.txt<br>
mv directory/filename .       Move a file called “filename” in a directory called "directory" in our current directory (dont forget the dot)<br>

IMPORTANT : mv works depending where you are, for example if you are in desktop$ and want to move a file in other folder in your same tree level, yo can :

mv file.txt newdirectory/    This moves a file called "file.txt " in the desktop directory in to a directory called "newdirectory"<br>


Copying and deleting files/directories

cp -r originaldirectoryname copydirectorname          This duplicate a directory called "originaldirectoryname" and gives it the name of "copydirectoryname"<br>
rm file.txt                                           This removes a file called "file.txt"<br>
rm -r directory                                       This removes a directory called "directory"<br>


Creating directories

mkdir -p directory1/directory2                        This creates a directoryA inside a directoryB<br>
mkdir -p newdirectory                                 This creates a new directory called "newdirectory" in our current location<br>


Creating users

whoami                                                Shows current user<br>
sudo adduser newusername                              This creates a new user called "newusername"<br>
su newusrename                                        Switch user <br>
exit                                                  Return to the last user<br>


File permissions

chmod                                                 Changes permission of a file or a directory<br>
chmod O + W    file.txt                               + gives acces to Others to Write in a file called file.txt<br>
chmod -x file.txt                                     - removes acces to ALL (user, group, others) to execute a file.txt<br>


Examples of changing permissions with octal numbers     r = 4          w = 2          x = 1             4+3+1 =7

chmod  777 file.txt               777 gives 100% acces to ALL(user,group and others) to read, write and excute a file called "file.txt"<br>
chmod 501 file.txt                501 gives read and write permission to user, no permissions to group, and execute permission to others<br> 

Changing user ownerships

sudo                                                  Act like a super user<br>
chown                                                 Changes file ownerships, sending files and their permissions to other user<br>
sudo chown otheruser file.txt                         We need to use sudo before chown, in orther to give the ownership of a file called "file.txt" to "otheruser"<br>
sudo chown otheruser:othergroup file.txt              This change the ownership of a file called file.txt to otheruser and othergroup<br>


Processes

top                                 Lets the users see the processes that are currently executing (in real time)<br>
?                                   For more options <br>
q                                   For quit  <br> 
ps                                  Lists all the processes<br>
ps aux                              Lists all the processes and their status<br>
  

Pausing and resuming a process

ctrl + Z                            Pauses a process e.g like when you are using the command top<br>
[1] + stopped nano file.txt --->  output that shows the job id, the current job , the status, the process and the file <br>

fg                                 Returns the recently paused process<br>
fg 1                               Returns the job [1] <br>
jobs                               Shows a list of all the paused processes<br>


Killing a process

ctrl + c                           Kills the current process<br>
kill - 9  1234                     Kills a process with an id 1234  IMMEDIATELY!<br>
kill - kill  1234                  kills a process with an id 1234  IMMEDIATELY!<br>
kill 1234                          Kills a process with an id of 1234 in other terminal<br>
kill -stop  1234                   Stops a process with an id 1234 in other terminal<br>


Enviroment variables

CREATING A VARIABLE :

newvariable = “this is a variable”  

ACCESING VARIABLES:

env                               Shows all the variables in the current enviroment (shell)<br>
$                                 Allow to use the variable e.g $newvariable <br>
echo                              Returns or repeats any argument<br>
echo $newvariable                 Returns the argument of a variable called "newvariable" <br>
ps1                               Current prompt, can be modified as a variable e.g. ps1 = newprompt$<br>
bash                              Creates a new shell, inside the shell ("a new session inside the current session")<br>
exit                              Return to the last session<br>

EXPORTING VARIABLES AND MAKE THEM ACCESIBLE IN OTHER SESSIONS:

export variable = “this is a variable”     Makes a variable called variable available in other shell/session<br>

PATH VARIABLE:

echo $PATH                             Return directories<br>
which echo                             Shows the location of a program e.g echo <br>
which top                              Shows the location of a program e.g. top<br>
export PATH=/home/username/bin:$PATH   Updates the path <br>



Find and Grep files/directories

find                                                 Locate a file/directory by name <br>
grep                                                 Locate a file/directory by pattern<br>
find . -name “file.txt”                              Locate in current directory(dot) a file called "file.txt"<br>
find directoryA directoryB -name “file.txt”          Locate in directoryA and directoryB a file with the name "file.txt"<br>
find / -name “file”                                  Locate a file called "file" in every directory<br>
grep “or” file.txt                                   Locate the kewyword “or” in a file called "file.txt"<br>
grep -n “or” file.txt                                Locate the line where the keyword “or” is in a file called "file.txt"<br>
grep -i “OR” file.txt                                -i "unlocks case sensitive"<br>
grep -v “or” file.txt                                Locate everything in a file called file.txt, that doesn’t contains “or”<br>


Redirections

grep “is”  file.txt > newfile.txt         This locates everything with the content “is” from a file called "file.txt", and sends it in a file called "newfile.txt" <br>
grep “is”  file.txt >> newfile.txt        This locates everything with the word “is” from a file called "file.txt", in a new file called "newfile.txt"  WITHOUT OVERWRITE ON IT, SENDING THIS CONTENT AT THE BOTTOM OF THE DOCUMENT<br>
find / -name “filename” 2> /dev/null      This send all the list of errors associated to a search using find to a directory called /dev/null where everything disappear, so you can find a file called “filename” without displaying the list of errors.<br>

Pipes

A | B | C  The "easiest" way to understand how to use pipes is :

Take the input of A and sends it as an output to B, which takes it as an input to display an output to C, then C takes that output and uses it as an input to output something... we can use as many pipes that we want.<br>
The standard input is the keyword<br>
The standard output is the terminal<br>

e.g.

ps aux  |  grep bash            This shows a list of  procceses(A) and sends this data as an input to the command "grep bash"(B), then 
grep bash takes this lits and "greps" for bash<br>

sort                            This sorts the lines of standard inputs and sends it to standards outputs<br>

e.g.

ps aux | grep bash | sort       This repeats the (ps aux |  grep bash ) command but shows the data, sorted<br>


Pipes and Redirections (the power of linux!)

ps aux | grep bash | sort > newfile.txt   This uses pipes and redirection to take output of "ps aux" , use it as an input to "grep bash" which its going to send an outupt sorted in to a new file called "newfile.txt"










