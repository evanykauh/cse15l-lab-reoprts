# Lab Report #5
### Evan Kauh
### March 11, 2022


### How I found the tests with different results:
I ran `diff`, comparing my results.txt file with the results.txt file from the markdown-parse provided in week 9. 

command run: ``diff my-markdown-parse/results.txt markdown-parse/results.txt``

## BUG #1
![bug 1 img](https://user-images.githubusercontent.com/94486303/157859826-6c3a66c1-cba3-437a-8f77-66cb241f84c7.png)

The markdown-parse.java implementation provided in week 9 returns `[moon.jpg]` in the array whereas the my-markdown-parse.java that I created returns an empty array. The correct output is an empty array since jpgs are not supposed to be added to the array as a link, which means that the provided markdown-parse has a problem in its code.

![markdown img bug1](https://user-images.githubusercontent.com/94486303/157859062-56665787-df73-420c-b623-ca779fc87d17.png)

As seen in the code above, the getLinks method never checks for .jpg tags before adding the "link" to the array and returning it. The way that I fixed this bug in my own program was that I created a string array of tags containing `.jpg`, `.png`, `.jpeg`, etc., and iterated through them, ensuring that the substring that was to be added to toReturn did not contain any of the tags. If it did, I would break out of the for loop before the code could add the substring to toReturn. 


## BUG #2
![bug 2 img](https://user-images.githubusercontent.com/94486303/157860270-e9f3793f-7062-475b-9093-c57267ae38ab.png)

In the screenshot above, my-markdown-parse returns an empty array with the given test file whereas the provided markdown-parse returns `[foo%20b&auml;]`. The correct output would return an empty array since `foo%20b&auml;` is not a correctly formatted link. This means that the provided markdown-parse has another problem in its code.

![markdown img bug2](https://user-images.githubusercontent.com/94486303/157861480-a9f34f4e-a600-4534-89de-00e9353991bd.png)

Nowhere in their code does getLinks() ever check for a `.com`, `.org`, or anything that may indicate that the substring is a functional link. To fix this, I might add a line of code that simply checks if the substring even contains a period:

`if(!markdown.substring(openParen+1, closeParen).contains(".")) break; `

This would resolve this particular bug since `foo%20b&auml;` does not contain a "." and thus cannot be a legitimate link. 