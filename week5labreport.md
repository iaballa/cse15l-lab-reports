# grep Research 
The following is a short page about the `grep` command and the following three options:
1. `-c` or `--count` for count
2. `-l` or `--files-with-matches` for files with matches
3.  ;alksdjf



For the purposes of this page, the directory I'm working in is called docsearch that roughly looks like:

<img width="144" alt="image" src="https://user-images.githubusercontent.com/114435397/201221393-57388014-0948-4ea6-b803-5243a06b7800.png">

Each folder within technical contains various text files relating to the name of the folder.

--- 

### What is `grep?`

`grep` is a command that you can use in the terminal to search any given input files for any patterns. A pattern being really any group of characters. Here is an excerpt from the grep manual, found when you type the command `man grep` into the terminal

<img width="514" alt="image" src="https://user-images.githubusercontent.com/114435397/201200664-03cc31c4-04b5-4213-89d2-4efdd0c546df.png">

Essentially, if you wanted to look within a certain file for every line that contains the pattern, you would just type `grep` followed by the pattern you want to search for, followed by the file you want to search within. 

For example, if you wanted to search for each line containing "cell" within a file called 1468-6708-3-1.txt, you would type the command `grep "cell" ./technical/biomed/1468-6708-3-1.txt`

This command gives the following output:

```
$ grep "cell" ./technical/biomed/1468-6708-3-1.txt 
          self-rated health (is your health excellent, very good,
          years (of 7) in which a person reported excellent, very
          (for persons who were never in excellent, very good, or
        EVGFP Is your health excellent, very good, good, fair or
```

Here, you can see that while there is no instance of just the word cell within the file, there are instances of cell within the word excellent four times in the file, and the output shows each line that the word excellent shows up since it contains cell.

--- 

### `grep` options
**1. `-c` or `--count`**

This option changes the output of the grep command to include only the count of lines that includes the pattern searched for. In the previous example, the output held 4 lines. However, by adding the -c option, the output changes to the number 4.

```
$ grep -c "cell" ./technical/biomed/1468-6708-3-1.txt                   
4
```

The exact same output occurs when you use `--count` instead of `-c`:
```
$ grep --count "cell" ./technical/biomed/1468-6708-3-1.txt
4
```

Here are three more examples with output before and after using the `-c` option:

**Example One:**

Here, I search for the term "angina" within file 1468-6708-3-3.txt within the biomed folder:
```
$ grep "angina" technical/biomed/1468-6708-3-3.txt 
        death, myocardial infarction, unstable angina, percutaneous
        63 hours) of admission for unstable angina or a non-Q-wave
        unstable angina or a non-Q wave myocardial infarction. In
``` 

With the `-c` option, the output changes to 3:
```
$ grep -c "angina" technical/biomed/1468-6708-3-3.txt
3
```
By using the `-c` option, the output has changed from including the entire line containing "angina", to the number/count of lines containing "angina" thus changing the lengthy output to something much shorter.

**Example Two:**

In this example, I search for the term "law" within file LegalServCorp_v_VelazquezDissent.txt within the government folder:
```
$ grep -c "law" ./technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt 
26
```
After typing grep in the terminal to search for the existence of "law" within the given file, I changed the output of the command with the option `-c` in order to make it more readable. If I hadn't used the `-c` option, the output would be much longer with extra words and information that I may not actually need.

**Example Three, with an example of what NOT to do:**

In this example, I search for the term "Abraham" within the entire 911report folder (by using *.txt) with the command 
`grep "Abraham" ./technical/911report/*.txt`. It yields the following output: 

```
$ grep "Abraham" ./technical/911report/*.txt 
./technical/911report/chapter-2.txt:                from the one and only God, the God of Abraham and of Jesus. These revelations,
./technical/911report/chapter-2.txt:                from Abraham through Jesus, complete God's message to humanity. The Hadith, which
```

However, in order to use the `-c` option to make this output simpler and more readable, I have to change the place that I am doing the search. If I keep my input the same and just add the `-c` option for the following command `grep -c "Abraham" ./technical/911report/*.txt"` I will get the very lengthy output of:
```
$ grep -c "Abraham" ./technical/911report/*.txt
./technical/911report/chapter-1.txt:0
./technical/911report/chapter-10.txt:0
./technical/911report/chapter-11.txt:0
./technical/911report/chapter-12.txt:0
./technical/911report/chapter-13.1.txt:0
./technical/911report/chapter-13.2.txt:0
./technical/911report/chapter-13.3.txt:0
./technical/911report/chapter-13.4.txt:0
./technical/911report/chapter-13.5.txt:0
./technical/911report/chapter-2.txt:2
./technical/911report/chapter-3.txt:0
./technical/911report/chapter-5.txt:0
./technical/911report/chapter-6.txt:0
./technical/911report/chapter-7.txt:0
./technical/911report/chapter-8.txt:0
./technical/911report/chapter-9.txt:0
./technical/911report/preface.txt:0
```

While this may be helpful in figuring out how many files contain "Abraham", it's not the most efficient way to do so. And the output of 
`entirefilepath:linescontainingsearchpattern` is kind of an eyesore. This leads me to my next option: `-l` that I'll cover after showing you how to properly use the `-c` option in this case.

Here, I correctly search for the term "Abraham" within file chapter-2.txt within the folder 911report by changing the file that I am searching in, a very important step when using `-c` to avoid super lengthy, unhelpful output:
```
$ grep -c "Abraham" ./technical/911report/chapter-2.txt
2
```

**2. `-l` or `--files-with-match`**

A better way to have approached the last example would have been to use the `-l` option. The `-l` option returns output containing only the files that contain a match. This option and `--files-with-match` both return the same output.

**Example One:**

In this example, I am using the `-l` option to find how many files contain "Abraham" inside the entire 911report folder (by using *.txt). 
```
$ grep -l "Abraham" ./technical/911report/*.txt
./technical/911report/chapter-2.txt
```
Here, we see that only one file within the 911report folder contains "Abraham", this file being chapter-2.txt. And, this output makes sense with the previous example we had. The following is the output of using `--files-with-matches` just to show you an alternate way to use this option. 

```
$ grep --files-with-matches "Abraham" ./technical/911report/*.txt
./technical/911report/chapter-2.txt
```

**Example Two:**
In this example, I use the `-l` option to find how many files contain "abortion" within the 














