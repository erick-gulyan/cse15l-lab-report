# Lab Report 5 Week 10

# Comparing CommonMark Outputs in Mine and Professor's MarkdownParse

## These steps below is how I went about comparing the outputs of my `Mardown-parse` with the Professor's

1. Ran markdown parse main with the input being all of the files in `test-files` folder using `script.sh`. 
2. Stored the output of the script in `results.txt`in the command line using `bash script.sh > results.txt`
3. Used `diff` command to compare the `results.txt` files from both Professor's and My test results.
4. Added command to print file name in script so I am aware which test file had the differences in `results.txt`.

`diff` command shown below:
<img width="608" alt="Screen Shot 2022-03-11 at 2 12 50 PM" src="https://user-images.githubusercontent.com/97641133/157979026-052d1c7f-ee8b-45fc-bc3a-cc6f6f530ac5.png">

## Test 1 
This test was run on file `576.md` from `test-files/`. The file contents are :
`![foo *bar*][foobar]`
`[FOOBAR]: train.jpg "train & tracks"`

After running the diff command, the differences between my file and the professor's is shown below:

<img width="107" alt="Screen Shot 2022-03-11 at 2 12 23 PM" src="https://user-images.githubusercontent.com/97641133/157978910-04f2eca5-5521-4536-a057-56e76ffc8303.png">

Prof's Output: `[]`
---
My Output: `train.jpg`
---
Expected Output: `[]`
---

I believe that my output is incorrect since the file doesn't follow the proper format for it to be considered a link, the format being:
`[Link](a.com)`. The problem with my code is the inability to understand the `:` character, and thus adding the jpg file to the ArrayList.
Instead, the file uses a `:` after the last closed bracket, thus this isnt a file. If we wanted to fix this, we could add an if statement which checks to see if index of `lastColon` is 1 after `lastClosedParen`. If so, break. If not, then continue. 

In my code, the area which would need to be fixed is shown below with the `else if` statement. Need to add additional condition if markdown.charAt(nextClosedBracket+1) = `:`, break.

<img width="516" alt="Screen Shot 2022-03-11 at 3 01 08 PM" src="https://user-images.githubusercontent.com/97641133/157985917-7f6d0ead-256d-4a29-84b3-5b4f56f73c18.png">

## Test 2
This test was run on file `578.md` from `test-files/`. The file contents are:

`My ![foo bar](/path/to/train.jpg  "title"   )`

The results of the diff command shown below:

<img width="142" alt="Screen Shot 2022-03-11 at 2 35 13 PM" src="https://user-images.githubusercontent.com/97641133/157983741-a26a5b13-946f-4e80-8946-c7fa230131e6.png">

My Output: `[]`
---
Prof's Output: `[<url>]`
---
Expected Output: `[<url>]`
---
The problem with my code is the inability to correctly understand a link when incorporating file paths. 

I believe that my output is incorrect for this case since the file follows proper order to product a link, that being `[Link](anything)`.
This given test link is special since it incorporates the use of paths and adds a "title" text inside of the link after the path argument followed preceeded by spaces. This issue could be fixed by adding an if statement which checks to see if the character after the `LastOpenParen` is `/`, if so, then the getLinks method which takes in a file path should be called to obtain the correct output, then return that output in the arrayList.

In my code, the area which would need to be fixed is shown below:

<img width="491" alt="Screen Shot 2022-03-11 at 3 03 53 PM" src="https://user-images.githubusercontent.com/97641133/157986086-38226f3e-ff92-4911-8f99-ad92a2936f91.png">

We should create an if statement which checks to see if `/` is found after lastopenParen, if so, then use the other getLinks method to find path.



