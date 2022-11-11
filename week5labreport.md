# grep Research 
The following is a short page about the `grep` command and the following three options:
1. `-c` or `--count` for output that returns the count of lines containing the search term
2. `-l` or `--files-with-matches` for output that returns files with matches 
3.  `-i` or `--ignore-case` for output of case insensitive searches


For the purposes of this page, the directory I'm working in is called docsearch that roughly looks like:


<img width="338" alt="image" src="https://user-images.githubusercontent.com/114435397/201237544-b350a969-5ea1-4933-b1b5-fdf51a59122b.png">

Each folder within technical contains various text files relating to the name of the folder.

--- 

### What is `grep?`

`grep` is a command that you can use in the terminal to search any given input files for any patterns. A pattern being really any group of characters. Here is an excerpt from the grep manual, found when you type the command `man grep` into the terminal

<img width="738" alt="image" src="https://user-images.githubusercontent.com/114435397/201235906-a8f0d645-4c22-4c9b-8143-972116cfb482.png">


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

Here is an excerpt from the grep manual, obtained by using the `man grep` command that explains this option.

<img width="518" alt="image" src="https://user-images.githubusercontent.com/114435397/201235957-e7a65107-4d39-41b8-9cb9-7ff0c5467f8f.png">


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
By using the `-c` option, the output has changed from including the entire line containing "angina", to the number/count of lines containing "angina" thus changing the lengthy output to something much shorter. This option is useful because it may help a premed student confirm that they are looking at the correct document, one that talks about/contains information relating to "angina."

**Example Two:**

In this example, I search for the term "law" within file LegalServCorp_v_VelazquezDissent.txt within the government folder:
```
$ grep -c "law" ./technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt 
26
```
After typing grep in the terminal to search for the existence of "law" within the given file, I changed the output of the command with the option `-c` in order to make it more readable. If I hadn't used the `-c` option, the output would be much longer with extra words and information that I may not actually need. This option is useful because it allows people to see just how many times the word "law" is mentioned in the file. 

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
This option is useful because it can help people determine how many files contain the pattern (even if the output can be difficult to read) and after using that information and refining their search, people can then use the option again to see how many times that term is used in the file. 

**2. `-l` or `--files-with-match`**

Here is an excerpt from the grep manual, obtained by using the `man grep` command that explains this option.

<img width="720" alt="image" src="https://user-images.githubusercontent.com/114435397/201236007-edc24d3a-cc7e-42c8-9a27-aaeb3cb40708.png">


A better way to have approached the last example would have been to use the `-l` option to first find which files contain the search term, and then go from there. The `-l` option returns output containing only the files that contain a match. This option and `--files-with-match` both return the same output.

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
This option is useful because it provides an easier way to search through files, and is a more clean way to find how many files include the term "Abraham." 

**Example Two:**

In this example, I use the `-l` option to find how many files contain "abortion" within the Media folder inside the government folder. 
```
$ grep -l "abortion" ./technical/government/Media/*.txt
./technical/government/Media/FY_04_Budget_Outlook.txt
./technical/government/Media/Terrorist_Attack.txt
```

Here, we see that two files in our search path contain "abortion", these files being FY_04_Budget_Outlook.txt and Terrorist_Attack.txt. Here, we know that we have searched through each .txt file because at the end of our search, we use *.txt. This option is useful because the output gives you the exact file name, making it easier for you to move forward with whatever documents you need to use. 

**Example Three:**

In this example, I use the `--files-with-matches` command to search for all instances of "proteomic" within the plos folder.
```
$ grep --files-with-matches "proteomic" ./technical/plos/*.txt
./technical/plos/journal.pbio.0020042.txt
./technical/plos/journal.pbio.0020206.txt
./technical/plos/pmed.0010066.txt
```

Here, I use the longer version of the option just to show that it still works as intended. Based on the output, we see that there are three files within the plos folder that contain the term "proteomic", these files being journal.pbio.0020042.txt, journal.pbio.0020206.txt, and pmed.0010066.txt. This option is useful because people reading your commands may not know exactly what `-l` does, and with a more descriptive option, more people can know what you are doing without having to look it up. 

**3. `-i` or `--ignore-case`**

Here is an excerpt from the grep manual, obtained by using the `man grep` command that explains this option.

<img width="576" alt="image" src="https://user-images.githubusercontent.com/114435397/201236055-f35567f8-764e-47ff-8465-ae2e6e2a9dbe.png">

The `-i` or `--ignore-case` option searches for the given pattern regardless of whether the match contains characters that are upper or lower case. Users can input the search term fully capitalized, fully uncapitalized, or capitalized and uncapitalized throughout and the output will still be the same because of the option. 

**Example One:**

Here, I search for the term "cONseRVeD" within the file journal.pbio.0020042.txt within the plos folder.
```
$ grep -i "cONseRVeD" ./technical/plos/journal.pbio.0020042.txt
        “conserved hypothetical protein” when they occur in more than one genome or simply a
        bioinformaticians to produce a list of all of the conserved hypothetical proteins that are
        valuable. Three general classes of such genes come to mind: (1) The conserved hypothetical
        conserved hypothetical gene that occurred in most genomes would be of higher priority than
        conserved. In fact, for a laboratory that happened to be already working on one of the
        one method might be better than another. The list would, of course, also include conserved
```
Since I used the `-i` option, the output contains each line containing some iteration of the word "cONseRVeD" even if the case of each letter does not exactly match. Of course, it would be strange that a word is capitalized like this, but with the option I don't have to worry about whether or not the term matches exactly making this a useful option. 

**Example Two:**

Here, I search for the term "california" within the file chapter-5.txt in the 911report folder. 
```
 $ grep -i "california" ./technical/911report/chapter-5.txt
                became the primary target. For similar reasons, California also became a target for
                headquarters, nuclear power plants, and the tallest buildings in California and the
                such as San Diego and Long Beach, California; brochures for schools; and airline
```

Since this is a proper document, "california" would obviously be capitalized, but since I used the `-i` option, the output contained each line containing "California" because again, the option is meant for the computer to ignore case mismatch. This option is useful for when people are unaware that a term may be a proper noun, and allows for people to still find it regardless of this mistake. 

**Example Three:**

Here, I use the longer version of the option `--ignore-case` to search for the pattern "acCOUNTing" within the file d01121g.txt inside the Gen_Account_Office folder inside the government folder.

```
$ grep --ignore-case "acCOUNTing" ./technical/government/Gen_Account_Office/d01121g.txt
United States General Accounting Office
United States General Accounting Office Office of Special
Special Investigations, U.S. General Accounting Office, 441 G.
```

Similar to the first example of this option, three instances of some variation of the characters "acCOUNTing" were found, and once again, the case of the letters did not affect the output of this command. By using this more descriptive option, on top of how useful it already is, more people can know what you are doing when looking at your commands, as well as yourself if you decide to revisit some old commands that you might have put into a script.
















