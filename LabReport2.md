# Lab Report #2
### Evan Kauh
### January 26, 2022

## Code Change #1

 ![commit1](https://user-images.githubusercontent.com/94486303/151503604-d2ae7c26-fc32-4c0a-9263-592322d4b058.png)

### Failure-inducing input: 

Text file that broke code: [text-file-3](https://evanykauh.github.io/markdown-parse/test-file-3)


### Symptom (command line)

![cmdLine1](https://user-images.githubusercontent.com/94486303/151503435-ffe490ed-49b0-45d2-b923-a1459c6809e6.png)

In the command line above, I call the MarkdownParse class on test-file-3.md, which reveals a bug in my code: if there is a close parenthases ')' within the link, the link will be cut short at that index in the output (as seen in the third link). The symptom in this scenario is the incorrect output that is produced as a result of the failure-inducing input. The third link in the array is supposed to be *https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574(v=vs.85)?redirectedfrom=MSDN* and not *https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574(v=vs.85*.  

- 2-3 sentences here

// TODO: Pick three code changes that your group worked on in labs 3 and 4 in order to fix a bug; these should be stored as commits on someone’s repository. Fork the repository so you have your own copy with all the work your group did if you haven’t already.

//For each of the three code changes:

1. Show a screenshot of the code change diff from Github (a page like this)
2. Link to the test file for a failure-inducing input that prompted you to make that change
3. Show the symptom of that failure-inducing input by showing the output of running the file at the command line for the version where it was failing (this should also be in the commit message history)
4. Write 2-3 sentences describing the relationship between the bug, the symptom, and the failure-inducing input.

// the link to the test file should be a link to a file like https://evanykauh.github.io/cse15l-lab-reoprts/newfile

