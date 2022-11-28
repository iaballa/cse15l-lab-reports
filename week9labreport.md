# Week 9 Lab Report - Ilia Aballa

For this week's lab report, I added more to my grade.sh file so that each submission would receive a different score depending on what was submitted. I broke the grading up into the following portions:
- 1 point for submitting the correct file
- 5 points for successful compilation
- 1 point for each test passed (4 total tests)

For a **grand score of 10 points**.

Here is my grader:
```
EXPECTED_FILE_NAME="ListExamples.java"
SCORE=0

rm -rf student-submission
git clone $1 student-submission

# Messages based on clone success
if [[ $? -eq 0 ]]
then
  echo "[SUCCESS] Cloned successfully."
else
  echo "[FAILURE] Clone failed. You may want to check the URL that was submitted."
  echo "Current Score: $SCORE / 10"
  exit 1
fi

cd student-submission
echo "Changed Directories into student-submission."

# Messages based on whether or not the correct file was submitted
if [[ -f $EXPECTED_FILE_NAME ]]
then
  echo "[SUCCESS] Found the expected file: $EXPECTED_FILE_NAME!"
  SCORE=$((SCORE+1))
  echo "Current score: $SCORE / 10"
else
  ACTUAL_FILES=`ls -1`
  echo "[FAILURE] Did not find the expected file: $EXPECTED_FILE_NAME."
  echo "Instead found: $ACTUAL_FILES"
  echo "POINTS: $SCORE / 10"
  exit 1
fi

CP=".:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar"

cp ../TestListExamples.java .
javac -cp $CP *.java 2> compile_error.txt

# Attempts to compile the submitted files, gives feedback based on compilation
if [[ $? -eq 0 ]]
then
  echo "[SUCCESS] Files compiled successfully, five points for successful compilation."
  SCORE=$((SCORE+5))
  echo "Current score: $SCORE / 10"
else
  MSG=`cat compile_error.txt | head -1`
  echo "[FAILURE] Files did not compile."
  echo "Compilation Error Message: ($MSG)"
  echo "Current score: $SCORE / 10"
  exit 1
fi

rm -rf student_results.txt
java -cp $CP org.junit.runner.JUnitCore TestListExamples > student_results.txt

# Calculates the student's score based on how many tests were passed
if [[ $? -eq 0 ]]
then
  RESULT=`cat student_results.txt | grep "OK"`
  echo "[SUCCESS] jUnit result: " $RESULT
  POINTS=`cat student_results.txt| grep "OK" | tr -cd [:digit:]`
  SCORE=$((SCORE+POINTS))
  echo "Current score: $SCORE / 10"
else
  RESULT=`cat student_results.txt | grep "Tests run:"`
  echo "[FAILURE] jUnit result: " $RESULT
  POINTS=4
  FAILURES=`cat student_results.txt | grep "Failures:" | tr -cd [0-3]`
  echo "Failed tests: $FAILURES"
  SUCCESSES=$((POINTS-FAILURES))
  echo "Passed tests: $SUCCESSES"
  SCORE=$((SCORE+SUCCESSES))
  echo "Current score: $SCORE / 10"
  exit 1
fi
```

Here are screenshots of different output for three different submissions:
1. the subtlely incorrect submission: 
<img width="844" alt="image" src="https://user-images.githubusercontent.com/114435397/204362776-a73903e7-6db1-4a93-a81b-0829bffaf841.png">
2. the mostly correct submission: 
<img width="860" alt="image" src="https://user-images.githubusercontent.com/114435397/204362968-da92a92e-1ae5-4ebc-903b-012e81035fb9.png">
3. and the submission with the incorrect filename:
<img width="621" alt="image" src="https://user-images.githubusercontent.com/114435397/204366910-7e32d545-57ea-4d89-946c-33e2adb11b44.png">



**Tracing the third example**:
`rm -rf student-submission`

`git clone $1 student-submission`
Cloning into 'student-submission'...

For the first if statement, the value was true because the repository was successfully cloned. The rest of the if statement does not run (everything between the else and fi) because we leave the if statement because the first condition is met. 

`cd student-submission`

`echo "Changed Directories into student-submission.`

For the second if statement, the value was false because we did not find the expected file. This means that unlike the first if statement, the second part does in fact run while the first part does not. We also exit the script at this point and do not continue further. 


