# Lab Report #4
### Evan Kauh
### February 25, 2022

*Note: (1) CommonMark demo site was used to determine what should be produced by text in code snippets and (2) I used Ryan Rong's markdown-parse repository from week 7

*[Link to my Repository](https://github.com/evanykauh/markdown-parse)

*[Link to Ryan Rong's Repository](https://github.com/RyanRongY/markdown-parse)


## What Should be Produced by getLinks()
(as determined by [CommonMark Demo Site](https://spec.commonmark.org/dingus/))


Snippet 1: [`google.com, google.com, ucsd.edu];

Snippet 2: [a.com, a.com(()), example.com]

Snippet 3: [https://ucsd-cse15l-w22.github.io/, example.com]

## How I turned it into a test in MarkdownParseTest.java
![test imgs](https://user-images.githubusercontent.com/94486303/155830143-6d89eff5-031c-4338-9dbc-840a7ff1de52.png)

## My implementation 
### None of my tests passed :(

### Test of Snippet 1:
![test result 1](https://user-images.githubusercontent.com/94486303/155830236-6d3773d7-fd07-49a8-bc52-7b4287dda125.png)

### Test of Snippet 2:
![test result 2](https://user-images.githubusercontent.com/94486303/155830244-d2616a2b-b5a9-4325-bbce-172dbc89b18b.png)

### Test of Snippet 3:
![test result 3](https://user-images.githubusercontent.com/94486303/155830259-9b0dbcf7-24f1-4b48-ae80-7ed399e42489.png)


## Ryan's implementation (the repo I reviewed in week 7)

### Test of Snippet 1:
![test result 1](https://user-images.githubusercontent.com/94486303/155834702-46a13378-2350-45b9-a3f1-5f2871f07e4d.png)

### Test of Snippet 2:
![test result 2](https://user-images.githubusercontent.com/94486303/155834752-bb10d7a8-b50d-420a-8cf5-3811b6c3b899.png)

### Test of Snippet 3:
![test result 3](https://user-images.githubusercontent.com/94486303/155834763-e8fcfd3a-264c-4dc1-800e-32581a2b4534.png)


## Answer the following questions with 2-3 sentences each:

### Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.

Yes. Having two ` marks inside and outside the brackets is supposed to break the link and produce no output. This is a special case that can be fixed by simply editing the if{} statement that adds the substring to toReturn. For example, I would add an && that doesn't execute the add() statement if there is a mark adjacent to the bracket and within it. 

### Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.


Yes, I do think that there is a simple change that could be made. To fix my progam to work for snippet 2, I would edit the statement that sets the closeParen index so that it ensures that it is the actual end of the link. For example, it would check if there is a next open bracket right after (indicating that it is the end of the link and the start of the next one) or if there exists no other close parenthases in the file all together, before setting the closeParen index. 

### Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.

No, because there are multiple issues in my program that need to be addressed for snippet 3 to pass the tests. (1) twitter.com should not appear as a link in the output, and even if it did, the extra space should be trimmed. (2) github.com should not appear in the output since there is no close parenthases before the beginning of the next link. This is a more involved change that may take around ten lines by itself since it's not a simple case that can be fixed by an if{} else{} statement. 