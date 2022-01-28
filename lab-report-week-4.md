## Erick Gulyan
**CSE 15L Week 4 Lab Report** 
---
Hello and Welcome to my Week 4 Lab Report where I will show you three different commits our lab group did to improve the MarkdownParse file.

1) We noticed that when the file we were working with had brackets or parenthensis which remained open and never closed, the code showed an infinite loop error and ran out of space on the heap. This error can be shown in the image below.

The file used was [this file](https://github.com/erick-gulyan/markdown-parse/blob/main/test2-infiniteloop.md?plain=1).

<img width="585" alt="loopbreaking" src="https://user-images.githubusercontent.com/97641133/151503778-7914225f-7876-4a82-9f19-5b3d3fea99f2.png">

To resolve this, we added code to check for the values of `nextOpenBracket`, `nextCloseBracket`, `openParen`, `closeParen`, to be -1. If so, then the code would break and thus, avoiding an infinite loop.
<img width="1401" alt="loops" src="https://user-images.githubusercontent.com/97641133/151503635-e0f3fb07-b165-45f4-9b5f-718ab240eca2.png">

The bug in the code is in the getLinks method where if the values of `nextOpenBracket`, `nextCloseBracket`, `openParen`, `closeParen` are not necessarily declared due to lack of them, the code will keep looping until it's found, which doesn't need to happen. The symptom of this is the terminal showing that the code runs infinitely until the heap has filled up and breaks. The failure inducing input in my file was the lack of `)` in the file to end the search.






---
