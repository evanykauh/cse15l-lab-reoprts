# Lab Report #2
### Evan Kauh
### January 26, 2022

## Code Change #1

 ![commit1](https://user-images.githubusercontent.com/94486303/151503604-d2ae7c26-fc32-4c0a-9263-592322d4b058.png)

### Failure-inducing input: 

Text file that broke code: [text-file-3.md](https://evanykauh.github.io/markdown-parse/test-file-3)


### Symptom (command line)

![cmdLine1](https://user-images.githubusercontent.com/94486303/151503435-ffe490ed-49b0-45d2-b923-a1459c6809e6.png)

In the command line above, I call the MarkdownParse class on test-file-3.md, which reveals a bug in my code: if there is a close parenthases ")" within the link, the link will be cut short at that index in the output (as seen in the third link). The symptom in this scenario is the incorrect output that is produced as a result of the failure-inducing input. The third link in the array is supposed to be *https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574(v=vs.85)?redirectedfrom=MSDN* and **not** *https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574(v=vs.85*.  

I fixed this by implementing a while loop that checks to make sure that the saved closeParen is the index where the link actually ends, and if not, iterate through to the next closeParen and repeat the process. 

## Code Change #2

![commit2](https://user-images.githubusercontent.com/94486303/151638961-f3e55c1e-dc15-43a7-b108-5532c8df6921.png)

### Failure-inducing input: 

Text file that broke code: [text-file-2.md](https://evanykauh.github.io/markdown-parse/test-file-2)


### Symptom (command line)

![cmdLine2](https://user-images.githubusercontent.com/94486303/151637138-f2c3f4af-8c42-4437-81a4-d1fce0b326c2.png)

In this test I call the MarkdownParse class on test-file-2.md, which reveals the bug that if the code were to come across the "!" in front of an image link, the code would include the image tag and attach that link to the previous link. The symptom in the command line is the incorrect output: *[https://www.youtube.com/watch?v=dQw4w9WgXcQ)
![another link!](https://images-na.ssl-images-amazon.com/images/I/91MteSqsrJL.jpgage.html)
[breaking link](https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574(v=vs.85)?redirectedfrom=MSDN)
[last link](https://www.adultswim.com/videos/rick-and-morty]*.

I fixed this bug by implementing an if() statement that checks if there is an "!" infront of the next openBracket (this indicates an image link). If there is, it terminates the nested while loop and continues on with the rest of the code normally. 

## Code Change #3

![commit3](https://user-images.githubusercontent.com/94486303/151637208-01650554-5dac-4f5a-b26a-b1aca7d18451.png)

### Failure-inducing input: 

Text file that broke code: [text-file-4.md](https://evanykauh.github.io/markdown-parse/test-file-4)


### Symptom (command line)

![cmdLine3](https://user-images.githubusercontent.com/94486303/151637363-ec6e3c39-0f57-415f-8696-56329cb934c9.png)

Lastly, I test test-file04.md (failure inducing input) which causes a bug in my nested while loop. Since there are no brackets or parenthases to find the index of, the while loop runs infinitely without producing any output. As seen above, the symptom is the lack of output no matter how long the program runs the code. 

I fixed this bug by including an if() statement in the beginning, checking if there exists any opening bracket for a link tag in the text file. If not, then the while loop is terminated and an empty array is produced in the ouput. 

