## Lab Report 3
In this lab report, I will show how to copy a whole directory into our ieng6 server, run the code, and also show some streamlined methods to copying directories.

First, we need to use the `scp` command as we have done in previous labs to copy files, but instead of a file, this time lets copy our entire `markdown-parse` Github directory!

In this case, `scp` works recursively to first copy the directory, then to copy all of the files inside of it one by one until all the files have been copied. (Note, the user only runs one command, the recursive calls happen in the background!).

--
First, we run `pwd` to print the working directory and show we are in the local directory. Then we ran `ls` to show all of the files in our current directory.

<img width="587" alt="Screen Shot 2022-02-10 at 8 25 24 PM" src="https://user-images.githubusercontent.com/97641133/153537453-52fc0775-9eab-4b1b-8116-11f5e731ea8c.png">



