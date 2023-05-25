# Project 4 - Functions

You will write a program that defines and uses its own functions. You will also
use the string class that is provided by the C++ standard.

## Important Links

- Review the [grading rubric](https://shanepanter.com/cs452/grading-rubric.html)

## Objectives

- Use cin to read data from the user
- Use cout to output to the standard output stream
- Use if/else statements
- Write your own functions
- Use methods provided by the string object
- Use an Iterator when breaking the barcode down
- Use Arrays to get input from the user

## Task 1 - Write the program

For faster sorting of letters, the United States Postal Service encourages
companies that send large volumes of mail to use a bar code denoting the zip
code.

![barcode.png](barcode.png)

The encoding scheme for a five-digit zip code is shown in the figure above.
There are full-height frame bars on each side. The five encoded digits are
followed by a check digit, which is computed as follows: Add up all digits, and
choose the check digit to make the sum a multiple of 10. For example, the zip
code 95014 has a sum of 19, so the check digit is 1 to make a sum equal to 20.
Each digit of the zip code, and the check digit, is encoded according to
table below where 0 denotes a half bar and 1 a full bar.

| Digit | Bar 1 (weight 7) | Bar 2 (weight 4) | Bar 3 (weight 2) | Bar 4 (weight 1) | Bar 5 (weight 0) |
| ----- | ---------------- | ---------------- | ---------------- | ---------------- | ---------------- |
| 1     | 0                | 0                | 0                | 1                | 1                |
| 2     | 0                | 0                | 1                | 0                | 1                |
| 3     | 0                | 0                | 1                | 1                | 0                |
| 4     | 0                | 1                | 0                | 0                | 1                |
| 5     | 0                | 1                | 0                | 1                | 0                |
| 6     | 0                | 1                | 1                | 0                | 0                |
| 7     | 1                | 0                | 0                | 0                | 1                |
| 8     | 1                | 0                | 0                | 1                | 0                |
| 9     | 1                | 0                | 1                | 0                | 0                |
| 0     | 1                | 1                | 0                | 0                | 0                |

The digit can be easily computed from the bar code using the column weights
7,4,2,1,0. For example, 01100 is 0 x 7 + 1 x 4 + 1 x 2 + 0 x 1 + 0 x 0 = 6. The
only exception is 0, which would yield 11 according to the weight formula.

Write a program that takes a bar code as a command line argument and prints the
correct zip code. For example the bar code below should output 95014.

`||:|:::|:|:||::::::||:|::|:::|||`

HINT: You will have to use the the argc array in main!

### Sample output

```bash
$ ./myprogram ||:|:::|:|:||::::::||:|::|:::|||
The value is 95014.
```

⚠ You **MUST** use functions for this program! You will lose points if you write
the whole program in main!

## Task 2 - Generate Build Files

There are two scripts in the root directory named `clean.sh` and `release.sh`.
One creates a release build to compile your project and the other will delete
all the temporary files that are created during the build process.

Run the `release.sh` script from the terminal to setup your project. Note
that your output will be slightly different than what is shown below because
cmake configures the build system specific to the system that it is running on.

```bash
shane|(master *%=):solution$ ./release.sh
-- The CXX compiler identification is AppleClang 14.0.3.14030022
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /Library/Developer/CommandLineTools/usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: ...
```

## Task 3 - Compile your code

After you have run `release.sh` you can `cd` into the build directory to compile
and run the program.

```bash
shane|(master *%=):build$ make
[ 50%] Building CXX object src/CMakeFiles/myprogram.dir/solution.cpp.o
[100%] Linking CXX executable ../myprogram
[100%] Built target myprogram
```

If your code that you wrote in task 1 was correct you should see a executable
named `myprogram` that you can now run to see the output. If your program did
not compile you will need to return to task 1 and fix your code and then return
to this task to compile your code again. You only need to run the `release.sh`
script once if you are recompiling you can skip Task 2 above.

## Task 4 - Complete the Retrospective

Once you have completed all the tasks open the file **Retrospective.md** and
complete each section that has a TODO label.

For the **Experience** section you need to detail your experience with this lab.

- Were there any things that you struggled with?
- Were there any parts of this lab that were unclear or poorly specified?
- Were you able to get the entire project done?

For the **Known issues or Bugs** section you need to detail any issues or bugs
that you have in your code. For example maybe your code crashes randomly and you
couldn't figure out why. If your code doesn't have any issues you can simply
write NONE in this section.

For the **Sources used** section you must detail any sources you used outside of
the textbook or course website. If you write NONE in this section it is assumed
that you didn't use google at all. Be safe CITE!

## Task 5 - Add, Commit, Push your code

Once you are finished you need to make sure that you have pushed all your code
to GitHub for grading! You will not be submitting anything to canvas everything
will be submitted through GitHub as demonstrated in class.
