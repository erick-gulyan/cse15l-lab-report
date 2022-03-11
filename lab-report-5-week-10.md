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
My Output: `train.jpg`
Expected Output: `[]`

I believe that my output is incorrect since the file doesn't follow the proper format for it to be considered a link, the format being:
`[Link](a.com)`
Instead, the file uses a `:` after the last closed bracket, thus this isnt a file. If we wanted to fix this, we could add an if statement which checks to see if index of `lastColon` is 1 after `lastClosedParen`. If so, break. If not, then continue. 

## Test 2
This test was run on file `578.md` from `test-files/`. The file contents are:

`My ![foo bar](/path/to/train.jpg  "title"   )`

The results of the diff command shown below:

<img width="142" alt="Screen Shot 2022-03-11 at 2 35 13 PM" src="https://user-images.githubusercontent.com/97641133/157983741-a26a5b13-946f-4e80-8946-c7fa230131e6.png">

My Output: `[]`
Prof's Output: `[<url>]`
Expected Output: `[]`

I believe that the professor's output is incorrect for this case since the file doesn't follow proper order to product a link, that being `[Link](anything)`.
This given test link is special since it incorporates the use of paths and adds a "title" text inside of the link after the path argument followed preceeded by spaces.
  



