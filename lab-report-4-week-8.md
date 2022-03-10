## Erick Gulyan, Lab 4 Week 8 Report
---
For the Three code snippets provided, I created a set of three tests to run on both my implementation of `markdown-parse` and another member of my lab group's implementation.

When running the test on my version of MD parse, the results are below:

<img width="1440" alt="workingtestonmyMDparse" src="https://user-images.githubusercontent.com/97641133/155817294-c28d0081-c5f4-4838-a099-1da177a51dad.png">

The photo above also shows the tests and their contents. Note snippet1/2/3 all correspond to the snippets given in the lab instructions.
## All tests are passing on my own MD Parse.

I have also included a photo showing these changes committed to my `markdown-parse` repository.

<img width="964" alt="commit" src="https://user-images.githubusercontent.com/97641133/155817394-82f7cd9e-ce32-44eb-849a-3ead8d0d123e.png">

## Kathy's MarkdownParse
[Link to repository](https://github.com/kathyychenn/markdown-parse)

When running the tests on Kathy's `markdown-parse`, I found that ALL Three Tests failed,  as shown below:

<img width="865" alt="kathy_tests_MDPARSE" src="https://user-images.githubusercontent.com/97641133/157586863-e75d53d5-e5d7-4d78-a720-9d317068894f.png">




## Fixing Changes to Kathy's MD Parse

### Code Snippet 1:
The test failed and showed the output: 

``java.lang.AssertionError: expected:<[google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.snippet1Test(MarkdownParseTest.java:68)``
        
There is a short fix to the markdown parse java file which could fix this issue. I believe if we add variables to keep track of the backtick character similar to parenthensis and brackets. With this, we can check to see if the backticks are located outside of the brackets to declare a link, or inside. This would fix the issue of the included backticks in the link. 
        
 
 
### Code Snippet 2:
The test failed and showed the output:

`java.lang.AssertionError: expected:<[a.com, a.com(()), example.com]> but was:<[a.com((]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.snippet2Test(MarkdownParseTest.java:76)`

This output tells us that markdownparse isnt updating the locations of the parenthensis correctly, thus adding extra items to the list.
 One short way to fix this could be to update the value of the lastClosedParenthensis at the beginning of the method to accurately find the last closed parenthensis and thus would avoid any issues such as the one above.

### Code Snippet 3:
The test failed and showed the output:
                `java.lang.AssertionError: expected:<[https://ucsd-cse15l-w22.github.io/]> but was:<[
                 https://ucsd-cse15l-w22.github.io/
                , github.com`

                And there's still some more text after that.

                [this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



                ]>
                        at org.junit.Assert.fail(Assert.java:89)
                        at org.junit.Assert.failNotEquals(Assert.java:835)
                        at org.junit.Assert.assertEquals(Assert.java:120)
                        at org.junit.Assert.assertEquals(Assert.java:146)
                        at MarkdownParseTest.snippet3Test(MarkdownParseTest.java:84)
        
 This output tells us that markdownparse isn't working correctly when dealing with the use of a `\n` character, by including them in the links area instead of ignoring the white space and `\n` characters. To fix this in one line, it would be best to add an if statement to check if the `\n` character was used after: `(,),[,]` and update the indices appropriately. 






