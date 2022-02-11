# How to log into a course-specific account on ieng6

## 1. Install VS Code

To download VS Code, go to [vs code download link](https://code.visualstudio.com/) and follow the instructions designed for you're type of computer. There should be versions for all of major operating systems, but if you have something like a chromebook, you won't be able to download it for now. 

When I finally had it installed, was able to open a VS code window like in the image below. 

![vs code](https://user-images.githubusercontent.com/94486303/149598386-314b0d6c-afe1-4df3-8ead-aebde3ae19a9.png)

## 2. Remotely Connecting

Now that I had VS Code, I used it to connect to a remote computer over the internet.

First, since I'm on Windows I installed a program called OpenSSH
- [ssh link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)
- This is a program that can connect my computer to other computers that have this kind of account

Second, I found my specific account. Since I'm in CSE 15L, I used the link below
- [Account link](https://sdacs.ucsd.edu/~icc/index.php)

Finally, I used the instructions in the link below to connect to the remote computer using VSCode’s remote option.
- [vs code instructions link](https://code.visualstudio.com/docs/remote/ssh#_connect-to-a-remote-host)

Now, to log in to my course-specific account I opened up a new terminal in VS Code. In the command I wrote my username after ssh: "$ ssh cs15lwi22acs@ieng6.ucsd.edu" ('acs' being my own letters in my course-specific account). And since this is the first time I'vs connected to this server, I got the message:

```
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```

Typed yes and press enter, then gave my password. Once I logged in, I saw the message: 

![terminal image](https://user-images.githubusercontent.com/94486303/149599607-ec3c087d-aa01-40ee-994b-090b60e7aaa6.png)

Now my terminal is officially connected to a computer in the CSE basement. 

## 3. Trying some commands

After logging in I played around with the Terminal by running some commands. Example commands that we were given are below: 


- cd ~
- cd
- ls -lat
- ls -a
- cp /home/linux/ieng6/cs15lwi22/public/hello.txt ~/
- cat /home/linux/ieng6/cs15lwi22/public/hello.txt

Mine looked something like this:

  ![terminal image](https://user-images.githubusercontent.com/94486303/149600104-caa6efee-5bbd-4948-bad9-fe2757339501.png) 

Side note: To log out of the remote server in your terminal, you can Ctrl-D or run the command `exit`


## 4. Moving Files with scp

To copy a file from my computer to a remote computer, I used the `scp` command. For example, if I had a file called WhereAmI.java, I would use the command:
- `scp WhereAmI.java cs15lwi22zz@ieng6.ucsd.edu:~/`

*One thing to remember: you must be in the terminal from the directory where you made this file to run this command. 

Overall, it looked something like this:

![scp image](https://user-images.githubusercontent.com/94486303/149600684-5a956e63-dee7-45f6-94a4-74752cca318c.png)

To check if it's there, I logged into ieng6 with ssh again, and used the ls commmand. There I saw the file there in my home directory.
  
## 5. Setting an SSH Key

What is an SSH Key? SSH keys use a program called ssh-keygen to create a pair of files called the public key and private key. You copy the public key to a particular location on the server, and the private key in a particular location on the client. Then, the ssh command can use the pair of files in place of your password.

To set this up, I typed ssh-keygen into my terminal. This generated the key pair and prompted me to enter a file in which to save the key. Then, after entering a passphrase of my choice, my keys and fingerprint were saved. The process should be like the image below: 

![ssh jey image1](https://user-images.githubusercontent.com/94486303/149603998-7b1a8bef-2bd5-41e4-b563-0b1cef7458ca.PNG)
![ssh key image2](https://user-images.githubusercontent.com/94486303/149603955-8c1036f7-6a10-463e-b66a-d9e6c31dba0c.PNG)

Now all that's left is to copy the public key to the .ssh directory of my user account on the server.

```
$ ssh cs15lwi22acs@ieng6.ucsd.edu
<Enter Password>
# now on server
$ mkdir .ssh
$ <logout>
# back on client
$ scp /Users/evank/.ssh/id_rsa.pub cs15lwi22acs@ieng6.ucsd.edu:~/.ssh/authorized_keys
```


## 6. Optimizing Remote Running

To make remote running even more pleasant, I used command lines within quotation marks to run everything on the server in the same ssh session:

![optimize ssh](https://user-images.githubusercontent.com/94486303/149604443-6d1268f6-180d-4955-9c61-f4da2a65a222.PNG)

You can do this with all different commands as well as multiple commands at once (as long as you separate them with semocolons.
Ex. 
```
scp WhereAmI.java cs15lwi22acs@ieng6.ucsd.edu:~/ ; ssh cs15lwi22acs@ieng6.ucsd.edu "javac WhereAmI.java ;  java WhereAmI"
```
The single line that I used above will log into my course-specific account, scp the WhereAmI.java file, compile and run it. 



