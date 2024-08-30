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
# Level 1
- "The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game."
- "Commands you may need to solve this level
ls , cd , cat , file , du , find"
# 
- In order to find the readme file we need to use the ls command. The ls command will list the files in the current folder.
- When we enter ls we can see that the only file in the current folder is the readme file.
- To read the content in this file we can use the cat command which is short for concatenate.
- The cat command will read the file and print the output in standard format to the console.
- once we enter the command "cat readme" we are presented with the password - ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
# Level 2
- "The password for the next level is stored in a file called - located in the home directory"
- "Commands you may need to solve this level
ls , cd , cat , file , du , find"
# 
- To log into the next level we need to use ssh again.
- After we are logged in we need to find the password.
- If we use the ls command again we can see a file named -
- When we try to the cat command on this file it does not work correctly.
- 
