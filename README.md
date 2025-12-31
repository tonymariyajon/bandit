# bandit
<img width="1355" height="967" alt="image" src="https://github.com/user-attachments/assets/890833d7-e8de-40d6-a34b-4b0c04de9596" />
LEVEL 0 --> LEVEL 1:
After connecting usign ssh give the command: ls

there is a file called readme (which contains password for the next level ) to read it

command : cat readme

flag : ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

LEVEL 1 --> LEVEL 2:
Using the Level 0 password we have to login into this level one

command: ssh bandit1@bandit.labs.overthewire.org -p 2220

in this if we give ls their is a file named - lets see how we can read a file with command : cat ./-

. --> current directory

/ --> path

--> file name
flag : 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

LEVEL 2 --> LEVEL 3 :
The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

command : ssh bandit2@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login to this level

bandit2@bandit:~$ ls --spaces in this filename--

to read this file commad : cat ./--spaces in this filename--

. --> current directory

/ --> path

--spaces in this filename-- --> file_name

flag: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

LEVEL 3 --> LEVEL 4:
The password for the next level is stored in a hidden file in the inhere directory.

commad : ssh bandit3@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

commad : ls

go to inhere folder and command : ls -la to list the hidden files and to read the hidden file

command: cat ...Hiding-From-You

flag : 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

LEVEL 4 --> LEVEL 5 :
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command

commad : ssh bandit4@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

command : ls

navigate to inhere folder command : cd inhere

there are many files in this we have to find human-readable file

by using the file command we can find what type of file it is

bandit4@bandit:~/inhere$ file ./-file0*

./-file00: data ./-file01: OpenPGP Public Key ./-file02: OpenPGP Public Key ./-file03: data ./-file04: data ./-file05: data ./-file06: data ./-file07: ASCII text ./-file08: data ./-file09: data

therefore ./-file07 is a human readable file

command : cat ./-file07

flag : 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

LEVEL 5 --> LEVEL 6 :
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable 1033 bytes in size not executable

command : ssh bandit5@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

go to inhere folder enter the command to find the file mentioned in the question

bandit5@bandit:~/inhere$ find . -type f -size 1033c -readable ! -executable ./maybehere07/.file2

now cat the file to read the flag

bandit5@bandit:~/inhere$ cat ./maybehere07/.file2

flag : HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

LEVEL 6 --> LEVEL 7 :
The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7 owned by group bandit6 33 bytes in size

command : ssh bandit6@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

navigate to root directory command : cat /

now lets search for the file in the server

command : bandit6@bandit:/$ find -size 33c -user bandit7 -group bandit6 -type f 2>/dev/null

./var/lib/dpkg/info/bandit7.password

now lets cat the contents of the file

command : cat ./var/lib/dpkg/info/bandit7.password

flag : morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

LEVEL 7 --> LEVEL 8 :
The password for the next level is stored in the file data.txt next to the word millionth

command : ssh bandit7@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

command : cat data.txt | grep millionth

flag : dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

LEVEL 8 --> LEVEL 9 :
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

command : ssh bandit8@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

command : sort data.txt | uniq -u

sort will arrange the file in alpahbetical order and uniq will remove the duplicates

flag : 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

LEVEL 9 --> LEVEL 10 :
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

command : ssh bandit9@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

since the data.txt is in a non human format we use strings to convert it into human readable format and grep = to find the flag

command : strings data.txt | grep =

flag : FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

LEVEL 10 --> LEVEL 11
The password for the next level is stored in the file data.txt, which contains base64 encoded data

command : ssh bandit10@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

When we cat the data.txt it is in the base64 encoded format : VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==

we want to decode this to find the flag

command : cat data.txt | base64 -d

flag : dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

LEVEL 11 --> LEVEL 12
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

command : ssh bandit11@bandit.labs.overthewire.org -p 2220

use the previous flag as password to login

cat data.txt to see the contents inside the file : Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4 , looks like it is encoded with rot13 lets decode it

use online rot13 decoder to find the flag

flag : 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
