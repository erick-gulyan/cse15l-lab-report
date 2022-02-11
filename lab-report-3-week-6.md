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
--
Now, after running that command, the entire markdown-parse directory should have been copied succesfully to our remote server. To check, we `ssh` into our remote server and ran `ls`, which shows all the directories/files.
<img width="574" alt="Screen Shot 2022-02-10 at 8 32 07 PM" src="https://user-images.githubusercontent.com/97641133/153537891-6a668688-ae71-4e2a-bcd6-2b4648ca260b.png">

Also running `ls -l` shows more information about the files/directories, including when each was copied in. This photo below shows it was copied in on Feb 10 at 8:29, which is when I copied this directory in.



Now, to speedrun this process, I combined multiple commands to:
1. Copy the directory
2. SSH into my remote server
3. Compile MarkDownParseTest.java
4. Run MarkDownParseTest JUnit tests.

The command I used was `scp -r . cs15lwi22age@ieng6.ucsd.edu:~/markdown-parse; ssh cs15lwi22age@ieng6.ucsd.edu javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java ;java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest`

Here is the result:
At first, I removed markdown-parse so then I can recopy it. Then ran the command:
<img width="574" alt="Screen Shot 2022-02-10 at 8 33 18 PM" src="https://user-images.githubusercontent.com/97641133/153537957-2daf1626-3a1a-4ca7-acc9-a204a9a41eed.png">

Now that all the files were copied in. The next command runs, which is the `ssh` command:

<img width="954" alt="Screen Shot 2022-02-10 at 9 02 10 PM" src="https://user-images.githubusercontent.com/97641133/153540110-1e32fec1-6d3a-44df-ba92-17fbf9e4691c.png">

Then: The JUnit tests run and show us the expected passing case.
<img width="332" alt="Screen Shot 2022-02-10 at 9 04 12 PM" src="https://user-images.githubusercontent.com/97641133/153540239-f7c1e352-fce5-44ae-a532-81349c8f6815.png">

Now that we ran a command doing all of these, we are done!

