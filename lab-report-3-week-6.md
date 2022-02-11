# Lab Report #3
### Evan Kauh
### February 11, 2022



## Copy whole directories with `scp -r`

### 1. `scp` markdown-parse directory to my ieng6 account
![scp img](https://user-images.githubusercontent.com/94486303/153679656-91e35044-2e84-404a-bf31-858a1fad3c56.png)
As seen in the image above, I scp all of the files in the Markdown-parse directory over to my course specific account. The *.java and *.md parts of the `scp` ensure that only files that end in ".java" and ".md" are copied over. 


### 2. Check dir was properly copied
![ls img](https://user-images.githubusercontent.com/94486303/153680178-8d44d3c9-8a65-4f5f-b159-6d23cd277377.png)
After copying the files over to the remote server, I like to check and make sure that they were copo=ied properly. The ls command is helpful as it displays the list of all the files in that current directory within the account. 

### 3. Compile and run tests for markdown-parse repository in ieng6 account
![compile and run img](https://user-images.githubusercontent.com/94486303/153679990-d677a4f8-666d-45d6-bd8c-03fa3d097555.png)
I first had to change the directory into the markdown-parse directory using the `cd` command. Then, to compile and run these newly copied files, I run the javac and java commands as usual. 


### 4. Combining `scp`, `;`, and `ssh` to copy the whole directory and run the tests in one line
![scp and ssh img](https://user-images.githubusercontent.com/94486303/153680767-efd8919d-ab48-4934-b0cf-ab328162564a.png)
Lastly, to practice efficiency, I attempted to do everything in one command line (using scp as well as compiling and running tests). This was done by adding the `;` between `scp`, `ssh`, and java commands. In the end, as seen above, everything runs at once and the tests pass as expected. 