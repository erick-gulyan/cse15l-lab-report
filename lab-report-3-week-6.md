## Lab Report 3
In this lab report, I will show how to copy a whole directory into our ieng6 server, run the code, and also show some streamlined methods to copying directories.

First, we need to use the `scp` command as we have done in previous labs to copy files, but instead of a file, this time lets copy our entire `markdown-parse` Github directory!

In this case, `scp` works recursively to first copy the directory, then to copy all of the files inside of it one by one until all the files have been copied. (Note, the user only runs one command, the recursive calls happen in the background!).

--
First, we run `pwd` to print the working directory and show we are in the local directory. Then we ran `ls` to show all of the files in our current directory.

<img width="587" alt="Screen Shot 2022-02-10 at 8 25 24 PM" src="https://user-images.githubusercontent.com/97641133/153537453-52fc0775-9eab-4b1b-8116-11f5e731ea8c.png">

Now, to copy a whole directory, we use the scp command as follows:
`$ scp -r . cs15lwi22age@ieng6.ucsd.edu:~/markdown-parse`
In this case, the "age" portion is for my personal account, other students will differ in these three letters for logging into their remote server.

Running this command, we now have:


<img width="577" alt="Screen Shot 2022-02-10 at 8 29 28 PM" src="https://user-images.githubusercontent.com/97641133/153537710-e63ac089-cd18-452a-a07b-697319ee0e03.png">

<img width="581" alt="Screen Shot 2022-02-10 at 8 29 55 PM" src="https://user-images.githubusercontent.com/97641133/153537736-7b8cea81-0796-4dee-abcf-2fcb8ab91225.png">

After running this command, the terminal shows a long list of files which are copied, the copy speed of each file, a timestamp of when the files were copied relative to eachother, and a completion percentage (which changed as they are copied in).


