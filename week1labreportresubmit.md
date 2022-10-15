# How to Log in to the UCSD Remote Computers

After retrieving your ieng6 specific account information at this link: [UCSD Account Retrieval](https://sdacs.ucsd.edu/~icc/index.php)

**1) Ensure that VSCode is installed**
- Follow [this link](https://code.visualstudio.com/download) to download VSCode
- Make sure you select the download for your specific OS.
- Your VSCode should look something like this when it is open:

![](https://user-images.githubusercontent.com/114435397/195970219-ba041bc3-de8d-46e9-a9de-6f17203dd9ad.png)

2) Open a terminal in VSCode
- At the top of your Mac, there should be a “Terminal” tab, select it, hover, and click on the New Terminal option. 

![](https://user-images.githubusercontent.com/114435397/195970225-06af6186-8582-424d-9dd0-f81ce894966d.png)

- A new terminal should look like this:

![](https://user-images.githubusercontent.com/114435397/195970235-21f834fe-5b70-4ead-a5e0-461bf6ee6109.png)


3) Use the ssh command to log in to your remote account:
- ssh cs15lfa22XX@ieng6.ucsd.edu 
- replace XX with your own account details
- When prompted by the terminal, input your password and press return
Upon logging in, it should look something like this:

![](https://user-images.githubusercontent.com/114435397/195970243-6e5d29e0-3f52-42ca-8ed7-92da137a0171.png)

(There is no password input because I have previously created a key in order to just log in right away using the username)

4) Try out some commands:
- ls

![](https://user-images.githubusercontent.com/114435397/195970253-4d74a697-6604-4626-9915-d11a8460b426.png)

- pwd
![](https://user-images.githubusercontent.com/114435397/195970262-5184ff05-9245-4770-ac9f-dc96112263f2.png)

- cat WhereAmI.java to print out the contents of WhereAmI.java
![](https://user-images.githubusercontent.com/114435397/195970267-b55efcb2-2a79-496a-8e1d-a36138b1495b.png)

- javac WhereAmI.java followed by java WhereAmI to run the code in the WhereAmI.java file
![](https://user-images.githubusercontent.com/114435397/195970267-b55efcb2-2a79-496a-8e1d-a36138b1495b.png)

4) Moving Files with scp
- Log out and create a file on your personal computer
- In this example, we’ll be using a file called LetsGo.java.
- Copy and paste the following code into your file:
```
public class LetsGo {
   public static void main(String[] args){
       System.out.println("LETS GOOOO");
   }
}
```

- Save, compile, and run it
![](https://user-images.githubusercontent.com/114435397/195970305-fcfb27a0-f5c7-4615-b76e-a1521cdd4833.png)

- Now, in the terminal, use the command: scp LetsGo.java cs15lfa22XX@ieng6.ucsd.edu:~/
- You will be prompted to type in your password if you have not created a key yet

![](https://user-images.githubusercontent.com/114435397/195970311-b497bd31-30d7-4481-9483-1ba544dacf0f.png)

- Log into your remote account, compile, and run the file
![](https://user-images.githubusercontent.com/114435397/195970314-8f3206c7-8c24-4103-9cb9-1bb79762d5df.png)

5) Getting an SSH key
- On your own computer, type the command ssh-keygen into the terminal and press return.
- (In this part of the tutorial, I am completing the steps in the remote server because a key already exists and I don’t want the output to be confusing for the reader.)
![](https://user-images.githubusercontent.com/114435397/195970321-f11520bc-b528-479d-b790-f0f320e39df3.png)

- When asked to enter in a file, press return for the default
- When asked for a passphrase, press return without any input
- When asked for the passphrase again, press return again

![](https://user-images.githubusercontent.com/114435397/195970330-6079f05f-ef19-4eed-9417-82d1537b407f.png)

- After pressing return multiple times, keep note of where the file was saved, as it should be noted after “Your public key has been saved in “ and then what follows afterwards
- Log in to the remote server
- When logged in, type the command mkdir .ssh
- Then, log out using exit command
- On your own computer, type the command:
- scp (where your key saved) cs15lfa22XX@ieng6.ucsd.edu:~/.ssh/authorized_keys
- Type in your password

![](https://user-images.githubusercontent.com/114435397/195970879-294060a5-21c8-450d-a81a-e4b83492a23a.png)

- Log in to the remove server without using a password
![](https://user-images.githubusercontent.com/114435397/195970883-5ef55b29-f995-4a42-86f0-0f01e3e8f08c.png)

6) Making Things Easier
- running ssh cs15lfa22XX@ieng6.ucsd.edu “ls” lists whatever is in the remote server from your personal computer
![](https://user-images.githubusercontent.com/114435397/195970893-ff4e98e7-f68e-4075-867e-d7d9d5eea09e.png)

- Using semicolons to run multiple commands at the same time works as well. Here, I print out whats in the contents of LetsGo.java, compile it, and run it from the remote server
![](https://user-images.githubusercontent.com/114435397/195970902-faa881d6-fee7-4d5c-bbeb-d1920c9de2b4.png)

- using the up arrow also cycles through recents commands run so that you don’t have to retype them







