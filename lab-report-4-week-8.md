## Erick Gulyan, Lab 4 Week 8 Report
---
For the Three code snippets provided, I created a set of three tests to run on both my implementation of `markdown-parse` and another member of my lab group's implementation.

When running the test on my version of MD parse, the results are below:

<img width="1440" alt="workingtestonmyMDparse" src="https://user-images.githubusercontent.com/97641133/155817294-c28d0081-c5f4-4838-a099-1da177a51dad.png">

The photo above also shows the tests and their contents. Note snippet1/2/3 all correspond to the snippets given in the lab instructions.
## All tests are passing on my own MD Parse.

I have also included a photo showing these changes committed to my `markdown-parse` repository.

<img width="964" alt="commit" src="https://user-images.githubusercontent.com/97641133/155817394-82f7cd9e-ce32-44eb-849a-3ead8d0d123e.png">

## Lab group member's MarkdownParse
[Link to repository](https://github.com/Rikochu/markdown-parse)

When running the tests on Rishi's `markdown-parse`, I found that test2 and test3 failed, while test1 passed, as shown below:

<img width="839" alt="testsrunonotherperson" src="https://user-images.githubusercontent.com/97641133/155817736-758cc4ee-a811-47cf-b179-d1294f7b1eb6.png">

Also showing running the tests on their MD parse.
<img width="1350" alt="someone elses md parse" src="https://user-images.githubusercontent.com/97641133/155817788-62b87220-0900-4ec0-a426-fd1e0790b52d.png">


## Fixing Changes to Lab Group Member's MD Parse

### Code Snippet 2:
The test failed and showed the output:
`java.lang.AssertionError: expected:<[]> but was:<[a.com, a.com(()), example.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.snippet2Test(MarkdownParseTest.java:49)`
        
 This output tells us that markdownparse isnt updating the locations of the parenthensis correctly, thus adding extra items to the list.
 One short way to fix this could be to update the value of the lastClosedParenthensis at the beginning of the method to accurately find the last closed parenthensis and thus would avoid any issues such as the one above.
 
### Code Snippet 3:
The test failed and showed the output:
`java.lang.StringIndexOutOfBoundsException: String index out of range: 465
        at java.base/java.lang.StringLatin1.charAt(StringLatin1.java:48)
        at java.base/java.lang.String.charAt(String.java:1512)
        at MarkdownParse.findCloseParen(MarkdownParse.java:14)
        at MarkdownParse.getLinks(MarkdownParse.java:36)
        at MarkdownParseTest.snippet3Test(MarkdownParseTest.java:56)`
        
 This output tells us that markdownparse isn't working correctly when dealing with the use of a `\n` character, thus giving us a String index out of bounds exception. To fix this in one line, it would be best to add an if statement to check if the `\n` character was used after: `(,),[,]` and update the indices appropriately. 






