#Linux Cheat sheet basic commads

##Show Lists

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

##Moving around the file system

Print working directory, shows where are we e.g /home/user/desktop/directory
```
pwd 
```
Change to a directory called "directory"
```
cd directory     
```
Change to a directory called directoryA inside a directory called directory
```
cd  /directoryA/directoryB/  
```
Change to the root directory
```
cd ~ 
```
Change to a directory in one superior level
```
cd ..    
```
Change more than one directory level 
```
cd ../..   
```

##Reading files

Prints out what’s inside a file
```
less file.txt     
```
Exit/escape from a file open with less
```
q    
```
Prints out multiple files e.g. cat file1.txt/ file2.txt 
```
cat  
```

##Edit files

Creates a new file called file.txt, or acces to a existing file called file.txt
```
nano file.txt    
```
Text editor for UNIX
```
pico file.txt   
```
Exit/escape the text editor
```
control +  x      
```

##Renaming/moving   files/directories

This changes the name of oldname.txt to newname.txt

```
mv oldname.txt  newname.txt 
```
Move a file called “filename” in a directory called "directory" in our current directory (dont forget the dot)
```
mv directory/filename .  
```

<b>IMPORTANT : mv works depending where you are, for example if you are in desktop$ and want to move a file in other folder in your same tree level, yo can :</b>

This moves a file called "file.txt " in the desktop directory in to a directory called "newdirectory"<br>
```
mv file.txt newdirectory/   
```

##Copying and deleting files/directories

This duplicate a directory called "originaldirectoryname" and gives it the name of "copydirectoryname"
```
cp -r originaldirectoryname copydirectorname    
```
This removes a file called "file.txt"
```
rm file.txt    
```
This removes a directory called "directory"
```
rm -r directory  
```

##Creating directories

This creates a directoryA inside a directoryB
```
mkdir -p directoryA/directoryB 
```
This creates a new directory called "newdirectory" in our current location
```
mkdir -p newdirectory     
```

##Creating users

Shows current user
```
whoami     
```
This creates a new user called "newusername"
```
sudo adduser newusername      
```
Switch user
```
su newusrename   
```
Return to the last user
```
exit
```

##File permissions

Changes permission of a file or a directory<br>
```
chmod    
```
+ gives acces to Others to Write in a file called file.txt
```
chmod O + W    file.txt    
```
- removes acces to ALL (user, group, others) to execute a file.txt
```
chmod -x file.txt    
```

<i>Examples of changing permissions with octal numbers     r = 4          w = 2          x = 1             4+3+1 =7</i>

777 gives 100% acces to ALL(user,group and others) to read, write and excute a file called "file.txt"
 ```
chmod  777 file.txt
```
501 gives read and write permission to user, no permissions to group, and execute permission to others
```
chmod 501 file.txt               
```

##Changing user ownerships

Act like a super user
```
sudo     
```
Changes file ownerships, sending files and their permissions to other user
```
chown     
```
We need to use sudo before chown, in orther to give the ownership of a file called "file.txt" to "otheruser"
```
sudo chown otheruser file.txt    
```
This change the ownership of a file called file.txt to otheruser and othergroup
```
sudo chown otheruser:othergroup file.txt       
```

##Processes

Lets the users see the processes that are currently executing (in real time)
```
top 
```
For more options 
```
?   
```
For quit  
```
q  
```
Lists all the processes
```
ps    
```
Lists all the processes and their status
```
ps aux  
```
  
##Pausing and resuming a process

Pauses a process e.g like when you are using the command top
```
ctrl + Z   
```
[1] + stopped nano file.txt --->  output that shows the job id, the current job , the status, the process and the file<br>

Returns the recently paused process
```
fg   
```
Returns the job [1] 
```
fg 1  
```
Shows a list of all the paused processes
```
jobs                               
```

##Killing a process

Kills the current process
```
ctrl + c   
```
Kills a process with an id 1234  IMMEDIATELY!
```
kill - 9  1234     
```
kills a process with an id 1234  IMMEDIATELY!
```
kill - kill  1234   
```
Kills a process with an id of 1234 in other terminal
```
kill 1234   
```
Stops a process with an id 1234 in other terminal
```
kill -stop  1234    
```

##Enviroment variables

<i>CREATING A VARIABLE :</i>
```
newvariable = “this is a variable”  
```

<i>ACCESING VARIABLES:</i>

Shows all the variables in the current enviroment (shell)
```
env  
```
Allow to use the variable e.g $newvariable 
```
$  
```
Returns or repeats any argument
```
echo   
```
Returns the argument of a variable called "newvariable" 
```
echo $newvariable    
```
Current prompt, can be modified as a variable e.g. ps1 = newprompt$<
```
ps1     
```
Creates a new shell, inside the shell ("a new session inside the current session")
```
bash     
```
Return to the last session
```
exit
```

<i>EXPORTING VARIABLES AND MAKE THEM ACCESIBLE IN OTHER SESSIONS:</i>

Make a variable called variable available in other shell/session
```
export variable = “this is a variable”     
```

PATH VARIABLE:

Return the path of all your directories
```
echo $PATH    
```
Shows the location of a program e.g echo 
```
which echo    
```
Shows the location of a program e.g. top
```
which top    
```
Updates the path 
```
export PATH=/home/username/bin:$PATH   
```

##Find and Grep files/directories

Locate a file/directory by name 
```
find  
```
Locate a file/directory by pattern
```
grep  
```
Locate in current directory(dot) a file called "file.txt"
```
find . -name “file.txt”   
```
Locate in directoryA and directoryB a file with the name "file.txt"
```
find directoryA directoryB -name “file.txt”   
```
Locate a file called "file" in every directory
```
find / -name “file” 
```
Locate the kewyword “or” in a file called "file.txt"
```
grep “or” file.txt    
```
Locate the line where the keyword “or” is in a file called "file.txt"
```
grep -n “or” file.txt      
```
-i "unlocks case sensitive"
```
grep -i “OR” file.txt      
```
Locate everything in a file called file.txt, that doesn’t contains “or”
```
grep -v “or” file.txt     
```

##Redirections

This locates everything with the content “is” from a file called "file.txt", and sends it in a file called "newfile.txt" 
```
grep “is”  file.txt > newfile.txt      
```
This locates everything with the word “is” from a file called "file.txt", in a new file called "newfile.txt"  WITHOUT OVERWRITE ON IT, SENDING THIS CONTENT AT THE BOTTOM OF THE DOCUMENT`
```
grep “is”  file.txt >> newfile.txt    
```
This send all the list of errors associated to a search using find to a directory called /dev/null where everything disappear, so you can find a file called “filename” without displaying the list of errors.
```
find / -name “filename” 2> /dev/null   
```

##Pipes

A | B | C  <i>The "easiest" way to understand how to use pipes is :</i>

<i>Take the input of A and sends it as an output to B, which takes it as an input to display an output to C, then C takes that output and uses it as an input to output something... we can use as many pipes that we want.<i><br>
<i>The standard input is the keyword</i><br>
<i>The standard output is the terminal</i><br>

<i>e.g.</i>

This shows a list of  procceses(A) and sends this data as an input to the command "grep bash"(B), then 
grep bash takes this lits and "greps" for bash<br>
```
ps aux  |  grep bash  
```

<i>sort, sorts the lines of standard inputs and sends it to standards outputs</i>

<i>e.g.</i>

This repeats the (ps aux |  grep bash ) command but shows the data, sorted
```
ps aux | grep bash | sort    
```

##Pipes and Redirections (the power of linux!)

This uses pipes and redirection to take output of "ps aux" , use it as an input to "grep bash" which its going to send an outupt sorted in to a new file called "newfile.txt"

```
ps aux | grep bash | sort > newfile.txt 
```










