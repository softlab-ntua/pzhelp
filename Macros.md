- Program and procedures
  - [`PROGRAM`](#program)
  - [`PROC`](#proc)
  - [`FUNC`](#func)
- Read/write methods
  - [`READ_INT`](#read_int)
  - [`READ_REAL`](#read_real)
  - [`READ_STRING`](#read_string)
  - [`SKIP_LINE`](#skip_line)
  - [`WRITE`](#write)
  - [`WRITELN`](#writeln)
- File input/output methods
  - [`INPUT`](#input)
  - [`OUTPUT`](#output)
- [FOR Loop](#for-loop)
- Operators and math functions
  - [`MOD`](#mod)
  - [`AND`](#and)
  - [`OR`](#or)
  - [`NOT`](#not)
  - [`min`](#min)
  - [`max`](#max)
- Dynamic memory management
  - [`NEW`](#new)
  - [`DELETE`](#delete)
- Real numbers and constants
  - [`REAL`](#real)
  - [`REAL_DIG`](#real_dig)
  - [`REAL_MIN`](#real_min)
  - [`REAL_MAX`](#real_max)
  - [`REAL_EPSILON`](#real_epsilon)



## PROGRAM

This macro defines the entry point of your program. Thus, you need to include your main code in a `PROGRAM {}` block.

```c
#include "pzhelp"

PROGRAM {
  WRITELN("Hello world!");
}
```



## PROC

Declares a procedure, i.e.\ a function that returns no value.

```c
PROC hello_world() {
  WRITELN("Hello world!");
  // no return value
}
```



## FUNC

Declares a function.

```c
FUNC int square(int x) {
  return x * x;
}
```


## READ_INT

Reads an integer from the user input and returns its value.

```c
int age = READ_INT();
```



## READ_REAL

Reads a [real](#real) variable from the user input and returns its value.

```c
REAL height = READ_REAL();
```



## READ_STRING

Reads a string, i.e.\ a sequence of characters, from the user input and returns its value. Requires two arguments, the first being the size of the string that will be read and the second being the string variable where the input will be stored. The function also returns a reference to that variable.

```c
char * name;
READ_STRING(20, name);
```

or more shortly,

```c
char * name = READ_STRING(20, name);
```



## SKIP_LINE

Skips a line from the user input by reading and ignoring characters until a new line or the end of file (EOF) is reached.

```c
SKIP_LINE();
```



## WRITE

Receives a list of arguments which can be variables of different types and displays them to the user, each one separated by a space character. Supported variable types are integers (unsigned, long and long long modifiers are also supported), REALs, floats, doubles, characters, strings and booleans.

REALs, floats and doubles are all displayed with a precision of six decimal places.

```c
WRITE(42, 3.14, ',', "no man is an island");
```



## WRITELN

Offers the same functionality as [WRITE](#write	), except it also prints a new line at the end of the output.

```c
WRITELN("This string will be printed on its own line");
```



## INPUT

Opens the file corresponding to the path passed as argument and redirects `stdin` to that file. This means that every input method, such as `READ_INT` or `READ_STRING` etc. will read from the file instead of the standard input.

```c
INPUT("grades.csv");
char * first_entry = READ_STRING(100, first_entry);
```



## OUTPUT

Opens the file corresponding to the path passed as argument and redirects `stdout` to that file. This means that every output method, such as `WRITE` or `WRITELN` etc. will print to that file instead of the standard output.

```c
OUTPUT("results.txt");
WRITELN("This will be stored in the results.txt file");
```



## FOR Loop

Repeats a block of code for a given number of iterations. FOR also checks if the control variable or the loop limit is changed inside the loop, in which cases it throws an error.

You need to specify the following parameters:

-   Control variable: The variable that is used to check the loop limits and that will change in each iteration. You need to have declared that variable before the loop block.
-   Start value: This will be the initial value of the control variable. Thus, the control variable will have that value in the first iteration.
-   End value: This will be the final value of the control variable. Thus, the control variable will have that value in the last iteration. Note that the loop doesn't stop right after the final value is assigned to the control variable, but at the end of that iteration.
-   Step value: This will be the step by which the control variable will be increased or decreased. If the step is such that the control variable can't take the exact final value, the loop will be stopped right after the final value is exceeded and the corresponding iteration will not be executed.

The syntax is rather simple. Examples:

```c
int i;
// Use "TO" between the start and the end value when the control variable is increasing
FOR(i, 1 TO 10) {
    WRITE(i, ' '); // output: 1 2 3 4 5 6 7 8 9 10
}
```

```c
int i;
// Use "DOWNTO" when the control variable is decreasing
FOR(i, 10 DOWNTO 1) {
    WRITE(i, ' '); // output: 10 9 8 7 6 5 4 3 2 1
}
```

```c
int i;
// this prints all the even numbers from 2 to 20
FOR(i, 2 TO 20 STEP 2) {
    WRITE(i, ' '); // output: 2 4 6 8 10 12 14 16 18 20
}
```

```c
int i;
// let's combine everything
FOR(i, 17 DOWNTO -5 STEP 4) {
    WRITE(i, ' '); // output: 17 13 9 5 1 -3
}
```



## MOD

Returns the remainder of the Euclidean division between two operands. If negative numbers are used, the sign of the remainder returned matches the sign of the dividend.

```c
int r = 42 MOD 17;
```



## AND

Returns the result of the AND operation between two boolean operands. Therefore, it returns `true` if and only if both of the operands have a boolean value of `true`.

```c
if(hour >= 5 AND hour < 12) {
    WRITELN("Good morning!");
}
```



## OR

Returns the result of the OR operation between two boolean operands. Therefore, it returns `true` if and only if either one of the operands has a boolean value of `true`.

```c
if(day == 6 OR day == 7) {
    WRITELN("It's weekend, let's PaRtY!");
}
```



## NOT

Negates the boolean value of an expression.

```c
if(NOT(month == 12 AND day == 7)) {
    WRITELN("It's not Noam Chomsky's birthday yet");
}
```



## min

Returns the minimum of two values passed as arguments.

```c
int answer = min(17, 42);
```



### max

Returns the maximum of two values passed as arguments.

```c
int only_answer = max(17, 42);
```



## NEW

Dynamically allocates memory. You need to pass the variable type that will be stored, as the first argument, in order to allocate the correct number of bytes.

You can also allocate an *array* of variables of that type, instead of just one variable, by passing the size of the array as the second argument.

Returns the address of the newly created variable or the address of the first item of the newly created array. That's why we need to store the returned value as a pointer (remember, a pointer is just a variable containing the address of another variable).

```c
int * shoe_size = NEW(int);
*shoe_size = 42;
```

```c
// this allows you to declare an array whose size may not be known at compile time
int len = READ_INT();
int * shoe_sizes = NEW(int, len);

int i;
FOR(i, 0 TO len - 1) {
    shoe_sizes[i] = 42;
}
```



## DELETE

Frees up memory that had been previously allocated. Receives as an argument a pointer to that memory. If the memory had been allocated to a dynamic array, DELETE will free up all the memory blocks which were occupied by that array.

```c
DELETE(arr);
```



## REAL

PZHelp declares the variable type `REAL`, used for storing real numbers. `REAL` variables accommodate 15 to 16 digits, including both those before and after the decimal point.

```c
REAL pi = 3.14159265358979;
```



## REAL_DIG

This is the number of decimal digits of precision for the `REAL` variable type.



## REAL_MIN

This is the minimum positive real number that is representable in type `REAL`.



## REAL_MAX

This is the maximum number representable in type `REAL`.



## REAL_EPSILON

This is the difference between 1 and the smallest number representable in type `REAL` that is greater than 1.

