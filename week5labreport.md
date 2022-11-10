# grep Research 
The following is a short page about the `grep` command and the following three options:


For the purposes of this page, the directory I'm working in is called docsearch that roughly looks like:

<img width="144" alt="image" src="https://user-images.githubusercontent.com/114435397/201221393-57388014-0948-4ea6-b803-5243a06b7800.png">

Each folder within technical contains various text files relating to the name of the folder. 

**What is `grep?`**

`grep` is a command that you can use in the terminal to search any given input files for any patterns. A pattern being really any group of characters. Here is an excerpt from the grep manual, found when you type the command `man grep` into the terminal

<img width="514" alt="image" src="https://user-images.githubusercontent.com/114435397/201200664-03cc31c4-04b5-4213-89d2-4efdd0c546df.png">

Essentially, if you wanted to look within a certain file for every line that contains the pattern, you would just type `grep` followed by the pattern you want to search for, followed by the file you want to search within. 

For example, if you wanted to search for each line containing "cell" within a file called 1468-6708-3-1.txt, you would type the command `grep "cell" ./technical/biomed/1468-6708-3-1.txt`

This command gives the following output:


