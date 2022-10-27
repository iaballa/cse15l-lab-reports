**CLONE REPOSITORY**

git clone https://github.com/ucsd-cse15l-f22/skill-demo1.git 

**BUILD LOCAL TESTS AND RUN**

javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java

java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore TestDocSearch

**FIX TEST**

line 14 TestDocSearch:

assertEquals(“There are 1391 total files to search.”, h.handleRequest(rootPath));

**BUILD AND RUN SERVER LOCAL**

javac Server.java DocSearchServer.java

java DocSearchServer 1025

http://localhost:1025

**TRY PATHS**

http://localhost:1025/

http://localhost:1025/search?q=biomed

**COPY TO REMOTE**

ssh cs15lfa22em@ieng6.ucsd.edu (given account and password)

git clone https://github.com/ucsd-cse15l-f22/skill-demo1.git 

cd skill-demo1

**TRY PATHS**

javac Server.java DocSearchServer.java

java DocSearchServer 1025

http://localhost:1025/

http://localhost:1025/search?q=biomed

**CHANGE PROGRAM**

change contents of if statement on line 47 to:

f.getName().contains(parameters[1])

**TRY CHANGES LOCALLY**

javac Server.java DocSearchServer.java

java DocSearchServer 1025


http://localhost:1025/search?q=rr74

should find only one file

**COPY TO REMOTE AND BUILD**

delete old DocSearchServer file from skill-demo1 in remote

ssh cs15lfa22em@ieng6.ucsd.edu (given account)

cd skill-demo1

rm DocSearchServer.java

exit

ON LOCAL: 

scp DocSearchServer.java cs15lfa22em@ieng6.ucsd.edu:~/skill-demo1 (replace with given account)


ssh cs15lfa22em@ieng6.ucsd.edu (given account)

cd skill-demo1

javac Server.java DocSearchServer.java

java DocSearchServer 1025


http://localhost:1025/search?q=rr74
