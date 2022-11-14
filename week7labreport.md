# Week 7 Lab Report - VIM

### Part 1:

From week 6's tasks, the task I'm including in this lab report is the second one, 
- "Changing the name of the start parameter and its uses to base."

In collaboration with my groupmate Alex Yang, we came up with the following set of keystrokes assuming that the user has already:
1) cloned the repository (https://github.com/ucsd-cse15l-f22/skill-demo1) with `git clone https://github.com/ucsd-cse15l-f22/skill-demo1`
2) changed the current directory to be said repository with `cd skill-demo1`
3) opened the DocSearchServer.java file with `vim DocSearchServer.java`

Assuming the above steps have already been completed, in order to change the name of each start parameter and its uses to base, the user must complete the following keystrokes:

`/start<Enter>cebase<Escape>n.n.<Escape>:wq<Enter>`

This adds up to 23 total keystrokes. Below are screenshots of each step in the process!

**1)** Searching for each occurrence of the word start within the program:

After completing the keystrokes `/start` the following should show up at the bottom of the file, then press `<Enter>`

![image](https://user-images.githubusercontent.com/114435397/201596243-7488418a-e821-4c37-a340-1137260decf0.png)


**2)** Editing the first occurrence of "start" to "base"

Press `ce` in order to make changes until the end of the current word.

![image](https://user-images.githubusercontent.com/114435397/201597299-e2736d31-3118-49fa-911f-d498e9ee005b.png)

Then, type `base` to replace "start:"

![image](https://user-images.githubusercontent.com/114435397/201597460-2109f10f-58ed-48d3-96eb-208b5978db6c.png)

Followed by the `<Escape>` key:

![image](https://user-images.githubusercontent.com/114435397/201597574-2dc79870-a6c8-4fd0-b1dc-ecf44c9acfa0.png)


**3)** Changing each occurrence of start (two ocurrences within the getFiles() method):

Press `n`:

![image](https://user-images.githubusercontent.com/114435397/201597905-33a57419-9631-4b0c-9d49-b83021eff200.png)

Press `.`:

![image](https://user-images.githubusercontent.com/114435397/201597971-02620e8f-b5b8-4aa6-85e4-cfe557a1668e.png)

Press `n`:

![image](https://user-images.githubusercontent.com/114435397/201598016-4fa7db95-9b5c-4452-a7d9-77dcbee54de3.png)

Press `.`:

![image](https://user-images.githubusercontent.com/114435397/201598057-a9d9d433-689d-45b6-b7bc-378d0d57557c.png)

Then press `<Escape>`.

**4)** Saving changes and quitting:

Press `:wq` and the following should show up at the bottom of the file:

![image](https://user-images.githubusercontent.com/114435397/201598363-ad826a02-4bdc-4d50-890f-f88a01672082.png)

Then, press `<Enter>`! And it should exit the file and take you back to the terminal. If you don't want to quit/exit the file, just skip pressing q and then press `<Enter>`.

--- 

### Part 2:
The following bullet points are from the Week 7 Lab Report write up:

- Once, start in Visual Studio Code and make the edit there, then scp the file to the remote server and run it there to confirm it works (you can just run bash test.sh on the remote to test it out). Consider having the appropriate scp command in your command history or easily copy-pasteable!

It took me 4:44.45 to complete the task using the first method, from opening the file in Visual Studio Code, making edits there manually, scp-ing and getting confused between directories, to finally copying it over, and checking to see that the proper changes were made. I had the following line readily available, though I did have a few hiccups before finally arriving at this correct command: 
`scp DocSearchServer.java cs15lfa22em@ieng.ucsd.edu:/home/linux/ieng6/cs15lfa22/cs15lfa22em/skill-demo1`.


- Second, start already logged into a ssh session. Then, make the edit for the task you chose in Vim, then exit Vim and run bash test.sh.

It took me 53.60 seconds to complete the task already logged in to ssh, cloning the repository, and making the changes using the vim keystrokes. There were way less issues with this second method than there were in the first method. 


**Responses to the two bullet points in the write up:**

- Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?

I would definitely prefer the second style if I was working on a program that was running remotely. This is because by already being logged into the remote server, I don't have to worry about getting the path of the file exactly correct when copying it over. Part of the reason that it took me so long to do the first method was because I forgot the colon directly after my remote account. By already being logged in, this is way smaller of an issue, and by using the vim keystrokes, I didn't have to individually search for each occurrence of start within the file. The vim keystrokes kind of did it for me, saving me lots of time. 

- What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)

If I'm going to be consistently making lots of changes, I'd definitely prefer the second method over the first. However, if I won't be editing the file as much, then I might be okay with doing the first method. It really depends on how often I'll be editing the file, and it also depends on how big it is. I don't want to be spending lots of my time just waiting around for the file to copy over. 






