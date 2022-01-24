## Erick Gulyan
**CSE 15L Week 2 Lab Report** 
---
Hello and Welcome to my Week 2 Lab Report where I will teach you how to setup your programming environment and login into your .ieng6 account.

---

## Step 1) Installing VScode
First, we need to download VS Code from your browser. Feel free to use this link to access the website for a quick download.
https://code.visualstudio.com/download

<img width="1263" alt="VSCODE_DOWNLOAD" src="https://user-images.githubusercontent.com/97641133/149434608-bd84a675-5263-48d5-a51b-f277ec235ac5.png">

After succesfully downloading VS Code, you should be able to open the application to the main page. You may also open up a file of code of your choice for view/edit.

<img width="776" alt="VSCODE_SETUP" src="https://user-images.githubusercontent.com/97641133/149435113-fa3ad285-8162-4e1a-af63-58c5aeff7b40.png">

---

## Step 2) Remotely Connecting
First, if you have a Windows computer you need to install OpenSSH at this link below:
https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse


Next, you would need to lookup your course-specific account for this course on this link below:
https://sdacs.ucsd.edu/~icc/index.php

Afterwards, you will open the terminal in VS Code under the **Terminal-> New Terminal**

In the Terminal you need to type "ssh" followed by your course specific account email. Your command should look like:
`ssh cs15lwi22zz@ieng6.ucsd.edu` with the "zz" being replaced by the characters to your specific account.

Next, the terminal should prompt you for a password, so enter your password for the course specific account.

You may be prompted by a message which says `The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? `

Type yes as a response.

Once the password is entered, your screen should look like this (Keep in mind, password will not display as you are typing).

<img width="771" alt="Screen Shot 2022-01-05 at 3 34 42 PM" src="https://user-images.githubusercontent.com/97641133/149435654-f13589f4-fbb5-45be-bc34-a5c12fac5870.png">

---

## Part 3) Run Some Commands

Now that we are logged into your @ieng6 account, we can try some terminal commands and learn more about the setup.

Some commands you can write are:
1. `cd ~`
2. `cd`
3. `ls -lat`
4. `ls -a`
5. `ls <directory> where  the <directory> is /home/linux/ieng6/cs15lwi22/cs15lwi22zzz` and the zzz at the end is your course account characters.
6. `ls`
7. `pwd`

Once you have tested some of these commands, note the output and try to figure out what they are doing!
Here are a few example commands and their outputs.

<img width="318" alt="Screen Shot 2022-01-05 at 3 47 58 PM" src="https://user-images.githubusercontent.com/97641133/149437516-8437d895-8d85-4eab-a454-852805643c2b.png">

Now, to log out of the remote server, you can do it two ways.
1. Use Control-D
2. Run the `exit` command in terminal


---

## Part 4) Moving Files with scp

In this step, were going to be moving files over from your client to your serber using the scp command.

`scp` means secure copy, and it will copy files from one specified place to another.

First, you're going to need to create a new java file called `WhereAmI.java` and fill it with the contents below.
`class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}`

After you have copied this and saved the file, run it using `javac WhereAmI.java` and `java WhereAmI`.
Note the output of the program, and remember it for a later step.

Then, you should use the command 
`scp WhereAmI.java cs15lwi22zz@ieng6.ucsd.edu:~/`
With "zz" again replaced by your course specific account. You will then be prompted for your password.

Afterwards, you can use `ls` in the terminal to see the file in your home directory on the remote server.

Now, run the `javac` and `java` command in the console for the file WhereAmI.java which is in the remote server.

Shocking? You should see a different output than when you ran it on your client. This is because it's now running on the server!
The picture below shows running the command on both client and server side by side. (Server run on right side).

<img width="468" alt="Screen Shot 2022-01-13 at 6 04 06 PM" src="https://user-images.githubusercontent.com/97641133/149438839-be1ec8b6-2c14-43f2-bed0-ae115384ab90.png">

You have now copied a file into your remote server and run code from that server. Well done!

---

## Part 5) SSH Keys

Now you should notice that it takes quite a bit of time to log into your remote server. Let's show you a way to speed it up a bit with SSH keys!

First, you would need to `exit` from the remote server. Next, you need to use the command:
`ssh-keygen` to generate a SSH key we will use for a speedy login. 

The terminal should output `Generating public/private rsa key pair.
Enter file in which to save the key (/Users/"youruser"/.ssh/id_rsa)`
You should input the same thing as what is inside the parenthensis ("youruser" replaced with the name of your user on your computer, not client).
 
Then it will ask you to enter a passphrase, which you could leave empty and hit Enter.
 
Afterwards, you should receive a confirmation message saying the identification has been saved in `Your Directory Input`.

Next, you should try logging into your remote server using the `ssh` command you have done already. (along with the password)

If you're on Windows, you will need to follow the extra `ssh-add` steps in https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation

Now in order to finish the setup of the SHH key, you will need to enter the command `mkdir .ssh` to make a new directory.

Next, we will need to `exit` the remote server and complete the remaining steps on the client.

On the client, you will need to copy the command:
`scp /Users/username/.ssh/id_rsa.pub cs15lwi22zz@ieng6.ucsd.edu:~/.ssh/authorized_keys`

You will need to replace the username with your computer user account name and the "zz" with the course specific account.

Once finished, you can log into your remote server using the `ssh` command. 

The login shouldn't require a password, and should instantly log you into your remote server as shown below.

<img width="664" alt="Screen Shot 2022-01-13 at 6 59 10 PM" src="https://user-images.githubusercontent.com/97641133/149444083-a7c9aa05-1956-42a4-a145-a9814147793e.png">

After this, your SSH key on your device is setup. (Note, this is specific to your device).

---

## Part 6) Optimizing Remote Running

Now, with our remote server setup and you having learned some commands, lets try to make some edits to `WhereAmI.java`.

Some useful tips is that you can seperate multiple different commands all in the same command line using semicolons `;`.

Also, you can use the up and down arrows on your keyboard to quickly pull up the last commands and cycle through them.
Similar to the photo below, we can log into our server and add commands as we are doing it such as `ls`.

In the example below, I used `scp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI` to log into my secure remote server, copy the file to the remote server, and run it through `javac` and `java` commands. In total, this process took 4 keystrokes: 2 clicks to open the terminal and one up arrow and one enter key stroke. Included below this is also another command which involved 3 key strokes, used to check the listed files in our secure remote server.


<img width="831" alt="Screen Shot 2022-01-24 at 1 12 08 PM" src="https://user-images.githubusercontent.com/97641133/150865678-90367362-234b-4d41-8514-23e3595c6ec7.png">


Now that we are able to quickly login and perform commands, time yourself to see how long it takes to login and run the `java` file in the terminal on your server.

And we are all done!


