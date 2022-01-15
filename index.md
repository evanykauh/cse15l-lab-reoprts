# How to log into a course-specific account on ieng6

## 1. Install VS Code

To download VS Code, go to [vs code download link](https://code.visualstudio.com/) and follow the instructions designed for you're type of computer. There should be versions for all of major operating systems, but if you have something like a chromebook, you won't be able to download it for now. 

When you do have it finally installed, you should be able to open a VS code window like in the image below. 

![vs code](https://user-images.githubusercontent.com/94486303/149598386-314b0d6c-afe1-4df3-8ead-aebde3ae19a9.png)

## 2. Remotely Connecting

Now that we have VS Code, let's use it to connect to a remote computer over the internet.

First, if you’re on Windows: install a program called OpenSSH
- [ssh link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)
- This is a program that can connect your computer to other computers that have this kind of account

Second, find you're course specific account. Since I'm in CSE 15L, I will use the link below
- [account link](https://sdacs.ucsd.edu/~icc/index.php)

Finally, use the instructions in the link below to connect to the remote computer using VSCode’s remote option.
- [link](https://code.visualstudio.com/docs/remote/ssh#_connect-to-a-remote-host)

Now open up a new terminal in VS Code. Your command should say "$ ssh cs15lwi22zz@ieng6.ucsd.edu" but with the "zz" replaced by the letters in your course-specific account. And since this is the first time you’ve connected to this server, you will probably get a message like this:

```
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```

Type yes and press enter, then give your password. Once you're logged in, you should see something like this: 

![terminal image](https://user-images.githubusercontent.com/94486303/149599607-ec3c087d-aa01-40ee-994b-090b60e7aaa6.png)

Congratulations! Now your terminal is officially connected to a computer in the CSE basement. 

## 3. Trying some commands

Now you can play around with the Terminal by running some of the commands below: 


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

To copy a file from your computer to a remote computer, you use the `scp` command. For example, if I had a file called WhereAmI.java, I would use the command:
- `scp WhereAmI.java cs15lwi22zz@ieng6.ucsd.edu:~/`

Remember, you must be in the terminal from the directory where you made this file to run this command. Overall, it'll look something like this:

![scp image](https://user-images.githubusercontent.com/94486303/149600684-5a956e63-dee7-45f6-94a4-74752cca318c.png)

To check if it's there, log into ieng6 with ssh again, and use ls. You should see the file there in your home directory.
  
## 5. Setting an SSH Key

What is an SSH Key? SSH keys use a program called ssh-keygen to create a pair of files called the public key and private key. You copy the public key to a particular location on the server, and the private key in a particular location on the client. Then, the ssh command can use the pair of files in place of your password.

To set this up, type ssh-keygen into your terminal. This will generate the key pair and prompt you to enter a file in which to save the key. Then, after entering a passphrase of your choice, your keys and fingerprint should be saved. The process should be like the image below: 

![ssh key image](https://user-images.githubusercontent.com/94486303/149601417-1e84ab1c-ef45-44ee-ab3c-a146e1175574.png)

Now all that's left is to copy the public key to the .ssh directory of your user account on the server.

```
$ ssh cs15lwi22zz@ieng6.ucsd.edu
<Enter Password>
# now on server
$ mkdir .ssh
$ <logout>
# back on client
$ scp /Users/joe/.ssh/id_rsa.pub cs15lwi22@ieng6.ucsd.edu:~/.ssh/authorized_keys
# You use your username and the path you saw in the command above
```


## 6. Optimizing Remote Running

To make remote running even more pleasant, I used command lines within quotation marks to run everything on the server in the same ssh session:






