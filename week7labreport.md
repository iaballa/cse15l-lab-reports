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

**4)** Saving changes:

Press `:wq` and the following should show up at the bottom of the file:

![image](https://user-images.githubusercontent.com/114435397/201598363-ad826a02-4bdc-4d50-890f-f88a01672082.png)

Then, press `<Enter>`! And it should exit the file and take you back to the terminal. 





