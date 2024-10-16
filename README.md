# OverTheWire
- This will document my journey through OverTheWire
- You can follow along at https://overthewire.org/wargames/bandit
# Level 0
- "The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1."
#
- This level is very straightforward. 
- To do this we need to head over to the command line.
- Once there we need to log in using the command below.
- ssh -p 2220 bandit0@bandit.labs.overthewire.org
- After we are logged in we can enter the password provided and continue to the next level.
# Level 0-1
- "The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game."
- "Commands you may need to solve this level
ls , cd , cat , file , du , find"
# 
- To find the readme file we need to use the ls command. The ls command will list the files in the current folder.
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
- When we try the cat command on this file it does not work correctly.
- Since using - will not work correctly we can specify the path to concatenate.
- The command is cat ./-
- The password is 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
# Level 2-3 
- "The password for the next level is stored in a file called spaces in this filename located in the home directory"
- "Commands you may need to solve this level - ls , cd , cat , file , du , find"
# 
- After we log in we use the ls command to list what is in the folder.
- We see that there is a file named "spaces in this filename"
- If we try to use the command cat spaces in this filename we get some errors.
- The cat command works on multiple files when separated with a space.
- When we entered "cat spaces in this filename" the command tried to concatenate each word as a different file.
- Since this is one file and not multiple this does not work.
- We need a way to specify that this is one file.
- We can specify this is a single file by putting quotes around the filename.
- The command is - cat "spaces in this filename"
- The password we get is MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
# Level 3-4 
- "The password for the next level is stored in a hidden file in the inhere directory."
- "Commands you may need to solve this level - ls , cd , cat , file , du , find"
#
- After we are logged in we use the ls command to see the contents again.
- We see that there is a directory named "inhere"
- We are going to use a new command to change directories. The command is cd.
- We use the command "cd inhere" and we are able to change directories.
- Once we are in the inhere directory we search the contents using the ls command.
- When we do this, we do not see anything.
- This is because the file is hidden. To see the file we can use the command ls -a which will list all files including hidden ones.
- When we do that, we can see a file named ...Hiding-From-You
- We then use the cat command to extract the password.
- The command is cat ...Hiding-From-You
- The password is 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
# Level 4-5
- "The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command."
- "Commands you may need to solve this level - ls , cd , cat , file , du , find"
#
- After we are logged in we use ls to see that inhere directory is there.
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
- Once inside the directory we use the ls -la command to look at all of the files in long format including the hidden ones.
- We can see that there are quite a few folders in here.
- Let's see if there are files inside of one of these folders.
- We can use the same command but point it at a folder.
- We use ls -la maybehere00 and see that there are a lot of files in just this one folder alone.
- We can assume that it would take too long to go through every single folder.
- We need to figure out a quicker way to find what we're looking for.
- In order to do this we can utilize the find command.
- The find command can search in various ways. It can find file types, and directories, and search by file size, etc.
- We can do this a couple of ways but let's just cut straight to the chase and try to search for the specific properties we need.
- To do that we can run this command. find -type f -size 1033c -readable ! -executable
- -type f tells it to only look for files
- -size 1033c tells it to only look for files that are 1033 bytes in size
- -readable tells it to only include readable files
- ! -executable excludes files that are executable because the ! negates the executable option. Therefore it returns only files that are not executable.
- We can also just search for files that are exactly 1033 bytes in size by using the command find -size 1033c.
- Both of these return us the same thing which is ./maybehere07/.file2
- We use the cat command to give us the password which is HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
# Level 6-7
- "The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, and 33 bytes in size."
"Commands you may need to solve this level - ls , cd , cat , file , du , find , grep"
#
- After we log in let's use the ls command to see what's going on.
- There are no files in here and if we use the ls -la command we do not find anything useful.
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
- After we are logged in we use the ls command and see the data.txt file.
- We can use the du command to check disk usage to see how big the data.txt file is.
- The command du -b data.txt will return us the exact amount of bytes the file is.
- When we enter the command we can see that the file is 4184396.
- We know from this that it would not be efficient to concatenate the whole file.
- We need another way to search for what we are looking for inside of the file.
- To do this we can use the grep command to search for the specific string we were given.
- We also need to use the pipe tool. This will connect the output of one command to the input of another. In this case, it will be cat and grep.
- When we enter "cat data.txt | grep millionth" we are telling the command line to print the contents of the data.txt file via cat and send it to grep which searches the content to find the word millionth.  
After we enter the command we can see the password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
# Level 8-9
- "The password for the next level is stored in the file data.txt and is the only line of text that occurs only once."
- "Commands you may need to solve this level - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd"
#
- Ok, let's check out what is in the folder.
- We see that there is a data.txt file in here.
- Let's check how big the file is using the same command as we did in the previous level.
- We can see that the file is 37831 bytes.
- Let's try something new and use the sort command.
- The sort command is used to sort the lines of text in alphabetical order. 
- When we run sort data.txt we can see that there are a ton of strings that are returned to us in alphabetical order.
- If we wanted we could take the time to find the line that occurs only once but this would be tedious.
- In order to find the line that only occurs once we can use the uniq command.
- The uniq command works by filtering out consecutive duplicate lines. 
- Therefore, this only works if we are able to first sort the lines.
- Let's try using what we learned previously with piping and send the sort output to uniq input.
- When we run "sort data.txt | uniq" we are presented with a list of lines that are all different.
- What this did was sort the lines in alphabetical order and then filter out any duplicates.
- We need to take this a step further and find the one line that only occurs once.
- To do this we need to use uniq -u.
- What this will do is display the "unique" line that only appears once. 
- When we run the command sort data.txt | uniq -u we find the password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
# Level 9-10
- "The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters."
- "Commands you may need to solve this level - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd"
#
- In this level, we will need to learn the strings command.
- The strings command is used to find human-readable strings in files.
- When we log into this level and concatenate the data.txt file we can see that there are a bunch of unreadable characters along with some letters and numbers.
- If we just ran the strings command by itself on the data.txt file it shows us every sequence of human-readable characters.
- We can find our answer by doing this but the challenge states that the string we are looking for is preceded by several "=" characters so let's incorporate that with the grep command.
- To do that we send the output of the strings data.txt command to a grep command.
- This is done with the syntax strings data.txt | grep ===
- This returns us with a few different strings but we can see which one is the password we're looking for. FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
# Level 10-11
- "The password for the next level is stored in the file data.txt, which contains base64 encoded data."
- "Commands you may need to solve this level - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd"
#
- Since the directions state that the data.txt file contains base64 encoded data I assume that we will use a base64 command.
- First, let's start by taking a look at what is inside the data.txt file when we just run the cat command.
- It looks like there is a string of encoded data so we need to figure out how to decode it.
- If we just run the command base64 data.txt we are actually just encoding it and we get an even longer string than before.
- We need to decode the file and its contents and to do that we can use base64 -d.
- When we run the command base64 -d data.txt we get the decoded data which is, "The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr."
# Level 11-12
- "The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions"
- "Commands you may need to solve this level - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd"
#
- For this level, we are going to learn a new command.
- The instructions on the website list Rot13 as helpful reading material.
- When we look we can see that "ROT13 is a simple letter substitution cipher that replaces a letter with the 13th letter after it in the Latin alphabet.
- If we look inside the data file we can see that there is a string of characters that we need to decipher.
- To do this we will use the tr command, which stands for translate.
- We first need to concatenate the data.txt and send the output to the tr command via piping.
- We also need to tell the tr command what to look for.
- We first want to define the range of letters, so to include all upper and lower case letters we can use 'A-Za-z'
- Next, we want to define how the characters in the first set will be deciphered. Remember ROT13 rotates by 13 places.
- To do that the command is 'N-ZA-Mn-za-m'
- We do not need to worry about numbers since Rot13 only affects alphabetic letters.
- the final command is cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
- The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
# Level 12-13
- "The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)"
- Commands you may need to solve this level - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file"
#
- The first thing we need to do when starting this level is to create a new directory so that we can copy the contents of the directory and then modify and create new files.
- We cannot do this in the current location.
- To do this we will use the mkdir command.
- First, we will navigate the/tmp directory using cd /tmp
- Next, we'll create the new directory using mktemp -d and then use cd to access the newly created directory.
- Now we can us the cp command to copy the data.txt file into the directory. cp ~/data.txt .
- We can now use the ls command to see that our data.txt file was copied into the directory.
- Now we can to rename the data.txt file to hexdump using the mv command. mv data.txt hexdump
- When we take a peak inside of the hexdump file we can see that is readable to us. cat hexdump | head
- Since we can read it we know that it is in hexdump format and in order to work with the original data we need to convert it back to a binary file.
- To do that we will use the xxd -r command which will revert it back. xxd -r hexdump compressed
- Now we need to decompress the data but to do that we need to figure out which decompression to use.
- Let's run the cat command on the hexdump file to try to find a clue.
- When we do that we can see that the first line starts with 1f8b 08, which means we need to use gzip to decompress it.
- In order to decompress it we need to first rename the file. mv compressed compressed.gz
- Next, we need to decompress the file using the gzip command. gzip -d compressed.gz
- After that, we can run xxd compressed and see that it still needs to be decompressed further.
- From the first line we can see that 425a 68, which after searching reveals to be bzip version 2.
- Knowing this we can follow the same steps as before. mv compressed compressed.bz2 and then follow it up with bzip2 -d compressed.bz2
- After running the xxd command again we see that the file is still compressed using gzip again.
- We follow the same steps to decompress further. mv compressed compressed.gz and then follow it up with gzip -d compressed.gz
- Alright, now when we run the xxd command we see that we have something new to work with.
- In the first line we can spot a data5.bin string.
- In order to extract the file we'll use the tar command.
- First, we need to rename the file and then we can use the tar command to extract the file. mv compressed compressed.tar followed by tar -xf compressed.tar
- This time when we ls the files in the directory we can see the data5.bin file in there as well.
- Now we can run the same xxd command on the data5.bin file and we see another file named data6.bin in the first line.
- We'll follow the same process to extract that one. tar -xf data5.bin
- Now we can see the new data6.bin file using the ls command.
- Next, we'll use xxd to see what's going on with it and see we need to decompress using bzip2 agian. bzip2 -d data6.bin
- We are returned with "bzip2: Can't guess original name for data6.bin -- using data6.bin.out" so now we use the tar command to extract further. tar -xf data6.bin.out
- When we search the directory now we find a new file named data8.bin
- After running the xxd command we find out that we need to decompress using gzip again. mv data8.bin data8.gz followed by gzip -d data8.gz
- When we search the directory this time we can see that the data8 file is fully decompressed! ls followed by cat data8
- Password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
# Level 13-14
- "The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on"
- "Commands you may need to solve this level - ssh, telnet, nc, openssl, s_client, nmap"
#
- I started by listing the contents of the current working directory to see what files were available.
- This revealed a file called sshkey.private, which is the SSH private key we'll use to log into the next level.
- To make sure this file is a private key, I used the head command to view the beginning of the file. head sshkey.private
- This displayed the private key, starting with: -----BEGIN RSA PRIVATE KEY-----
- Now that we know this is the correct private key, we can proceed to use it for logging into bandit14.
- I used the SSH command along with the -i flag to specify the private key file and logged in to bandit14. ssh -i sshkey.private -p 2220 bandit14@localhost
- When prompted about the fingerprint confirmation, I typed "yes."
- The -i flag tells SSH to use the private key stored in sshkey.private.
- The -p 2220 specifies the port number (2220), as required by the server.
- We're logging in as user bandit14 on the same machine (localhost) so we use bandit14@localhost
- We can now see in the command prompt that we are logged in as bandit14@bandit.
- We can also use whoami to verify.
- Next, we need to retrieve the password for bandit14
- The instructions tell us that the password is stored in /etc/bandit_pass/bandit14
- Finally, I use the cat command to get the password. cat /etc/bandit_pass/bandit14
- The password is MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
# Level 14-15
- "The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost."
- "Commands you may need to solve this level - ssh, telnet, nc, openssl, s_client, nmap"
#
- For this level, I will just continue as bandit14 from the previous level since I am already logged in.
- Next, I needed to submit the password to port 30000 on localhost.
- To do that I will use the command nc localhost 30000
- nc (netcat) is a command-line tool used to send and receive data over a network. It’s great for creating client-server connections or listening on ports.
- localhost refers to the current machine we are logged into. Its IP address is 127.0.0.1. This allows us to access network services running on the same machine.
- After running the command nc localhost 30000 I used the password for the current level to obtain the password for the next level.
- The password is 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
# Level 15-16
- "The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption."
- "Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage."
- "Commands you may need to solve this level - ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss"
#
- The task specifies that I need to send the password for bandit15 to port 30001 on localhost using SSL encryption. To do this, I'll use the openssl s_client command, which allows me to connect to a server using SSL/TLS.
- SSL (Secure Sockets Layer) and TLS (Transport Layer Security) are protocols that provide encryption for secure communication over a network.
- In this case, the communication with port 30001 needs to be encrypted using SSL.
- To establish a secure connection to port 30001 on localhost, I used the following command: openssl s_client -connect localhost:30001
- The command openssl s_client is a command-line tool provided by the OpenSSL library. It acts as a simple client to establish a connection using SSL/TLS.
- The command -connect localhost:30001 tells the openssl client to connect to localhost (the same machine) on port 30001, which requires SSL encryption.
- Once connected I entered the password for the current level.
- After that, I was given the password for the next level.
- The password is kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
# Level 16-17
- "The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it."
- "Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage."
- "Commands you may need to solve this level - ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss"
#
- We know that the service we need is running on one of the ports between 31000 and 32000, so I used the nmap command to scan for services within that range. nmap -sV -T4 -p 31000-32000 localhost
- nmap is a command-line tool used for network scanning. It helps identify open ports, the services running on those ports, and sometimes the versions of those services.
- -sV tells nmap to attempt service version detection. In this case, it will try to identify the type of service running on each open port and report its version. This is crucial to figure out which ports are running SSL or other protocols.
- -T4: The -T option controls the speed of the scan. T4 is an aggressive timing option that makes the scan faster without sacrificing too much accuracy. This is useful for getting results quickly.
- -p 31000-32000 specifies the range of ports to scan. We are focusing on ports between 31000 and 32000 because the task specifies that the service we need to find is within this range.
- localhost refers to the current machine we are working on (the Bandit server), using its IP address 127.0.0.1. By scanning localhost, we’re checking for services running on the same machine, rather than on a remote server.
- The scan results showed five open ports within the specified range. Among these, only two ports (31518 and 31790) were using SSL encryption, which is a key requirement for this task.
- Port 31518: Runs an ssl/echo service. The echo service simply returns whatever data is sent to it, which makes it unlikely to be the correct service for this challenge.
- Port 31790: Runs an SSL-encrypted service but is labeled as ssl/unknown, which indicates it is not easily identifiable by nmap. Additionally, this service returns the message “Enter correct password,” suggesting that this is the service we need to interact with.
- Given this, port 31790 is the most promising candidate for submitting the current password.
- Now that we know the service on port 31790 uses SSL encryption, I used openssl s_client to securely connect to the service and send the current level’s password:










