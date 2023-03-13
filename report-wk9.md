# Lab Report: Week 9

## Finished Lab 6 Grading Script

### Final `bash.sh` Code
``` bash
BUILD_DIR="./student-submission-build"
SOURCE_DIR="./student-submission"
SOURCE_FILE="ListExamples.java"
TEST="TestListExamples"

CPATH_UNIX=":.:./lib/*:$BUILD_DIR:"
CPATH_WIN=";.;./lib/*;$BUILD_DIR;"
CPATH="$CPATH_UNIX$CPATH_WIN"

function cleanup()
{
	echo -e "\n\n---\n\n$1"
	rm -rf $SOURCE_DIR $BUILD_DIR
	exit
}

rm -rf student-submission
git clone $1 student-submission
echo 'Finished cloning'

if [ ! -f  "$SOURCE_DIR/$SOURCE_FILE" ]
then
	cleanup "GRADING ERROR: $SOURCE_FILE not found!"
fi

mkdir -p $BUILD_DIR
javac -cp $CPATH *.java "$SOURCE_DIR/$SOURCE_FILE" -d $BUILD_DIR

if [ $? != 0 ]
then
	cleanup "GRADING ERROR: $SOURCE_FILE compilation failed!"
fi

RESULT=`java -cp $CPATH org.junit.runner.JUnitCore $TEST`

if [ -z `echo "$RESULT" | grep -o "FAILURES!!!"` ]
then
	TOTAL=`echo "$RESULT" | grep -oP "(?<=OK \()[0-9]*"`
	PASSED=$TOTAL
else
	echo "$RESULT"
	TOTAL=`echo "$RESULT" | grep -oP "(?<=Tests run: )[0-9]*"`
	FAILED=`echo "$RESULT" | grep -oP "(?<=Failures: )[0-9]*"`
	PASSED=$(( TOTAL - FAILED ))
fi

cleanup "GRADING SUCCESS: $PASSED/$TOTAL points"
```

### Rough Explanation of Interesting Bits
* Classpath actually has both UNIX and Windows delimiters (`:`/`;`). On one half it has the full classpath with the UNIX delimiter `:`, and on the other half it has the same classpath but using the Windows delimiter `;`. This way, the script works on both UNIX and Windows (though this solution is quite janky).
* Outputs the binary \*.class files
* Begins by declaring a `cleanup()` function that just prints a message, removes the temporary `student-submission` and `build` directories, and exits the script. This is done throughout the script, so I put it in a function to reduce repetition.
* Doesn't copy files to/from `student-submission` directory, but instead just passes the specific `student-submission/ListExamples.java` file to `javac`
* Uses `grep` regex to search for the number of tests passed/failed in order to give a point score at the end

### Example I/O
Note: I also added an extra test named `testFilter`, since the given test file did not include any tests for the `filter` method.

* Correct implementation (GitHub repository: https://github.com/ucsd-cse15l-f22/list-methods-corrected)
    ![image](https://user-images.githubusercontent.com/46171121/224591163-675c89d7-3c90-4c36-91f5-089a303c800c.png)

* Incorrect implementation (GitHub repository: https://github.com/ucsd-cse15l-f22/list-methods-lab3)
    ![image](https://user-images.githubusercontent.com/46171121/224590918-e9edbe63-aff7-43e4-a545-8c97cda62a69.png)

* Subtly incorrect implementation (GitHub repository: https://github.com/ucsd-cse15l-f22/list-examples-subtle)
    ![image](https://user-images.githubusercontent.com/46171121/224591731-75cf881a-4ad6-4433-80b8-c465b58cf14c.png)

* Syntax error (GitHub repository: https://github.com/ucsd-cse15l-f22/list-methods-compile-error)
      ![image](https://user-images.githubusercontent.com/46171121/224591278-43bbb622-85c9-4019-b947-4f2cb0491392.png)

* Incorrect method signature (GitHub repository: https://github.com/ucsd-cse15l-f22/list-methods-signature)
    ![image](https://user-images.githubusercontent.com/46171121/224591403-c543da1f-cbf7-428e-9672-b4d997f92749.png)

* Incorrect filename (GitHub repository: https://github.com/ucsd-cse15l-f22/list-methods-filename)
    ![image](https://user-images.githubusercontent.com/46171121/224591517-012b27bd-8d18-4a78-b02c-1c979753c8a5.png)
