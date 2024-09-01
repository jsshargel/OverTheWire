# OverTheWire
- This will document my journey through OverTheWire
- You can follow along at https://overthewire.org/wargames/bandit
# Level 0
- "The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1."
#
- This level is very straightfoward. 
- To do this we need to head over to the command line.
- Once there we need to log in using the command below.
- ssh -p 2220 bandit0@bandit.labs.overthewire.org
- After we are logged in we can enter the password provided and continue to the next level.
# Level 0-1
- "The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game."
- "Commands you may need to solve this level
ls , cd , cat , file , du , find"
# 
- In order to find the readme file we need to use the ls command. The ls command will list the files in the current folder.
- When we enter ls we can see that the only file in the current folder is the readme file.
- To read the content in this file we can use the cat command which is short for concatenate.
- The cat command will read the file and print the output in standard format to the console.
- once we enter the command "cat readme" we are presented with the password - ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
# Level 1-2
- "The password for the next level is stored in a file called - located in the home directory"
- "Commands you may need to solve this level - ls , cd , cat , file , du , find"
# 
- To log into the next level we need to use ssh again.
- After we are logged in we need to find the password.
- If we use the ls command again we can see a file named -
- When we try to the cat command on this file it does not work correctly.
- Since using - will not work correctly we can specifiy the path in order to concatenate.
- The command is cat ./-
- The password is 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
# Level 2-3 
- "The password for the next level is stored in a file called spaces in this filename located in the home directory"
- "Commands you may need to solve this level - ls , cd , cat , file , du , find"
# 
- After we long in we use the ls command to list what is in the folder.
- We see that there is a file named "spaces in this filename"
- If we try to use the command cat spaces in this filename we get some errors.
- The cat command works on multiple files when seperated with a space.
- When we entered "cat spaces in this filename" the command tried to concatenate each word as a different file.
- Since this is one file and not multiple this does not work.
- We need a way to specifiy that this is one file.
- We can specifiy this is a single file by putting quotes around the filename.
- The command is - cat "spaces in this filename"
- The password we get is MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
# Level 3-4 
- "The password for the next level is stored in a hidden file in the inhere directory."
- "Commands you may need to solve this level - ls , cd , cat , file , du , find"
#
- After we are logged in we use the ls command to see the contents agian.
- We see that there is a directory named "inhere"
- We are going to use a new command to change directories. The command is cd.
- We use the command "cd inhere" and we are able to change directories.
- Once we are in the inhere directory we search the contents using the ls command.
- When we do this we do we do not see anything.
- This is because the file is hidden. In order to see the file we can use the command ls -a which will list all files including hidden ones.
- The when we do that we can see a file named ...Hiding-From-You
- We then use the cat command to extract the password.
- The command is cat ...Hiding-From-You
- The password is 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
# Level 4-5
- "The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command."
- "Commands you may need to solve this level - ls , cd , cat , file , du , find"
#
- After we are logged in we us ls to see that inhere directory is there.
- Then we cd directories using the cd command.
- After we are in the inhere directory we use the ls -la command.
- When we do this we are able to see all files in long format. We could also use just the ls command but the ls -la command might give us more clues.
- Once we do that we still are unable to easily decipher which file is human-readable.
- If we wanted to we could use the cat command to search them one by one but that is not a very good way considering there are 10 files.
- In order to list each file type in the current directory we need to do something new.
- We can use the file command to determine file types.
- But how do we print the file types for every file in the directory?
- We do this by using a wildcard to list all of the file types instead of just one.
- The command is *
- Again we have the file names starting with - so to get around this we use the same solution as before.
- The command is file ./*
- Once we run this command we see that -file07 is ACII text and is different than the others.
- To obtain the password we run the command cat ./-file07
- The password is 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
# Level 5-6
- "The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable, 1033 bytes in size, and not executable."
- "Commands you may need to solve this level -ls , cd , cat , file , du , find"
#
- First things first we will cd into the inhere directory.
- Once inside the directory we us the ls -la command to look at all of the files in long format including the hidden ones.
- We can see that there are quite a few folders in here.
- Let's see if there are files inside of one of these folders.
- We can use the same command but point it at a folder.
- We use ls -la maybehere00 and see that there are a lot of files in just this one folder alone.
- We can assume that it would take too long to go through ever single folder.
- We need to figure out a quicker way to find what we're looking for.
- In order to do this we can utilize the find command.
- The find command can search in various ways. It can find file types, directories, search by file size etc.
- We can do this a couple of ways but lets just cut straight to the chase and try to search for the specific properties we need.
- To do that we can run this command. find -type f -size 1033c -readable ! -executable
- -type f tells it to only look for files
- -size 1033c tells it to only look for files that are 1033 bytes in size
- -readable tells it to only include files that are readable
- ! -executable excludes files that are executable because the ! negates the executable option. Therefore it returns only files that are not executable.
- We can also just search for and files that are exactly 1033 bytes in size by using the command find -size 1033c.
- Both of these return us the same thing which is ./maybehere07/.file2
- We use the cat command to give us the password which is HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
# Level 6-7
- "The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, and 33 bytes in size."
"Commands you may need to solve this level - ls , cd , cat , file , du , find , grep"
#
- After we log in lets use the ls command to see whats going on.
- There are no files in here and if we use the ls -la command we do not find anything usefule.
- Let's use the find command again to see what we can come up with.
- We will use find / to search the root directory.
- Let's try find / -type f -user bandit7 -group bandit6 -size 33c
- When we do this we get a lot of results with a lot of denied permissions.
- However, when we look through them we can see our file since it is the only one without permissions denied.
- If there had been a lot more permissions denied this might take some time to comb through so let's figure out a way to return just what we are looking for.
- We can use 2>/dev/null to hide all of the error messages and this should give us our file.
- The final command is find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
- This returns us /var/lib/dpkg/info/bandit7.password
- We use the cat command to get our password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
# Level 7-8
- "The password for the next level is stored in the file data.txt next to the word millionth"
- "Commands you may need to solve this level - man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd"
#
- 































