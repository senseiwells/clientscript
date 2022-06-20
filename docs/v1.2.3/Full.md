# Documentation

This page is a step by step guide to get you started with Arucas, showing you how to install the language, and how to write code for the language, showing you what is possible in the language as well as its features.

This guide is for Arucas 1.2.0+

> #### [Installation ](#installation)
> #### [Development Environment ](#development-environment)

> #### [Comments ](#comments)
> #### [Literals ](#literals)
> #### [Variables ](#variables)
> #### [Output ](#output)
> #### [Input ](#input)
> #### [Operators ](#operators)
> #### [Conditional Statements ](#conditional-statements)
> #### [Switch Statements ](#switch-statements)
> #### [Loops ](#loops)
> #### [Functions ](#functions)
> #### [Members ](#members)
> #### [Lists ](#lists)
> #### [Maps ](#maps)
> #### [Errors ](#errors)
> #### [Imports ](#imports)
> #### [Classes ](#classes)
> #### [Enums ](#enums)
> #### [Threads ](#threads)
> #### [Java](#java-integration)

## Installation

This installation guide is for those who want to just run vanilla Arucas not bundled in with another application. If you are running Arucas inside another application you can just skip this part.

First you need to install the latest version of Arucas, you can download the jar file from [here](https://github.com/senseiwells/Arucas/releases). 
After downloading the jar make sure you have Java 16 or above installed as Arucas relies on this, you can then run the jar using the command line:
```
java -jar Arucas-1.2.0.jar -noformat
```
Now you will be running the Arucas Interpreter, here you can type any Arucas code and it will be run, if you want to exit the interpreter you can simply type:
```
exit
```
To run a file with Arucas code from the command line you can use the Built-in function:
```kotlin
run("path/of/arucas/file.arucas");
```
Alternatively you can do this directly in the command line to run a file:
```
path/of/arucas/file.arucas
```

## Development Environment

We recommend the use of the [Arucas Plugin](https://github.com/Kariaro/ArucasHighlighter/tree/main) designed for IntelliJ by [HardCoded](https://github.com/Kariaro), this highlights your code informing you of errors in your code, and adding nice colours :).

Alternatively if you do not wish to use IntelliJ another option is to use VSCode and set the language to `Java`, and disable validation for error highlighting. You can also configure VSCode to automatically recognise `.arucas` files as Java.

#

So now that you are able to run Arucas files what do we put inside? If you have not already you should take a look at the [Language Syntax]() page briefly but we will cover everything in detail here.

## Comments

Lets start by introducing comments, comments don't do anything in terms of running the code but instead they allow you to describe what is happening in the code, when the code is run all comments are completely ignored.

There are two types of comments, single line and multiline. A single line comment can be written by typing `//` followed by your text, and a multi line comment consists of `/*` followed by your line(s) of text and then closed with `*/`:
```
// This is a single line comment
/*
 This is a multi line comment
 Very cool!
 */
```
An important thing to note about single line comments is that text will only be ignored after the `//`, anything on the left of the comment will still run as code.

## Literals

### String literals

Creating a string is similar to all other languages, you can create a string of characters by using double quotes, `""`, or single quotes, `''`, this is personal preference as there is no difference.
```kotlin
"Example string"
'Example string'
```
You are also able to escape certain characters by using the `\` character, this is to be able to use `"`, `'`, and other characters like tab `\t`, and newline `\n` inside of strings.
```kotlin
"\tIntended example with new line\n"
```

Now if you tried to just have a string literal in an Arucas file it would throw an error, this is because all code expressions must be followed by a `;`, this is how the language is able to know when one expression ends and another starts.
```kotlin
"This is valid syntax!";
```

### Number literals

Numbers are very easy to create, you can simply just type them! Numbers can be easily modified and are an essential value, we will explore more about how to manilpulate numbers in the operators section.
```kotlin
0; 1; 2; 3; 4; 5;
```
Decimals are also supported:
```kotlin
1.5; 3.1415926; 
```
You are also able to write numbers in hexadecimal (base 16), don't worry if you don't know what this is, it's not necessary to use, just a handy feature.
```kotlin
0xFF; 0x1B9E00;
```

### Boolean literals

Booleans are very simple, there are just two possible literals for these.
```kotlin
true;
false;
```
These values are used to do boolean logic which we will cover in the operators section.

### Null literal

Null is as simple as it gets, there is only one literal for it:
```
null;
```
The `null` value represents nothing, it is used when a value doesn't exist, be careful will how it is used though, null safety is important, you don't want to get `null` values where you want other values.

### List literals

Lists are a more complex data structure and these allow you store many values of any type inside of it, including other lists. Lists in Arucas have a very simple syntax:
```kotlin
["Example", 1, true, null];
```
Lists are great for storing many pieces of data in one place. We will cover lists more in detail later in this guide.

### Map literals

Maps are also a complex data structure that allow you to map one value to another, allowing you to make keys to access values. The syntax is very straightforward:
```kotlin
// Here we are mapping numbers to their names
{1: "one", 2: "two", 3: "three"};
```
Maps are a fast way of storing data that needs to be accessed, again we will cover maps in greate detail later.

## Variables

A key part of programming is being able to manipulate data and we do this by using variables, you can think of a variable like a container. To define a variable we need to give it a name and then a value, and we can assign the variable with the value by using the assignment operator, `=`:
```kotlin
exampleVariable = "Example string";
```
Assigning a variable is like putting something inside the container.

Variable names can only include letters and underscores, by convention variable names should follow camel casing, this is where you capitalise all the words bar the first then squash them together.

Once you have defined a variable you can reassign the variable by again using the assignment operator.
```kotlin
exampleVariable = "Example string";
exampleVariable = "Overwritten!";
// exampleVariable now stores the value: "Overwritten"
```
Variables can store any type of value, we will come onto other types of values, for example numbers or booleans.

Now once you have stored a value in a variable you can use it by referencing the name of the variable, refering back to the previous analogy, this is like peeking into the container to see what is inside.
```kotlin
exampleVariable = "Example string";
print(exampleVariable);
// We would get an output of: Example string
```

## Output

Now we know how to create a string we can output it to the console. We can do this by using a function, we will cover functions in more detail later but for now we can just use it and accept that it works. The main function that you will use to output is called `print`, and to call the function we follow the name up with a pair of brackets:
```kotlin
print();
```
This won't actually print anything since we haven't told it what to print. We can provide this information by adding arguments inside our brackets:
```kotlin
// Having 1 parameter in the print function causes 
// it to automatically add a new line after it
print("Hello World!");
// This would print: Hello World\n
```
The `print` function also has the capability of concatenating (joining) strings togther
```kotlin
print("Hello", "World");
// This would print: Hello World
```
## Input

We can take input from the console, by using another simple function called `input`, unlike print this function can only have one parameter, this is the prompt that the user is displayed with for their input:
```kotlin
input("What is your name? ");
```
The user will then be able to type in the console and once they press enter their input will be submitted.

So now that we've got the function to prompt the user with input we need to store it, and we can to this by using a variable, like before how we stored literals inside a variable we can store what we call the return value of the function in a variable too:
```kotlin
userInput = input("What is your name? ");
```
Now that we have the user input stored in a variable we can use it inside our code:
```kotlin
userInput = input("What is your name? ");
// If the user inputted "mike"
print("Your name is: ", userInput, "\n");
// This should print Your name is: mike\n
```

## Operators

There are quite a few operators in Arucas but don't worry most of them are similar to other languages and are easy to pick up!

### `(` and `)` - Brackets

While not necessarily an operator I think that brackets are an important thing to mention before we talk about the other operators. Similar to what you might have learnt in maths brackets allow you to change the order of operations. We will cover where brackets may be useful in the following operators.

### `=` - Assignment

We have already covered this operator, the assignment operator, briefly when talking about creating variables, but I will reiterate, this operator allows you to assign a value to a variable:
```kotlin
exampleVariable = "Example string";
```
The assignment operator also has a neat feature that allows you to assign multiple values at the same time using lists:
```kotlin
example1, example2, example3 = [1, 2, 3];
print(example1); // This would print 1
print(example2); // This would print 2
print(example3); // This would print 3
```
This works with any list but the list must be the same size as the number of values you want to assign to:
```kotlin
// This would crash since there is not a match
// with the number of variables and values
example1, example2 = [1, 2, 3];
```

Another thing that is important about assignment is that it will also return the value that was just assigned, for example:
```kotlin
v = 10;
print(v = 12);
// This will print 12 because the assignment
// returns the value that was assigned which was 12
```
A mention about brackets here, the value being assigned will always be evaluated first so for example:
```kotlin
v = 0;
// We will cover the addition operator in the next
// section you might want to read that first then come back
print(v = 10 + 3);
// This will print 13 because v was assigned
// to the value of 13 because 10 + 3 = 13
```
But what if we want to assign a value to a variable then manipulate that value to print:
```kotlin
v = 0;
// We put the assignment in brackets so it
// happens with out adding the 3 to the 10
print((v = 10) + 3);
// This will print 13 because v was assigned to 10
// and then the assignment returned the value which 
// in this case was 10, then it added 3 to that value
// which equals 13 which was then printed

print(v);
// This will print 10 since we did not assign 13 to v
``` 

### `+` - Addition

This is the addition operator, this allows you to add two things together, usually numbers, but this operator by default also works with strings to concatenate them.
```kotlin
result = 9 + 10;
print(result); 
// This would print 21... I mean 19

print(0.5 + 0.5);
// This would print 1

stringResult = "5" + "6";
print(stringResult);
// This would print 56

print("Hello W" + "orld");
// This would print Hello World 
```

The addition operator can also be used as a unary operator, this means that you can have it on the left side of a value with no other value on the left like this:
```kotlin
print(+10);
// This would print 10
```
This is pretty redundant but is to be consistent with the subtraction unary operator.

### `-` - Subtraction

This is the subtraction operator, this allows you to take away one value to another, by default this operator only works with numbers.
```kotlin
someMath = 29 - 8;
print(someMath);
// This would print 21

print(9 - 80);
// This would print -71
```

The subtraction operator can also be used as a unary operator, this allows you to write negative values:
```kotlin
print(-10);
// This would print -10
```
An important thing to note is that the subtraction operator has a low predecence and so it will be applied last, here is an example:
```kotlin
-2 ^ 2; // -> -4, this does 2 ^ 2 then makes it negative

(-2) ^ 2; // -> 4
```

### `*` - Multiplication

This is the multiplication operator, and this allows you to multiply two values together, by default this only works with numbers.
```kotlin
print(5 * 4);
// This would print 20

print(20 * 0.5);
// This would print 10
```

An important thing to note is that multiplication will take precedence over addition and subtraction, here's an example:
```kotlin
3 + 4 * 5; // -> 23
```
If you want addition to take precedence then you will need to use brackets:
```kotlin
(3 + 4) * 5; // -> 35
```

### `/` - Division

This is the division operator, this allows for dividing of two values, by default this only works with numbers.
```kotlin
print(20 / 2);
// This would print 10

print(3.141 / 500);
// This would print 0.006282
```

Similar to multiplication division takes precedence over addition and subtraction.

### `^` - Exponent

This is the exponent operator and allows you to raise a base to a power, by default this only works with numners.
```kotlin
print(2 ^ 5);
// This would print 32

print(25 ^ 0.5);
// This would print 5
```

Exponents take precedence over both addition, subtraction, multiplication, and division, here's an example:
```kotlin
5 * 2 ^ 3; // -> 40

(5 * 2) ^ 3; // -> 1000
```

### `++` and `--` - Increment and Decrement

These are the increment and decrement operators, by default these only work on numbers, these are just syntactic sugar for making a value equal to one more or less than it's current value:
```kotlin
value = 9;
value++; // value now equals 10
value--; // value now equals 9
```
Using the increment and decrement operators is the exact same as writing:
```kotlin
value = 9;
value = value + 1; // value now equals 10
value = value - 1; // value now equals 9
```
Internally Arucas compiles the first example into the second example. The increment and decrement are just a short hand.

### `.` - Dot

The dot operator is used to access and call members of a value, don't worry if you don't know what this means yet we will cover this in more detail. Every value has members by default and this is how you can interact with them.
```kotlin
value = "Example string";
value = value.uppercase();
// value now equals "EXAMPLE STRING"
```

### `&&` - AND

This is the and operator and by default is used between boolean values for boolean logic. Here is and example:
```kotlin
true && true; // -> true
true && false; // -> false
false && true; // -> false
false && false; // -> false
```
The and operator takes two boolean values and will only return `true` if both boolean values are `true` otherwise it will return `false`.

An important feature of this and operator is that it short circuits. Now to explain this you need to understand that the expressions are evaluated one at a time and it goes from left to right. If the left expression of the and operator is `false` then it knows that no matter whether the right hand side is `true` or fast it will always return `false` so it skips evaluating the right hand side.

If you want to use an and operator that evaluates both sides you can use the bitwise and operator `&`, we will go over this later.

### `||` - OR

This is the or operator and by default is used between boolean values for boolean logic. Here is an example:
```kotlin
true || true; // -> true
true || false; // -> true
false || true; // -> true
false || false; // -> false
```
The or operator takes two booleans and will only return `true` if at least one of the boolean values is `true`, otherwise it will return `false`.

Similarly to the and operator, this will short circuit, if the left hand side evaluates to `true` then it will always return `true` so it skips evaluating the right hand side.

If you want to use an or operator that evaluates both sides you can use the bitwise or operator `|`, we will again go over this later.

### `~` - XOR

This is the exclusive or operator and can be used with booleans (as well as numbers, but will cover this later) by default. Here is an example:
```kotlin
true ~ true; // -> false
true ~ false; // -> true
false ~ true; // -> true
false ~ false; // -> false
```
This exclusive or operator takes two boolean and will only return `true` if the boolean values are different from each other, in this case one must always be `true`, and one must always be `false` for it to return `true`.

This operator does not short circuit since it always needs to check both left and right hand side, this is the same operator that is used for the bitwise XOR, we will go over this later.

### `!` - NOT

This is the not operator and by default only can be used for booleans, this inverts the boolean, here is an exampe:
```kotlin
!true; // -> false
!false; // -> true
```
This takes the boolean and returns the opposite boolean value, unlike the other operators shown this a unary only operator, meaning it only has a value on the right hand side and not the left.

### `==` - Equals

This is the equals operator and can be used between any values, it checks whether two values are equal.
```kotlin
true == false; // -> false
"string" == "string"; // -> true

num = 10;
num == 10; // -> true
```
This is often useful for doing `null` checks, the safest way to do a null check is the following:
```kotlin
example = null;
example = "";
null == example; // -> false
```

### `>`, `<`, `>=`, and `<=` - Comparison

These are the comparison operators that can be used to see whether values are greater than, less than, greater than or equal, or less than or equal. Be default this only works with numbers.
```kotlin
9 > 5; // -> true
9 < 5; // -> false
5 >= 5; // -> true
6.5 <= 6.2; // -> false 
```

### `&` - Bitwise AND

This is the bitwise and operator, this works on both booleans and numbers. On booleans it acts similar to the `&&` operator but does not short circuit. On numbers it compares the bits, here is an example of `420 & 255`
```
110100100 <- 420
011111111 <- 255
--------- &
010100100 <- 164
```
It compares the bits in each position with eachother and will only return 1 if both bits in both numbers are 1 in that position.

### `|` - Bitwise OR

This is the bitwise or operator, this works on both booleans and numbers. On booleans it acts similar to the `|` operator but does not short circuit. On numbers it compares the bits, here is an example of `240 | 14`
```
11110000 <- 240
00001110 <- 14
-------- |
11111110 <- 254
```
It compares the bits in each position with eachother and will return 1 if either of the bits at that position is 1.

### `~` - Bitwise XOR

This is the bitwise exclusive or operator, this is the same operator that is used for the boolean xor previously mentioned, but this can also be used to manipulate bits. Here is an example: `165 ~ 170`
```
10100101 <- 165
10101010 <- 170
-------- ~
00001111 <- 15
```
It compares the bits in each position with eachother and will only return 1 if only 1 of the bits is 1 and the other is 0.

### `>>` and `<<` - Bitshift right and Bitshift left

These are the bitshifting operators, these by default only work on numbers, they work by taking the bits of the number and shifting them left or right by a certain amount.
```kt
255 >> 2; // 11111111 -> 00111111 = 63
64 << 1; // 0100000 -> 10000000 = 128
```

## Scopes

Scopes are sections in your program that you definte your code, scopes determine what variables, functions, and classes are accessible, by default the program runs in the global scope where everything is accessible to the rest of thr program.

You are able to define scopes by using the `{` and `}`. For example:
```kotlin
// Global scope
{
    // Defined scope
}
```

Anything that is defined in a scope is only accessible to that scope and any scopes inside of that scope:
```kotlin
// Global scope
// Anything here is accessible ANYWHERE in the program
// i is in the global scope
i = 10;
{
    print(i); // -> 10
    // j is in a sub scope and cannot be accessed
    // in any parent scope, in this case that would
    // be the global scope
    j = 20;
    {
        print(i); // -> 10
        print(j); // -> 20
        // Both i and j are accessible because this
        // scope has parents with both of these values
    }
}
print(j); 
// This would throw an Error because
// j is not defined in this scope

print(i); // -> 10
```

Assigning variables in scope also works similarly, if a variable is defined in the global scope and you reassign that variable in a scope then the variables in the global scope will be modified.
```kotlin
i = 0;
{
    i = 10;
}
{
    i = i - 1;
}
print(i); // -> 9
```

## Conditional Statements

Conditional statements allow you to branch your code into different scopes based on a boolean. The keywords that are used for conditional statements are `if` and `else`. It works by evaluating an expression, if it evaluates to true then it will run the scope after the `if` statement, otherwise if there is an `else` after the if then it will run that scope instead:
```kotlin
if (true) {
    // This will always be run
    // since true is always true
}

if (false) {
    // This will never run
    // since false is always not true
}
else {
    // This will always run
}
```

Here is a better example:
```kotlin
name = input("What is your name");
if (name == "Sensei") {
    print("Wow that's a very cool name!");
}
else {
    print("That's a cool name but not as cool as Sensei!");
}
```

Short hand syntax, this syntax applies for most statements that have a scope after it.
This allows you to not use the braces after a statement but only allows you to have one statement inside of it:
```kotlin
// Skipping the braces
// for one statement
if (true) print("That was true");
else print("This is imposible");
```

This short hand syntax allows use to easily chain these conditional statements to create `else if`:
```kotlin
if (false) {
    // Do something
}
else if (true) {
    // Do something else
}

// This above is the same as writing:
if (false); // Do something
else {
    if (true) {
        // Do something else
    }
}
// You are just skipping the braces after else
// since if is only one statement
```

Long chains of `else if`s are not recommended and instead you should take a look at the `switch` statement which has a much nicer syntax than:
```kotlin
name = input("Name?");
if (name == "Alex") {
    // Alex
}
else if (name == "James") {
    // James
}
else if (name == "Xavier") {
    // Xavier
}
else if (name == "Jenny") {
    // Jenny
}
// ...
```

## Switch Statements

Switch statements allows you to match values with an input, switch statements are faster when comparing literals (String, Number, Boolean, Null) as they can be evaluated at compile time. Switch statements have cases and will match the input to a case which will then run a scope accordingly. Switch statements cannot have duplicate literals but can have expressions that are evaluated at run time (like functions):
```kotlin
name = input("Name?");
switch (name) {
    case "Alex" -> {
        // Alex
    }
    case "James" -> {
        // Alex
    }
    case "Xavier" -> {
        // Xavier
    }
    case "Jenny" -> {
        // Jenny
    }
}

switch (name) {
    case input("Name again?") -> {
        // name == input("Name again?")
    }
}
```

Switch statements also have the ability to have multiple values for each case, as well as having a default case which will be run if the input matches none of the cases.
```kotlin
name = input("Name?");
switch(name) {
    case "Alex", "Steve" -> {
        // name == "Alex" || name == "Steve"
    }
    case null -> {
        // name == null
    }
    default -> {
        // Name was not Alex or Steve and was not null
    }
}
```

## Loops

There are different ways of looping in Arucas, they all are similar but some work better in certain applications.

### `while`

While loops are the simplist form of loops they work by checking a condition then running a section of code, after it has finished running it will return to the condition and check it again, the loop will end when the condition is evaluated to false or if a `break` statement is used inside of a loop, but will will cover this later.

Here is a simple example of how you could make an infinite loop that will never end.
```kotlin
// The condition inside this while expression 
// is true, this means it will always be true
// and as a result this loop will never end
while (true) {
}
// This program will never end naturally
```

You can use a while loop to iterate over numbers, here is an example:
```kotlin
counter = 0;
// This will loop until counter >= 10
while (counter < 10) {
    counter++;
    // Increments the counter by 1
}
```

However this way of iterating can lead to human errors, accidentally missing the increment of the counter would lead to the loop never ending and so we would more commonly use a `for` loop. 

### `for`

The for keyword is used to define a for loop, similar to the C style loop. The for expression contains 3 sub expressions, the first is evaluated at the start of the loop only, the second is evaluated as the condition for the loop to continue similar to the while loop, and the last gets executed whenever the loop reaches the end.
```kotlin
// Usually define the initial variable in the first expression (i = 0)
// The condition in the second (i < 10)
// Thirdly the expression that gets run at the end of each loop (i++)
for (i = 0; i < 10; i++) {
}
```

Similarly to the while loop you can easily make an infinite for loop, the expressions in the for loop can remain empty allowing you to do something similar to the following:
```kotlin
// No first expression
// Condition is always true
// No final expression
for (; true;) {
}
```

A common use for `for` loops is iterating over the indexes of a list, we haven't covered lists in great detail just yet but you are welcome to come back here once we have.
```kotlin
list = ["foo", "bar", "baz"];

// Remember indexes start at 0!
for (i = 0; i < len(list); i++) {
    item = list.get(i);
    print(item);
}
```

### `foreach`

For each is a developed version of the for loop allowing easier iteration of collections, this could be lists, sets, collectors, etc.
Similar to the previous example in the for loop but you do not need to define an index to iterate over, you can just simply iterate over each item in the list.
```kotlin
list = ["foo", "bar", "baz"];

foreach (item : list) {
    print(item);
}
```

This is a much simplier way of iterating, something that you should keep in mind is that when iterating over maps, it iterates over the keys in the map, you can then use that to get the value if you wish:
```kotlin
map = {"foo": "oof", "bar": "rab", "baz": "zab"};

foreach (key : map) {
    value = map.get(key);
    print(key);   // -> foo, bar, baz
    print(value); // -> oof, rab, zab
}
```

### `break`

The break keyword allows you to break out of a loop at any point, and the lopp will no longer be executed further, this cannot break out of nested loops only the most recent loop that you are inside. The break keyword works inside of `while`, `for`, and `foreach` loops.
```kotlin
// Same iteration as shown before from 0-9
for (i = 0; i < 10; i++) {
    // If i is greater than 5 we stop and break the loop
    if (i > 5) {
        break;
    }
}
```

### `continue`

The continue keyword is similar to the break keyword in that it allows you to disrupt the flow of a loop. Unlike the break keyword however this doesn't terminate the loop, instead it stops the loop and returns it back to the beginning, this works with `while`, `for`, and `foreach` loops.
```kotlin
for (i = 0; i < 10; i++) {
    if (i == 6) {
        // We go back to the start of the loop
        // the final statement in the for loop
        // still gets executed so i increments
        continue;
    }
    print(i); // 0, 1, 2, 3, 4, 5, 7, 8, 9 <- no 6
}
```

### Recursion

Recursion is a type of loop or iteration that works when a function calls itself causing a chain effect, usually the function has a condition where it does not call itself and exits, usually recursion is slower than the other traditional loops and is more unsafe as it can lead to a possibility of the stack overflowing which will lead to it throwing an error.
```kotlin
// This function is unsafe and will result in a stack overflow
fun recurse() {
    // Calls itself
    recurse();
}
```

A more safe approach if you must use recursion is to have a counter that lets the function know how deep it is:
```kotlin
fun recurse(depth) {
    if (depth > 10) {
        print("Depth of 10, stopping...");
        return;
    }
    // Increase the depth ever time we recurse
    recurse(depth + 1);
}
// This is now safe to call, it will only call itself
// Until it hits the depth limit
recurse(0);
```

## Functions

Functions are a great abstraction that we use to hide complexity and easily reuse code, functions allow you to write code that can be executed from elsewhere in your program by referencing the functions name, or identifier. 

### Simple Functions

Functions in Arucas are defined with the `fun` keyword followed by an identifier then brackets which contain your parameters for the function we will cover this more in a moment, then it is followed by some statements in a scope, here is an example:
```kotlin
fun exampleFunction() {
    print("Function was called");
}

// To call a function we use the name of the
// function then brackets to call it
// similar to how we use the print function
exampleFunction(); // prints "Function was called"
```

Now if we wanted to add some parameters:
```kotlin
// The parameter is a variable that you can
// use inside of your function, in this case
// we take in a name then use it to print a statement
fun anotherFunction(name) {
    print("Your name is " + name + "!");
}

// To call the function with a parameter we 
// just need to do the same as before but
// include what we want to pass into the function
// as the name variable
anotherFunction("sensei"); // prints "Your name is sensei!"
```

You can add more parameters by adding commas and listing all the parameters you wish to take in:
```kotlin
// Parameter names must be different
// so you can differentiate between them in the function
fun moreFunction(number1, number2) {
    // We take both numbers and print the sum of them
    print(number1 + number2);
}

// To call the function we put the parameters
// we want to pass in separated by commas in the
// same order that the function has them
// in this case number1 = 9, number2 = 10
moreFunction(9, 10); // prints 19
```

### Variable Parameters

You are also able to take in a variable amount of parameters, this means that you can call the function with as many parameters as you want and it is passed into the function as a list. To do this we define the parameter in the function followed by `...`. 
```kotlin
// The numbers parameter is always a list
// filled in with the parameters
variableParameters(numbers...) {
    total = 0;
    // Since numbers is a list we can iterate
    // over it using a foreach loop
    foreach (num : numbers) {
        total = total + num;
    }
    // This function adds up all the given numbers
    // and then outputs the total
    print(total);
}

variableParameters(1, 2, 3, 4, 9); // prints 19
// numbers = [1, 2, 3, 4, 9]

variableParameters(); // prints 0
// numbers = []

variableParameters(-9); // prints -9
// numbers = [-9]
```

Another important thing to know is that functions are first class objects, meaning that they are treated just like any other value. So you can store functions in variables and pass functions into other functions which allows you to write more flexible code.
```kotlin
fun exampleFunction() {
    print("Example function was called!");
}

// We don't call the function just reference it by it's name
// so exampleFunction not exampleFunction()
variable = exampleFunction;

// Now since variable stores the exampleFunction function
// we can actually call variable as if it were a function
variable(); // prints "Example function was called!"
```

### Lambdas

You are also able to create anonymous functions or more frequently called lambdas, these functions can be defined on the go and cannot be called like normal functions since they do not exist with a name, but you can still call them through a variable like previously shown, you can definte an anonymous function with the `fun` keyword and skipping he identifier and then brackets with the parameters followed by your statements in a scope.
```kotlin
lambda = fun() {
    print("This is a lambda");
};
lambda(); // prints "This is a lambda"
```

Here is a use when you need to pass a function into another function:
```kotlin
fun runFunctionWithDelay(delay, function) {
    // This pauses the program for an amount of milliseconds
    sleep(delay);
    // This calls the function
    function();
}

// In this case our lambda cannot have parameters
// because runFunctionWithDelay doesn't pass in any parameters
runFunctionWithDelay(100, fun() {
    print("Printed after 100 milliseconds");
});
```

### Return Statements

Functions have the ability to return values, functions technically always return values infact, similar to how the `input` function works which we looked at earlier that returns whatever the user inputted into the console. Return statements can be used inside of functions to return a value, you can do this by using the `return` keyword followed by a value, or alternatively if you don't want to return a value you can just leave it blank, if you leave it blank then the function will by default just return `null`, then follow that by a semicolon:
```kotlin
fun biggerThanFive(num) {
    if (num > 5) {
        return "Bigger than 5";
    }
    return "Smaller than 5";
}

// We need to assign the return value to something
biggerThan5 = biggerThanFive(20); // -> "Bigger than 5"

print(biggerThan5); // prints "Bigger than 5"

// We can also ignore the return value if we don't want it
biggerThanFive(4);
// In this case ignoring the return value is pointless but
// this may be the case of other functions that run code
```

Here is an example where `return` is used to escape a function to stop its execution, return does not always need to return a value and this is a very common usecase which can reduce your indentation level which can make your code cleaner and easier to read overall. 
```kotlin
fun printNameIfOver18(name, age) {
    if (age < 18) {
        // Under 18 so we don't want to
        // execute any more of this function
        // so we just return out of the function
        return;
    }
    print(name);
}

// Another way of writing the previous function
fun printNameIfOver18(name, age) {
    // In this case the indentation doesn't matter
    // but when you have long chains it can make a 
    // big difference and so you might want to return
    if (age >= 18) {
        print(name);
    }
}
```

### Function Scoping

Functions capture variables in the previous scopes to be able to use them in the scope, this lets you use variables from previous scopes:
```kotlin
{
    // Inner scope
    inner = "Random String";
    fun doSomething() {
        print(inner);
    }
    
    doSomething();
}
```

However functions also have a special property where since they capture the whole previous scope that can access variables that are not yet defined:
```kotlin
{
    fun doSomething() {
        // Technically this variable doesn't exist yet
        print(postFunctionVariable);
    }

    // Now it exists
    postFunctionVariable = 10;

    // Now we call the function
    doSomething();
}
```

However if you call the function before you definte the variable the program will throw an error:
```kotlin
{
    fun doSomething() {
        // Technically this variable doesn't exist yet
        print(postFunctionVariable);
    }

    // Now we call the function
    doSomething();
    // This will crash because postFunctionVariable is not defined yet!

    // Now it exists
    postFunctionVariable = 10;
}
```

Here is an example that may seem confusing at first but understanding how scoping of functions works helps:
```kotlin
fun generatePrintFunction(stringToPrint) {
    function = fun() {
        // The stringToPrint variable is captured here
        // and saved for later in this function
        print(stringToPrint);
    };
    return function;
}

printFunction = generatePrintFunction("FOO");
// printFunction now contains a lambda that prints a string
// the lambda has the variable "FOO" saved in it that it will use
// when we call the printFunction

printFunction(); // prints "FOO"
```

Another example where the variable changed between function calls:
```kotlin
variable = 10;

fun printSomething() {
	print(variable);
}

printSomething(); // prints 10

variable = 20;
printSomething(); // prints 20
```

### Overloading Functions

Overloading functions is the ablility to have functions that have different number of parameters defined separately and not interfer with eachother, overloading functions are possible inside of classes which we will cover later, but defining functions in the scope you cannot overload them, one will simply overwrite the other. This may be possible at a later date at which point this section of the documentation will be updated.

Here is an example:
```kotlin
fun exampleFunction() {
    print("ExampleFunction");
}

exampleFunction(); // prints "ExampleFunction"

// Define another function with name exampleFunction
// with different amount of parameters
fun exampleFunction(parameter) {
    print("ExampleFunctionWithParam");
}

exampleFunction(null); // prints "ExampleFunctionWithParam"

exampleFunction(); // throws an error since original function was overwritten
```  

This however is not the case with built in functions, since they are implemented internally they work slightly different and as such they are able to be overloaded, all information on built in overloads will be documented separately, see the next section on Built In Functions.

### Built In Functions

Throughout this documentation I have been using built in functions, these functions are implemented natively in the language that allow you to do the basic functions, some examples that I have been using are `print`, `input`, and `sleep`.
There is a list of these basic functions and these provide some key functionality to the language so you should review them, and they can be found on the separate page [here](). 

## Members

Members are part of values, they can either be functions or fields. They allow you to interact and use part of the values. These are usually accessed through the `.` operator, followed by the field or function name (and brackets if you are calling the function). Classes can also have members, these are known as static members, static members are not based on an object but instead on the class definition itself.
```kotlin
hello = "hElLo";
// Lowercase is a method of <String>, and
// when it gets called it returns a complete
// lowercase representation of the string
print(hello.lowercase());

// type is a static field of the String class
// this is the type that represents the class
print(String.type);
```

Usually each class has its own static members and each value has its own members too, these are documented on a separate page and you can find that [here]().

## Lists

Lists are a form of collection, they are key data structure in the language, they allow you to store multiple values inside of one value, lists in Arucas are dynamic meaning that they do not have a fixed size you are also able to put any type of value in a list. Lists are ordered data structure meaning their order stays consistent with how you input values into the list.

### Simple Lists

Lists are very simple to use, as mentioned earlier in the documentation they can be declared with the List literal `[]`:
```kotlin
// Creating an empty list
list = [];
```

You are also able to put values inside the square brackets to declare a list with items in them.
```kotlin
// List with values 1, 2, "string"
list = [1, 2, "string"];
```

We can get the number of values inside of a list by using a built in function: `len`:
```kotlin
print(len([true, false, null])); // -> 3

print(len([])); // -> 0
```

### Using Lists

An important concept is understanding indexes of lists, each value as an index in a list with the first value in the list having an index of 0 and then incrementing by one until the last value. We can then use this to access values in the list.
```kotlin
list = ["first", "second", "third"];

// Index 0 corralates to the first index
print(list.get(0)); // -> "first"

// A short hand for accessing lists was introduced in 1.2.0
// We can use the [] operator to access an index in the list
print(list[1]); // -> "second"
```
Something to note is that if an index is provided that is outside the bounds of the list then an error will be thrown.

To manipulate the contents of the list we can take a look at the available methods:
```kotlin
list = [1, 2, 3];

// append method adds a value **to the end** of the list
list.append(4);

// insert method adds a value at a specific index in the list
list.insert(0, 0); // list = [0, 1, 2, 3]

// remove methods removes a value at a specific index
list.remove(3); // list = [0, 1, 2]

// set method sets the value at a specific index
list.set(0, "zero"); // list = ["zero", 1, 2]

// A short hand for assigning indexes of lists was introduced in 1.2.0
// We can again use the [] operator to assign an index in the list
list[1] = "one"; // list = ["zero", "one", 2]
```

### List Unpacking

Lists provide special functionality in Arucas as they provide the ability to unpack them. This means you are able to extract all of the variables in the list into variables. Here is an example:
```kotlin
// position with list having x, y, and z coordinates
position = [100, 50, -900];

// If we wanted to extract those we could do this:
x = position.get(0);
y = position.get(1);
z = position.get(2);

// Or we can use a shorthand: list unpacking
x, y, z = position; // x = 100, y = 50, z = -900

// To be able to do this the number of variables
// you are assigning must be equal to the length
// of the list, otherwise it will throw an error
```

Changing the values in the variables will not change the values in the list:
```kotlin
position = [100, 50, 200];
print(position); // -> [100, 50, 200]

x, y, z = position; // x = 100, y = 50, z = 200

x = 10;
// We now set x to 10 but this does not change
// the value in the list that x was assigned first

print(position); // -> [100, 50, 200]
```

## Maps

Maps like lists are a form of collection, maps can be seen as similar to lists, but instead of using indexes to access a value maps allow you to definte a specific key value to access certain values. Maps have a literal and by default these will be ordered based on the order they are inputted. Maps also have no fixed size.

### Simple Maps

Maps have a literal: `{}` which can be used to create maps. In the literal you must declare a key and a value which are separated by a colon:
```kotlin
map = {"key": "value"};

// We can also declare an empty map
map = {};
```
Any types can be used for keys or values, for custom classes you need to ensure they have an appropriate hashing function however we will cover this later in the classes section.

To define multiple key value pairs we just separate them with a comma, this is usually done over multiple lines:
```kotlin
map = {
    "key": "value",
    "otherKey": "value",
    "foo": "bar"
};
```

Similarly to Lists we can get the length of the map by using `len`, this returns the number of key value pairs:
```kotlin
len({"a": "A", "b": "B"}); // -> 2

len({}); // -> 0
```

### Using Maps

Maps are very similar to lists except using specific keys to access and assign values, here are some examples:
```kotlin
map = {
    "one": 1,
    "two": 2,
    "three": 3
};

// get method allows us to get a value using a key
print(map.get("one")); // -> 1
// Similarly to lists maps also allow the short hand by

// using the bracket operator
print(map["two"]); // -> 2

// put method allows us to add a key value pair
// this will replace any previous value with the given key
map.put("four", 4); // map = {"one": 1, "two": 2, "three": 3, "four": 4}

// Here is an example of it replacing an existing key
map.put("four", 0); // map = {"one": 1, "two": 2, "three": 3, "four": 0}

// Similar to list we can also set keys by using the bracket operator
map["four"] = 4; // map = {"one": 1, "two": 2, "three": 3, "four": 4}

// remove method removes a key and value from the map
map.remove("one"); // map = {"two": 2, "three": 3, "four": 4}
```

Some other useful methods of the map are those that get all of the keys and values:
```kotlin
map = {
    "one": 1,
    "two": 2,
    "three": 3
};

// These methods return lists containing keys and values
keys = map.getKeys(); // keys = ["one", "two", "three"]
values = map.getValues(); // values = [1, 2, 3]
```

Another useful thing to note is that when using the `foreach` loop maps will loop over their keys, inside of the loop you can the use it to access the value:
```kotlin
map = {
    "one": 1,
    "two": 2,
    "three": 3
};

foreach (key : map) {
    value = map[key];
    // Do something
}
```

### Sets

Sets are another form of collection. A set is basically just a map that doesn't have values, this allows for a list-like collection however you cannot access the values using an index and cannot have duplicate values in the set. Sets have the benefit that they are faster to search than lists, an example of this will be shown in the section.

Unlike Maps and Lists, Sets do not have a literal form and so you will need to use the `Set` class to create a set, we do this by using the `of` method that can take an arbitrary amount of parameters:
```kotlin
// Empty set
Set.of();

Set.of(1, 2, 3); // -> <1, 2, 3>
```

As previously mentioned sets have the benefit of a fast searching algorithm, here is an example:
```kotlin
validNames = Set.of("Foo", "Bar", "Baz");

name = "Some Example Name";

// contains method is much faster than list
if (validNames.contains(name)) {
    print("You are valid");
}
```

## Errors

### Creation

### Throwing 

### Catching

## Imports

## Classes

Classes in Arucas allow for abstraction, they provide a way to encapsulate values into another value, and classes let you define certain behaviour with the value such as interactions with operators and the methods that the value has.

### Syntax

The class syntax is very simple and similar to many other languages, we use the `class` keyword to declare a class definition followed by the name of the class and then a series of class statements which we will cover further on in this section.
```kotlin
// Classes follow Pascal Naming
class ExampleClass {
}
```

### Constructors

Constructors are essentially functions that are run when the class is instantiated. These are often used to set fields and often take parameters. By default if no constructor is declared then a synthetic constructor is created: you will be able to construct the class without any parameters. However if any constructors are defined this synthetic constructor will not be available.

To define a constructor in a class we use the class name followed by brackets which can contain parameters and then followed by a statement which is run when the class is instantiated.
```kotlin
class ExampleClass {
    // Constructor
    ExampleClass() {
    }
}
```

### Fields

### Methods

### Operators

### Static Methods and Fields

## Enums

### Syntax

### Constructors

## Threads

### Purpose

### Creation

### Stopping Threads

### Thread Safety

## Java Integration

If there are specific things you want to achieve that aren't possible with the base language you may want to look into calling Java code from within your script. This is possibly by using the `util.Internal` library and importing the `Java` class.
```kotlin
import Java from util.Internal;
``` 

### Java Types

There are many static methods for the Java class and these will be key for creating Java typed values. One such method is `valueOf`, this converts any Arucas typed value into a Java one:
```kotlin
import Java from util.Internal;

jString = Java.of(""); // Arucas String type -> Java String type
```

All Java typed values have the Arucas type of `Java` and they all have some basic methods you can use, these allow you to access their methods and fields which we will explore later in this documentation. Another method which is important is the `toArucas` method which tries to convert the Java typed value back into an Arucas typed value.
```kotlin
import Java from util.Internal;

jString = Java.of(""); // Java String type

string = jString.toArucas(); // Back to Arucas String type
``` 

Not every Java type has a conversion and so if you try to convert a Java type that does not have a conversion it will simply just return itself.

### Methods and Fields

`Java` values have a property that allows them to call Java methods, there are different ways this can be done but the advised way is to call the method as usual:
```kotlin
import Java from util.Internal;

jString = Java.of("");
// Java methods return Java typed values too
// The isBlank method is a Java method!
jBoolean = jString.isBlank();

if (jBoolean.toArucas()) {
    print("String was blank");
}
```
You are also able to call methods with parameters the same way you would call an Arucas function, however the types of the values must match the method signiture, the arguments you pass in should generally be Java typed.

Something to note about methods is that they use the Java reflection library internally which makes calling Java methods quite slow. On a small scale this is fine however if you plan on repeatedly call a method you should consider delegating the method. When the method is delegated the Internal library creates a MethodHandle which is significantly faster.
```kotlin
import Java from util.Internal;

jString = Java.of("");
delegate = jString.isBlank;

for (i = 0; i < 100; i++) {
    delegate();
}
```

Accessing fields is also similar to Arucas this can be done by just using the dot operator:
```kotlin
import Java from util.Internal;

array = Java.arrayOf();
// length field of Java array type
array.length;
```

### Constructing Java Objects

Now this is great but what if we want to construct a Java Object? Well we can use `Java.constructClass()`, this method takes in the class name and then any amount of parameters:
```kotlin
import Java from util.Internal;

ArrayList = "java.util.ArrayList";

// From looking at Java code this would invoke the
// constructor with no parameters
jList = Java.constructClass(ArrayList);

// Adding Java Strings into ArrayList
jList.add("One"); 
jList.add("Two");
```

As mentioned before Arucas values can be converted to Java values and you have the ability to construct Java classes but there are still some cases where Java type values cannot be created. These are primitives, arrays, and lambdas. To remedy this the Java class provides static methods to create these types of values:
```kotlin
import Java from util.Internal;

Java.intOf(10); // Creates Java int type
Java.floatOf(9.5); // Creates Java float type
Java.charOf("h"); // Creates Java char type
// ...

Java.arrayOf("wow", 7, false); // Creats Object[] with values, arbitrary arguments
Java.intArray(10); // Creats int[] with size passed in
Java.byteArray(10); // Creates byte[] with size passed in
// ...

// Runnables take no args and returns nothing
Java.runnableOf(fun() {
    print("runnable!");
});
// Consumables take 1 arg and returns nothing
Java.consumerOf(fun(arg) {
    print("consumer!: " + arg);
});
// Suppliers take no args and returns something
Java.supplierOf(fun() {
    print("supplier!");
    return false;
});
// Functions take 1 arg and returns something
Java.functionOf(fun(arg) {
    print("function!: " + arg);
    return true;
});
```

### Static Methods and Fields

Now we know how we can construct Object and call their methods in Java, what about static methods and fields? Well this is done again through the Java class with a static method:
```kotlin
import Java from util.Internal;

Integer = "java.lang.Integer";

// Class name, method name, parameters...
Java.callStaticMethod(Integer, "parseInt", "120");

// Class name, field name
Java.getStaticField(Integer, "MAX_VALUE");

// Class name, field name, new value (must be correct type)
// Obviously this won't work, but it's just an example
Java.setStaticField(Integer, "MAX_VALUE", Java.intOf(100));"
```

#


# Language Syntax

## Literals

Arucas provides 6 object types that you are able to create with literals, these are:

`Number` - An object containing a floating point number, represented by a number

`String` - An object containing an array of characters, represented by any text within two double or single quote marks

`Boolean` - An object containing only one of two possible values, represented by `true` or `false` 

`List` - An object containing a list of other objects, represented by having object seperated with comma's within square brackets

`Map` - An object containing a list of key and value pairs of objects, represented by having a list of pairs of objects separated by colons within curly brackets

`Null` - An object representing nothing, represented by `null`

## Basic Operators:

`=` - This assigns a value to a variable

`+` - This adds two numbers together or concatenates two strings

`-` - This subtracts one number from another

`*` - This multiplies one number from another

`/` - This divides one number by another

`^` - This multiplies one number by itself a number of times

`++` - This increments the value of a number by one

`--` - This decrements the value of a number by one

`.` - This allows you to access members of a value

## Logical Operators:

`&&` - This is the logical AND

`||` - This is the logical OR

`!` - This is the logical NOT

`~` - This is the logical XOR

`==` - This evaluates whether two objects are equal

`>` - This evaluates whether a number is more than another

`<` - This evaluates whether a number is less than another

`>=` - This evaluates whether a number is greater than or equal to another

`<=` - This evaluates whether a number is less than or equal to another

One thing to note for AND and OR is that the left side will always be evaluated first, and if it does not evaluate to `true` in case of AND, or `false` in the case of OR, the right side will not be evalutated.

Another thing to note is that custom classes are able to override some of these operators changing their functionality, more information will be on this in the classes section.

## Bitwise Operators:

`&` - This is the bitwise AND

`|` - This is the bitwise OR

`~` - This is the bitwise XOR

`>>` - Right bitshift

`<<` - Left bitshift

One thing to note is that the bitwise AND and OR also work for Booleans, however they do not short circuit, so in the case of AND if the left side was evaluated to `false` it would still evaluate the left side, and similarly OR will evaluate the right side even if the left was already `true`.

## Comments:

You are able to make comments in your code that the compiler will ignore.

`//` - Used to comment until a line break

`/* */` - Used for multi-line comments

## Keywords:


### `{` and `}` 

- These are used to define scopes, or code blocks
- Scopes can contain multiple lines of code inside then and usually is idented to visually show it's in a different scope. Any variables initialised inside of a scope cannot be accessed outside of that scope, but variables defined outside of the scope can be accessed and assigned inside of that scope, scopes can be used independantly as well as with other statements.

Example:
```kotlin
outside = 9;
{
    // variable only defined inside this scope
    inside = 10;
    // variable defined outside of the scope can be assigned and accessed
    outside = outside - 2;
}
// this would crash as 'inside' doesn't exist outside the scope
outside = inside;
```

### `fun` 

- This is used for defining functions
- Functions can have parameters, however functions outside of classes cannot be overloaded, overloaded functions can not be delegated. Functions are called by having their name followed by two brackets.

Examples:
```kotlin
fun doSomething() {
    print("something");
}

fun doSomethingElse(foo) {
    print(foo);
}

doSomething();
```

A thing to note is that the language is not fussy with how you format you code, in terms of new lines and spaces. So formatting like this is considered valid:

```kotlin
fun doSomething()
{
    if (true) print("");
}
```

### `return` 

- This is for escaping out of a function or file
- You are able to return a value, however this is not required. If there is no return statement in a function it will automatically return `null`, you can also return a value out of a file.

Examples:
```kotlin
fun doSomething() {
    return "something";
}

return doSomething();
```

### `if`, `else if`, and `else` 

- These are for evaluating boolean expressions
- You cannot have `else if`s and `else` without an `if`, if one of these has an expression evaluates to true the code inside of their code block will be executed, and the rest will be ignored.

Examples:
```kotlin
if (false) { 
    print("foo"); 
} 
else if (false) { 
    print("bar"); 
} 
else { 
    print("baz"); 
}
```

### `switch`, `case`, and `default` 

- These are for matching values
- Switch statements can compare a value to both literals and other expressions, similar to an if statement, you cannot have two of the same literal in the cases and the switch statement is evaluated from first case down to last case with literals being the first thing that is checked in each case. If the value does not match any cases it will run the default branch. You cannot have more than one default branch.

Example:
```kotlin
fun getNum() {
    return 1;
}

number = 1;
switch (number) {
    // Even though getNum comes before 1 the value
    // will check against literals first, so in this
    // case getNum will ne
    case getNum(), 1, 2, 3 -> {
        print("low");
    }
    case 4, 5 -> { }
    case 6 -> {
        print("highest");
    }
    default -> {
        print("unkown");
    }
}
```

### `while` 

- This is for creating a simple loop
- `while` evaluates a boolean expression similar to `if`, and if it evaluates to `true` then it will execute the code inside, and then go back to the top and repeat the process until it evaluates to `false`.

Examples:
```kotlin
while (true) {
    print("This is an infinite loop");
}

i = 0;
while (i < 10) {
    print(i);
    i++;
}
```

### `for` 

- This is for creating an iteration loop
- `for` takes in three expressions, the first will only be executed once at the start, the second is similar to the condition in a while loop, and the third gets executed every time the `for` loop completes.

Example:
```kotlin
/* 
 * This example is exactly the same as the previous 
 * while loop example, just more consise
 */
for (i = 0; i < 10; i++) {
    print(i);
}

list = [4, 5, 2, 7];
for (i = 0; i < len(list); i++) {
    value = list.get(i);
    print(value);
}
```

### `foreach` 

- This is for iterating over the values in a lists
- `foreach` this is similar to the Java enhanced for loop, you have an identifier which will hold your value and the desired list that you want to iterate over.

Example:
```kotlin
// this does the same as the previous for loop example, just more consise
list = [4, 5, 2, 7];
for (value : list) {
    print(value);
}
```

### `continue` 

- This allows you to return to the top of a loop

Example:
```kotlin
for (i = 0; i < 10; i++) {
    if (i == 3) {
        continue;
    }
    print(i);
}
```

### `break` 

- This allows you to escape a loop or case statement

Examples:
```kotlin
for (i = 0; i < 10; i++) {
    if (i == 3) {
        break;
    }
    print(i);
}

number = 18;
switch ("foo") {
    case "bar", "baz" -> {
        print("b");
    } 
    case "foo", "faz" -> {
        if (number >= 18) {
            break;
        }
        print("f");
    }
}
```

### `throw`

- This keyword is used to throw an error
- You can only throw `Error`s, you can construct an `Error` by using the `Error` class, if these go uncaught they will crash the program.

Example:
```kotlin
throw new Error("Something went wrong!", 540);
```

### `try` and `catch` 

- These are used to handle exceptions
- `catch` can only catch `Error`s, the caught value will be of type `Error` which encapsulates the error message and possibly a value. If errors go uncaught they will crash the program.

Example:
```kotlin
try {
    throw null;
}
catch (error) {
    print(error);
}
```

### `class` 

- This is used to define a `class`
- Classes allow for encapsulation, wrapping other objects (values) into a single object, this class defines that single object and what that object is able to do. 
- If a class has no constructors you will be able to construct that class with no parameters. Classes also allow you to define methods, or class functions.  You can overload constructors, and methods in a class by differing the number of parameters.
- You can initialise the class members in the constructor, or initialise them when you define them. If you do not define them they will default to being `null`.

Example:
```kotlin
class Example {
    var other1;
    var other2 = 10;

    Example() { }

    Example(param) {
        this.other1 = param;
    }
}
```

### `var` 

- This is used for declaring variables inside classes
- The var keyword can be used for `static` an non-`static` variables.
- These variables you define can be access using the `.` operator

Examples:
```kotlin
class Example {
    var pi = 3.14;
    var name = "sensei";
}
```

### `.` 

- This is used to access members of an object
- This can be used on `class` names for `static` members or on an object for the object members.

Example:
```kotlin
class Example {
    var number = 10;
    
    // If there is no constructor
    // Arucas generates a synthetic one

    fun printNumber() {
        print(this.number);
    }
}

// We are able to construct it with no parameters
example = new Example();

// these two do the same thing
print(example.number);
example.printNumber();
```

### `this` 

- This is used for refering to itself inside a class
- `this` is passed in internally, and you will have access to it inside a class constructor, method, or operator method, `this` allows you to refer to all of the members inside of your class, you can assign, access, or call them.

Example:
```kotlin
class Example {
    var number = 10;

    fun setNumber(newNumber) {
        this.number = newNumber;
    }

    fun resetNumber() {
        this.number = 10;
    }
}

e = new Example();
// When we call a method on a value
// it internally passes itself as a parameter
// so you could think of it as resetNumber(e)
// where inside the resetNumber function
// e is referenced with the this keyword
e.resetNumber();
``` 

### `new` 

- This is used to construct a new object
- This is used for custom classes, as the built in objects cannot be constructed, as they have literals. This will return a new instance of that object.

Examples:
```kotlin
class Example {
    var number = 10;
    
    // We have multiple constructors
    Example() { }
    
    Example(number) {
        this.number = number;
    }
}

// Construction
defaultExample = new Example();
myExample = new Example(20);
```

### `operator` 

- This allows you to override operator methods for an object
- An important thing to note about this is that it will be the left side's operator method that will get used, for example `a + b` would result in `a`'s plus operator getting called not `b`'s. Whereas `b + a` would result in `b`'s plus operator getting called not `a`'s
- The operators that you can override are: `+`, `-`, `*`, `/`, `^`, `<`, `<=`, `>`, `>=`, `==`, and `!`

Examples:
```kotlin
class Example {
    var number = 10;

    operator + (other) {
        return this.number + other;
    }

    operator ! () {
        return this.number * -1;
    }

    operator == (other) {
        return this.number == other;
    }
}

// Constructing the class using the new keyword
example = new Example();

plusExample = example + 10; // this would return 20
notExample = !example; // this would return -10
equalsExample = example == 10; // this would return true

// this would throw an error, because 10's operator is being called not example's
errorExample = 10 + example; 
``` 

### `static` 

- This lets you define `static` members, methods, and initialisers in a class
- `static` members and methods can be access without an instance of the class. And a `static` initialiser will run when the class is evaluated, `static` methods can be overloaded. `static` members are access by typing the `class` name followed by a `.` and then the member name.

Example:
```kotlin
class Example {
    static var number = 10;

    static {
        print("Example class was loaded");
    }

    static fun print() {
        print(Example.number);
    }

    static fun print(prefix) {
        print("%s %s".formatted(prefix, Example.number)); 
    }
}
```

`enum`

- Enums are somwhat similar to classes, but they cannot be constructed and instead have static-like variables of the type that cannot be modified. Enums are great if you want constants that can also encapsulate other values.

Example:
```kotlin
// Every enum by default has 2 static functions
// Direction.values() and Direction.fromString(str)
// they get all the values of the enum and convert
// a string to a enum by name respectively. 
enum Direction {
    NORTH("North"),
    // You can have brackets if you want
    SOUTH(),
    // Or not
    EAST,
    WEST("Wow");

    Direction() {
        // All enum values by default have
        // 2 methods, getName and ordinal
        // getting the name of the enum and the
        // index of the enum respectively
        this.prettyName = this.getName();
    }
    
    /* Constructors are used when initialising
     * the enum values, they can take any values
     */
    Direction(prettyName) {
        this.prettyName = prettyName;
    }

    /* Not a good way to do this, should have
     * opposite as a member variable but this is
     * just an example.
     */
    fun getOpposite() {
        switch(this) {
            case Direction.NORTH -> return Direction.SOUTH;
            case Direction.SOUTH -> return Direction.NORTH;
            case Direction.EAST -> return Direction.WEST;
            case Direction.WEST -> return Direction.EAST;
        }
    }
}

// Direction.NORTH = "Random Value!"; <-- This would crash
// direction = new Direction(); <-- This would also crash
print(Direction.NORTH.getOpposite());
```

`import` and `from`

- These keywords allow you to import classes from other files.
- Currently cyclical imports are not supported but usually you don't need two files importing eachother.

```kotlin
// Imports all classes from util.Internal file
import * from util.Internal;
// Only imports Collector class from util.Collection
import Collector from util.Collection;
// If you want to import your own file you must have it
// inside your libraries folder, in Vanilla arucas this
// is Users/user/.arucas/libs/

// Since we are importing the Collector class we can not use it
collector = Collector.of(1, 2, 3, 4, 5, 6);
list = collector.filter(fun(value) { return value > 4; }).toList();
print(list);
```

#


## BuiltInExtension  
  
### `getArucasVersion()`  
- Description: This is used to get the version of Arucas that is currently running  
- Returns - String: the version of Arucas that is currently running  
- Example:  
```kt  
getArucasVersion();  
```  
  
### `getMilliTime()`  
- Description: This is used to get the current time in milliseconds  
- Returns - Number: the current time in milliseconds  
- Example:  
```kt  
getMilliTime();  
```  
  
### `debug(bool)`  
- Description: This is used to enable or disable debug mode  
- Parameter - Boolean (`bool`): true to enable debug mode, false to disable debug mode  
- Example:  
```kt  
debug(true);  
```  
  
### `runFromString(string)`  
- Description: This is used to evaluate a string as a script  
- Parameter - String (`string`): the string to evaluate  
- Returns - Value: the return value of the script  
- Example:  
```kt  
runFromString('return 1;');  
```  
  
### `getNanoTime()`  
- Description: This is used to get the current time in nanoseconds  
- Returns - Number: the current time in nanoseconds  
- Example:  
```kt  
getNanoTime();  
```  
  
### `getTime()`  
- Description: This is used to get the current time formatted with HH:mm:ss in your local time  
- Returns - String: the current time formatted with HH:mm:ss  
- Example:  
```kt  
getTime();  
```  
  
### `isMain()`  
- Description: This is used to check whether the script is the main script  
- Returns - Boolean: true if the script is the main script, false if it is not  
- Example:  
```kt  
isMain();  
```  
  
### `throwRuntimeError(message)`  
- Deprecated: You should use the `throw` keyword  
- Description: This is used to throw a runtime error  
- Parameter - String (`message`): the message of the error  
- Throws - Error:  
  - `'the error with the message'`  
- Example:  
```kt  
throwRuntimeError('I'm throwing this error');  
```  
  
### `experimental(bool)`  
- Description: This is used to enable or disable experimental mode  
- Parameter - Boolean (`bool`): true to enable experimental mode, false to disable experimental mode  
- Example:  
```kt  
experimental(true);  
```  
  
### `run(path)`  
- Description: This is used to run a .arucas file, you can use on script to run other scripts  
- Parameter - String (`path`): as a file path  
- Returns - Value: any value that the file returns  
- Throws - Error:  
  - `'Failed to execute script...'`  
- Example:  
```kt  
run('/home/user/script.arucas');  
```  
  
### `getUnixTime()`  
- Description: This is used to get the current time in seconds since the Unix epoch  
- Returns - Number: the current time in seconds since the Unix epoch  
- Example:  
```kt  
getUnixTime();  
```  
  
### `sleep(milliseconds)`  
- Description: This pauses your program for a certain amount of milliseconds  
- Parameter - Number (`milliseconds`): milliseconds to sleep  
- Example:  
```kt  
sleep(1000);  
```  
  
### `random(bound)`  
- Description: This is used to generate a random integer between 0 and the bound  
- Parameter - Number (`bound`): the maximum bound (exclusive)  
- Returns - Number: the random integer  
- Example:  
```kt  
random(10);  
```  
  
### `input(prompt)`  
- Description: This is used to take an input from the user  
- Parameter - String (`prompt`): the prompt to show the user  
- Returns - String: the input from the user  
- Example:  
```kt  
input('What is your name?');  
```  
  
### `print(printValue...)`  
- Description: This prints a number of values to the console  
- Parameter - Value (`printValue...`): the value to print  
- Example:  
```kt  
print('Hello World', 'This is a test', 123);  
```  
  
### `print(printValue)`  
- Description: This prints a value to the console  
- Parameter - Value (`printValue`): the value to print  
- Example:  
```kt  
print('Hello World');  
```  
  
### `len(collection)`  
- Description: This is used to get the length of a collection or string  
- Parameter - String (`collection`): the collection or string  
- Throws - Error:  
  - `'Cannot pass ... into len()'`  
- Example:  
```kt  
len("Hello World");  
```  
  
### `stop()`  
- Description: This is used to stop a script  
- Example:  
```kt  
stop();  
```  
  
### `callFunctionWithList(function, list)`  
- Deprecated: You should use Function class `Function.callWithList(fun() {}, [])`  
- Description: This is used to call a function with a list of arguments  
- Parameters:  
  - Function (`function`): the function  
  - List (`list`): the list of arguments  
- Returns - Value: the return value of the function  
- Example:  
```kt  
callFunctionWithList(fun(n1, n2, n3) { }, [1, 2, 3]);  
```  
  
### `suppressDeprecated(bool)`  
- Description: This is used to enable or disable suppressing deprecation warnings  
- Parameter - Boolean (`bool`): true to enable suppressing deprecation warnings, false to disable suppressing deprecation warnings  
- Example:  
```kt  
suppressDeprecated(true);  
```  
  
### `getDate()`  
- Description: This is used to get the current date formatted with dd/MM/yyyy in your local time  
- Returns - String: the current date formatted with dd/MM/yyyy  
- Example:  
```kt  
getDate();  
```  
  
  
## MinecraftExtension  
  
### `getMinecraftClient()`  
- Deprecated: Use 'MinecraftClient.getClient()'  
- Description: This gets the MinecraftClient instance  
- Returns - MinecraftClient: The MinecraftClient instance  
- Example:  
```kt  
getMinecraftClient();  
```  
  
### `hold()`  
- Description: This freezes the current thread and halts execution, same functionality as 'Thread.freeze()'  
- Example:  
```kt  
hold();  
```

#


# Block class  
Block class for Arucas.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<Block>.getBlockProperties()`  
- Description: This gets the properties of the Block  
You can find a list of all block properties  
[here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Block_states)  
- Returns - Map: the properties of the Block, may be empty if there are no properties  
- Example:  
```kt  
block.getBlockProperties();  
```  
  
### `<Block>.hasBlockPosition()`  
- Description: This checks if the Block has a position or not  
- Returns - Boolean: true if the Block has a position  
- Example:  
```kt  
block.hasBlockPosition();  
```  
  
### `<Block>.isSideSolidFullSquare(side)`  
- Description: This checks if the Block is solid on the full square  
- Parameter - String (`side`): the side to check, for example: 'north', 'south', 'east', 'west', 'up', 'down'  
- Returns - Boolean: true if the Block is solid on the full square  
- Example:  
```kt  
block.isSideSolidFullSquare('north');  
```  
  
### `<Block>.getFullId()`  
- Description: This gets the full id of the Block, for example: 'minecraft:stone'  
- Returns - String: the full id of the Block  
- Example:  
```kt  
block.getFullId();  
```  
  
### `<Block>.sideCoversSmallSquare(side)`  
- Description: This checks if the Block covers a small square  
- Parameter - String (`side`): the side to check, for example: 'north', 'south', 'east', 'west', 'up', 'down'  
- Returns - Boolean: true if the Block covers a small square  
- Example:  
```kt  
block.sideCoversSmallSquare('north');  
```  
  
### `<Block>.getId()`  
- Description: This gets the id of the Block, for example: 'stone'  
- Returns - String: the id of the Block  
- Example:  
```kt  
block.getId();  
```  
  
### `<Block>.isSpawnable()`  
- Description: This checks if the Block is spawnable in the case of zombies  
- Returns - Boolean: true if the Block is spawnable in the case of zombies  
- Example:  
```kt  
block.isSpawnable();  
```  
  
### `<Block>.isSpawnable(entity)`  
- Description: This checks if the Block is spawnable in the case of the given entity  
- Parameter - Entity (`entity`): the entity to check  
- Returns - Boolean: true if the Block is spawnable in the case of the given entity  
- Example:  
```kt  
block.isSpawnable(zombie);  
```  
  
### `<Block>.mirrorFrontBack()`  
- Description: This mirrors the Block around the front and back  
- Returns - Block: the mirrored Block  
- Example:  
```kt  
block.mirrorFrontBack();  
```  
  
### `<Block>.mirrorLeftRight()`  
- Description: This mirrors the Block around the left and right  
- Returns - Block: the mirrored Block  
- Example:  
```kt  
block.mirrorLeftRight();  
```  
  
### `<Block>.getPos()`  
- Description: This gets the position of the Block  
- Returns - Pos: the position of the Block, may be null if the Block has no position  
- Example:  
```kt  
block.getPos();  
```  
  
### `<Block>.isSolidBlock()`  
- Description: This checks if the Block is a solid block  
- Returns - Boolean: true if the Block is a solid block  
- Example:  
```kt  
block.isSolidBlock();  
```  
  
### `<Block>.isTransparent()`  
- Description: This checks if the Block is transparent  
- Returns - Boolean: true if the Block is transparent  
- Example:  
```kt  
block.isTransparent();  
```  
  
### `<Block>.isReplaceable()`  
- Description: This checks if the Block is replaceable  
- Returns - Boolean: true if the Block is replaceable  
- Example:  
```kt  
block.isReplaceable();  
```  
  
### `<Block>.getLuminance()`  
- Description: This gets the luminance of the Block  
- Returns - Number: the luminance of the Block  
- Example:  
```kt  
block.getLuminance();  
```  
  
### `<Block>.rotateYCounterClockwise()`  
- Description: This rotates the Block 90 degrees counter-clockwise  
- Returns - Block: the rotated Block  
- Example:  
```kt  
block.rotateYCounterClockwise();  
```  
  
### `<Block>.isFluidSource()`  
- Description: This checks if the Block is a fluid source  
- Returns - Boolean: true if the Block is a fluid source  
- Example:  
```kt  
block.isFluidSource();  
```  
  
### `<Block>.asItemStack()`  
- Description: This gets the ItemStack of the Block, if the block has no item it will return air  
- Returns - ItemStack: the ItemStack of the Block  
- Example:  
```kt  
block.asItemStack();  
```  
  
### `<Block>.getMaterial()`  
- Description: This gets the material of the Block  
- Returns - Material: the material of the Block  
- Example:  
```kt  
block.getMaterial();  
```  
  
### `<Block>.rotateYClockwise()`  
- Description: This rotates the Block 90 degrees clockwise  
- Returns - Block: the rotated Block  
- Example:  
```kt  
block.rotateYClockwise();  
```  
  
### `<Block>.getTranslatedName()`  
- Description: This gets the translated name of the Block, for example  
'stone' would return 'Stone' if your language is in English  
- Returns - String: the translated name of the Block  
- Example:  
```kt  
block.getTranslatedName();  
```  
  
### `<Block>.getX()`  
- Description: This gets the X position of the Block  
- Returns - Number: the X position of the Block, may be null if the Block has no position  
- Example:  
```kt  
block.getX();  
```  
  
### `<Block>.getY()`  
- Description: This gets the Y position of the Block  
- Returns - Number: the Y position of the Block, may be null if the Block has no position  
- Example:  
```kt  
block.getY();  
```  
  
### `<Block>.getZ()`  
- Description: This gets the Z position of the Block  
- Returns - Number: the Z position of the Block, may be null if the Block has no position  
- Example:  
```kt  
block.getZ();  
```  
  
### `<Block>.getBlastResistance()`  
- Description: This gets the blast resistance of the Block  
- Returns - Number: the blast resistance of the Block  
- Example:  
```kt  
block.getBlastResistance();  
```  
  
### `<Block>.getHardness()`  
- Description: This gets the hardness of the Block  
- Returns - Number: the hardness of the Block  
- Example:  
```kt  
block.getHardness();  
```  
  
### `<Block>.isFluid()`  
- Description: This checks if the Block is a fluid  
- Returns - Boolean: true if the Block is a fluid  
- Example:  
```kt  
block.isFluid();  
```  
  
### `<Block>.isBlockEntity()`  
- Description: This checks if the Block is a BlockEntity  
- Returns - Boolean: true if the Block is a BlockEntity  
- Example:  
```kt  
block.isBlockEntity();  
```  
  
## Static Methods  
  
### `Block.of(material)`  
- Description: This creates a Block from a material or string  
- Parameter - MaterialLike (`material`): the material, item stack, block, or string to create the Block from  
- Returns - Block: the Block created from the material or string  
- Example:  
```kt  
Block.of(Material.STONE);  
```  
  
  
# Boolean class  
Boolean class for Arucas.  
  
This class cannot be constructed since Booleans have literals.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
  
  
# BoxShape class  
BoxShape class for Arucas.  
  
This class allows you to create box shapes that can be rendered in the world.  
  
Import with `import BoxShape from Minecraft;`  
  
Fully Documented.  
  
## Members  
  
### `<BoxShape>.pos1`  
- Description: The first position of the shape  
- Type: Pos  
- Assignable: false  
- Example:  
```kt  
shape.pos1;  
```  
### `<BoxShape>.pos2`  
- Description: The second position of the shape  
- Type: Pos  
- Assignable: false  
- Example:  
```kt  
shape.pos2;  
```  
  
## Constructors  
  
### `new BoxShape(pos)`  
- Description: Creates a new box shape, this is used to render boxes  
- Parameter - Pos (`pos`): The position which will be used for the first and second corner of the box  
- Example:  
```kt  
new BoxShape(new Pos(0, 0, 0));  
```  
### `new BoxShape(pos1, pos2)`  
- Description: Creates a new box shape, this is used to render boxes  
- Parameters:  
  - Pos (`pos1`): The position of the first corner of the box  
  - Pos (`pos2`): The position of the second corner of the box  
- Example:  
```kt  
new BoxShape(new Pos(0, 0, 0), new Pos(10, 10, 10));  
```  
### `new BoxShape(x, y, z)`  
- Description: Creates a new box shape, this is used to render boxes  
- Parameters:  
  - Number (`x`): The x position which will be used for the first and second corner of the box  
  - Number (`y`): The y position which will be used for the first and second corner of the box  
  - Number (`z`): The z position which will be used for the first and second corner of the box  
- Example:  
```kt  
new BoxShape(0, 0, 0);  
```  
### `new BoxShape(x1, y1, z1, x2, y2, z2)`  
- Description: Creates a new box shape, this is used to render boxes  
- Parameters:  
  - Number (`x1`): The x position of the first corner of the box  
  - Number (`y1`): The y position of the first corner of the box  
  - Number (`z1`): The z position of the first corner of the box  
  - Number (`x2`): The x position of the second corner of the box  
  - Number (`y2`): The y position of the second corner of the box  
  - Number (`z2`): The z position of the second corner of the box  
- Example:  
```kt  
new BoxShape(0, 0, 0, 10, 10, 10);  
```  
  
## Methods  
  
### `<BoxShape>.setColour(colour)`  
- Description: This sets the colour of the shape, using a single value, this  
function also has a sibling named `setColor()` that has the same functionality  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setColour(0xFF0000);  
```  
  
### `<BoxShape>.setColour(red, green, blue)`  
- Description: This sets the colour of the shape, using three values this function  
also has a sibling named `setColor()` that has the same functionality  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setColour(34, 55, 0);  
```  
  
### `<BoxShape>.setRenderThroughBlocks(boolean)`  
- Description: This sets whether the shape should render through blocks  
- Parameter - Boolean (`boolean`): whether the shape should render through blocks  
- Example:  
```kt  
shape.setRenderThroughBlocks(true);  
```  
  
### `<BoxShape>.setZScale(zScale)`  
- Description: This sets the z scale of the shape  
- Parameter - Number (`zScale`): the z scale of the shape  
- Example:  
```kt  
shape.setZScale(3.5);  
```  
  
### `<BoxShape>.setGreen(green)`  
- Description: This sets the green value of the shape, using a single value  
- Parameter - Number (`green`): the amount of green between 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setGreen(34);  
```  
  
### `<BoxShape>.setOutlineGreen(green)`  
- Description: This sets the outline green value of the shape, using a single value  
- Parameter - Number (`green`): the amount of green between 0 - 255  
- Example:  
```kt  
shape.setOutlineGreen(34);  
```  
  
### `<BoxShape>.setRed(red)`  
- Description: This sets the red value of the shape, using a single value  
- Parameter - Number (`red`): the amount of red between 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setRed(34);  
```  
  
### `<BoxShape>.getYTilt()`  
- Description: This gets the y tilt of the shape  
- Returns - Number: the y tilt  
- Example:  
```kt  
shape.getYTilt();  
```  
  
### `<BoxShape>.getOpacity()`  
- Description: This returns the opacity of the shape  
- Returns - Number: the opacity of the shape  
- Example:  
```kt  
shape.getOpacity();  
```  
  
### `<BoxShape>.setPos1(pos1)`  
- Description: This sets the first position of the shape  
- Parameter - Pos (`pos1`): the first position of the shape  
- Example:  
```kt  
shape.setPos1(new Pos(1, 0, 100));  
```  
  
### `<BoxShape>.centerPositions()`  
- Description: This centers the positions of the shape  
- Example:  
```kt  
shape.centerPositions();  
```  
  
### `<BoxShape>.getRed()`  
- Description: This returns the red value of the shape  
- Returns - Number: the red value of the shape  
- Example:  
```kt  
shape.getRed();  
```  
  
### `<BoxShape>.getRGBList()`  
- Description: This returns the RGB value of the shape as a list  
- Returns - List: the RGB value of the shape as a list in the form [red, green, blue]  
- Example:  
```kt  
r, g, b = shape.getRGBList();  
```  
  
### `<BoxShape>.setBlue(blue)`  
- Description: This sets the blue value of the shape, using a single value  
- Parameter - Number (`blue`): the amount of blue between 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setBlue(34);  
```  
  
### `<BoxShape>.stopRendering()`  
- Description: This stops the shape from rendering  
- Example:  
```kt  
shape.stopRendering();  
```  
  
### `<BoxShape>.setOutlinePixelWidth(width)`  
- Description: This sets the outline pixel width of the shape, using a single value  
- Parameter - Number (`width`): the width of the outline in pixels  
- Example:  
```kt  
shape.setOutlinePixelWidth(5);  
```  
  
### `<BoxShape>.setYScale(yScale)`  
- Description: This sets the y scale of the shape  
- Parameter - Number (`yScale`): the y scale of the shape  
- Example:  
```kt  
shape.setYScale(2.5);  
```  
  
### `<BoxShape>.getYScale()`  
- Description: This gets the y scale of the shape  
- Example:  
```kt  
shape.getYScale();  
```  
  
### `<BoxShape>.getRGBAList()`  
- Description: This returns the RGBA value of the shape as a list  
- Returns - List: the RGBA value of the shape as a list in the form [red, green, blue, opacity]  
- Example:  
```kt  
r, g, b, a = shape.getRGBAList();  
```  
  
### `<BoxShape>.getZTilt()`  
- Description: This gets the z tilt of the shape  
- Returns - Number: the z tilt  
- Example:  
```kt  
shape.getZTilt();  
```  
  
### `<BoxShape>.render()`  
- Description: This sets the shape to be rendered indefinitely, the shape will only stop rendering when the script ends or when you call the stopRendering() method  
- Example:  
```kt  
shape.render();  
```  
  
### `<BoxShape>.setZTilt(zTilt)`  
- Description: This sets the z tilt of the shape  
- Parameter - Number (`zTilt`): the z tilt  
- Example:  
```kt  
shape.setZTilt(100);  
```  
  
### `<BoxShape>.getRGB()`  
- Description: This returns the RGB value of the shape  
- Returns - Number: the RGB value of the shape as a single number in the form 0xRRGGBB  
- Example:  
```kt  
shape.getRGB();  
```  
  
### `<BoxShape>.getZScale()`  
- Description: This gets the z scale of the shape  
- Example:  
```kt  
shape.getZScale();  
```  
  
### `<BoxShape>.setXScale(xScale)`  
- Description: This sets the x scale of the shape  
- Parameter - Number (`xScale`): the x scale of the shape  
- Example:  
```kt  
shape.setXScale(1.5);  
```  
  
### `<BoxShape>.setScale(xScale, yScale, zScale)`  
- Description: This sets the scale of the shape  
- Parameters:  
  - Number (`xScale`): the x scale of the shape  
  - Number (`yScale`): the y scale of the shape  
  - Number (`zScale`): the z scale of the shape  
- Example:  
```kt  
shape.setScale(1.5, 2.5, 3.5);  
```  
  
### `<BoxShape>.setOutlineRed(red)`  
- Description: This sets the outline red value of the shape, using a single value  
- Parameter - Number (`red`): the amount of red between 0 - 255  
- Example:  
```kt  
shape.setOutlineRed(34);  
```  
  
### `<BoxShape>.setYTilt(yTilt)`  
- Description: This sets the y tilt of the shape  
- Parameter - Number (`yTilt`): the y tilt  
- Example:  
```kt  
shape.setYTilt(100);  
```  
  
### `<BoxShape>.shouldRenderThroughBlocks()`  
- Description: This returns whether the shape should render through blocks  
- Returns - Boolean: whether the shape should render through blocks  
- Example:  
```kt  
shape.shouldRenderThroughBlocks();  
```  
  
### `<BoxShape>.getBlue()`  
- Description: This returns the blue value of the shape  
- Returns - Number: the blue value of the shape  
- Example:  
```kt  
shape.getBlue();  
```  
  
### `<BoxShape>.setPos2(pos2)`  
- Description: This sets the second position of the shape  
- Parameter - Pos (`pos2`): the second position of the shape  
- Example:  
```kt  
shape.setPos2(new Pos(100, 0, 200));  
```  
  
### `<BoxShape>.setTilt(xTilt, yTilt, zTilt)`  
- Description: This sets the tilt of the shape  
- Parameters:  
  - Number (`xTilt`): the x tilt  
  - Number (`yTilt`): the y tilt  
  - Number (`zTilt`): the z tilt  
- Example:  
```kt  
shape.setTilt(100, 0, 80);  
```  
  
### `<BoxShape>.setColor(colour)`  
- Description: This sets the colour of the shape, using a single value, this  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setColor(0xFF0000);  
```  
  
### `<BoxShape>.setColor(red, green, blue)`  
- Description: This sets the colour of the shape, using three values this function  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setColor(34, 55, 0);  
```  
  
### `<BoxShape>.setOutlineBlue(blue)`  
- Description: This sets the outline blue value of the shape, using a single value  
- Parameter - Number (`blue`): the amount of blue between 0 - 255  
- Example:  
```kt  
shape.setOutlineBlue(34);  
```  
  
### `<BoxShape>.setOutlineColour(colour)`  
- Description: This sets the width of the shape, using a single value, this function  
also has a sibling named `setOutlineColor()` that has the same functionality  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setOutlineColour(0xFF00FF);  
```  
  
### `<BoxShape>.setOutlineColour(red, green, blue)`  
- Description: This sets the outline colour of the shape, using three values, this function  
also has a sibling named `setOutlineColor()` that has the same functionality  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Example:  
```kt  
shape.setOutlineColour(255, 0, 255);  
```  
  
### `<BoxShape>.getGreen()`  
- Description: This returns the green value of the shape  
- Returns - Number: the green value of the shape  
- Example:  
```kt  
shape.getGreen();  
```  
  
### `<BoxShape>.getXScale()`  
- Description: This gets the x scale of the shape  
- Example:  
```kt  
shape.getXScale();  
```  
  
### `<BoxShape>.setOutlineColor(colour)`  
- Description: This sets the width of the shape, using a single value, this function  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setOutlineColor(0xFF00FF);  
```  
  
### `<BoxShape>.setOutlineColor(red, green, blue)`  
- Description: This sets the outline colour of the shape, using three values, this function  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Example:  
```kt  
shape.setOutlineColor(255, 0, 255);  
```  
  
### `<BoxShape>.setXTilt(xTilt)`  
- Description: This sets the x tilt of the shape  
- Parameter - Number (`xTilt`): the x tilt  
- Example:  
```kt  
shape.setXTilt(100);  
```  
  
### `<BoxShape>.getXTilt()`  
- Description: This gets the x tilt of the shape  
- Returns - Number: the x tilt  
- Example:  
```kt  
shape.getXTilt();  
```  
  
### `<BoxShape>.setOpacity(alpha)`  
- Description: This sets the opacity of the shape, using a single value  
- Parameter - Number (`alpha`): the opacity, where 255 is solid colour and 0 is no colour  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setOpacity(34);  
```  
  
  
  
# Collector class  
Collector class for Arucas.  
  
This class is similar to Java streams, allowing for easy modifications of collections.  
  
Import with `import Collector from util.Collection;`  
  
Fully Documented.  
  
## Methods  
  
### `<Collector>.flatten()`  
- Description: If there are values in the collector that are collections they will be expanded,   
collections inside collections are not flattened, you would have to call this method again  
- Returns - Collector: a new Collector with the expanded values  
- Example:  
```kt  
Collector.of([1, 2, [3, 4]]).flatten();  
```  
  
### `<Collector>.filter(predicate)`  
- Description: This filters the collection using the predicate  
- Parameter - Function (`predicate`): a function that takes a value and returns Boolean, true if it should be kept, false if not  
- Returns - Collector: the filtered collection  
- Throws - Error:  
  - `'Predicate must return Boolean'`  
- Example:  
```kt  
Collector.of([1, 2, 3]).filter(fun(value) {  
 return value < 3;});  
```  
  
### `<Collector>.toSet()`  
- Description: This puts all the values in the collector into a set and returns it  
- Returns - Set: a set with all the values in the collector  
- Example:  
```kt  
Collector.of([1, 2, 3]).toSet();  
```  
  
### `<Collector>.forEach(function)`  
- Description: This iterates over all the values in the Collector and calls the passed in function with each value  
- Parameter - Function (`function`): a function that takes a value and returns nothing  
- Returns - Collector: the Collector  
- Example:  
```kt  
Collector.of([1, 2, 3]).forEach(fun(value) {  
 print(value);});  
```  
  
### `<Collector>.noneMatch(predicate)`  
- Description: This checks if none of the values in the collection match the predicate  
- Parameter - Function (`predicate`): a function that takes a value and returns Boolean, true if it matches, false if not  
- Returns - Boolean: true if none of the values match the predicate, false if not  
- Throws - Error:  
  - `'Predicate must return Boolean'`  
- Example:  
```kt  
Collector.of([1, 2, 3]).noneMatch(fun(value) {  
 return value < 5;});  
```  
  
### `<Collector>.toList()`  
- Description: This puts all the values in the collector into a list and returns it  
- Returns - List: a list with all the values in the collector  
- Example:  
```kt  
Collector.of([1, 2, 3]).toList();  
```  
  
### `<Collector>.map(mapper)`  
- Description: This maps the values in Collector to a new value  
- Parameter - Function (`mapper`): a function that takes a value and returns a new value  
- Returns - Collector: a new Collector with the mapped values  
- Example:  
```kt  
Collector.of([1, 2, 3]).map(fun(value) {  
 return value * 2;});  
```  
  
### `<Collector>.allMatch(predicate)`  
- Description: This checks if all the values in the collection match the predicate  
- Parameter - Function (`predicate`): a function that takes a value and returns Boolean, true if it matches, false if not  
- Returns - Boolean: true if all the values match the predicate, false if not  
- Throws - Error:  
  - `'Predicate must return Boolean'`  
- Example:  
```kt  
Collector.of([1, 2, 3]).anyMatch(fun(value) {  
 return value < 5;});  
```  
  
### `<Collector>.anyMatch(predicate)`  
- Description: This checks if any of the values in the collection match the predicate  
- Parameter - Function (`predicate`): a function that takes a value and returns Boolean, true if it matches, false if not  
- Returns - Boolean: true if any of the values match the predicate, false if not  
- Throws - Error:  
  - `'Predicate must return Boolean'`  
- Example:  
```kt  
Collector.of([1, 2, 3]).anyMatch(fun(value) {  
 return value < 3;});  
```  
  
## Static Methods  
  
### `Collector.of(value...)`  
- Description: This creates a collector for a collection  
- Parameter - Value (`value...`): the values you want to evaluate  
- Returns - Collector: the collector  
- Example:  
```kt  
Collector.of(1, 2, '3');  
```  
  
### `Collector.of(collection)`  
- Description: This creates a collector for a collection  
- Parameter - Collection (`collection`): the collection of values you want to evaluate  
- Returns - Collector: the collector  
- Throws - Error:  
  - `'... is not a collection'`  
- Example:  
```kt  
Collector.of([1, 2, 3]);  
```  
  
### `Collector.isCollection(value)`  
- Description: This checks if the value is a collection  
- Parameter - Value (`value`): the value you want to check  
- Returns - Boolean: true if the value is a collection  
- Example:  
```kt  
Collector.isCollection([1, 2, 3]);  
```  
  
  
# CommandBuilder class  
CommandBuilder class for Arucas.  
  
This class allows you to build commands for Minecraft.  
  
Import with `import CommandBuilder from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<CommandBuilder>.executes(function)`  
- Description: This sets the function to be executed when the command is executed,  
this should have the correct amount of parameters for the command  
- Parameter - CommandBuilder (`function`): the function to execute  
- Returns - CommandBuilder: the parent command builder  
- Example:  
```kt  
commandBuilder.executes(fun() { });  
```  
  
### `<CommandBuilder>.then(childBuilder)`  
- Description: This adds a child CommandBuilder to your command builder  
- Parameter - CommandBuilder (`childBuilder`): the child command builder to add  
- Returns - CommandBuilder: the parent command builder  
- Example:  
```kt  
commandBuilder.then(CommandBuilder.literal('subcommand'));  
```  
  
## Static Methods  
  
### `CommandBuilder.fromMap(argumentMap)`  
- Description: Creates an argument builder from a map.  
The map must contain a 'name' key as a String that is the name of the command,  
the map then can contain 'subcommands' as a map which contains the subcommands,  
the key of the subcommands is the name of the subcommand, and the value is a map,  
if the name is encased in '<' and '>' it will be treated as an argument, otherwise it will be treated as a literal.  
You can chain arguments by leaving a space in the name like: 'literal <arg>'.  
If the key has no name and is just an empty string the value will be used as the function  
which will be executed when the command is executed, the function should have the appropriate  
number of parameters, the number of parameters is determined by the number of arguments.  
Argument types are defined in the main map under the key 'arguments' with the value of a map  
the keys of this map should be the names of your arguments used in your subcommands,  
this should be a map and must have the key 'type' which should be a string that is the type of the argument.  
Optionally if the type is of 'integer' or 'double' you can also have the key 'min' and 'max' with numbers as the value,  
and if the type is of 'enum' you must have the key 'enum' with the enum class type as the value: 'enum': MyEnum.type.  
You can also optionally have 'suggests' which has the value of a list of strings that are suggestions for the argument.  
You can also optionally have 'suggester' which has the value of a function that will be called to get suggestions for the argument,  
this function should have arbitrary number of parameters which will be the arguments that the user has entered so far.  
The possible argument types are: 'PlayerName', 'Word', 'GreedyString', 'Double', 'Integer', 'Boolean', 'Enum',  
'ItemStack', 'Particle', 'RecipeId', 'EntityId', 'EnchantmentId'  
- Parameter - Map (`argumentMap`): the map of arguments  
- Returns - CommandBuilder: the argument builder  
- Example:  
```kt  
effectCommandMap = {  
 "name" : "effect", "subcommands" : { "give" : { "<targets> <effect>" : { "" : fun(target, effect) { // do something }, "<seconds>" : { "" : fun(target, effect, second) { // do something }, "<amplifier>" : { "" : fun(target, effect, second, amplifier) { // do something }, "<hideParticle>" : { "" : fun(target, effect, second, amplifier, hideParticle) { // do something } } } } } }, "clear" : { "" : fun() { // do something }, "<targets>" : { "" : fun(target) { // do something }, "<effect>" : { "" : fun(target, effect) { // do something } } } } }, "arguments" : { "targets" : { "type" : "Entity" }, "effect" : { "type" : "Effect", "suggests" : ["effect1", "effect2"] }, "seconds" : { "type" : "Integer", "min" : 0, "max" : 1000000 }, "amplifier" : { "type" : "Integer", "min" : 0, "max" : 255 }, "hideParticle" : { "type" : "Boolean" } }};  
effectCommand = CommandBuilder.fromMap(effectCommandMap);  
```  
  
### `CommandBuilder.argument(argumentName, argumentType)`  
- Description: Creates an argument builder with a specific argument type, and a name  
to see all the different types refer to CommandBuilder.fromMap(...)  
- Parameters:  
  - String (`argumentName`): the name of the argument  
  - String (`argumentType`): the type of the argument  
- Returns - CommandBuilder: the argument builder  
- Example:  
```kt  
CommandBuilder.argument('test', 'entityid');  
```  
  
### `CommandBuilder.argument(argumentName, argumentType, suggestions)`  
- Description: Creates an argument builder with a specific argument type, a name, and a default value  
to see all the different types refer to CommandBuilder.fromMap(...)  
- Parameters:  
  - String (`argumentName`): the name of the argument  
  - String (`argumentType`): the type of the argument  
  - List (`suggestions`): a list of strings for the suggestions for the argument  
- Returns - CommandBuilder: the argument builder  
- Example:  
```kt  
CommandBuilder.argument('test', 'word', ['wow', 'suggestion']);  
```  
  
### `CommandBuilder.literal(argument)`  
- Description: Creates a literal argument with just a string  
- Parameter - String (`argument`): the literal argument  
- Returns - CommandBuilder: the argument builder  
- Example:  
```kt  
CommandBuilder.literal('test');  
```  
  
  
# Config class  
Config class for Arucas.  
  
This class allows you to create configs for your scripts  
  
Import with `import Config from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<Config>.resetToDefault()`  
- Description: Resets the config to the default value  
- Example:  
```kt  
config.resetToDefault();  
```  
  
### `<Config>.getValue()`  
- Description: Gets the value of the config  
- Returns - Value: The value of the config  
- Example:  
```kt  
config.getValue();  
```  
  
### `<Config>.toJson()`  
- Description: Converts the config into a json value, this will not keep the listeners  
- Returns - Json: The config as a json value  
- Example:  
```kt  
config.toJson();  
```  
  
### `<Config>.getName()`  
- Description: Gets the name of the config  
- Returns - String: The name of the config  
- Example:  
```kt  
config.getName();  
```  
  
### `<Config>.getType()`  
- Description: Gets the type of the config  
- Returns - String: The type of the config  
- Example:  
```kt  
config.getType();  
```  
  
### `<Config>.setValue(value)`  
- Description: Sets the value of the config, if the value is invalid it will not be changed  
- Parameter - Value (`value`): The new value of the config  
- Example:  
```kt  
config.setValue(10);  
```  
  
### `<Config>.getDescription()`  
- Description: Gets the description of the config  
- Returns - String: The description of the config  
- Example:  
```kt  
config.getDescription();  
```  
  
### `<Config>.addListener(listener)`  
- Description: Adds a listener to the config, the listener will be called when the config is changed  
The listener must have one parameter, this is the rule that was changed  
- Parameter - Function (`listener`): The listener to add  
- Example:  
```kt  
config.addListener(function(newValue) {  
 print(newValue);});  
```  
  
### `<Config>.getDefaultValue()`  
- Description: Gets the default value of the config  
- Returns - Value: The default value of the config  
- Example:  
```kt  
config.getDefaultValue();  
```  
  
### `<Config>.getOptionalInfo()`  
- Description: Gets the optional info of the config  
- Returns - String: The optional info of the config  
- Example:  
```kt  
config.getOptionalInfo();  
```  
  
## Static Methods  
  
### `Config.fromMap(map)`  
- Description: Creates a config from a map  
The map must contain the following keys:  
'type' which is the type of the config which can be 'boolean', 'cycle', 'double', 'double_slider', 'integer', 'integer_slider', 'list', or 'string',  
'name' which is the name of the config  
And can optionally contain the following keys:  
'description' which is a description of the config,  
'optional_info' which is an optional info for the config,  
'default_value' which is the default value of the config,  
'value' which is the current value of the config,   
'listener' which is a function that will be called when the config changes, this must have 1 parameter which is the rule that was changed,  
'max_length' which is the max length for the input of the config, this must be an integer > 0, default is 32  
And 'cycle' types must contain the following keys:  
'cycle_values' which is a list of values that the config can cycle through.  
And slider types must contain the following keys:  
'min' which is the minimum value of the slider,  
'max' which is the maximum value of the slider  
- Parameter - Map (`map`): The map to create the config from  
- Returns - Config: The config created from the map  
- Throws - Error:  
  - `'Config map must contain a type that is a string'`  
  - `'Config map must contain a name that is a string'`  
  - `''cycle' type must have 'cycle_values' as a list'`  
  - `'... type must have 'min' as a number'`  
  - `'... type must have 'max' as a number'`  
  - `'Invalid config type ...'`  
- Example:  
```kt  
configMap = {  
 "type": "string", "name": "My Config", "description": "This is my config", "optional_info": "This is an optional info", "default_value": "foo", "value": "bar", "listener": fun(newValue) { }, "max_length": 64};  
config = Config.fromMap(configMap);  
```  
  
### `Config.fromListOfMap(list)`  
- Description: Creates a config from a list of config maps  
- Parameter - List (`list`): The list of config maps  
- Returns - List: A list of configs created from the list of config maps  
- Example:  
```kt  
configs = [  
 { "type": "boolean", "name": "My Config", "description": "This is my config" }, { "type": "cycle", "name": "My Cycle Config", "description": "This is my cycle config", "cycle_values": ["one", "two", "three"], "default_value": "two" }];  
configs = Config.fromListOfMap(configs);  
```  
  
  
# ConfigHandler class  
ConfigHandler class for Arucas.  
  
This class allows you to easily read and write config files.  
  
Import with `import ConfigHandler from Minecraft;`  
  
Fully Documented.  
  
## Constructors  
  
### `new ConfigHandler(name)`  
- Description: Creates a new ConfigHandler, this is used to read and save configs  
- Parameter - String (`name`): The name of the config, this will also be the name of the config file  
- Example:  
```kt  
new ConfigHandler('MyConfig');  
```  
### `new ConfigHandler(name, read)`  
- Description: Creates a new ConfigHandler, this is used to read and save configs  
- Parameters:  
  - String (`name`): The name of the config, this will also be the name of the config file  
  - Boolean (`read`): Whether or not to read the config on creation  
- Example:  
```kt  
new ConfigHandler('MyConfig', false);  
```  
  
## Methods  
  
### `<ConfigHandler>.createScreen(title)`  
- Description: Creates a new config screen containing all of the configs in the handler, in alphabetical order  
- Parameter - Text (`title`): The title of the screen  
- Returns - Screen: The new config screen  
- Example:  
```kt  
configHandler.createScreen();  
```  
  
### `<ConfigHandler>.createScreen(title, alphabetical)`  
- Description: Creates a new config screen containing all of the configs in the handler  
- Parameters:  
  - Text (`title`): The title of the screen  
  - Boolean (`alphabetical`): Whether or not to sort the configs alphabetically  
- Returns - Screen: The new config screen  
- Example:  
```kt  
configHandler.createScreen();  
```  
  
### `<ConfigHandler>.read()`  
- Description: Reads the all the configs from the file  
If configs are already in the handler, only the values  
will be overwritten  
- Example:  
```kt  
configHandler.read();  
```  
  
### `<ConfigHandler>.getName()`  
- Description: Gets the name of the config  
- Returns - String: The name of the config  
- Example:  
```kt  
configHandler.getName();  
```  
  
### `<ConfigHandler>.resetAllToDefault()`  
- Description: Resets all configs to their default values  
- Example:  
```kt  
configHandler.resetAllToDefault();  
```  
  
### `<ConfigHandler>.setSavePath(savePath)`  
- Description: Sets the path to save the configs to, this shouldn't include the file name  
- Parameter - File (`savePath`): The path to save the configs to  
- Example:  
```kt  
configHandler.setSavePath(new File('/home/user/scripts/'));  
```  
  
### `<ConfigHandler>.willSaveOnClose()`  
- Description: Gets whether or not the configs will be saved when the script ends  
- Returns - Boolean: Whether or not the configs will be saved when the script ends  
- Example:  
```kt  
configHandler.willSaveOnClose();  
```  
  
### `<ConfigHandler>.addConfig(config)`  
- Description: Adds a config to the handler  
- Parameter - Config (`config`): The config to add  
- Example:  
```kt  
config = Config.fromMap({  
 "type": "boolean", "name": "My Config", "description": "This is my config"});  
configHandler.addConfig(config);  
```  
  
### `<ConfigHandler>.save()`  
- Description: Saves the configs to the file  
- Example:  
```kt  
configHandler.save();  
```  
  
### `<ConfigHandler>.setSaveOnClose(saveOnClose)`  
- Description: Sets whether or not the configs should be saved when the script ends, by default this is true  
- Parameter - Boolean (`saveOnClose`): Whether or not the configs should be saved when the script ends  
- Example:  
```kt  
configHandler.setSaveOnClose(false);  
```  
  
### `<ConfigHandler>.removeConfig(name)`  
- Description: Removes a config from the handler  
- Parameter - String (`name`): The name of the config to remove  
- Example:  
```kt  
configHandler.removeConfig('My Config');  
```  
  
### `<ConfigHandler>.getAllConfigs()`  
- Description: Gets all the configs in the handler  
- Returns - List: All the configs in the handler  
- Example:  
```kt  
configHandler.getAllConfigs();  
```  
  
### `<ConfigHandler>.addConfigs(configs)`  
- Description: Adds multiple configs to the handler  
- Parameter - List (`configs`): The configs to add  
- Example:  
```kt  
config = Config.fromMap({  
 "type": "boolean", "name": "My Config", "description": "This is my config"});  
configHandler.addConfigs([config]);  
```  
  
### `<ConfigHandler>.getConfig(name)`  
- Description: Gets a config from the handler  
- Parameter - String (`name`): The name of the config  
- Returns - Config: The config  
- Example:  
```kt  
configHandler.getConfig('MyConfig');  
```  
  
  
  
# DiscordAttachment class  
DiscordAttachment class for Arucas.  
  
This class lets you download and manipulate discord attachments.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<DiscordAttachment>.getUrl()`  
- Description: This allows you to get the url of the attachment  
- Returns - String: the url of the attachment  
- Example:  
```kt  
attachment.getUrl()  
```  
  
### `<DiscordAttachment>.getSize()`  
- Description: This allows you to get the size of the attachment  
- Returns - Number: the size of the attachment in bytes  
- Example:  
```kt  
attachment.getSize()  
```  
  
### `<DiscordAttachment>.isImage()`  
- Description: This allows you to check if the attachment is an image  
- Returns - Boolean: true if the attachment is an image, false otherwise  
- Example:  
```kt  
attachment.isImage()  
```  
  
### `<DiscordAttachment>.saveToFile(file)`  
- Description: This allows you to save an attachment to a file  
- Parameter - File (`file`): the file you want to save the attachment to  
- Example:  
```kt  
attachment.saveToFile(new File('/home/user/Attachment.jpeg'))  
```  
  
### `<DiscordAttachment>.getFileExtension()`  
- Description: This allows you to get the file extension of the attachment  
- Returns - String: the file extension of the attachment  
- Example:  
```kt  
attachment.getFileExtension()  
```  
  
### `<DiscordAttachment>.isVideo()`  
- Description: This allows you to check if the attachment is a video  
- Returns - Boolean: true if the attachment is a video, false otherwise  
- Example:  
```kt  
attachment.isVideo()  
```  
  
### `<DiscordAttachment>.getFileName()`  
- Description: This allows you to get the file name of the attachment  
- Returns - String: the file name of the attachment  
- Example:  
```kt  
attachment.getFileName()  
```  
  
  
  
# DiscordBot class  
DiscordBot class for Arucas.  
  
This class lets you create a Discord bot and interact with it.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Constructors  
  
### `new DiscordBot(token)`  
- Description: This creates a new DiscordBot instance  
- Parameter - String (`token`): The token of the bot  
- Example:  
```kt  
new DiscordBot('token')  
```  
  
## Methods  
  
### `<DiscordBot>.removeCommand(commandName)`  
- Description: This removes a slash command from the bot  
- Parameter - String (`commandName`): the name of the command  
- Example:  
```kt  
bot.removeCommand('command')  
```  
  
### `<DiscordBot>.getServer(serverId)`  
- Description: This gets a server by its id  
- Parameter - String (`serverId`): the id of the server  
- Returns - DiscordServer: the server  
- Throws - Error:  
  - `'Server with id ... couldn't be found'`  
- Example:  
```kt  
bot.getServer('12345678901234567890123456789012')  
```  
  
### `<DiscordBot>.getActivity()`  
- Description: This gets the activity of the bot  
- Returns - String: The activity of the bot, null if no activity  
- Example:  
```kt  
bot.getActivity()  
```  
  
### `<DiscordBot>.stop()`  
- Description: This stops the bot  
- Example:  
```kt  
bot.stop()  
```  
  
### `<DiscordBot>.getChannel(channelId)`  
- Description: This gets a channel by its id  
- Parameter - String (`channelId`): the id of the channel  
- Returns - DiscordChannel: the channel  
- Throws - Error:  
  - `'Channel with id ... couldn't be found'`  
- Example:  
```kt  
bot.getChannel('12345678901234567890123456789012')  
```  
  
### `<DiscordBot>.addCommand(commandMap)`  
- Description: This adds a slash command to the bot  
Each command must have a name and description, it can have a command, define the next subcommand with 'next'  
and subcommands must have the argument type, and can have whether it is required or not  
types: 'string', 'integer', 'number', 'boolean', 'user', 'channel', and 'attachment'  
- Parameter - Map (`commandMap`): the command map  
- Throws - Error:  
  - `'Command must have name and a description'`  
  - `'Slash command went too deep'`  
  - `'Command must include option type'`  
  - `'Invalid option'`  
- Example:  
```kt  
bot.addCommand({  
 "name": "command", "description": "Does something", "command": fun(event) { // passes in the event // do stuff } "next: { "name": "subcommand", "description": "Does something else", "required": true, "type": "String", "command": fun(event, string) { // passes in the event and the string argument // do stuff } }});  
```  
  
### `<DiscordBot>.getStatus()`  
- Description: This gets the status of the bot  
- Returns - String: The status of the bot  
- Example:  
```kt  
bot.getStatus()  
```  
  
### `<DiscordBot>.registerEvent(eventName, function)`  
- Description: This registers a function to be called when an event is triggered  
- Parameters:  
  - String (`eventName`): the name of the event  
  - Function (`function`): the function to be called  
- Example:  
```kt  
bot.registerEvent('MessageReceivedEvent', function(event) { })  
```  
  
### `<DiscordBot>.getUserId()`  
- Description: This gets the user id of the bot  
- Returns - String: The user id of the bot  
- Example:  
```kt  
bot.getUserId()  
```  
  
### `<DiscordBot>.setStatus(status)`  
- Description: This sets the status of the bot  
- Parameter - String (`status`): The status you want the bot to have  
- Throws - Error:  
  - `'... is an invalid status'`  
- Example:  
```kt  
bot.setStatus('ONLINE')  
```  
  
### `<DiscordBot>.setActivity(activity, message)`  
- Description: This sets the activity of the bot  
- Parameters:  
  - String (`activity`): The activity you want the bot to have  
  - String (`message`): The message you want to display  
- Throws - Error:  
  - `'... is an invalid activity'`  
- Example:  
```kt  
bot.setActivity('PLAYING', 'Arucas')  
```  
  
  
  
# DiscordChannel class  
DiscordChannel class for Arucas.  
  
This class allows you to get and send messages in the channel  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<DiscordChannel>.sendFile(file)`  
- Description: This sends a file to this channel  
- Parameter - File (`file`): the file you want to send  
- Returns - DiscordMessage: the message that was sent  
- Example:  
```kt  
channel.sendFile(new File('a/b/totally_real_file.txt'));  
```  
  
### `<DiscordChannel>.getMessageFromId(messageId)`  
- Description: This gets a message by its id  
- Parameter - String (`messageId`): the id of the message  
- Returns - DiscordMessage: the message  
- Throws - Error:  
  - `'Message with id ... couldn't be found'`  
- Example:  
```kt  
channel.getMessageFromId('12345678901234567890123456789012');  
```  
  
### `<DiscordChannel>.getHistory(amount)`  
- Description: This gets the last X messages  
- Parameter - Number (`amount`): the amount of messages to get  
- Returns - List: the messages  
- Example:  
```kt  
channel.getMessages(10);  
```  
  
### `<DiscordChannel>.sendEmbed(embedMap)`  
- Description: This sends an embed to this channel.  
In the embed map, you can use the following keys:  
'title' as String, ''description' as String or List of String, 'colour'/'color' as Number  
'fields' as Map with keys: ('name' as String, 'value' as String, 'inline' as Boolean)  
and 'image' as String that is an url  
- Parameter - Map (`embedMap`): the embed map  
- Returns - DiscordMessage: the message that was sent  
- Example:  
```kt  
channel.sendEmbed({  
 'title': 'EMBED!', 'description': ['Wow', 'Nice'], 'colour': 0xFFFFFF});  
```  
  
### `<DiscordChannel>.sendMessage(message)`  
- Description: This sends a message to this channel  
- Parameter - String (`message`): the message  
- Returns - DiscordMessage: the message that was sent  
- Example:  
```kt  
channel.sendMessage('Hello World!');  
```  
  
### `<DiscordChannel>.markTyping()`  
- Description: This marks the bot as typing in this channel, it lasts 10 seconds or until the message is sent  
- Example:  
```kt  
channel.markTyping();  
```  
  
  
  
# DiscordEvent class  
DiscordEvent class for Arucas.  
  
This class is an event wrapper that you can use to access event parameters.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<DiscordEvent>.getServer()`  
- Description: This gets the server that is related to the event  
- Returns - DiscordServer: the server  
- Throws - Error:  
  - `'... has no server'`  
- Example:  
```kt  
event.getServer();  
```  
  
### `<DiscordEvent>.getChannel()`  
- Description: This gets the channel that is related to the event  
- Returns - DiscordChannel: the channel  
- Throws - Error:  
  - `'... has no channel'`  
- Example:  
```kt  
event.getChannel();  
```  
  
### `<DiscordEvent>.getEventName()`  
- Description: This gets the name of the event  
- Returns - String: the name of the event  
- Example:  
```kt  
event.getEventName();  
```  
  
### `<DiscordEvent>.getUser()`  
- Description: This gets the user that is related to the event  
- Returns - DiscordUser: the user  
- Throws - Error:  
  - `'... has no user'`  
- Example:  
```kt  
event.getUser();  
```  
  
### `<DiscordEvent>.getMessage()`  
- Description: This gets the message that is related to the event  
- Returns - DiscordMessage: the message  
- Throws - Error:  
  - `'... has no message'`  
- Example:  
```kt  
event.getMessage();  
```  
  
### `<DiscordEvent>.replyWithEmbed(embedMap)`  
- Description: This replies to the event with the given embed map  
In the embed map, you can use the following keys:  
'title' as String, ''description' as String or List of String, 'colour'/'color' as Number  
'fields' as Map with keys: ('name' as String, 'value' as String, 'inline' as Boolean)  
and 'image' as String that is an url  
- Parameter - Map (`embedMap`): the embed map  
- Example:  
```kt  
event.replyWithEmbed({  
 'title': 'EMBED!', 'description': ['Wow', 'Nice'], 'colour': 0xFFFFFF});  
```  
  
### `<DiscordEvent>.replyWithFile(file)`  
- Description: This replies to the event with the given file  
- Parameter - File (`file`): the file  
- Example:  
```kt  
event.replyWithFile(new File('/path/to/file.txt'));  
```  
  
  
  
# DiscordMessage class  
DiscordMessage class for Arucas.  
  
This class allows you to interact with Discord messages.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<DiscordMessage>.getServer()`  
- Description: This gets the server the message was sent in  
- Returns - DiscordServer: The server the message was sent in  
- Example:  
```kt  
message.getServer();  
```  
  
### `<DiscordMessage>.isPinned()`  
- Description: This checks if the message is pinned  
- Returns - Boolean: true if the message is pinned, false if not  
- Example:  
```kt  
message.isPinned();  
```  
  
### `<DiscordMessage>.getAuthor()`  
- Description: This gets the author of the message  
- Returns - DiscordUser: The author of the message  
- Example:  
```kt  
message.getAuthor();  
```  
  
### `<DiscordMessage>.getId()`  
- Description: This gets the id of the message  
- Returns - String: The id of the message  
- Example:  
```kt  
message.getId();  
```  
  
### `<DiscordMessage>.isEdited()`  
- Description: This checks if the message is edited  
- Returns - Boolean: true if the message is edited, false if not  
- Example:  
```kt  
message.isEdited();  
```  
  
### `<DiscordMessage>.delete()`  
- Description: This deletes the message  
- Example:  
```kt  
message.delete();  
```  
  
### `<DiscordMessage>.replyWithEmbed(embedMap)`  
- Description: This replies to the message with the given embed map  
In the embed map, you can use the following keys:  
'title' as String, ''description' as String or List of String, 'colour'/'color' as Number  
'fields' as Map with keys: ('name' as String, 'value' as String, 'inline' as Boolean)  
and 'image' as String that is an url  
- Parameter - Map (`embedMap`): the embed map  
- Returns - DiscordMessage: the message that was sent  
- Example:  
```kt  
message.replyWithEmbed({  
 'title': 'EMBED!', 'description': ['Wow', 'Nice'], 'colour': 0xFFFFFF});  
```  
  
### `<DiscordMessage>.getAttachments()`  
- Description: This gets the attachments of the message  
- Returns - List: List with the attachments of the message  
- Example:  
```kt  
message.getAttachments();  
```  
  
### `<DiscordMessage>.addReaction(emojiId)`  
- Description: This adds a reaction to the message with a specific emoji id  
- Parameter - String (`emojiId`): the emoji id  
- Throws - Error:  
  - `'... is not a valid emote id'`  
- Example:  
```kt  
message.addReaction('012789012930198');  
```  
  
### `<DiscordMessage>.pin(bool)`  
- Description: This pins the message if true, and removes if false  
- Parameter - Boolean (`bool`): true to pin, false to unpin  
- Example:  
```kt  
message.pin(true);  
```  
  
### `<DiscordMessage>.addReactionUnicode(unicode)`  
- Description: This adds a reaction to the message with a specific unicode  
- Parameter - String (`unicode`): the unicode character  
- Example:  
```kt  
message.addReactionUnicode('\uD83D\uDE00');  
```  
  
### `<DiscordMessage>.getChannel()`  
- Description: This gets the channel the message was sent in  
- Returns - DiscordChannel: The channel the message was sent in  
- Example:  
```kt  
message.getChannel();  
```  
  
### `<DiscordMessage>.removeAllReactions()`  
- Description: This removes all reactions from the message  
- Example:  
```kt  
message.removeAllReactions();  
```  
  
### `<DiscordMessage>.getRaw()`  
- Description: This gets the raw message content  
- Returns - String: The raw message content  
- Example:  
```kt  
message.getRaw();  
```  
  
### `<DiscordMessage>.toString()`  
- Description: This gets the raw message content  
- Returns - String: The raw message content  
- Example:  
```kt  
message.toString();  
```  
  
### `<DiscordMessage>.reply(message)`  
- Description: This replies to the message with the given message  
- Parameter - String (`message`): the message  
- Returns - DiscordMessage: the message that was sent  
- Example:  
```kt  
message.reply('Replied!');  
```  
  
### `<DiscordMessage>.replyWithFile(file)`  
- Description: This replies to the message with the given file  
- Parameter - File (`file`): the file  
- Returns - DiscordMessage: the message that was sent  
- Example:  
```kt  
message.replyWithFile(new File('path/to/file'));  
```  
  
  
  
# DiscordServer class  
DiscordServer class for Arucas.  
  
This class allows you to interact with Discord servers.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<DiscordServer>.unban(user)`  
- Description: This unbans a user from the server  
- Parameter - DiscordUser (`user`): the user to unban  
- Example:  
```kt  
server.unban(user);  
```  
  
### `<DiscordServer>.kick(user)`  
- Description: This kicks a user from the server  
- Parameter - DiscordUser (`user`): the user to kick  
- Throws - Error:  
  - `'Member was null'`  
- Example:  
```kt  
server.kick(user);  
```  
  
### `<DiscordServer>.getMemberCount()`  
- Description: This gets the amount of members in the server  
- Returns - Number: the amount of members  
- Example:  
```kt  
server.getMemberCount();  
```  
  
### `<DiscordServer>.getOwnerId()`  
- Description: This gets the id of the owner of the server  
- Returns - String: the id of the owner  
- Example:  
```kt  
server.getOwnerId();  
```  
  
### `<DiscordServer>.createRole(roleMap)`  
- Description: This creates a role in the server  
In the role map you can have the following keys:  
'name' as String, 'colour'/'color' as Number, 'hoisted' as Boolean, 'mentionable as Boolean'  
and 'permissions' as a List of Strings, for example ['Manage Channels', 'Manage Server'], see Discord for more  
- Parameter - Map (`roleMap`): the map of the role  
- Example:  
```kt  
server.createRole({  
 "name": "new role", "colour": 0xFFFFFF, "permissions": ["Manage Permissions", "Ban Members", "Administrator"], "hoisted": true, "mentionable": true});  
```  
  
### `<DiscordServer>.getUserFromId(userId)`  
- Description: This gets a user from the server by their id  
- Parameter - String (`userId`): the id of the user  
- Returns - DiscordUser: the user, if the user cannot be found returns null  
- Example:  
```kt  
server.getUserFromId('12345678901234567890123456789012');  
```  
  
### `<DiscordServer>.ban(user)`  
- Description: This bans a user from the server  
- Parameter - DiscordUser (`user`): the user to ban  
- Example:  
```kt  
server.ban(user);  
```  
  
### `<DiscordServer>.ban(user, reason)`  
- Description: This bans a user from the server, with a reason  
- Parameters:  
  - DiscordUser (`user`): the user to ban  
  - String (`reason`): the reason for the ban  
- Example:  
```kt  
server.ban(user, 'The ban hammer has struck!');  
```  
  
  
  
# DiscordUser class  
DiscordUser class for Arucas.  
  
This class is used to interact with Discord users.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<DiscordUser>.getName()`  
- Description: This gets the name of the user  
- Returns - String: The name of the user  
- Example:  
```kt  
user.getName();  
```  
  
### `<DiscordUser>.getId()`  
- Description: This gets the id of the user  
- Returns - String: The id of the user  
- Example:  
```kt  
user.getId();  
```  
  
### `<DiscordUser>.getTag()`  
- Description: This gets the tag of the user, the numbers after the #  
- Returns - String: The tag of the user  
- Example:  
```kt  
user.getTag();  
```  
  
### `<DiscordUser>.getNameAndTag()`  
- Description: This gets the name and tag of the user  
- Returns - String: The name and tag of the user  
- Example:  
```kt  
user.getNameAndTag();  
```  
  
  
  
# Entity class  
Entity class for Arucas.  
  
This class is mostly used to get data about entities.  
  
Import with `import Entity from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<Entity>.getFullBiome()`  
- Description: This gets the biome of the entity, this returns the full biome id, so for example 'minecraft:plains'  
- Returns - String: the biome id of the biome the entity is in  
- Example:  
```kt  
entity.getFullBiome();  
```  
  
### `<Entity>.getAge()`  
- Description: This gets the age of the entity in ticks  
- Returns - Number: the age of the entity in ticks  
- Example:  
```kt  
entity.getAge();  
```  
  
### `<Entity>.getNbt()`  
- Description: This gets the nbt of the entity as a map  
- Returns - Map: the nbt of the entity  
- Example:  
```kt  
entity.getNbt();  
```  
  
### `<Entity>.getWorld()`  
- Description: This gets the world the entity is in  
- Returns - World: the world the entity is in  
- Example:  
```kt  
entity.getWorld();  
```  
  
### `<Entity>.collidesWith(pos, block)`  
- Description: This checks whether the entity collides with a block at a given position  
- Parameters:  
  - Pos (`pos`): the position to check  
  - Block (`block`): the block to check  
- Returns - Boolean: whether the entity collides with the block  
- Example:  
```kt  
entity.collidesWith(Pos.get(0, 0, 0), Block.of('minecraft:stone'));  
```  
  
### `<Entity>.getHitbox()`  
- Description: This gets the hitbox of the entity in a list containing the two corners of the hitbox, the minimum point and the maximum point  
- Returns - List: the hitbox of the entity  
- Example:  
```kt  
entity.getHitbox();  
```  
  
### `<Entity>.getFullId()`  
- Description: This gets the full id of the entity, this returns the full id, so for example  
'minecraft:cow' you can find all entityNames on  
[Joa's Entity Property Encyclopedia](https://joakimthorsen.github.io/MCPropertyEncyclopedia/entities.html)  
- Returns - String: the full id of the entity  
- Example:  
```kt  
entity.getFullId();  
```  
  
### `<Entity>.isSprinting()`  
- Description: Returns true if the player is sprinting  
- Returns - Boolean: true if the player is sprinting, false if not  
- Example:  
```kt  
entity.isSprinting();  
```  
  
### `<Entity>.getId()`  
- Description: This gets the id of the entity, this returns the id, so for example 'cow'  
- Returns - String: the id of the entity  
- Example:  
```kt  
entity.getId();  
```  
  
### `<Entity>.setGlowing(glowing)`  
- Description: This sets the entity to either start glowing or stop glowing on the client  
- Parameter - Boolean (`glowing`): the glowing state  
- Example:  
```kt  
entity.setGlowing(true);  
```  
  
### `<Entity>.getEntityIdNumber()`  
- Description: This gets the entity id number of the entity  
- Returns - Number: the entity id number  
- Example:  
```kt  
entity.getEntityIdNumber();  
```  
  
### `<Entity>.isOf(entityId)`  
- Description: This checks if the entity is of the given entity id  
- Parameter - String (`entityId`): the entity id to check  
- Returns - Boolean: true if the entity is of the given entity id  
- Example:  
```kt  
entity.isOf('cow');  
```  
  
### `<Entity>.getPos()`  
- Description: This gets the position of the entity  
- Returns - Pos: the position of the entity  
- Example:  
```kt  
entity.getPos();  
```  
  
### `<Entity>.getDimension()`  
- Description: This gets the dimension of the entity  
- Returns - String: the dimension id of dimension the entity is in  
- Example:  
```kt  
entity.getDimension();  
```  
  
### `<Entity>.isGlowing()`  
- Description: Returns true if the entity is glowing  
- Returns - Boolean: true if the entity is glowing, false if not  
- Example:  
```kt  
entity.isGlowing();  
```  
  
### `<Entity>.isSubmergedInWater()`  
- Description: Returns true if the entity is submerged in water  
- Returns - Boolean: true if the entity is submerged in water, false if not  
- Example:  
```kt  
entity.isSubmergedInWater();  
```  
  
### `<Entity>.getBiome()`  
- Description: This gets the biome of the entity, this only returns the path, so for example 'plains'  
- Returns - String: the biome id of the biome the entity is in  
- Example:  
```kt  
entity.getBiome();  
```  
  
### `<Entity>.getLookingAtBlock()`  
- Description: This gets the block that the entity is currently looking at  
with a max range of 20 blocks, if there is no block then it will return air  
- Returns - Block: the block that the entity is looking at, containing the position  
- Example:  
```kt  
entity.getLookingAtBlock();  
```  
  
### `<Entity>.getLookingAtBlock(maxDistance)`  
- Description: This gets the block that the entity is currently looking at  
with a specific max range, if there is no block then it will return air  
- Parameter - Number (`maxDistance`): the max range to ray cast  
- Returns - Block: the block that the entity is looking at, containing the position  
- Example:  
```kt  
entity.getLookingAtBlock(10);  
```  
  
### `<Entity>.getLookingAtBlock(maxDistance, fluidType)`  
- Description: This gets the block that the entity is currently looking at  
with a specific max range, and optionally whether fluids should  
be included, if there is no block then it will return air  
- Parameters:  
  - Number (`maxDistance`): the max range to ray cast  
  - String (`fluidType`): the types of fluids to include, either 'none', 'sources', or 'all'  
- Returns - Block: the block that the entity is looking at, containing the position  
- Example:  
```kt  
entity.getLookingAtBlock(10, 'sources');  
```  
  
### `<Entity>.getLookingAtPos(maxDistance)`  
- Description: This gets the position that the entity is currently looking at with a specific max range  
- Parameter - Number (`maxDistance`): the max range to ray cast  
- Returns - Pos: the position that the entity is looking at, containing the x, y, and z  
- Example:  
```kt  
entity.getLookingAtPos(10);  
```  
  
### `<Entity>.isInLava()`  
- Description: Returns true if the entity is in lava  
- Returns - Boolean: true if the entity is in lava, false if not  
- Example:  
```kt  
entity.isInLava();  
```  
  
### `<Entity>.getCustomName()`  
- Description: This gets the custom name of the entity if it has one  
- Returns - String: the custom name of the entity if it has one, otherwise null  
- Example:  
```kt  
entity.getCustomName();  
```  
  
### `<Entity>.getEntityUuid()`  
- Description: This gets the uuid of the entity  
- Returns - String: the uuid of the entity  
- Example:  
```kt  
entity.getEntityUuid();  
```  
  
### `<Entity>.isTouchingWater()`  
- Description: Returns true if the entity is touching water  
- Returns - Boolean: true if the entity is touching water, false if not  
- Example:  
```kt  
entity.isTouchingWater();  
```  
  
### `<Entity>.isFalling()`  
- Description: Returns true if the entity is falling  
- Returns - Boolean: true if the entity is falling, false if not  
- Example:  
```kt  
entity.isFalling();  
```  
  
### `<Entity>.isTouchingWaterOrRain()`  
- Description: Returns true if the entity is touching water or rain  
- Returns - Boolean: true if the entity is touching water or rain, false if not  
- Example:  
```kt  
entity.isTouchingWaterOrRain();  
```  
  
### `<Entity>.getSquaredDistanceTo(otherEntity)`  
- Description: This gets the squared distance between the entity and the other entity  
- Parameter - Entity (`otherEntity`): the other entity  
- Returns - Number: the squared distance between the entities  
- Example:  
```kt  
entity.getSquaredDistanceTo(Player.get());  
```  
  
### `<Entity>.getYaw()`  
- Description: This gets the yaw of the entity (horizontal head rotation)  
- Returns - Number: the yaw of the entity, between -180 and 180  
- Example:  
```kt  
entity.getYaw();  
```  
  
### `<Entity>.getTranslatedName()`  
- Description: This gets the translated name of the entity, for example 'minecraft:pig' would return 'Pig' if your language is in english  
- Returns - String: the translated name of the entity  
- Example:  
```kt  
entity.getTranslatedName();  
```  
  
### `<Entity>.getX()`  
- Description: This gets the x position of the entity  
- Returns - Number: the x position of the entity  
- Example:  
```kt  
entity.getX();  
```  
  
### `<Entity>.getPitch()`  
- Description: This gets the pitch of the entity (vertical head rotation)  
- Returns - Number: the pitch of the entity, between -90 and 90  
- Example:  
```kt  
entity.getPitch();  
```  
  
### `<Entity>.getY()`  
- Description: This gets the y position of the entity  
- Returns - Number: the y position of the entity  
- Example:  
```kt  
entity.getY();  
```  
  
### `<Entity>.getZ()`  
- Description: This gets the z position of the entity  
- Returns - Number: the z position of the entity  
- Example:  
```kt  
entity.getZ();  
```  
  
### `<Entity>.isSneaking()`  
- Description: Returns true if the player is sneaking  
- Returns - Boolean: true if the player is sneaking, false if not  
- Example:  
```kt  
entity.isSneaking();  
```  
  
### `<Entity>.getDistanceTo(otherEntity)`  
- Description: This gets the distance between the entity and the other entity  
- Parameter - Entity (`otherEntity`): the other entity  
- Returns - Number: the distance between the entities  
- Example:  
```kt  
entity.getDistanceTo(Player.get());  
```  
  
### `<Entity>.isOnFire()`  
- Description: Returns true if the entity is on fire  
- Returns - Boolean: true if the entity is on fire, false if not  
- Example:  
```kt  
entity.isOnFire();  
```  
  
### `<Entity>.isOnGround()`  
- Description: Returns true if the entity is on the ground  
- Returns - Boolean: true if the entity is on the ground, false if not  
- Example:  
```kt  
entity.isOnGround();  
```  
  
## Static Methods  
  
### `Entity.of(entityId)`  
- Description: This converts an entityId into an entity instance  
- Parameter - String (`entityId`): the entityId to convert to an entity  
- Returns - Entity: the entity instance from the id  
- Throws - Error:  
  - `'... is not a valid entity'`  
- Example:  
```kt  
Entity.of('minecraft:pig');  
```  
  
  
# Enum class  
Enum class for Arucas.  
  
All enums extends this class.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<Enum>.getName()`  
- Description: This allows you to get the name of the enum value  
- Returns - String: the name of the enum value  
- Example:  
```kt  
enum.getName();  
```  
  
### `<Enum>.ordinal()`  
- Description: This allows you to get the ordinal of the enum value  
- Returns - Number: the ordinal of the enum value  
- Example:  
```kt  
enum.ordinal();  
```  
  
  
  
# Error class  
Error class for Arucas.  
  
This class is the only type that can be thrown  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Constructors  
  
### `new Error()`  
- Description: This creates a new Error value with no message  
- Example:  
```kt  
new Error();  
```  
### `new Error(details)`  
- Description: This creates a new Error value with the given details as a message  
- Parameter - String (`details`): the details of the error  
- Example:  
```kt  
new Error('This is an error');  
```  
### `new Error(details, value)`  
- Description: This creates a new Error value with the given details as a message and the given value  
- Parameters:  
  - String (`details`): the details of the error  
  - Value (`value`): the value that is related to the error  
- Example:  
```kt  
new Error('This is an error', [1, 2, 3]);  
```  
  
## Methods  
  
### `<Error>.getValue()`  
- Description: This returns the value that is related to the error  
- Returns - Value: the value that is related to the error  
- Example:  
```kt  
error.getValue();  
```  
  
### `<Error>.getDetails()`  
- Description: This returns the raw message of the error  
- Returns - String: the details of the error  
- Example:  
```kt  
error.getDetails();  
```  
  
### `<Error>.getFormattedDetails()`  
- Description: This returns the message of the error in a formatted string  
- Returns - String: the details of the error  
- Example:  
```kt  
error.getFormattedDetails();  
```  
  
  
  
# FakeBlock class  
FakeBlock class for Arucas.  
  
This class can be used to create fake blocks which can be rendered in the world.  
  
Import with `import FakeBlock from Minecraft;`  
  
Fully Documented.  
  
## Constructors  
  
### `new FakeBlock(block, pos)`  
- Description: Creates a fake block with the given block and position  
- Parameters:  
  - Block (`block`): The block to use  
  - Pos (`pos`): The position of the block  
- Example:  
```kt  
new FakeBlock(Material.BEDROCK.asBlock(), new Pos(0, 0, 0));  
```  
  
## Methods  
  
### `<FakeBlock>.getZScale()`  
- Description: This gets the z scale of the shape  
- Example:  
```kt  
shape.getZScale();  
```  
  
### `<FakeBlock>.getBlock()`  
- Description: Gets the current block type of the fake block  
- Returns - Block: The block type of the fake block  
- Example:  
```kt  
fakeBlock.getBlock();  
```  
  
### `<FakeBlock>.getDirection()`  
- Description: This gets the direction of the shape  
- Returns - String: the direction of the shape as a string, this can be 'north', 'south', 'east', 'west', 'down', or 'up', null if it has no direction  
- Example:  
```kt  
shape.getDirection();  
```  
  
### `<FakeBlock>.setXScale(xScale)`  
- Description: This sets the x scale of the shape  
- Parameter - Number (`xScale`): the x scale of the shape  
- Example:  
```kt  
shape.setXScale(1.5);  
```  
  
### `<FakeBlock>.setScale(xScale, yScale, zScale)`  
- Description: This sets the scale of the shape  
- Parameters:  
  - Number (`xScale`): the x scale of the shape  
  - Number (`yScale`): the y scale of the shape  
  - Number (`zScale`): the z scale of the shape  
- Example:  
```kt  
shape.setScale(1.5, 2.5, 3.5);  
```  
  
### `<FakeBlock>.setYTilt(yTilt)`  
- Description: This sets the y tilt of the shape  
- Parameter - Number (`yTilt`): the y tilt  
- Example:  
```kt  
shape.setYTilt(100);  
```  
  
### `<FakeBlock>.setBlock(block)`  
- Description: Sets the block type to render of the fake block  
- Parameter - Block (`block`): The block to render  
- Example:  
```kt  
fakeBlock.setBlock(Material.BEDROCK.asBlock());  
```  
  
### `<FakeBlock>.setZScale(zScale)`  
- Description: This sets the z scale of the shape  
- Parameter - Number (`zScale`): the z scale of the shape  
- Example:  
```kt  
shape.setZScale(3.5);  
```  
  
### `<FakeBlock>.getYTilt()`  
- Description: This gets the y tilt of the shape  
- Returns - Number: the y tilt  
- Example:  
```kt  
shape.getYTilt();  
```  
  
### `<FakeBlock>.setTilt(xTilt, yTilt, zTilt)`  
- Description: This sets the tilt of the shape  
- Parameters:  
  - Number (`xTilt`): the x tilt  
  - Number (`yTilt`): the y tilt  
  - Number (`zTilt`): the z tilt  
- Example:  
```kt  
shape.setTilt(100, 0, 80);  
```  
  
### `<FakeBlock>.setPos(pos)`  
- Description: Sets the position of the fake block  
- Parameter - Pos (`pos`): The position of the block  
- Example:  
```kt  
fakeBlock.setPos(new Pos(0, 0, 0));  
```  
  
### `<FakeBlock>.getXScale()`  
- Description: This gets the x scale of the shape  
- Example:  
```kt  
shape.getXScale();  
```  
  
### `<FakeBlock>.stopRendering()`  
- Description: This stops the shape from rendering  
- Example:  
```kt  
shape.stopRendering();  
```  
  
### `<FakeBlock>.setYScale(yScale)`  
- Description: This sets the y scale of the shape  
- Parameter - Number (`yScale`): the y scale of the shape  
- Example:  
```kt  
shape.setYScale(2.5);  
```  
  
### `<FakeBlock>.getYScale()`  
- Description: This gets the y scale of the shape  
- Example:  
```kt  
shape.getYScale();  
```  
  
### `<FakeBlock>.getPos()`  
- Description: Gets the current position of the fake block  
- Returns - Pos: The position of the fake block  
- Example:  
```kt  
fakeBlock.getPos();  
```  
  
### `<FakeBlock>.setDirection(direction)`  
- Description: This sets the direction of the shape  
- Parameter - String (`direction`): the direction of the shape as a string, this can be 'north', 'south', 'east', 'west', 'down', or 'up'  
- Example:  
```kt  
shape.setDirection('down');  
```  
  
### `<FakeBlock>.setXTilt(xTilt)`  
- Description: This sets the x tilt of the shape  
- Parameter - Number (`xTilt`): the x tilt  
- Example:  
```kt  
shape.setXTilt(100);  
```  
  
### `<FakeBlock>.getZTilt()`  
- Description: This gets the z tilt of the shape  
- Returns - Number: the z tilt  
- Example:  
```kt  
shape.getZTilt();  
```  
  
### `<FakeBlock>.render()`  
- Description: This sets the shape to be rendered indefinitely, the shape will only stop rendering when the script ends or when you call the stopRendering() method  
- Example:  
```kt  
shape.render();  
```  
  
### `<FakeBlock>.getXTilt()`  
- Description: This gets the x tilt of the shape  
- Returns - Number: the x tilt  
- Example:  
```kt  
shape.getXTilt();  
```  
  
### `<FakeBlock>.setZTilt(zTilt)`  
- Description: This sets the z tilt of the shape  
- Parameter - Number (`zTilt`): the z tilt  
- Example:  
```kt  
shape.setZTilt(100);  
```  
  
  
  
# FakeEntity class  
FakeEntity class for Arucas.  
  
This allows you to create a fake entity which can be rendered in the world.  
  
Import with `import FakeEntity from Minecraft;`  
  
Fully Documented.  
  
## Members  
  
### `<FakeEntity>.world`  
- Description: The world that the entity is being rendered in  
- Type: World  
- Assignable: false  
- Example:  
```kt  
fakeEntity.world;  
```  
### `<FakeEntity>.pos`  
- Description: The position of the entity  
- Type: Pos  
- Assignable: false  
- Example:  
```kt  
fakeEntity.pos;  
```  
### `<FakeEntity>.bodyYaw`  
- Description: The yaw of the entity  
- Type: Number  
- Assignable: false  
- Example:  
```kt  
fakeEntity.bodyYaw;  
```  
### `<FakeEntity>.pitch`  
- Description: The pitch of the entity  
- Type: Number  
- Assignable: false  
- Example:  
```kt  
fakeEntity.pitch;  
```  
### `<FakeEntity>.entity`  
- Description: The entity that is being rendered  
- Type: Entity  
- Assignable: false  
- Example:  
```kt  
fakeEntity.entity;  
```  
### `<FakeEntity>.yaw`  
- Description: The yaw of the entity  
- Type: Number  
- Assignable: false  
- Example:  
```kt  
fakeEntity.yaw;  
```  
  
## Constructors  
  
### `new FakeEntity(entity, world)`  
- Description: Creates a new fake entity  
- Parameters:  
  - Entity (`entity`): The entity that you want to create into a fake entity  
  - World (`world`): The world that the entity is being rendered in  
- Example:  
```kt  
fakeEntity = new FakeEntity();  
```  
  
## Methods  
  
### `<FakeEntity>.setPos(pos)`  
- Description: Sets the position of the entity with no interpolation  
- Parameter - Pos (`pos`): The new position of the entity  
- Example:  
```kt  
fakeEntity.setPos(new Pos(0, 0, 0));  
```  
  
### `<FakeEntity>.setPos(pos, interpolationSteps)`  
- Description: Sets the position of the entity  
- Parameters:  
  - Pos (`pos`): The new position of the entity  
  - Number (`interpolationSteps`): The number of interpolation steps to take  
- Example:  
```kt  
fakeEntity.setPos(new Pos(0, 0, 0), 0);  
```  
  
### `<FakeEntity>.setPos(x, y, z)`  
- Description: Sets the position of the entity with no interpolation  
- Parameters:  
  - Number (`x`): The new x position of the entity  
  - Number (`y`): The new y position of the entity  
  - Number (`z`): The new z position of the entity  
- Example:  
```kt  
fakeEntity.setPos(0, 0, 0);  
```  
  
### `<FakeEntity>.setPos(x, y, z, interpolationSteps)`  
- Description: Sets the position of the entity  
- Parameters:  
  - Number (`x`): The new x position of the entity  
  - Number (`y`): The new y position of the entity  
  - Number (`z`): The new z position of the entity  
  - Number (`interpolationSteps`): The number of interpolation steps to take  
- Example:  
```kt  
fakeEntity.setPos(0, 0, 0, 10);  
```  
  
### `<FakeEntity>.spawn()`  
- Description: Spawns the entity (makes it render in the world)  
- Example:  
```kt  
fakeEntity.spawn();  
```  
  
### `<FakeEntity>.updatePosAndRotation(pos, yaw, pitch)`  
- Description: Updates the position and rotation of the entity with no interpolation  
- Parameters:  
  - Pos (`pos`): The new position of the entity  
  - Number (`yaw`): The new yaw of the entity  
  - Number (`pitch`): The new pitch of the entity  
- Example:  
```kt  
fakeEntity.updatePosAndRotation(new Pos(100, 0, 100), 0, 0);  
```  
  
### `<FakeEntity>.updatePosAndRotation(pos, yaw, pitch, interpolationSteps)`  
- Description: Updates the position and rotation of the entity  
- Parameters:  
  - Pos (`pos`): The new position of the entity  
  - Number (`yaw`): The new yaw of the entity  
  - Number (`pitch`): The new pitch of the entity  
  - Number (`interpolationSteps`): The number of interpolation steps to take  
- Example:  
```kt  
fakeEntity.updatePosAndRotation(new Pos(100, 0, 100), 0, 0, 10);  
```  
  
### `<FakeEntity>.setPitch(pitch)`  
- Description: Sets the pitch of the entity with no interpolation  
- Parameter - Number (`pitch`): The new pitch of the entity  
- Example:  
```kt  
fakeEntity.setPitch(0);  
```  
  
### `<FakeEntity>.setPitch(pitch, interpolationSteps)`  
- Description: Sets the pitch of the entity  
- Parameters:  
  - Number (`pitch`): The new pitch of the entity  
  - Number (`interpolationSteps`): The number of interpolation steps to take  
- Example:  
```kt  
fakeEntity.setPitch(0, 10);  
```  
  
### `<FakeEntity>.despawn()`  
- Description: Despawns the entity (makes it not render in the world)  
- Example:  
```kt  
fakeEntity.despawn();  
```  
  
### `<FakeEntity>.setWorld(world)`  
- Description: Sets the world that the entity is being rendered in  
- Parameter - World (`world`): The world that the entity is being rendered in  
- Example:  
```kt  
fakeEntity.setWorld(MinecraftClient.getClient().getWorld());  
```  
  
### `<FakeEntity>.setBodyYaw(bodyYaw)`  
- Description: Sets the body yaw of the entity with no interpolation  
- Parameter - Number (`bodyYaw`): The new body yaw of the entity  
- Example:  
```kt  
fakeEntity.setBodyYaw(0);  
```  
  
### `<FakeEntity>.setBodyYaw(bodyYaw, interpolationSteps)`  
- Description: Sets the body yaw of the entity  
- Parameters:  
  - Number (`bodyYaw`): The new body yaw of the entity  
  - Number (`interpolationSteps`): The number of interpolation steps to take  
- Example:  
```kt  
fakeEntity.setBodyYaw(0, 10);  
```  
  
### `<FakeEntity>.setYaw(yaw)`  
- Description: Sets the yaw of the entity with no interpolation  
- Parameter - Number (`yaw`): The new yaw of the entity  
- Example:  
```kt  
fakeEntity.setYaw(0);  
```  
  
### `<FakeEntity>.setYaw(yaw, interpolationSteps)`  
- Description: Sets the yaw of the entity  
- Parameters:  
  - Number (`yaw`): The new yaw of the entity  
  - Number (`interpolationSteps`): The number of interpolation steps to take  
- Example:  
```kt  
fakeEntity.setYaw(0, 10);  
```  
  
  
  
# FakeScreen class  
FakeScreen class for Arucas.  
  
This class extends Screen and so inherits all of their methods too,  
this class is used to create client side inventory screens.  
  
Import with `import FakeScreen from Minecraft;`  
  
Fully Documented.  
  
## Constructors  
  
### `new FakeScreen(name, rows)`  
- Description: Creates a FakeScreen instance with given name and given amount of rows  
- Parameters:  
  - String (`name`): the name of the screen  
  - Number (`rows`): the number of rows between 1 - 6  
- Example:  
```kt  
new FakeScreen('MyScreen', 6);  
```  
  
## Methods  
  
### `<FakeScreen>.getStackForSlot(slotNum)`  
- Description: Gets the stack for the given slot, if the slot is out of bounds it returns null  
- Parameter - Number (`slotNum`): the slot number  
- Returns - ItemStack: the stack for the given slot  
- Example:  
```kt  
fakeScreen.getStackForSlot(0);  
```  
  
### `<FakeScreen>.onClick(function)`  
- Description: This sets the callback for when a slot is clicked in the inventory  
- Parameter - Function (`function`): the callback function which must have 3 parameters, which will be passed in when it is called, item, slotNum, action, being ItemStack, Number, and String respectively  
- Example:  
```kt  
fakeScreen.onClick(fun(item, slotNum, action) {  
 // action can be any of the following: // 'PICKUP', 'QUICK_MOVE', 'SWAP', 'CLONE', 'THROW', 'QUICK_CRAFT', or 'PICKUP_ALL' print(action);});  
```  
  
### `<FakeScreen>.setStackForSlot(slotNum, stack)`  
- Description: Sets the stack for the given slot, if the slot is out of bounds it won't be set  
- Parameters:  
  - Number (`slotNum`): the slot number  
  - ItemStack (`stack`): the stack to set  
- Example:  
```kt  
fakeScreen.setStackForSlot(0, Material.DIAMOND_BLOCK.asItemStack());  
```  
  
  
  
# File class  
File class for Arucas.  
  
This class allows you to manipulate files.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Constructors  
  
### `new File(path)`  
- Description: This creates a new File object with set path  
- Parameter - String (`path`): the path of the file  
- Example:  
```kt  
new File('foo/bar/script.arucas')  
```  
  
## Methods  
  
### `<File>.read()`  
- Description: This reads the file and returns the contents as a string  
- Returns - String: the contents of the file  
- Throws - Error:  
  - `'There was an error reading the file: ...'`  
  - `'Out of Memory - The file you are trying to read is too large'`  
- Example:  
```kt  
file.read()  
```  
  
### `<File>.getName()`  
- Description: This returns the name of the file  
- Returns - String: the name of the file  
- Example:  
```kt  
File.getName()  
```  
  
### `<File>.getAbsolutePath()`  
- Description: This returns the absolute path of the file  
- Returns - String: the absolute path of the file  
- Example:  
```kt  
file.getAbsolutePath()  
```  
  
### `<File>.getPath()`  
- Description: This returns the path of the file  
- Returns - String: the path of the file  
- Example:  
```kt  
file.getPath()  
```  
  
### `<File>.exists()`  
- Description: This returns if the file exists  
- Returns - Boolean: true if the file exists  
- Throws - Error:  
  - `'Could not check file: ...'`  
- Example:  
```kt  
file.exists()  
```  
  
### `<File>.createDirectory()`  
- Description: This creates all parent directories of the file if they don't already exist  
- Returns - Boolean: true if the directories were created  
- Throws - Error:  
  - `'...'`  
- Example:  
```kt  
file.createDirectory()  
```  
  
### `<File>.getSubFiles()`  
- Description: This returns a list of all the sub files in the directory  
- Returns - List: a list of all the sub files in the directory  
- Throws - Error:  
  - `'Could not find any files'`  
- Example:  
```kt  
file.getSubFiles()  
```  
  
### `<File>.delete()`  
- Description: This deletes the file  
- Returns - Boolean: true if the file was deleted  
- Throws - Error:  
  - `'Could not delete file: ...'`  
- Example:  
```kt  
file.delete()  
```  
  
### `<File>.write(string)`  
- Description: This writes a string to a file  
- Parameter - String (`string`): the string to write to the file  
- Throws - Error:  
  - `'There was an error writing the file: ...'`  
- Example:  
```kt  
file.write('Hello World!')  
```  
  
### `<File>.open()`  
- Description: This opens the file (as in opens it on your os)  
- Example:  
```kt  
file.open()  
```  
  
## Static Methods  
  
### `File.getDirectory()`  
- Description: This returns the file of the working directory  
- Returns - File: the file of the working directory  
- Example:  
```kt  
File.getDirectory()  
```  
  
  
# Function class  
Function class for Arucas.  
  
Adds utilities for delegating and calling functions.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Static Methods  
  
### `Function.call(delegate, parameters...)`  
- Description: Calls the given delegate with the given arbitrary parameters  
- Parameters:  
  - Function (`delegate`): the delegate to call  
  - Value (`parameters...`): the parameters to pass to the delegate  
- Returns - Value: the return value of the delegate  
- Example:  
```kt  
Function.call(Function.getBuiltIn('print', 1), 'Hello World!');  
```  
  
### `Function.getMethod(value, methodName, parameterCount)`  
- Description: Returns a method delegate with the given name and parameter count  
- Parameters:  
  - Value (`value`): the value to call the method on  
  - String (`methodName`): the name of the method  
  - Number (`parameterCount`): the parameter count of the method  
- Returns - Function: the method delegate  
- Example:  
```kt  
Function.getMethod('String', 'contains', 1);  
```  
  
### `Function.callWithList(delegate, parameters)`  
- Description: Calls the given delegate with the given parameters  
- Parameters:  
  - Function (`delegate`): the delegate to call  
  - List (`parameters`): the parameters to pass to the delegate  
- Returns - Value: the return value of the delegate  
- Example:  
```kt  
Function.callWithList(fun(m1, m2) { }, ['Hello', 'World']);  
```  
  
### `Function.getBuiltIn(functionName, parameterCount)`  
- Description: Returns a built-in function delegate with the given name and parameter count  
- Parameters:  
  - String (`functionName`): the name of the function  
  - Number (`parameterCount`): the parameter count of the function  
- Returns - Function: the built-in function delegate  
- Example:  
```kt  
Function.getBuiltIn('print', 1);  
```  
  
  
# GameEvent class  
GameEvent class for Arucas.  
  
This class allows you to register listeners for game events in Minecraft.  
  
Import with `import GameEvent from Minecraft;`  
  
Fully Documented.  
  
## Constructors  
  
### `new GameEvent(eventName, onEvent)`  
- Description: This creates a new GameEvent, that is not cancellable  
- Parameters:  
  - String (`eventName`): The name of the event, you can find these on the GameEvents page  
  - Function (`onEvent`): The function to run when the event is called, some events may have parameters  
- Example:  
```kt  
new GameEvent('onClientTick', fun() { });  
```  
### `new GameEvent(eventName, onEvent, cancellable)`  
- Description: This creates a new GameEvent  
- Parameters:  
  - String (`eventName`): The name of the event, you can find these on the GameEvents page  
  - Function (`onEvent`): The function to run when the event is called, some events may have parameters  
  - Boolean (`cancellable`): Whether or not the event is cancellable, if it is then it will run on the main thread  
- Example:  
```kt  
new GameEvent('onClientTick', fun() { }, true);  
```  
  
## Methods  
  
### `<GameEvent>.unregister()`  
- Description: This unregisters the event  
- Example:  
```kt  
gameEvent.unregister();  
```  
  
### `<GameEvent>.isRegistered()`  
- Description: This returns whether or not the event is registered  
- Returns - Boolean: Whether or not the event is registered  
- Example:  
```kt  
gameEvent.isRegistered();  
```  
  
### `<GameEvent>.register()`  
- Description: This registers the event  
- Example:  
```kt  
gameEvent.register();  
```  
  
## Static Methods  
  
### `GameEvent.cancel()`  
- Description: If called on a cancellable event, this will stop execution and cancel the event,  
if called on a non-cancellable event, or not on an event, this will throw an error  
- Example:  
```kt  
GameEvent.cancel();  
```  
  
### `GameEvent.unregisterAll()`  
- Description: This unregisters all events registered by this script  
- Example:  
```kt  
GameEvent.unregisterAll();  
```  
  
  
# ItemEntity class  
ItemEntity class for Arucas.  
  
This class extends Entity and so inherits all of their methods too,  
ItemEntities are entities that are dropped items.  
  
Import with `import ItemEntity from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<ItemEntity>.getCustomName()`  
- Description: This method returns the custom name of the ItemEntity  
- Returns - String: the custom name of the entity  
- Example:  
```kt  
itemEntity.getCustomName();  
```  
  
### `<ItemEntity>.getItemAge()`  
- Description: This method returns the age of the ItemEntity  
this is increased every tick and the item entity despawns after 6000 ticks  
- Returns - Number: the age of the entity  
- Example:  
```kt  
itemEntity.getItemAge();  
```  
  
### `<ItemEntity>.getItemStack()`  
- Description: This method returns the ItemStack that is held in the ItemEntity  
- Returns - ItemStack: the ItemStack that the entity holds  
- Example:  
```kt  
itemEntity.getItemStack();  
```  
  
### `<ItemEntity>.getThrower()`  
- Description: This method returns the player that threw the ItemEntity  
- Example:  
```kt  
itemEntity.getThrower();  
```  
  
  
  
# ItemStack class  
ItemStack class for Arucas.  
  
This class represents an item stack. It can be used to create new item stacks, or to modify existing ones.  
  
Import with `import ItemStack from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<ItemStack>.getMaxCount()`  
- Description: This gets the max stack size of the ItemStack  
- Returns - Number: the max stack size of the ItemStack  
- Example:  
```kt  
itemStack.getMaxCount();  
```  
  
### `<ItemStack>.getNbt()`  
- Description: This gets the NBT data of the ItemStack as a Map  
- Returns - Map: the NBT data of the ItemStack  
- Example:  
```kt  
itemStack.getNbt();  
```  
  
### `<ItemStack>.setCustomName(customName)`  
- Description: This sets the custom name of the ItemStack  
- Parameter - Text (`customName`): the custom name of the ItemStack, this can be text or string  
- Returns - ItemStack: the ItemStack with the new custom name  
- Example:  
```kt  
itemStack.setCustomName('My Pickaxe');  
```  
  
### `<ItemStack>.getCustomName()`  
- Description: This gets the custom name of the ItemStack  
- Returns - String: the custom name of the ItemStack  
- Example:  
```kt  
itemStack.getCustomName();  
```  
  
### `<ItemStack>.getFullId()`  
- Description: This gets the full id of the ItemStack, for example: 'minecraft:diamond_sword'  
- Returns - String: the full id of the ItemStack  
- Example:  
```kt  
itemStack.getFullId();  
```  
  
### `<ItemStack>.getId()`  
- Description: This gets the id of the ItemStack, for example: 'diamond_sword'  
- Returns - String: the id of the ItemStack  
- Example:  
```kt  
itemStack.getId();  
```  
  
### `<ItemStack>.getMiningSpeedMultiplier(block)`  
- Description: This gets the mining speed multiplier of the ItemStack for the given Block,  
for example a diamond pickaxe on stone would have a higher multiplier than air on stone  
- Parameter - Block (`block`): the Block to get the mining speed multiplier for  
- Returns - Number: the mining speed multiplier of the ItemStack for the given Block  
- Example:  
```kt  
pickaxe = Material.DIAMOND_PICKAXE.asItemStack();  
goldBlock = Material.GOLD_BLOCK.asBlock();  
  
pickaxe.getMiningSpeedMultiplier(goldBlock);  
```  
  
### `<ItemStack>.isBlockItem()`  
- Description: This checks if the ItemStack can be placed as a block  
- Returns - Boolean: true if the ItemStack can be placed as a block, false otherwise  
- Example:  
```kt  
itemStack.isBlockItem();  
```  
  
### `<ItemStack>.getEnchantments()`  
- Description: This gets the enchantments of the item, in a map containing the  
id of the enchantment as the key and the level of the enchantment as the value  
- Returns - Map: the enchantments of the item, map may be empty  
- Example:  
```kt  
itemStack.getEnchantments();  
```  
  
### `<ItemStack>.getDurability()`  
- Description: This gets the durability of the item  
- Returns - Number: the durability of the item  
- Example:  
```kt  
itemStack.getDurability();  
```  
  
### `<ItemStack>.getMaterial()`  
- Description: This gets the material of the ItemStack  
- Returns - Material: the material of the ItemStack  
- Example:  
```kt  
itemStack.getMaterial();  
```  
  
### `<ItemStack>.isNbtEqual(itemStack)`  
- Description: This checks if the ItemStack has the same NBT data as the other given ItemStack  
- Parameter - ItemStack (`itemStack`): the other ItemStack to compare to  
- Returns - Boolean: true if the ItemStack has the same NBT data as the other given ItemStack  
- Example:  
```kt  
itemStack.isNbtEqual(Material.GOLD_INGOT.asItemStack());  
```  
  
### `<ItemStack>.getTranslatedName()`  
- Description: This gets the translated name of the ItemStack, for example  
'diamond_sword' would return 'Diamond Sword' if your language is English  
- Returns - String: the translated name of the ItemStack  
- Example:  
```kt  
itemStack.getTranslatedName();  
```  
  
### `<ItemStack>.asEntity()`  
- Description: This creates an item entity with the item  
- Returns - ItemEntity: the entity of the ItemStack  
- Throws - Error:  
  - `'Item cannot be converted to an ItemEntity'`  
- Example:  
```kt  
itemStack.asEntity();  
```  
  
### `<ItemStack>.setItemLore(lore)`  
- Description: This sets the lore of the ItemStack  
- Parameter - List (`lore`): the lore of the ItemStack as a list of Text  
- Returns - ItemStack: the ItemStack with the new lore  
- Example:  
```kt  
itemStack = Material.DIAMOND_PICKAXE.asItemStack();  
itemStack.setItemLore([  
 Text.of('This is a pickaxe'), Text.of('It is made of diamond')]);  
```  
  
### `<ItemStack>.asBlock()`  
- Description: This gets the block of the ItemStack  
- Returns - Block: the block item of the ItemStack  
- Throws - Error:  
  - `'Item cannot be converted to a block'`  
- Example:  
```kt  
itemStack.asBlock();  
```  
  
### `<ItemStack>.setStackSize(stackSize)`  
- Description: This sets the stack size of the ItemStack  
- Parameter - Number (`stackSize`): the stack size of the ItemStack  
- Returns - ItemStack: the ItemStack with the new stack size  
- Example:  
```kt  
itemStack.setStackSize(5);  
```  
  
### `<ItemStack>.isStackable()`  
- Description: This checks if the ItemStack is stackable  
- Returns - Boolean: true if the ItemStack is stackable, false otherwise  
- Example:  
```kt  
itemStack.isStackable();  
```  
  
### `<ItemStack>.getMaxDurability()`  
- Description: This gets the max durability of the item  
- Returns - Number: the max durability of the item  
- Example:  
```kt  
itemStack.getMaxDurability();  
```  
  
### `<ItemStack>.setNbt(nbtMap)`  
- Description: This sets the NBT data of the ItemStack  
- Parameter - Map (`nbtMap`): the NBT data of the ItemStack as a map  
- Returns - ItemStack: the ItemStack with the new NBT data  
- Example:  
```kt  
itemStack.setNbt({'Enchantments': []});  
```  
  
### `<ItemStack>.getCount()`  
- Description: This gets the count of the ItemStack, the amount of items in the stack  
- Returns - Number: the count of the ItemStack  
- Example:  
```kt  
itemStack.getCount();  
```  
  
## Static Methods  
  
### `ItemStack.of(material)`  
- Description: This creates an ItemStack from a material or a string  
- Parameter - MaterialLike (`material`): the material, item stack, block, or string to create the ItemStack from  
- Returns - ItemStack: the new ItemStack instance  
- Example:  
```kt  
ItemStack.of('dirt');  
```  
  
### `ItemStack.parse(nbtString)`  
- Description: This creates an ItemStack from a NBT string, this can be in the form of a map  
or an ItemStack NBT, or like the item stack command format  
- Parameter - String (`nbtString`): the NBT string to create the ItemStack from  
- Returns - ItemStack: the new ItemStack instance  
- Example:  
```kt  
ItemStack.parse('{id:"minecraft:dirt",Count:64}')  
```  
  
  
# Java class  
Java class for Arucas.  
  
This allows for direct interaction from Arucas to Java  
  
Import with `import Java from util.Internal;`  
  
Fully Documented.  
  
## Methods  
  
### `<Java>.callMethod(methodName, parameters...)`  
- Deprecated: You should call the method directly on the value: Java.valueOf('').isBlank();  
- Description: This calls the specified method with the specified parameters, this is slower   
than calling a delegate, this is the same speed as calling the method directly on the value however  
- Parameters:  
  - String (`methodName`): the name of the method  
  - Value (`parameters...`): the parameters to call the method with, this may be none, a note - if you are calling a VarArgs method you must pass a Java Object array with your VarArg arguments  
- Returns - Java: the return value of the method call wrapped in the Java wrapper  
- Throws - Error:  
  - `'No such method ... with ... parameters exists for ...'`  
  - `'First parameter must be name of method'`  
- Example:  
```kt  
Java.valueOf('').callMethod('isBlank');  
```  
  
### `<Java>.setField(fieldName, value)`  
- Deprecated: You should assign the value directly on the value: Java.constructClass('me.senseiwells.impl.Test').A = 'Hello';  
- Description: This sets the specified field to the specified value  
- Parameters:  
  - String (`fieldName`): the name of the field  
  - Value (`value`): the value to set the field to, the value type must match the type of the field  
- Example:  
```kt  
Java.constructClass('me.senseiwells.impl.Test').setField('A', 'Hello');  
```  
  
### `<Java>.getField(fieldName)`  
- Deprecated: You should call the method directly on the value: Java.constructClass('me.senseiwells.impl.Test').A;  
- Description: This returns the Java wrapped value of the specified field  
- Parameter - String (`fieldName`): the name of the field  
- Returns - Java: the Java wrapped value of the field  
- Example:  
```kt  
Java.constructClass('me.senseiwells.impl.Test').getField('A');  
```  
  
### `<Java>.toArucas()`  
- Description: This converts the Java value to an Arucas Value  
- Returns - Value: the Value in Arucas, this may still be of Java value if the value cannot be converted into an Arucas value, values like Strings, Numbers, Lists, etc... will be converted  
- Example:  
```kt  
Java.valueOf([1, 2, 3]).toArucas();  
```  
  
### `<Java>.getMethodDelegate(methodName, parameters)`  
- Description: This returns a method delegate for the specified method name and parameters,   
delegating the method is much faster since it uses MethodHandles, so if you are calling   
a method repetitively it is faster to delegate the method and then call the delegate  
- Parameters:  
  - String (`methodName`): the name of the method  
  - Number (`parameters`): the number of parameters  
- Returns - Function: the function containing the Java method delegate  
- Throws - Error:  
  - `'No such method ... with ... parameters can be found'`  
- Example:  
```kt  
Java.valueOf('string!').getMethodDelegate('isBlank', 0);  
```  
  
## Static Methods  
  
### `Java.floatOf(num)`  
- Description: Creates a Java value float, to be used in Java, since floats cannot be explicitly declared in Arucas  
- Parameter - Number (`num`): the number to convert to a Java float  
- Returns - Java: the float in Java wrapper  
- Example:  
```kt  
Java.floatOf(1.0);  
```  
  
### `Java.shortOf(num)`  
- Description: Creates a Java value short, to be used in Java since shorts cannot be explicitly declared in Arucas  
- Parameter - Number (`num`): the number to convert to a Java short  
- Returns - Java: the short in Java wrapper  
- Example:  
```kt  
Java.shortOf(0xFF);  
```  
  
### `Java.classFromName(className)`  
- Description: Gets a Java class from the name of the class  
- Parameter - String (`className`): the name of the class you want to get  
- Returns - Java: the Java Class<?> value wrapped in the Java wrapper  
- Throws - Error:  
  - `'No such class with ...'`  
- Example:  
```kt  
Java.classFromName('java.util.ArrayList');  
```  
  
### `Java.longArray(size)`  
- Description: Creates a Java long array with a given size, the array is filled with 0's   
by default and can be filled with only longs  
- Parameter - Number (`size`): the size of the array  
- Returns - Java: the Java long array  
- Example:  
```kt  
Java.longArray(10);  
```  
  
### `Java.supplierOf(function)`  
- Description: Creates a Java Supplier object from a given function  
- Parameter - Function (`function`): the function to be executed, this must have no parameters and must return (supply) a value  
- Returns - Java: the Java Supplier object  
- Example:  
```kt  
Java.supplierOf(fun() {  
 return "supplier";});  
```  
  
### `Java.functionOf(function)`  
- Description: Creates a Java Function object from a given function  
- Parameter - Function (`function`): the function to be executed, this must have one parameter and must return a value  
- Returns - Java: the Java Function object  
- Example:  
```kt  
Java.functionOf(fun(num) {  
 return num + 10;});  
```  
  
### `Java.doubleOf(num)`  
- Description: Creates a Java value double, to be used in Java  
- Parameter - Number (`num`): the number to convert to a Java double  
- Returns - Java: the double in Java wrapper  
- Example:  
```kt  
Java.doubleOf(1.0);  
```  
  
### `Java.getStaticField(className, fieldName)`  
- Description: Gets a static field Java value from a Java class  
- Parameters:  
  - String (`className`): the name of the class  
  - String (`fieldName`): the name of the field  
- Returns - Java: the Java value of the field wrapped in the Java wrapper  
- Throws - Error:  
  - `'No such class with ...'`  
- Example:  
```kt  
Java.getStaticField('java.lang.Integer', 'MAX_VALUE');  
```  
  
### `Java.constructClass(className, parameters...)`  
- Description: This constructs a Java class with specified class name and parameters  
- Parameters:  
  - String (`className`): the name of the class  
  - Value (`parameters...`): any parameters to pass to the constructor, there may be no parameters, again if calling VarArgs constructor you must have your VarArg parameters in a Java Object array  
- Returns - Java: the constructed Java Object wrapped in the Java wrapper  
- Throws - Error:  
  - `'First parameter must be a class name'`  
  - `'No such class with ...'`  
  - `'No such constructor with ... parameters exists for ...'`  
- Example:  
```kt  
Java.constructClass('java.util.ArrayList');  
```  
  
### `Java.shortArray(size)`  
- Description: Creates a Java short array with a given size, the array is filled with 0's   
by default and can be filled with only shorts  
- Parameter - Number (`size`): the size of the array  
- Returns - Java: the Java short array  
- Example:  
```kt  
Java.shortArray(10);  
```  
  
### `Java.runnableOf(function)`  
- Description: Creates a Java Runnable object from a given function  
- Parameter - Function (`function`): the function to be executed, this must have no parameters and any return values will be ignored  
- Returns - Java: the Java Runnable object  
- Example:  
```kt  
Java.runnableOf(fun() {  
 print('runnable');});  
```  
  
### `Java.charOf(string)`  
- Description: Creates a Java value char, to be used in Java since chars cannot be explicitly declared in Arucas  
- Parameter - String (`string`): the string with one character to convert to a Java char  
- Returns - Java: the char in Java wrapper  
- Throws - Error:  
  - `'String must be 1 character long'`  
- Example:  
```kt  
Java.charOf('f');  
```  
  
### `Java.charArray(size)`  
- Description: Creates a Java char array with a given size, the array is filled with null's   
(null characters) by default and can be filled with only chars  
- Parameter - Number (`size`): the size of the array  
- Returns - Java: the Java char array  
- Example:  
```kt  
Java.charArray(10);  
```  
  
### `Java.intOf(num)`  
- Description: Creates a Java value int, to be used in Java since ints cannot be explicitly declared in Arucas  
- Parameter - Number (`num`): the number to convert to a Java int  
- Returns - Java: the int in Java wrapper  
- Example:  
```kt  
Java.intOf(0xFF);  
```  
  
### `Java.floatArray(size)`  
- Description: Creates a Java float array with a given size, the array is filled with 0's   
by default and can be filled with only floats  
- Parameter - Number (`size`): the size of the array  
- Returns - Java: the Java float array  
- Example:  
```kt  
Java.floatArray(10);  
```  
  
### `Java.booleanArray(size)`  
- Description: Creates a Java boolean array with a given size, the array is filled with false   
by default and can be filled with only booleans  
- Parameter - Number (`size`): the size of the array  
- Returns - Java: the Java boolean array  
- Example:  
```kt  
Java.booleanArray(10);  
```  
  
### `Java.doubleArray(size)`  
- Description: Creates a Java double array with a given size, the array is filled with 0's   
by default and can be filled with only doubles  
- Parameter - Number (`size`): the size of the array  
- Returns - Java: the Java double array  
- Example:  
```kt  
Java.doubleArray(10);  
```  
  
### `Java.byteOf(num)`  
- Description: Creates a Java value byte, to be used in Java since bytes cannot be explicitly declared in Arucas  
- Parameter - Number (`num`): the number to convert to a Java byte  
- Returns - Java: the byte in Java wrapper  
- Example:  
```kt  
Java.byteOf(0xFF);  
```  
  
### `Java.valueOf(value)`  
- Description: Converts any Arucas value into a Java value then wraps it in the Java wrapper and returns it  
- Parameter - Value (`value`): any value to get the Java value of  
- Example:  
```kt  
Java.valueOf('Hello World!');  
```  
  
### `Java.byteArray(size)`  
- Description: Creates a Java byte array with a given size, the array is filled with 0's   
by default and can be filled with only bytes  
- Parameter - Number (`size`): the size of the array  
- Returns - Java: the Java byte array  
- Example:  
```kt  
Java.byteArray(10);  
```  
  
### `Java.longOf(num)`  
- Description: Creates a Java value long, to be used in Java since longs cannot be explicitly declared in Arucas  
- Parameter - Number (`num`): the number to convert to a Java long  
- Returns - Java: the long in Java wrapper  
- Example:  
```kt  
Java.longOf(1000000000.0);  
```  
  
### `Java.arrayOf(values...)`  
- Description: Creates a Java Object array with a given values, this will be the size of the array,   
again this cannot be used to create primitive arrays  
- Parameter - Value (`values...`): the values to add to the array  
- Returns - Java: the Java Object array  
- Example:  
```kt  
Java.arrayOf(1, 2, 3, 'string!', false);  
```  
  
### `Java.arrayWithSize(size)`  
- Description: Creates a Java Object array with a given size, the array is filled with null values   
by default and can be filled with any Java values, this array cannot be expanded  
- Parameter - Number (`size`): the size of the array  
- Returns - Java: the Java Object array  
- Example:  
```kt  
Java.arrayWithSize(10);  
```  
  
### `Java.booleanOf(bool)`  
- Description: Creates a Java value boolean, to be used in Java  
- Parameter - Boolean (`bool`): the boolean to convert to a Java boolean  
- Returns - Java: the boolean in Java wrapper  
- Example:  
```kt  
Java.booleanOf(true);  
```  
  
### `Java.intArray(size)`  
- Description: Creates a Java int array with a given size, the array is filled with 0's   
by default and can be filled with only ints  
- Parameter - Number (`size`): the size of the array  
- Returns - Java: the Java int array  
- Example:  
```kt  
Java.intArray(10);  
```  
  
### `Java.callStaticMethod(className, methodName, parameters...)`  
- Description: Calls a static method of a Java class, this is slower than delegating a method, but better for a one off call  
- Parameters:  
  - String (`className`): the name of the class  
  - String (`methodName`): the name of the method  
  - Value (`parameters...`): any parameters to call the method with, this can be none, a note - if you are calling a VarArg method then you must have your VarArg parameters in a Java Object array  
- Returns - Java: the return value of the method wrapped in the Java wrapper  
- Throws - Error:  
  - `'First parameter must be a class name and the second parameter must be a method name'`  
  - `'No such class with ...'`  
  - `'No such method ... with ... parameters exists for ...'`  
- Example:  
```kt  
Java.callStaticMethod('java.lang.Integer', 'parseInt', '123');  
```  
  
### `Java.setStaticField(className, fieldName, newValue)`  
- Description: Sets a static field in a Java class with a new value, the type of the new value needs to match the type of the field,   
you can pass in Java wrapped values to guarantee type matching, they will be unwrapped, regular values will be converted  
- Parameters:  
  - String (`className`): the name of the class  
  - String (`fieldName`): the name of the field  
  - Value (`newValue`): the new value  
- Throws - Error:  
  - `'No such class with ...'`  
- Example:  
```kt  
// Obviously this won't work, but it's just an example  
Java.setStaticField('java.lang.Integer', 'MAX_VALUE', Java.intOf(100));"  
```  
  
### `Java.getStaticMethodDelegate(className, methodName, parameters)`  
- Description: Gets a static method delegate from a Java class, delegating the method is much faster than directly calling it since it uses MethodHandles,   
if you are repetitively calling a static method you should delegate it and call that delegate  
- Parameters:  
  - String (`className`): the name of the class  
  - String (`methodName`): the name of the method  
  - Number (`parameters`): the number of parameters  
- Returns - Function: the delegated Java method in an Arucas Function  
- Throws - Error:  
  - `'No such class with ...'`  
  - `'No such method ... with ... parameters can be found'`  
- Example:  
```kt  
Java.getStaticMethodDelegate('java.lang.Integer', 'parseInt', 1);  
```  
  
### `Java.consumerOf(function)`  
- Description: Creates a Java Consumer object from a given function  
- Parameter - Function (`function`): the function to be executed, this must have one parameter and any return values will be ignored, the parameter type is unknown at compile time  
- Returns - Java: the Java Consumer object  
- Example:  
```kt  
Java.consumerOf(fun(something) {  
 print(something);});  
```  
  
  
# Json class  
Json class for Arucas.  
  
This class allows you to create and manipulate JSON objects.  
  
Import with `import Json from util.Json;`  
  
Fully Documented.  
  
## Methods  
  
### `<Json>.writeToFile(file)`  
- Description: This writes the Json to a file  
- Parameter - File (`file`): the file that you want to write to  
- Throws - Error:  
  - `'There was an error writing the file: ...'`  
- Example:  
```kt  
json.writeToFile(new File('D:/cool/realDirectory'));  
```  
  
### `<Json>.getValue()`  
- Description: This converts the Json back into a Value  
- Returns - Value: the Value parsed from the Json  
- Example:  
```kt  
json.getValue();  
```  
  
## Static Methods  
  
### `Json.fromMap(map)`  
- Description: This converts a map into a Json, an important thing to note is that  
any values that are not Numbers, Booleans, Lists, Maps, or Null will use their  
toString() member to convert them to a string  
- Parameter - Map (`map`): the map that you want to parse into a Json  
- Returns - Json: the Json parsed from the map  
- Example:  
```kt  
Json.fromMap({'key': ['value1', 'value2']});  
```  
  
### `Json.fromList(list)`  
- Description: This converts a list into a Json, an important thing to note is that  
any values that are not Numbers, Booleans, Lists, Maps, or Null will use their  
toString() member to convert them to a string  
- Parameter - List (`list`): the list that you want to parse into a Json  
- Returns - Json: the Json parsed from the list  
- Example:  
```kt  
Json.fromList(['value', 1, true]);  
```  
  
### `Json.fromString(string)`  
- Description: This converts a string into a Json provided it is formatted correctly  
- Parameter - String (`string`): the string that you want to parse into a Json  
- Returns - Json: the Json parsed from the string  
- Throws - Error:  
  - `'Json could not be parsed'`  
- Example:  
```kt  
Json.fromString('{"key":"value"}');  
```  
  
  
# KeyBind class  
KeyBind class for Arucas.  
  
This class allows you to create key binds that can be used, everything is  
handled for you internally so you just need to regers the key bind and  
the function you want to run when it is pressed.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Members  
  
### `<KeyBind>.callback`  
- Description: The callback function that is called when the key bind is pressed  
- Type: Function  
- Assignable: false  
- Example:  
```kt  
keyBind.callback;  
```  
  
## Constructors  
  
### `new KeyBind(keyName)`  
- Description: Creates a new key bind  
- Parameter - String (`keyName`): the name of the key  
- Example:  
```kt  
new KeyBind('MyKey');  
```  
  
## Methods  
  
### `<KeyBind>.getKey()`  
- Description: Gets the key bind's key  
- Returns - String: the key bind's key  
- Example:  
```kt  
keyBind.getKey();  
```  
  
### `<KeyBind>.setCallback(callback)`  
- Description: Sets the callback function for the key bind  
- Parameter - Function (`callback`): the callback function  
- Example:  
```kt  
keyBind.setCallback(fun() { print('My key was pressed'); });  
```  
  
### `<KeyBind>.setKey(keyName)`  
- Description: Sets the key bind to a new key  
- Parameter - String (`keyName`): the name of the key  
- Example:  
```kt  
keyBind.setKey('f');  
```  
  
  
  
# LineShape class  
LineShape class for Arucas.  
  
This class allows you to create a line shape which can be used to draw lines in the world.  
  
Import with `import LineShape from Minecraft;`  
  
Fully Documented.  
  
## Members  
  
### `<LineShape>.pos1`  
- Description: The first position of the shape  
- Type: Pos  
- Assignable: false  
- Example:  
```kt  
shape.pos1;  
```  
### `<LineShape>.pos2`  
- Description: The second position of the shape  
- Type: Pos  
- Assignable: false  
- Example:  
```kt  
shape.pos2;  
```  
  
## Constructors  
  
### `new LineShape(pos1, pos2)`  
- Description: Creates a new line shape  
- Parameters:  
  - Pos (`pos1`): The starting position of the line  
  - Pos (`pos2`): The ending position of the line  
- Example:  
```kt  
new LineShape(new Pos(0, 0, 0), new Pos(1, 1, 1));  
```  
### `new LineShape(x1, y1, z1, x2, y2, z2)`  
- Description: Creates a new line shape  
- Parameters:  
  - Number (`x1`): The x position of the starting position of the line  
  - Number (`y1`): The y position of the starting position of the line  
  - Number (`z1`): The z position of the starting position of the line  
  - Number (`x2`): The x position of the ending position of the line  
  - Number (`y2`): The y position of the ending position of the line  
  - Number (`z2`): The z position of the ending position of the line  
- Example:  
```kt  
new LineShape(0, 0, 0, 1, 1, 1);  
```  
  
## Methods  
  
### `<LineShape>.setColour(colour)`  
- Description: This sets the colour of the shape, using a single value, this  
function also has a sibling named `setColor()` that has the same functionality  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setColour(0xFF0000);  
```  
  
### `<LineShape>.setColour(red, green, blue)`  
- Description: This sets the colour of the shape, using three values this function  
also has a sibling named `setColor()` that has the same functionality  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setColour(34, 55, 0);  
```  
  
### `<LineShape>.setRenderThroughBlocks(boolean)`  
- Description: This sets whether the shape should render through blocks  
- Parameter - Boolean (`boolean`): whether the shape should render through blocks  
- Example:  
```kt  
shape.setRenderThroughBlocks(true);  
```  
  
### `<LineShape>.setZScale(zScale)`  
- Description: This sets the z scale of the shape  
- Parameter - Number (`zScale`): the z scale of the shape  
- Example:  
```kt  
shape.setZScale(3.5);  
```  
  
### `<LineShape>.setGreen(green)`  
- Description: This sets the green value of the shape, using a single value  
- Parameter - Number (`green`): the amount of green between 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setGreen(34);  
```  
  
### `<LineShape>.setOutlineGreen(green)`  
- Description: This sets the outline green value of the shape, using a single value  
- Parameter - Number (`green`): the amount of green between 0 - 255  
- Example:  
```kt  
shape.setOutlineGreen(34);  
```  
  
### `<LineShape>.setRed(red)`  
- Description: This sets the red value of the shape, using a single value  
- Parameter - Number (`red`): the amount of red between 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setRed(34);  
```  
  
### `<LineShape>.getYTilt()`  
- Description: This gets the y tilt of the shape  
- Returns - Number: the y tilt  
- Example:  
```kt  
shape.getYTilt();  
```  
  
### `<LineShape>.getOpacity()`  
- Description: This returns the opacity of the shape  
- Returns - Number: the opacity of the shape  
- Example:  
```kt  
shape.getOpacity();  
```  
  
### `<LineShape>.setPos1(pos1)`  
- Description: This sets the first position of the shape  
- Parameter - Pos (`pos1`): the first position of the shape  
- Example:  
```kt  
shape.setPos1(new Pos(1, 0, 100));  
```  
  
### `<LineShape>.centerPositions()`  
- Description: This centers the positions of the shape  
- Example:  
```kt  
shape.centerPositions();  
```  
  
### `<LineShape>.getRed()`  
- Description: This returns the red value of the shape  
- Returns - Number: the red value of the shape  
- Example:  
```kt  
shape.getRed();  
```  
  
### `<LineShape>.getRGBList()`  
- Description: This returns the RGB value of the shape as a list  
- Returns - List: the RGB value of the shape as a list in the form [red, green, blue]  
- Example:  
```kt  
r, g, b = shape.getRGBList();  
```  
  
### `<LineShape>.setBlue(blue)`  
- Description: This sets the blue value of the shape, using a single value  
- Parameter - Number (`blue`): the amount of blue between 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setBlue(34);  
```  
  
### `<LineShape>.stopRendering()`  
- Description: This stops the shape from rendering  
- Example:  
```kt  
shape.stopRendering();  
```  
  
### `<LineShape>.setOutlinePixelWidth(width)`  
- Description: This sets the outline pixel width of the shape, using a single value  
- Parameter - Number (`width`): the width of the outline in pixels  
- Example:  
```kt  
shape.setOutlinePixelWidth(5);  
```  
  
### `<LineShape>.setYScale(yScale)`  
- Description: This sets the y scale of the shape  
- Parameter - Number (`yScale`): the y scale of the shape  
- Example:  
```kt  
shape.setYScale(2.5);  
```  
  
### `<LineShape>.getYScale()`  
- Description: This gets the y scale of the shape  
- Example:  
```kt  
shape.getYScale();  
```  
  
### `<LineShape>.getRGBAList()`  
- Description: This returns the RGBA value of the shape as a list  
- Returns - List: the RGBA value of the shape as a list in the form [red, green, blue, opacity]  
- Example:  
```kt  
r, g, b, a = shape.getRGBAList();  
```  
  
### `<LineShape>.getZTilt()`  
- Description: This gets the z tilt of the shape  
- Returns - Number: the z tilt  
- Example:  
```kt  
shape.getZTilt();  
```  
  
### `<LineShape>.render()`  
- Description: This sets the shape to be rendered indefinitely, the shape will only stop rendering when the script ends or when you call the stopRendering() method  
- Example:  
```kt  
shape.render();  
```  
  
### `<LineShape>.setZTilt(zTilt)`  
- Description: This sets the z tilt of the shape  
- Parameter - Number (`zTilt`): the z tilt  
- Example:  
```kt  
shape.setZTilt(100);  
```  
  
### `<LineShape>.getRGB()`  
- Description: This returns the RGB value of the shape  
- Returns - Number: the RGB value of the shape as a single number in the form 0xRRGGBB  
- Example:  
```kt  
shape.getRGB();  
```  
  
### `<LineShape>.getZScale()`  
- Description: This gets the z scale of the shape  
- Example:  
```kt  
shape.getZScale();  
```  
  
### `<LineShape>.setXScale(xScale)`  
- Description: This sets the x scale of the shape  
- Parameter - Number (`xScale`): the x scale of the shape  
- Example:  
```kt  
shape.setXScale(1.5);  
```  
  
### `<LineShape>.setScale(xScale, yScale, zScale)`  
- Description: This sets the scale of the shape  
- Parameters:  
  - Number (`xScale`): the x scale of the shape  
  - Number (`yScale`): the y scale of the shape  
  - Number (`zScale`): the z scale of the shape  
- Example:  
```kt  
shape.setScale(1.5, 2.5, 3.5);  
```  
  
### `<LineShape>.setOutlineRed(red)`  
- Description: This sets the outline red value of the shape, using a single value  
- Parameter - Number (`red`): the amount of red between 0 - 255  
- Example:  
```kt  
shape.setOutlineRed(34);  
```  
  
### `<LineShape>.setYTilt(yTilt)`  
- Description: This sets the y tilt of the shape  
- Parameter - Number (`yTilt`): the y tilt  
- Example:  
```kt  
shape.setYTilt(100);  
```  
  
### `<LineShape>.shouldRenderThroughBlocks()`  
- Description: This returns whether the shape should render through blocks  
- Returns - Boolean: whether the shape should render through blocks  
- Example:  
```kt  
shape.shouldRenderThroughBlocks();  
```  
  
### `<LineShape>.getBlue()`  
- Description: This returns the blue value of the shape  
- Returns - Number: the blue value of the shape  
- Example:  
```kt  
shape.getBlue();  
```  
  
### `<LineShape>.setPos2(pos2)`  
- Description: This sets the second position of the shape  
- Parameter - Pos (`pos2`): the second position of the shape  
- Example:  
```kt  
shape.setPos2(new Pos(100, 0, 200));  
```  
  
### `<LineShape>.setTilt(xTilt, yTilt, zTilt)`  
- Description: This sets the tilt of the shape  
- Parameters:  
  - Number (`xTilt`): the x tilt  
  - Number (`yTilt`): the y tilt  
  - Number (`zTilt`): the z tilt  
- Example:  
```kt  
shape.setTilt(100, 0, 80);  
```  
  
### `<LineShape>.setColor(colour)`  
- Description: This sets the colour of the shape, using a single value, this  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setColor(0xFF0000);  
```  
  
### `<LineShape>.setColor(red, green, blue)`  
- Description: This sets the colour of the shape, using three values this function  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setColor(34, 55, 0);  
```  
  
### `<LineShape>.setOutlineBlue(blue)`  
- Description: This sets the outline blue value of the shape, using a single value  
- Parameter - Number (`blue`): the amount of blue between 0 - 255  
- Example:  
```kt  
shape.setOutlineBlue(34);  
```  
  
### `<LineShape>.setOutlineColour(colour)`  
- Description: This sets the width of the shape, using a single value, this function  
also has a sibling named `setOutlineColor()` that has the same functionality  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setOutlineColour(0xFF00FF);  
```  
  
### `<LineShape>.setOutlineColour(red, green, blue)`  
- Description: This sets the outline colour of the shape, using three values, this function  
also has a sibling named `setOutlineColor()` that has the same functionality  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Example:  
```kt  
shape.setOutlineColour(255, 0, 255);  
```  
  
### `<LineShape>.getGreen()`  
- Description: This returns the green value of the shape  
- Returns - Number: the green value of the shape  
- Example:  
```kt  
shape.getGreen();  
```  
  
### `<LineShape>.getXScale()`  
- Description: This gets the x scale of the shape  
- Example:  
```kt  
shape.getXScale();  
```  
  
### `<LineShape>.setOutlineColor(colour)`  
- Description: This sets the width of the shape, using a single value, this function  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setOutlineColor(0xFF00FF);  
```  
  
### `<LineShape>.setOutlineColor(red, green, blue)`  
- Description: This sets the outline colour of the shape, using three values, this function  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Example:  
```kt  
shape.setOutlineColor(255, 0, 255);  
```  
  
### `<LineShape>.setXTilt(xTilt)`  
- Description: This sets the x tilt of the shape  
- Parameter - Number (`xTilt`): the x tilt  
- Example:  
```kt  
shape.setXTilt(100);  
```  
  
### `<LineShape>.getXTilt()`  
- Description: This gets the x tilt of the shape  
- Returns - Number: the x tilt  
- Example:  
```kt  
shape.getXTilt();  
```  
  
### `<LineShape>.setOpacity(alpha)`  
- Description: This sets the opacity of the shape, using a single value  
- Parameter - Number (`alpha`): the opacity, where 255 is solid colour and 0 is no colour  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setOpacity(34);  
```  
  
  
  
# List class  
List class for Arucas.  
  
This class cannot be constructed since it has a literal, `[]`  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<List>.set(value, index)`  
- Description: This allows you to set the value at a specific index  
- Parameters:  
  - Value (`value`): the value you want to set  
  - Number (`index`): the index you want to set the value at  
- Returns - List: the list  
- Throws - Error:  
  - `'Index is out of bounds'`  
- Example:  
```kt  
`['object', 81, 96, 'case'].set('foo', 1);`  
```  
  
### `<List>.containsAll(collection)`  
- Description: This allows you to check if the list contains all the values in a collection  
- Parameter - Collection (`collection`): the collection you want to check for  
- Returns - Boolean: true if the list contains all the values in the collection, false otherwise  
- Throws - Error:  
  - `'... is not a collection'`  
- Example:  
```kt  
`['object', 81, 96, 'case'].containsAll(['foo', 'bar']);`  
```  
  
### `<List>.clear()`  
- Description: This allows you to clear all the values the list  
- Example:  
```kt  
`['object', 81, 96, 'case'].clear();`  
```  
  
### `<List>.isEmpty()`  
- Description: This allows you to check if the list is empty  
- Returns - Boolean: true if the list is empty, false otherwise  
- Example:  
```kt  
`['object', 81, 96, 'case'].isEmpty();`  
```  
  
### `<List>.insert(value, index)`  
- Description: This allows you to insert a value at a specific index  
- Parameters:  
  - Value (`value`): the value you want to insert  
  - Number (`index`): the index you want to insert the value at  
- Returns - List: the list  
- Throws - Error:  
  - `'Index is out of bounds'`  
- Example:  
```kt  
`['object', 81, 96, 'case'].insert('foo', 1);`  
```  
  
### `<List>.concat(otherList)`  
- Deprecated: You should use `<List>.addAll(collection)` instead  
- Description: This allows you to concatenate two lists  
- Parameter - List (`otherList`): the list you want to concatenate with  
- Returns - List: the concatenated list  
- Example:  
```kt  
`['object', 81, 96, 'case'].concat(['foo', 'bar']);`  
```  
  
### `<List>.remove(index)`  
- Description: This allows you to remove the value at a specific index  
- Parameter - Number (`index`): the index of the value you want to remove  
- Returns - Value: the value that was removed  
- Throws - Error:  
  - `'Index is out of bounds'`  
- Example:  
```kt  
`['object', 81, 96, 'case'].remove(1);`  
```  
  
### `<List>.contains(value)`  
- Description: This allows you to check if the list contains a value  
- Parameter - Value (`value`): the value you want to check for  
- Returns - Boolean: true if the list contains the value, false otherwise  
- Example:  
```kt  
`['object', 81, 96, 'case'].contains('foo');`  
```  
  
### `<List>.addAll(collection)`  
- Description: This allows you to add all the values in a collection to the list  
- Parameter - Collection (`collection`): the collection you want to add  
- Returns - List: the list  
- Throws - Error:  
  - `'... is not a collection'`  
- Example:  
```kt  
`['object', 81, 96, 'case'].addAll(['foo', 'bar']);`  
```  
  
### `<List>.get(index)`  
- Description: This allows you to get the value at a specific index  
- Parameter - Number (`index`): the index of the value you want to get  
- Returns - Value: the value at the index  
- Throws - Error:  
  - `'Index is out of bounds'`  
- Example:  
```kt  
`['object', 81, 96, 'case'].get(1);`  
```  
  
### `<List>.toString()`  
- Description: This converts the list to a string and evaluating any collections inside it  
- Returns - String: the string representation of the set  
- Example:  
```kt  
`['object', 81, 96, 'case'].toString();`  
```  
  
### `<List>.indexOf(value)`  
- Description: This allows you to get the index of a value in the list  
- Parameter - Value (`value`): the value you want to check for  
- Returns - Number: the index of the value, -1 if the value is not in the list  
- Example:  
```kt  
`['object', 81, 96, 'case'].indexOf('case');`  
```  
  
### `<List>.append(value)`  
- Description: This allows you to append a value to the end of the list  
- Parameter - Value (`value`): the value you want to append  
- Returns - List: the list  
- Example:  
```kt  
`['object', 81, 96, 'case'].append('foo');`  
```  
  
  
  
# LivingEntity class  
LivingEntity class for Arucas.  
  
This class extends Entity and so inherits all of their methods too,  
LivingEntities are any entities that are alive, so all mobs  
  
Import with `import LivingEntity from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<LivingEntity>.isFlyFalling()`  
- Description: This checks if the LivingEntity is fly falling (gliding with elytra)  
- Returns - Boolean: true if the LivingEntity is fly falling  
- Example:  
```kt  
livingEntity.isFlyFalling();  
```  
  
### `<LivingEntity>.getStatusEffects()`  
- Description: This gets the LivingEntity's status effects, you can find  
a list of all the ids of the status effects  
[here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Effects)  
- Returns - List: a list of status effects, may be empty  
- Example:  
```kt  
livingEntity.getStatusEffects();  
```  
  
### `<LivingEntity>.getHealth()`  
- Description: This gets the LivingEntity's current health  
- Returns - Number: the LivingEntity's health  
- Example:  
```kt  
livingEntity.getHealth();  
```  
  
  
  
# Map class  
Map class for Arucas.  
  
This class cannot be constructed since it has a literal, `{}`  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<Map>.getValues()`  
- Description: This allows you to get the values in the map  
- Returns - List: a complete list of all the values  
- Example:  
```kt  
{'key': 'value', 'key2', 'value2'}.getValues();  
```  
  
### `<Map>.containsKey(key)`  
- Description: This allows you to check if the map contains a specific key  
- Parameter - Value (`key`): the key you want to check  
- Returns - Boolean: true if the map contains the key, false otherwise  
- Example:  
```kt  
{'key': 'value'}.containsKey('key');  
```  
  
### `<Map>.putAll(another map)`  
- Description: This allows you to put all the keys and values of another map into this map  
- Parameter - Map (`another map`): the map you want to merge into this map  
- Example:  
```kt  
{'key': 'value'}.putAll({'key2': 'value2'});  
```  
  
### `<Map>.get(key)`  
- Description: This allows you to get the value of a key in the map  
- Parameter - Value (`key`): the key you want to get the value of  
- Returns - Value: the value of the key, will return null if non-existent  
- Example:  
```kt  
{'key': 'value'}.get('key');  
```  
  
### `<Map>.isEmpty()`  
- Description: This allows you to check if the map is empty  
- Returns - Boolean: true if the map is empty, false otherwise  
- Example:  
```kt  
{'key': 'value'}.isEmpty();  
```  
  
### `<Map>.clear()`  
- Description: This allows you to clear the map of all the keys and values  
- Example:  
```kt  
{'key': 'value'}.clear();  
```  
  
### `<Map>.toString()`  
- Description: This allows you to get the string representation of the map and evaluating any collections inside it  
- Returns - String: the string representation of the map  
- Example:  
```kt  
{'key': []}.toString();  
```  
  
### `<Map>.getKeys()`  
- Description: This allows you to get the keys in the map  
- Returns - List: a complete list of all the keys  
- Example:  
```kt  
{'key': 'value', 'key2', 'value2'}.getKeys();  
```  
  
### `<Map>.putIfAbsent(key, value)`  
- Description: This allows you to put a key and value in the map if it doesn't exist  
- Parameters:  
  - Value (`key`): the key you want to put  
  - Value (`value`): the value you want to put  
- Returns - Value: the previous value associated with the key, null if none  
- Example:  
```kt  
{'key': 'value'}.putIfAbsent('key2', 'value2');  
```  
  
### `<Map>.remove(key)`  
- Description: This allows you to remove a key and its value from the map  
- Parameter - Value (`key`): the key you want to remove  
- Returns - Value: the value associated with the key, null if none  
- Example:  
```kt  
{'key': 'value'}.remove('key');  
```  
  
### `<Map>.put(key, value)`  
- Description: This allows you to put a key and value in the map  
- Parameters:  
  - Value (`key`): the key you want to put  
  - Value (`value`): the value you want to put  
- Returns - Value: the previous value associated with the key, null if none  
- Example:  
```kt  
{'key': 'value'}.put('key2', 'value2');  
```  
  
## Static Methods  
  
### `Map.unordered()`  
- Description: This function allows you to create an unordered map  
- Returns - Map: an unordered map  
- Example:  
```kt  
Map.unordered();  
```  
  
  
# Material class  
Material class for Arucas.  
  
This class represents all possible item and block types  
and allows you to convert them into instances of ItemStacks and Blocks  
  
Import with `import Material from Minecraft;`  
  
Fully Documented.  
  
## Static Members  
  
### `Material.ALL`  
- Description: This is a list of all materials in the game, including items and blocks, each material also has it's own member  
- Type: Material  
- Assignable: false  
- Example:  
```kt  
Material.ALL;  
```  
  
## Methods  
  
### `<Material>.getTranslatedName()`  
- Description: This gets the translated name of the ItemStack, for example:   
Material.DIAMOND_SWORD would return 'Diamond Sword' if your language is English  
- Returns - String: the translated name of the Material  
- Example:  
```kt  
material.getTranslatedName();  
```  
  
### `<Material>.asBlock()`  
- Description: This converts the material into a Block  
- Returns - Block: the Block representation of the material  
- Throws - Error:  
  - `'Material cannot be converted to a block'`  
- Example:  
```kt  
material.asBlock();  
```  
  
### `<Material>.getFullId()`  
- Description: This returns the full id of the material, for example: 'minecraft:diamond'  
- Returns - String: the full id representation of the material  
- Example:  
```kt  
material.getFullId();  
```  
  
### `<Material>.getId()`  
- Description: This returns the id of the material, for example: 'diamond'  
- Returns - String: the id representation of the material  
- Example:  
```kt  
material.getId();  
```  
  
### `<Material>.asItemStack()`  
- Description: This converts the material into an ItemStack  
- Returns - ItemStack: the ItemStack representation of the material  
- Throws - Error:  
  - `'Material cannot be converted to an item stack'`  
- Example:  
```kt  
material.asItemStack();  
```  
  
## Static Methods  
  
### `Material.of(id)`  
- Description: This converts a block or item id into a Material  
- Parameter - String (`id`): the id of the block or item  
- Returns - Material: the material instance from the id  
- Throws - Error:  
  - `'... is not a valid Material'`  
- Example:  
```kt  
Material.of('diamond');  
```  
  
  
# Math class  
Math class for Arucas.  
  
Provides many basic math functions. This is a utility class, and cannot be constructed.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Static Members  
  
### `Math.root2`  
- Description: The value of root 2  
- Type: Number  
- Assignable: false  
- Example:  
```kt  
Math.root2;  
```  
### `Math.pi`  
- Description: The value of pi  
- Type: Number  
- Assignable: false  
- Example:  
```kt  
Math.pi;  
```  
### `Math.e`  
- Description: The value of e  
- Type: Number  
- Assignable: false  
- Example:  
```kt  
Math.e;  
```  
  
## Static Methods  
  
### `Math.tan(num)`  
- Description: Returns the tangent of a number  
- Parameter - Number (`num`): the number to get the tangent of  
- Returns - Number: the tangent of the number  
- Example:  
```kt  
Math.tan(Math.pi);  
```  
  
### `Math.cosec(num)`  
- Description: Returns the cosecant of a number  
- Parameter - Number (`num`): the number to get the cosecant of  
- Returns - Number: the cosecant of the number  
- Example:  
```kt  
Math.cosec(Math.pi);  
```  
  
### `Math.mod(num1, num2)`  
- Description: Returns the modulus of a division  
- Parameters:  
  - Number (`num1`): the number to divide  
  - Number (`num2`): the divisor  
- Returns - Number: the modulus of the division  
- Example:  
```kt  
Math.mod(5, 2);  
```  
  
### `Math.max(num1, num2)`  
- Description: Returns the largest number  
- Parameters:  
  - Number (`num1`): the first number to compare  
  - Number (`num2`): the second number to compare  
- Returns - Number: the largest number  
- Example:  
```kt  
Math.max(5, 2);  
```  
  
### `Math.log(num)`  
- Description: Returns the natural logarithm of a number  
- Parameter - Number (`num`): the number to get the logarithm of  
- Returns - Number: the natural logarithm of the number  
- Example:  
```kt  
Math.log(Math.e);  
```  
  
### `Math.log(base, num)`  
- Description: Returns the logarithm of a number with a specified base  
- Parameters:  
  - Number (`base`): the base  
  - Number (`num`): the number to get the logarithm of  
- Returns - Number: the logarithm of the number  
- Example:  
```kt  
Math.log(2, 4);  
```  
  
### `Math.log10(num)`  
- Description: Returns the base 10 logarithm of a number  
- Parameter - Number (`num`): the number to get the logarithm of  
- Returns - Number: the base 10 logarithm of the number  
- Example:  
```kt  
Math.log10(100);  
```  
  
### `Math.cos(num)`  
- Description: Returns the cosine of a number  
- Parameter - Number (`num`): the number to get the cosine of  
- Returns - Number: the cosine of the number  
- Example:  
```kt  
Math.cos(Math.pi);  
```  
  
### `Math.cot(num)`  
- Description: Returns the cotangent of a number  
- Parameter - Number (`num`): the number to get the cotangent of  
- Returns - Number: the cotangent of the number  
- Example:  
```kt  
Math.cot(Math.pi);  
```  
  
### `Math.toDegrees(num)`  
- Description: Converts a number from radians to degrees  
- Parameter - Number (`num`): the number to convert  
- Returns - Number: the number in degrees  
- Example:  
```kt  
Math.toDegrees(Math.pi);  
```  
  
### `Math.ceil(num)`  
- Description: Rounds a number up to the nearest integer  
- Parameter - Number (`num`): the number to round  
- Returns - Number: the rounded number  
- Example:  
```kt  
Math.ceil(3.5);  
```  
  
### `Math.toRadians(num)`  
- Description: Converts a number from degrees to radians  
- Parameter - Number (`num`): the number to convert  
- Returns - Number: the number in radians  
- Example:  
```kt  
Math.toRadians(90);  
```  
  
### `Math.arccos(num)`  
- Description: Returns the arc cosine of a number  
- Parameter - Number (`num`): the number to get the arc cosine of  
- Returns - Number: the arc cosine of the number  
- Example:  
```kt  
Math.arccos(Math.cos(Math.pi));  
```  
  
### `Math.sec(num)`  
- Description: Returns the secant of a number  
- Parameter - Number (`num`): the number to get the secant of  
- Returns - Number: the secant of the number  
- Example:  
```kt  
Math.sec(Math.pi);  
```  
  
### `Math.abs(num)`  
- Description: Returns the absolute value of a number  
- Parameter - Number (`num`): the number to get the absolute value of  
- Returns - Number: the absolute value of the number  
- Example:  
```kt  
Math.abs(-3);  
```  
  
### `Math.min(num1, num2)`  
- Description: Returns the smallest number  
- Parameters:  
  - Number (`num1`): the first number to compare  
  - Number (`num2`): the second number to compare  
- Returns - Number: the smallest number  
- Example:  
```kt  
Math.min(5, 2);  
```  
  
### `Math.round(num)`  
- Description: Rounds a number to the nearest integer  
- Parameter - Number (`num`): the number to round  
- Returns - Number: the rounded number  
- Example:  
```kt  
Math.round(3.5);  
```  
  
### `Math.arctan(num)`  
- Description: Returns the arc tangent of a number  
- Parameter - Number (`num`): the number to get the arc tangent of  
- Returns - Number: the arc tangent of the number  
- Example:  
```kt  
Math.arctan(Math.tan(Math.pi));  
```  
  
### `Math.sqrt(num)`  
- Description: Returns the square root of a number  
- Parameter - Number (`num`): the number to square root  
- Returns - Number: the square root of the number  
- Example:  
```kt  
Math.sqrt(9);  
```  
  
### `Math.sin(num)`  
- Description: Returns the sine of a number  
- Parameter - Number (`num`): the number to get the sine of  
- Returns - Number: the sine of the number  
- Example:  
```kt  
Math.sin(Math.pi);  
```  
  
### `Math.rem(num1, num2)`  
- Description: Returns the remainder of a division  
- Parameters:  
  - Number (`num1`): the number to divide  
  - Number (`num2`): the divisor  
- Returns - Number: the remainder of the division  
- Example:  
```kt  
Math.rem(5, 2);  
```  
  
### `Math.floor(num)`  
- Description: Rounds a number down to the nearest integer  
- Parameter - Number (`num`): the number to round  
- Returns - Number: the rounded number  
- Example:  
```kt  
Math.floor(3.5);  
```  
  
### `Math.arcsin(num)`  
- Description: Returns the arc sine of a number  
- Parameter - Number (`num`): the number to get the arc sine of  
- Returns - Number: the arc sine of the number  
- Example:  
```kt  
Math.arcsin(Math.sin(Math.pi));  
```  
  
### `Math.clamp(value, min, max)`  
- Description: Clamps a value between a minimum and maximum  
- Parameters:  
  - Number (`value`): the value to clamp  
  - Number (`min`): the minimum  
  - Number (`max`): the maximum  
- Returns - Number: the clamped value  
- Example:  
```kt  
Math.clamp(10, 2, 8);  
```  
  
  
# MerchantScreen class  
MerchantScreen class for Arucas.  
  
This class extends Screen and so inherits all of their methods too,  
this class is used to add functionality to trading screens.  
  
Import with `import MerchantScreen from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<MerchantScreen>.clearTrade()`  
- Description: This clears the currently selected trade  
- Throws - Error:  
  - `'Not in merchant gui'`  
- Example:  
```kt  
screen.clearTrade();  
```  
  
### `<MerchantScreen>.isTradeSelected()`  
- Description: This returns true if a trade is selected  
- Returns - Boolean: true if a trade is selected  
- Example:  
```kt  
screen.isTradeSelected();  
```  
  
### `<MerchantScreen>.isTradeDisabled(index)`  
- Description: This returns true if a trade is disabled at an index  
- Parameter - Number (`index`): the index of the trade  
- Returns - Boolean: true if a trade is disabled  
- Example:  
```kt  
screen.isTradeDisabled(1);  
```  
  
### `<MerchantScreen>.getVillagerProfession()`  
- Description: This gets the profession of the villager  
- Returns - String: the profession of the villager, for example: 'armorer', 'mason', 'weaponsmith'  
- Throws - Error:  
  - `'Merchant isn't a villager'`  
- Example:  
```kt  
screen.getVillagerProfession();  
```  
  
### `<MerchantScreen>.getTradeList()`  
- Description: This gets a list of all the merchant's trades  
- Returns - List: the list of all the Trades  
- Example:  
```kt  
screen.getTradeList();  
```  
  
### `<MerchantScreen>.tradeSelectedAndThrow()`  
- Description: This trades the currently selected trade and throws the items that were traded  
- Throws - Error:  
  - `'Not in merchant gui'`  
- Example:  
```kt  
screen.tradeSelectedAndThrow();  
```  
  
### `<MerchantScreen>.getTradeItemForIndex(index)`  
- Description: This gets the item stack of a trade at a certain index  
- Parameter - Number (`index`): the index of the trade  
- Returns - ItemStack: the item stack of the trade  
- Throws - Error:  
  - `'Not in merchant gui'`  
  - `'That trade is out of bounds'`  
- Example:  
```kt  
screen.getTradeItemForIndex(0);  
```  
  
### `<MerchantScreen>.tradeSelected()`  
- Description: This trades the currently selected trade  
- Throws - Error:  
  - `'Not in merchant gui'`  
- Example:  
```kt  
screen.tradeSelected();  
```  
  
### `<MerchantScreen>.getTradeListSize()`  
- Description: This gets the size of all the trades available  
- Returns - Number: the size of the trade list  
- Example:  
```kt  
screen.getTradeListSize();  
```  
  
### `<MerchantScreen>.selectTrade(index)`  
- Description: This selects the currently selected trade, as if you were to click it  
- Parameter - Number (`index`): the index of the trade  
- Throws - Error:  
  - `'Not in merchant gui'`  
- Example:  
```kt  
screen.selectTrade(0);  
```  
  
### `<MerchantScreen>.getPriceForIndex(index)`  
- Description: This gets the price of a trade at a certain index  
- Parameter - Number (`index`): the index of the trade  
- Returns - Number: the price of the trade  
- Throws - Error:  
  - `'Not in merchant gui'`  
  - `'That trade is out of bounds'`  
- Example:  
```kt  
screen.getPriceForIndex(0);  
```  
  
### `<MerchantScreen>.getVillagerLevel()`  
- Description: This gets the level of the villager  
- Returns - Number: the level of the villager  
- Throws - Error:  
  - `'Merchant isn't a villager'`  
- Example:  
```kt  
screen.getVillagerLevel();  
```  
  
### `<MerchantScreen>.getIndexOfTradeItem(materialLike)`  
- Description: This gets the index of a trade for a certain item  
- Parameter - MaterialLike (`materialLike`): the item to get the index of  
- Returns - Number: the index of the trade  
- Throws - Error:  
  - `'Not in merchant gui'`  
- Example:  
```kt  
screen.getIndexOfTradeItem(Material.DIAMOND_PICKAXE.asItemStack());  
```  
  
### `<MerchantScreen>.doesVillagerHaveTrade(materialLike)`  
- Description: This checks if the villager has a trade for a certain item  
- Parameter - MaterialLike (`materialLike`): the item or material to check for  
- Returns - Boolean: true if the villager has a trade for the item, false otherwise  
- Throws - Error:  
  - `'Not in merchant gui'`  
  - `'That trade is out of bounds'`  
- Example:  
```kt  
screen.doesVillagerHaveTrade(Material.DIAMOND_PICKAXE.asItemStack());  
```  
  
### `<MerchantScreen>.tradeIndex(index)`  
- Description: This makes your player trade with the merchant at a certain index  
- Parameter - Number (`index`): the index of the trade  
- Throws - Error:  
  - `'Not in merchant gui'`  
- Example:  
```kt  
screen.tradeIndex(0);  
```  
  
  
  
# MinecraftClient class  
MinecraftClient class for Arucas.  
  
This allows for many core interactions with the MinecraftClient  
  
Import with `import MinecraftClient from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<MinecraftClient>.getCursorStack()`  
- Description: This returns the item stack that is currently being held by the cursor  
- Returns - ItemStack: the item stack, will be Air if there is nothing  
- Example:  
```kt  
client.getCursorStack();  
```  
  
### `<MinecraftClient>.getWorld()`  
- Description: This returns the world that is currently being played on  
- Returns - World: the world  
- Example:  
```kt  
client.getWorld();  
```  
  
### `<MinecraftClient>.getPlayer()`  
- Description: This returns the current player on the client  
- Returns - Player: the main player  
- Example:  
```kt  
client.getPlayer();  
```  
  
### `<MinecraftClient>.getEssentialClientValue(ruleName)`  
- Description: This gets the value of the given client rule  
- Parameter - String (`ruleName`): the client rule  
- Returns - Value: the value of the client rule  
- Throws - Error:  
  - `'Invalid ClientRule name'`  
- Example:  
```kt  
client.getEssentialClientValue('overrideCreativeWalkSpeed');  
```  
  
### `<MinecraftClient>.createFakeScreen(screenName, rows)`  
- Deprecated: You should use 'new FakeScreen(string, rows)' instead  
- Description: This creates a fake screen with the given name and number of rows of slots available (1 - 6)  
- Parameters:  
  - String (`screenName`): the name of the screen  
  - Number (`rows`): number of rows  
- Returns - Value: the fake screen  
- Example:  
```kt  
client.createFakeScreen('Name', 3);  
```  
  
### `<MinecraftClient>.entityFromString(string)`  
- Deprecated: You should use 'Entity.of(string)' instead  
- Description: This creates an entity from the given string  
- Parameter - String (`string`): the string to parse  
- Returns - Value: the entity  
- Example:  
```kt  
client.entityFromString('pig');  
```  
  
### `<MinecraftClient>.runOnMainThread(function)`  
- Description: This runs the given function on the main thread  
- Parameter - Function (`function`): the function to run  
- Example:  
```kt  
client.runOnMainThread(fun() { print('Do something'); });  
```  
  
### `<MinecraftClient>.syncToTick()`  
- Description: Synchronizes the current thread in Arucas to the next game tick  
- Throws - Error:  
  - `'Tried to sync non Arucas Thread'`  
- Example:  
```kt  
client.syncToTick();  
```  
  
### `<MinecraftClient>.uuidFromPlayerName(name)`  
- Description: This will return the uuid from the given player name  
- Parameter - String (`name`): the player name  
- Returns - String: the uuid, null if the player name is not found  
- Example:  
```kt  
client.uuidFromPlayerName('senseiwells');  
```  
  
### `<MinecraftClient>.addCommand(command)`  
- Description: This allows you to register your own client side command in game  
- Parameter - Map (`command`): a command map or a command builder  
- Example:  
```kt  
client.addCommand({  
 "name": "example", "subcommands": { }, "arguments": { }});  
```  
  
### `<MinecraftClient>.releaseKey(key)`  
- Description: This allows you to simulate a key release inside of Minecraft, this  
is useful for keys that only work on release, for example `F3`  
- Parameter - String (`key`): the key to release  
- Throws - Error:  
  - `'Tried to press unknown key'`  
- Example:  
```kt  
client.releaseKey('f');  
```  
  
### `<MinecraftClient>.screenshot()`  
- Description: This makes the client take a screenshot  
- Example:  
```kt  
client.screenshot();  
```  
  
### `<MinecraftClient>.screenshot(name)`  
- Description: This makes the client take a screenshot and saves it with a given name  
- Parameter - String (`name`): the name of the file  
- Example:  
```kt  
client.screenshot('screenshot.png');  
```  
  
### `<MinecraftClient>.removeAllGameEvents()`  
- Deprecated: You should use 'GameEvent.unregisterAll()' instead  
- Description: This unregisters all game events  
- Example:  
```kt  
client.removeAllGameEvents();  
```  
  
### `<MinecraftClient>.getServerName()`  
- Description: This gets the current connected server's name that you have set it to in the multiplayer screen  
- Returns - String: the server name  
- Example:  
```kt  
client.getServerName();  
```  
  
### `<MinecraftClient>.getServerIp()`  
- Description: This will return the server ip  
- Returns - String: The server ip, null if in single player  
- Example:  
```kt  
client.getServerIp();  
```  
  
### `<MinecraftClient>.getClientRenderDistance()`  
- Description: This returns the current render distance set on the client  
- Returns - Number: the render distance  
- Example:  
```kt  
client.getClientRenderDistance();  
```  
  
### `<MinecraftClient>.setCursorStack(itemStack)`  
- Description: This sets the item stack that is currently being held by the cursor, this does not work  
in normal screens only in FakeScreens, this does not actually pick up an item just display like you have  
- Parameter - ItemStack (`itemStack`): the item stack to set  
- Example:  
```kt  
client.setCursorStack(Material.DIAMOND.asItemStack());  
```  
  
### `<MinecraftClient>.blockFromString(string)`  
- Deprecated: You should use 'Block.of(string)' instead  
- Description: This creates a block from the given string  
- Parameter - String (`string`): the string to parse  
- Returns - Value: the block  
- Example:  
```kt  
client.blockFromString('dirt');  
```  
  
### `<MinecraftClient>.playSound(soundId, volume, pitch)`  
- Description: This plays the given sound with the given volume and pitch around the player  
sound id's can be found [here](https://minecraft.fandom.com/wiki/Sounds.json#Sound_events)  
- Parameters:  
  - String (`soundId`): the sound id you want to play  
  - Number (`volume`): the volume of the sound  
  - Number (`pitch`): the pitch of the sound  
- Example:  
```kt  
client.playSound('entity.lightning_bolt.thunder', 1, 1);  
```  
  
### `<MinecraftClient>.sendScriptPacket(values...)`  
- Description: This sends a script packet to the server  
You can send the follow types of values:  
Boolean, Number, String, List (of numbers), Text, ItemStack, Pos, and NbtMaps  
You can send byte, int, and long arrays by using the strings 'b', 'i', and 'l' at the start of the list  
- Parameter - Value (`values...`): the data you want to send to the server  
- Example:  
```kt  
client.sendScriptPacket('test', false, ['l', 9999, 0, 45]);  
```  
  
### `<MinecraftClient>.stripFormatting(string)`  
- Description: This strips the formatting from the given string  
- Parameter - String (`string`): the string to strip  
- Returns - String: the stripped string  
- Example:  
```kt  
client.stripFormatting('§cHello§r');  
```  
  
### `<MinecraftClient>.getVersion()`  
- Description: This returns the current version of Minecraft you are playing  
- Returns - String: the version for example: '1.17.1'  
- Example:  
```kt  
client.getVersion();  
```  
  
### `<MinecraftClient>.textFromString(string)`  
- Deprecated: You should use 'Text.of(string)' instead  
- Description: This creates a text from the given string  
- Parameter - String (`string`): the string to parse  
- Returns - Value: the text  
- Example:  
```kt  
client.textFromString('Any Text!');  
```  
  
### `<MinecraftClient>.getScriptsPath()`  
- Description: This gets the script directory path, this is where all scripts are stored  
- Returns - String: the script directory path  
- Example:  
```kt  
client.getScriptPath();  
```  
  
### `<MinecraftClient>.canSendScriptPacket()`  
- Description: Returns whether the server supports client script packets  
- Returns - Boolean: Whether the client can send packets to the server  
- Example:  
```kt  
client.canSendScriptPacket()  
```  
  
### `<MinecraftClient>.getLatestChatMessage()`  
- Description: This will return the latest chat message  
- Returns - Text: the latest chat message, null if there is none  
- Example:  
```kt  
client.getLatestChatMessage();  
```  
  
### `<MinecraftClient>.renderFloatingItem(itemStack)`  
- Description: This renders an item in front of the player using the totem of undying animation  
- Parameter - ItemStack (`itemStack`): the item stack to render  
- Example:  
```kt  
client.renderFloatingItem(Material.DIAMOND.asItemStack());  
```  
  
### `<MinecraftClient>.getModList()`  
- Description: This gets a list of all the mod ids of the mods installed  
- Returns - List: the mod ids  
- Example:  
```kt  
client.getModList();  
```  
  
### `<MinecraftClient>.tick()`  
- Description: This ticks the client  
- Example:  
```kt  
client.tick();  
```  
  
### `<MinecraftClient>.getPing()`  
- Description: This gets the current connected server's ping  
- Returns - Number: the server ping in milliseconds  
- Throws - Error:  
  - `'Failed to get server ping'`  
- Example:  
```kt  
client.getPing();  
```  
  
### `<MinecraftClient>.resetEssentialClientRule(ruleName)`  
- Description: This resets the given client rule to its default value  
- Parameter - String (`ruleName`): the client rule  
- Throws - Error:  
  - `'Invalid ClientRule name'`  
- Example:  
```kt  
client.resetEssentialClientRule('highlightLavaSources');  
```  
  
### `<MinecraftClient>.getRunDirectory()`  
- Description: Returns the directory where the client is running  
- Returns - File: the Minecraft run directory  
- Example:  
```kt  
client.getRunDirectory();  
```  
  
### `<MinecraftClient>.itemFromString(string)`  
- Deprecated: You should use 'ItemStack.of(string)' instead  
- Description: This creates an item stack from the given string  
- Parameter - String (`string`): the string to parse  
- Returns - Value: the item stack  
- Example:  
```kt  
client.itemFromString('dirt');  
```  
  
### `<MinecraftClient>.parseStringToNbt(string)`  
- Description: This parses a string and turns it into a Nbt compound  
- Parameter - String (`string`): the string to parse  
- Returns - Value: the Nbt compound  
- Example:  
```kt  
client.parseStringToNbt('{"test":"test"}');  
```  
  
### `<MinecraftClient>.pressKey(key)`  
- Description: This allows you to simulate a key press inside of Minecraft, this will only press the key down  
- Parameter - String (`key`): the key to press  
- Throws - Error:  
  - `'Tried to press key outside of Minecraft'`  
- Example:  
```kt  
client.pressKey('f');  
```  
  
### `<MinecraftClient>.clearChat()`  
- Description: This will clear the chat hud  
- Example:  
```kt  
client.clearChat();  
```  
  
### `<MinecraftClient>.holdKey(key, milliseconds)`  
- Description: This allows you to simulate a key being held inside of Minecraft, this will press, hold, and release  
- Parameters:  
  - String (`key`): the key to hold  
  - Number (`milliseconds`): the number of milliseconds you want it held for  
- Throws - Error:  
  - `'Tried to press unknown key'`  
- Example:  
```kt  
client.holdKey('f', 100);  
```  
  
### `<MinecraftClient>.setEssentialClientRule(ruleName, value)`  
- Description: This sets the given client rule to the given value  
- Parameters:  
  - String (`ruleName`): the client rule  
  - Value (`value`): the new value for the rule  
- Throws - Error:  
  - `'Invalid ClientRule name'`  
  - `'Cannot set that value'`  
- Example:  
```kt  
client.setEssentialClientRule('highlightLavaSources', false);  
```  
  
### `<MinecraftClient>.setClientRenderDistance(number)`  
- Description: This sets the render distance on the client  
- Parameter - Number (`number`): the render distance  
- Example:  
```kt  
client.setClientRenderDistance(10);  
```  
  
### `<MinecraftClient>.playerNameFromUuid(uuid)`  
- Description: This will return the player name from the given uuid  
- Parameter - String (`uuid`): the uuid as a string  
- Returns - String: the player name, null if the uuid is not found  
- Example:  
```kt  
client.playerNameFromUuid('d4fca8c4-e083-4300-9a73-bf438847861c');  
```  
  
### `<MinecraftClient>.getFps()`  
- Description: This gets the current fps  
- Returns - Number: the fps  
- Example:  
```kt  
client.getFps();  
```  
  
### `<MinecraftClient>.isInSinglePlayer()`  
- Description: This will return true if the client is in single player mode  
- Returns - Boolean: true if the client is in single player mode  
- Example:  
```kt  
client.isInSinglePlayer();  
```  
  
## Static Methods  
  
### `MinecraftClient.get()`  
- Description: Returns the MinecraftClient instance  
- Returns - MinecraftClient: the MinecraftClient instance  
- Example:  
```kt  
MinecraftClient.get();  
```  
  
### `MinecraftClient.getClient()`  
- Description: Returns the MinecraftClient instance  
- Returns - MinecraftClient: the MinecraftClient instance  
- Example:  
```kt  
MinecraftClient.getClient();  
```  
  
  
# Network class  
Network class for Arucas.  
  
Allows you to do http requests. This is a utility class and cannot be constructed.  
  
Import with `import Network from util.Network;`  
  
Fully Documented.  
  
## Static Methods  
  
### `Network.downloadFile(url, file)`  
- Description: Downloads a file from an url to a file  
- Parameters:  
  - String (`url`): the url to download from  
  - File (`file`): the file to download to  
- Returns - Boolean: whether the download was successful  
- Example:  
```kt  
Network.downloadFile('https://arucas.com', new File('dir/downloads'));  
```  
  
### `Network.openUrl(url)`  
- Description: Opens an url in the default browser  
- Parameter - String (`url`): the url to open  
- Throws - Error:  
  - `'Failed to open url ...'`  
- Example:  
```kt  
Network.openUrl('https://google.com');  
```  
  
### `Network.requestUrl(url)`  
- Description: Requests an url and returns the response  
- Parameter - String (`url`): the url to request  
- Returns - String: the response from the url  
- Throws - Error:  
  - `'Failed to request data from ...'`  
- Example:  
```kt  
Network.requestUrl('https://google.com');  
```  
  
  
# Null class  
Null class for Arucas.  
  
This class cannot be constructed since null has a literal `null`.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
  
  
# Number class  
Number class for Arucas.  
  
This class cannot be constructed as it has a literal representation. For math related functions see the Math class.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<Number>.isInfinite()`  
- Description: This allows you to check if a number is infinite  
- Returns - Boolean: true if the number is infinite  
- Example:  
```kt  
(1/0).isInfinite();  
```  
  
### `<Number>.round()`  
- Description: This allows you to round a number to the nearest integer  
- Returns - Number: the rounded number  
- Example:  
```kt  
3.5.round();  
```  
  
### `<Number>.absolute()`  
- Deprecated: You should use `Math.abs(num)`  
- Description: This allows you to get the absolute value of a number  
- Returns - Number: the absolute value of the number  
- Example:  
```kt  
(-5).absolute();  
```  
  
### `<Number>.toDegrees()`  
- Deprecated: You should use `Math.toDegrees(num)`  
- Description: This allows you to convert a number in radians to degrees  
- Returns - Number: the number in degrees  
- Example:  
```kt  
Math.pi.toDegrees();  
```  
  
### `<Number>.toRadians()`  
- Deprecated: You should use `Math.toRadians(num)`  
- Description: This allows you to convert a number in degrees to radians  
- Returns - Number: the number in radians  
- Example:  
```kt  
5.toRadians();  
```  
  
### `<Number>.ceil()`  
- Description: This allows you to round a number up to the nearest integer  
- Returns - Number: the rounded number  
- Example:  
```kt  
3.5.ceil();  
```  
  
### `<Number>.isNaN()`  
- Description: This allows you to check if a number is not a number  
- Returns - Boolean: true if the number is not a number  
- Example:  
```kt  
(0/0).isNaN();  
```  
  
### `<Number>.floor()`  
- Description: This allows you to round a number down to the nearest integer  
- Returns - Number: the rounded number  
- Example:  
```kt  
3.5.floor();  
```  
  
### `<Number>.modulus(otherNumber)`  
- Deprecated: You should use `Math.mod(num1, num2)`  
- Description: This allows you to get the modulus of two numbers  
- Parameter - Number (`otherNumber`): the divisor  
- Returns - Number: the modulus of the two numbers  
- Example:  
```kt  
5.modulus(2);  
```  
  
  
  
# Object class  
Object class for Arucas.  
  
This is the base class for every other class in Arucas.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<Object>.uniqueHash()`  
- Description: This returns the unique hashcode of the value, this is different for every instance of a value  
- Returns - Number: the unique hashcode of the value  
- Example:  
```kt  
'thing'.uniqueHash();  
```  
  
### `<Object>.hashCode()`  
- Description: This returns the hashcode of the value, this is mainly used for maps and sets  
- Returns - Number: the hashcode of the value  
- Example:  
```kt  
'thing'.hashCode();  
```  
  
### `<Object>.equals(other)`  
- Deprecated: You should use '=='  
- Description: This checks whether the value is equal to another value  
- Parameter - Value (`other`): the other value you want to check against  
- Returns - Boolean: whether the values are equal  
- Example:  
```kt  
10.equals(20);  
```  
  
### `<Object>.toString()`  
- Description: This returns the string representation of the value  
- Returns - String: the string representation of the value  
- Example:  
```kt  
[10, 11, 12].toString();  
```  
  
### `<Object>.copy()`  
- Description: This returns a copy of the value, some values might just return themselves  
- Returns - Value: the copy of the value  
- Example:  
```kt  
10.copy();  
```  
  
### `<Object>.getValueType()`  
- Deprecated: You should use 'Type.of(<Value>).getName()'  
- Description: This returns the name of the type of the value  
- Returns - String: the name of the type of value  
- Example:  
```kt  
10.getValueType();  
```  
  
### `<Object>.instanceOf(type)`  
- Description: This checks whether this value is an instance of another type  
- Parameter - Type (`type`): the other type you want to check against  
- Returns - Boolean: whether the value is of that type  
- Example:  
```kt  
10.instanceOf(String.type);  
```  
  
  
  
# OtherPlayer class  
OtherPlayer class for Arucas.  
  
This class is used to represent all players, mainly other players,  
this class extends LivingEntity and so inherits all of their methods too  
  
Import with `import OtherPlayer from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<OtherPlayer>.getAllSlotsFor(materialLike)`  
- Description: This gets all the slot numbers of the specified item in the players combined inventory  
- Parameter - MaterialLike (`materialLike`): the item or material you want to get the slot of  
- Returns - List: the slot numbers of the item, empty list if not found  
- Example:  
```kt  
otherPlayer.getAllSlotsFor(Material.DIAMOND);  
```  
  
### `<OtherPlayer>.getSlotFor(materialLike)`  
- Description: This gets the slot number of the specified item in the players combined inventory  
- Parameter - MaterialLike (`materialLike`): the item or material you want to get the slot of  
- Returns - Number: the slot number of the item, null if not found  
- Example:  
```kt  
otherPlayer.getSlotFor(Material.DIAMOND.asItemStack());  
```  
  
### `<OtherPlayer>.getHeldItem()`  
- Description: This gets the players currently selected item, in their main hand  
- Returns - ItemStack: the currently selected item  
- Example:  
```kt  
otherPlayer.getHeldItem();  
```  
  
### `<OtherPlayer>.getItemForSlot(slotNum)`  
- Description: This gets the item in the specified slot, in the total players inventory, including inventories of open containers  
- Parameter - Number (`slotNum`): the slot number you want to get  
- Returns - ItemStack: the item in the specified slot  
- Throws - Error:  
  - `'That slot is out of bounds'`  
- Example:  
```kt  
otherPlayer.getItemForSlot(0);  
```  
  
### `<OtherPlayer>.getCurrentSlot()`  
- Description: This gets the players currently selected slot  
- Returns - Number: the currently selected slot number  
- Example:  
```kt  
otherPlayer.getCurrentSlot();  
```  
  
### `<OtherPlayer>.getSaturation()`  
- Description: This gets the saturation level of the player  
- Returns - Number: the saturation level  
- Example:  
```kt  
otherPlayer.getSaturation();  
```  
  
### `<OtherPlayer>.getPlayerName()`  
- Description: This gets the players name  
- Returns - String: the players name  
- Example:  
```kt  
otherPlayer.getPlayerName();  
```  
  
### `<OtherPlayer>.getFishingBobber()`  
- Description: This gets the fishing bobber that the player has  
- Returns - Entity: the fishing bobber entity, null if the player isn't fishing  
- Example:  
```kt  
otherPlayer.getFishingBobber();  
```  
  
### `<OtherPlayer>.getLevels()`  
- Description: This gets the number of experience levels the player has  
- Returns - Number: the number of experience levels  
- Example:  
```kt  
otherPlayer.getLevels();  
```  
  
### `<OtherPlayer>.isInventoryFull()`  
- Description: This gets whether the players inventory is full  
- Returns - Boolean: whether the inventory is full  
- Example:  
```kt  
otherPlayer.isInventoryFull();  
```  
  
### `<OtherPlayer>.getTotalSlots()`  
- Description: This gets the players total inventory slots  
- Returns - Number: the players total inventory slots  
- Example:  
```kt  
otherPlayer.getTotalSlots();  
```  
  
### `<OtherPlayer>.getAbilities()`  
- Description: This gets the abilities of the player in a map  
For example:  
`{"invulnerable": false, "canFly": true, "canBreakBlocks": true, "isCreative": true, "walkSpeed": 1.0, "flySpeed": 1.2}`  
- Returns - Map: the abilities of the player  
- Example:  
```kt  
otherPlayer.getAbilities();  
```  
  
### `<OtherPlayer>.getItemForPlayerSlot(slotNum)`  
- Description: This gets the item in the specified slot, in the players inventory, not including inventories of open containers  
- Parameter - Number (`slotNum`): the slot number you want to get  
- Returns - ItemStack: the item in the specified slot  
- Throws - Error:  
  - `'That slot is out of bounds'`  
- Example:  
```kt  
otherPlayer.getItemForPlayerSlot(0);  
```  
  
### `<OtherPlayer>.getGamemode()`  
- Description: This gets the players gamemode  
- Returns - String: the players gamemode as a string, null if not known, for example 'creative', 'survival', 'spectator'  
- Example:  
```kt  
otherPlayer.getGamemode();  
```  
  
### `<OtherPlayer>.getHunger()`  
- Description: This gets the hunger level of the player  
- Returns - Number: the hunger level  
- Example:  
```kt  
otherPlayer.getHunger();  
```  
  
  
  
# Player class  
Player class for Arucas.  
  
This class is used to interact with the main player, this extends OtherPlayer  
and so inherits all methods from that class.  
  
Import with `import Player from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<Player>.openScreen(screen)`  
- Description: This opens a screen for the player, this cannot open server side screens  
- Parameter - Screen (`screen`): the screen to open  
- Throws - Error:  
  - `'Opening handled screens is unsafe'`  
- Example:  
```kt  
player.openScreen(new FakeScreen('MyScreen', 4));  
```  
  
### `<Player>.getSwappableHotbarSlot()`  
- Description: This will get the next empty slot in the hotbar starting from the current slot  
going right, and if it reaches the end of the hotbar it will start from the beginning.  
If there is no empty slot it will return any slot that doesn't have an item with  
an enchantment that is in the hotbar, again going from the current slot  
if there is no such slot it will return the current selected slot  
- Returns - Number: the slot that is swappable  
- Example:  
```kt  
player.getSwappableHotbarSlot();  
```  
  
### `<Player>.anvilRename(name, predicate)`  
- Description: This allows you to name an item in an anvil  
- Parameters:  
  - String (`name`): the name you want to give the item  
  - Function (`predicate`): whether the ItemStack meets a certain criteria  
- Returns - Boolean: whether the anvilling was successful, if the player doesn't have enough levels it will return the xp cost  
- Throws - Error:  
  - `'Not in anvil gui'`  
  - `'Invalid function parameter'`  
- Example:  
```kt  
// Rename any shulker box  
player.anvilRename("Rocket Box",  
 fun(item) { isShulker = item.getItemId().containsString("shulker_box")); return isShulker; });  
```  
  
### `<Player>.anvil(predicate1, predicate2)`  
- Description: This allows you to combine two items in an anvil  
- Parameters:  
  - Function (`predicate1`): a function determining whether the first ItemStack meets a criteria  
  - Function (`predicate2`): a function determining whether the second ItemStack meets a criteria  
- Returns - Boolean: whether the anvilling was successful, if the player doesn't have enough levels it will return the xp cost  
- Throws - Error:  
  - `'Not in anvil gui'`  
  - `'Invalid function parameter'`  
- Example:  
```kt  
// Enchant a pickaxe with mending  
player.anvil(  
 // Predicate for pick fun(item) { // We want a netherite pickaxe without mending if (item.getItemId() == "netherite_pickaxe") { hasMending = item.getEnchantments().getKeys().contains("mending"); return !hasMending; } return false; }, // Predicate for book fun(item) { // We want a book with mending if (item.getItemId() == "enchanted_book") { hasMending = item.getEnchantments().getKeys().contains("mending"); return hasMending; } return false; });  
```  
  
### `<Player>.use(action)`  
- Description: This allows you to make your player use  
- Parameter - String (`action`): the type of action, either 'hold', 'stop', or 'once'  
- Throws - Error:  
  - `'Must pass 'hold', 'stop', or 'once' into use()'`  
- Example:  
```kt  
player.use('hold');  
```  
  
### `<Player>.craftRecipe(recipe)`  
- Description: This allows you to craft a predefined recipe  
- Parameter - Recipe (`recipe`): the recipe you want to craft  
- Throws - Error:  
  - `'Must be in a crafting GUI'`  
- Example:  
```kt  
player.craftRecipe(Recipe.CHEST);  
```  
  
### `<Player>.craft(recipe)`  
- Description: This allows you to craft a recipe, this can be 2x2 or 3x3  
The list you pass in must contain Materials or ItemStacks  
Most of the time you should use craftRecipe instead  
- Parameter - List (`recipe`): a list of materials making up the recipe you want to craft including air  
- Throws - Error:  
  - `'Must be in a crafting GUI'`  
  - `'You must be in a crafting table to craft a 3x3'`  
  - `'Recipe must either be 3x3 or 2x2'`  
  - `'The recipe must only include items or materials'`  
- Example:  
```kt  
chestRecipe = [  
 Material.OAK_PLANKS, Material.OAK_PLANKS, Material.OAK_PLANKS, Material.OAK_PLANKS,    Material.AIR    , Material.OAK_PLANKS, Material.OAK_PLANKS, Material.OAK_PLANKS, Material.OAK_PLANKS];  
player.craft(chestRecipe);  
```  
  
### `<Player>.interactWithEntity(entity)`  
- Description: This allows your player to interact with an entity without  
having to be looking at it or clicking on the entity  
- Parameter - Entity (`entity`): the entity to interact with  
- Example:  
```kt  
allEntities = client.getWorld().getAllEntities();  
foreach (entity : allEntities) {  
 if (entity.getId() == "villager" && player.getSquaredDistanceTo(entity) < 5) { player.interactWithEntity(entity); break; }}  
```  
  
### `<Player>.messageActionBar(message)`  
- Description: This allows you to set the current memssage displaying on the action bar  
- Parameter - Text (`message`): the message to send, can also be string  
- Example:  
```kt  
player.messageActionBar('Hello World!');  
```  
  
### `<Player>.getLookingAtEntity()`  
- Description: This gets the entity that the player is currently looking at  
- Returns - Entity: the entity that the player is looking at  
- Example:  
```kt  
player.getLookingAtEntity();  
```  
  
### `<Player>.attackBlock(pos, direction)`  
- Description: This allows you to attack a block at a position and direction  
- Parameters:  
  - Pos (`pos`): the position of the block  
  - String (`direction`): the direction of the attack, e.g. 'up', 'north', 'east', etc.  
- Example:  
```kt  
player.attackBlock(new Pos(0, 0, 0), 'up');  
```  
  
### `<Player>.attackBlock(x, y, z, direction)`  
- Description: This allows you to attack a block at a position and direction  
- Parameters:  
  - Number (`x`): the x position  
  - Number (`y`): the y position  
  - Number (`z`): the z position  
  - String (`direction`): the direction of the attack, e.g. 'up', 'north', 'east', etc.  
- Example:  
```kt  
player.attackBlock(0, 0, 0, 'up');  
```  
  
### `<Player>.logout(message)`  
- Description: This forces the player to leave the world  
- Parameter - String (`message`): the message to display to the player on the logout screen  
- Example:  
```kt  
player.logout('You've been lazy!');  
```  
  
### `<Player>.dropItemInHand(dropAll)`  
- Description: This drops the item(s) in the player's main hand  
- Parameter - Boolean (`dropAll`): if true, all items in the player's main hand will be dropped  
- Example:  
```kt  
player.dropItemInHand(true);  
```  
  
### `<Player>.setSelectedSlot(slot)`  
- Description: This allows you to set the slot number your player is holding  
- Parameter - Number (`slot`): the slot number, must be between 0 - 8  
- Throws - Error:  
  - `'Number must be between 0 - 8'`  
- Example:  
```kt  
player.setSelectedSlot(0);  
```  
  
### `<Player>.attack(action)`  
- Description: This allows you to make your player attack  
- Parameter - String (`action`): the type of action, either 'hold', 'stop', or 'once'  
- Throws - Error:  
  - `'Must pass 'hold', 'stop', or 'once' into attack()'`  
- Example:  
```kt  
player.attack('once');  
```  
  
### `<Player>.swingHand(hand)`  
- Description: This will play the player's hand swing animation for a given hand  
- Parameter - String (`hand`): the hand to swing, this should be either 'main_hand' or 'off_hand'  
- Example:  
```kt  
player.swingHand('main_hand');  
```  
  
### `<Player>.stonecutter(itemInput, itemOutput)`  
- Description: This allows you to use the stonecutter  
- Parameters:  
  - MaterialLike (`itemInput`): the item or material you want to input  
  - MaterialLike (`itemOutput`): the item or material you want to craft  
- Returns - Boolean: whether the result was successful  
- Throws - Error:  
  - `'Not in stonecutter gui'`  
  - `'Recipe does not exist'`  
- Example:  
```kt  
player.stonecutter(Material.STONE.asItemstack(), Material.STONE_BRICKS.asItemStack());  
```  
  
### `<Player>.setSneaking(sneaking)`  
- Description: This sets the player's sneaking state  
- Parameter - Boolean (`sneaking`): the sneaking state  
- Example:  
```kt  
player.setSneaking(true);  
```  
  
### `<Player>.setWalking(walking)`  
- Description: This sets the player's walking state  
- Parameter - Boolean (`walking`): the walking state  
- Example:  
```kt  
player.setWalking(true);  
```  
  
### `<Player>.breakBlock(pos)`  
- Description: This breaks a block at a given position, if it is able to be broken  
- Parameter - Pos (`pos`): the position of the block  
- Returns - Boolean: whether the block can be broken  
- Example:  
```kt  
player.breakBlock(new Pos(0, 0, 0));  
```  
  
### `<Player>.breakBlock(pos, function)`  
- Description: This breaks a block at a given position, if it is able to be broken  
and runs a function when the block is broken, or when the block cannot be broken  
- Parameters:  
  - Pos (`pos`): the position of the block  
  - Function (`function`): the function to run when the block is broken  
- Returns - Boolean: whether the block can be broken  
- Example:  
```kt  
player.breakBlock(new Pos(0, 0, 0), fun() { print('broken'); });  
```  
  
### `<Player>.jump()`  
- Description: This will make the player jump if they are on the ground  
- Example:  
```kt  
player.jump();  
```  
  
### `<Player>.openInventory()`  
- Description: This opens the player's inventory  
- Example:  
```kt  
player.openInventory();  
```  
  
### `<Player>.swapPlayerSlotWithHotbar(slot)`  
- Description: This allows you to swap a slot in the player's inventory with the hotbar  
- Parameter - Number (`slot`): the slot to swap  
- Throws - Error:  
  - `'That slot is out of bounds'`  
- Example:  
```kt  
player.swapPlayerSlotWithHotbar(15);  
```  
  
### `<Player>.spectatorTeleport(entity)`  
- Description: This allows you to teleport to any entity as long as you are in spectator mode  
- Parameter - Entity (`entity`): the entity to teleport to  
- Example:  
```kt  
player.spectatorTeleport(player.getLookingAtEntity());  
```  
  
### `<Player>.getBlockBreakingSpeed(block)`  
- Description: This returns the block breaking speed of the player on a block including enchanements and effects  
- Parameter - Block (`block`): the block to get the speed of  
- Example:  
```kt  
speed = player.getBlockBreakingSpeed(Material.GOLD_BLOCK.asBlock());  
```  
  
### `<Player>.closeScreen()`  
- Description: This closes the current screen  
- Example:  
```kt  
player.closeScreen();  
```  
  
### `<Player>.getCurrentScreen()`  
- Description: This gets the current screen the player is in  
- Returns - Screen: the screen the player is in, if the player is not in a screen it will return null  
- Example:  
```kt  
screen = player.getCurrentScreen();  
```  
  
### `<Player>.updateBreakingBlock(pos)`  
- Description: This allows you to update your block breaking progress at a position  
- Parameter - Pos (`pos`): the position of the block  
- Example:  
```kt  
player.updateBreakingBlock(new Pos(0, 0, 0));  
```  
  
### `<Player>.updateBreakingBlock(x, y, z)`  
- Description: This allows you to update your block breaking progress at a position  
- Parameters:  
  - Number (`x`): the x position  
  - Number (`y`): the y position  
  - Number (`z`): the z position  
- Example:  
```kt  
player.updateBreakingBlock(0, 0, 0);  
```  
  
### `<Player>.fakeLook(yaw, pitch, direction, duration)`  
- Description: This makes the player 'fake' looking in a direction, this can be  
used to place blocks in unusual orientations without moving the camera  
- Parameters:  
  - Number (`yaw`): the yaw to look at  
  - Number (`pitch`): the pitch to look at  
  - String (`direction`): the direction to look at  
  - Number (`duration`): the duration of the look in ticks  
- Example:  
```kt  
player.fakeLook(90, 0, 'up', 100);  
```  
  
### `<Player>.say(message)`  
- Description: This allows you to make your player send a message in chat, this includes commands  
- Parameter - String (`message`): the message to send  
- Example:  
```kt  
player.say('/help');  
```  
  
### `<Player>.swapSlots(slot1, slot2)`  
- Description: The allows you to swap two slots with one another  
A note about slot order is that slots go from top to bottom  
- Parameters:  
  - Number (`slot1`): the slot to swap with slot2  
  - Number (`slot2`): the slot to swap with slot1  
- Throws - Error:  
  - `'That slot is out of bounds'`  
- Example:  
```kt  
player.swapSlots(13, 14);  
```  
  
### `<Player>.message(message)`  
- Description: This allows you to send a message to your player, only they will see this, purely client side  
- Parameter - Text (`message`): the message to send, can also be string  
- Example:  
```kt  
player.message('Hello World!');  
```  
  
### `<Player>.look(yaw, pitch)`  
- Description: This sets the player's look direction  
- Parameters:  
  - Number (`yaw`): the yaw of the player's look direction  
  - Number (`pitch`): the pitch of the player's look direction  
- Example:  
```kt  
player.look(0, 0);  
```  
  
### `<Player>.shiftClickSlot(slot)`  
- Description: This allows you to shift click a slot  
- Parameter - Number (`slot`): the slot to click  
- Throws - Error:  
  - `'That slot is out of bounds'`  
- Example:  
```kt  
player.shiftClickSlot(9);  
```  
  
### `<Player>.dropAll(materialLike)`  
- Description: This drops all items of a given type in the player's inventory  
- Parameter - MaterialLike (`materialLike`): the item stack, or material type to drop  
- Example:  
```kt  
player.dropAll(Material.DIRT.asItemStack());  
```  
  
### `<Player>.lookAtPos(pos)`  
- Description: This makes your player look towards a position  
- Parameter - Pos (`pos`): the position to look at  
- Example:  
```kt  
player.lookAtPos(pos);  
```  
  
### `<Player>.lookAtPos(x, y, z)`  
- Description: This makes your player look towards a position  
- Parameters:  
  - Number (`x`): the x coordinate of the position  
  - Number (`y`): the y coordinate of the position  
  - Number (`z`): the z coordinate of the position  
- Example:  
```kt  
player.lookAtPos(0, 0, 0);  
```  
  
### `<Player>.swapHands()`  
- Description: This will swap the player's main hand with the off hand  
- Example:  
```kt  
player.swapHands();  
```  
  
### `<Player>.clickSlot(slot, click, action)`  
- Description: This allows you to click a slot with either right or left click  
and a slot action, the click must be either 'left' or 'right' or a number (for swap).  
The action must be either 'click', 'shift_click', 'swap', 'middle_click',  
'throw', 'drag', or 'double_click'  
- Parameters:  
  - Number (`slot`): the slot to click  
  - String (`click`): the click type, this should be either 'left' or 'right'  
  - String (`action`): the action to perform  
- Throws - Error:  
  - `'Invalid clickData must be 'left' or 'right' or a number'`  
  - `'Invalid slotActionType, see Wiki'`  
  - `'That slot is out of bounds'`  
- Example:  
```kt  
player.clickSlot(9, 'left', 'double_click');  
```  
  
### `<Player>.dropSlot(slot)`  
- Description: This allows you to drop the items in a slot  
- Parameter - Number (`slot`): the slot to drop  
- Throws - Error:  
  - `'That slot is out of bounds'`  
- Example:  
```kt  
player.dropSlot(9);  
```  
  
### `<Player>.attackEntity(entity)`  
- Description: This makes your player attack an entity without  
having to be looking at it or clicking on the entity  
- Parameter - Entity (`entity`): the entity to attack  
- Example:  
```kt  
allEntities = client.getWorld().getAllEntities();  
foreach (entity : allEntities) {  
 if (entity.getId() == "villager" && player.getSquaredDistanceTo(entity) < 5) { player.attackEntity(entity); break; }}  
```  
  
### `<Player>.setSprinting(sprinting)`  
- Description: This sets the player's sprinting state  
- Parameter - Boolean (`sprinting`): the sprinting state  
- Example:  
```kt  
player.setSprinting(true);  
```  
  
### `<Player>.interactBlock(pos, direction)`  
- Description: This allows you to interact with a block at a position and direction  
- Parameters:  
  - Pos (`pos`): the position of the block  
  - String (`direction`): the direction of the interaction, e.g. 'up', 'north', 'east', etc.  
- Example:  
```kt  
player.interactBlock(new Pos(0, 0, 0), 'up');  
```  
  
### `<Player>.interactBlock(pos, direction, hand)`  
- Description: This allows you to interact with a block at a position, direction, and hand  
- Parameters:  
  - Pos (`pos`): the position of the block  
  - String (`direction`): the direction of the interaction, e.g. 'up', 'north', 'east', etc.  
  - String (`hand`): the hand to use, e.g. 'main_hand', 'off_hand'  
- Example:  
```kt  
player.interactBlock(new Pos(0, 0, 0), 'up', 'off_hand');  
```  
  
### `<Player>.interactBlock(x, y, z, direction)`  
- Description: This allows you to interact with a block at a position and direction  
- Parameters:  
  - Number (`x`): the x position  
  - Number (`y`): the y position  
  - Number (`z`): the z position  
  - String (`direction`): the direction of the interaction, e.g. 'up', 'north', 'east', etc.  
- Example:  
```kt  
player.interactBlock(0, 100, 0, 'up');  
```  
  
### `<Player>.interactBlock(pos, direction, hand, blockPos, insideBlock)`  
- Description: This allows you to interact with a block at a position and direction  
This function is for very specific cases where there needs to be extra precision  
like when placing stairs or slabs in certain directions, so the first set of  
coords is the exact position of the block, and the second set of coords is the position  
- Parameters:  
  - Pos (`pos`): the exact position of the block  
  - String (`direction`): the direction of the interaction, e.g. 'up', 'north', 'east', etc.  
  - String (`hand`): the hand to use, e.g. 'main_hand', 'off_hand'  
  - Pos (`blockPos`): the position of the block  
  - Boolean (`insideBlock`): whether the player is inside the block  
- Example:  
```kt  
player.interactBlock(new Pos(0, 15.5, 0), 'up', new Pos(0, 15, 0), true, 'off_hand');  
```  
  
### `<Player>.interactBlock(x, y, z, direction, blockX, blockY, blockZ, insideBlock)`  
- Description: This allows you to interact with a block at a position and direction  
This function is for very specific cases where there needs to be extra precision  
like when placing stairs or slabs in certain directions, so the first set of  
coords is the exact position of the block, and the second set of coords is the position  
- Parameters:  
  - Number (`x`): the exact x position  
  - Number (`y`): the exact y position  
  - Number (`z`): the exact z position  
  - String (`direction`): the direction of the interaction, e.g. 'up', 'north', 'east', etc.  
  - Number (`blockX`): the x position of the block  
  - Number (`blockY`): the y position of the block  
  - Number (`blockZ`): the z position of the block  
  - Boolean (`insideBlock`): whether the player is inside the block  
- Example:  
```kt  
player.interactBlock(0, 100.5, 0, 'up', 0, 100, 0, true);  
```  
  
## Static Methods  
  
### `Player.get()`  
- Description: This gets the main player  
- Returns - Player: The main player  
- Example:  
```kt  
player = Player.get();  
```  
  
  
# Pos class  
Pos class for Arucas.  
  
This class is a wrapper for 3 coordinate points in Minecraft  
  
Import with `import Pos from Minecraft;`  
  
Fully Documented.  
  
## Constructors  
  
### `new Pos(list)`  
- Description: Creates a new Pos object with the given coordinates in a list  
- Parameter - List (`list`): the list containing three coordinates  
- Example:  
```kt  
new Pos([1, 2, 3])  
```  
### `new Pos(x, y, z)`  
- Description: This creates a new Pos with the given x, y, and z  
- Parameters:  
  - Number (`x`): the x position  
  - Number (`y`): the y position  
  - Number (`z`): the z position  
- Example:  
```kt  
new Pos(100, 0, 96);  
```  
  
## Methods  
  
### `<Pos>.add(pos)`  
- Description: This returns a new Pos with the current pos x, y, and z added by the given pos x, y, and z  
- Parameter - Pos (`pos`): the Pos to add by  
- Returns - Pos: the new Pos  
- Example:  
```kt  
pos.add(new Pos(2, 3, 5));  
```  
  
### `<Pos>.add(x, y, z)`  
- Description: This returns a new Pos with the current pos x, y, and z added by the given x, y, and z  
- Parameters:  
  - Number (`x`): the x adder  
  - Number (`y`): the y adder  
  - Number (`z`): the z adder  
- Returns - Pos: the new Pos  
- Example:  
```kt  
pos.add(2, 3, 5);  
```  
  
### `<Pos>.crossProduct(pos)`  
- Description: This returns the cross product of the current pos and the given pos  
- Parameter - Pos (`pos`): the Pos to cross product with  
- Returns - Pos: the cross product  
- Example:  
```kt  
pos.crossProduct(new Pos(2, 3, 5));  
```  
  
### `<Pos>.getX()`  
- Description: This returns the x position of the Pos  
- Returns - Number: the x position  
- Example:  
```kt  
pos.getX();  
```  
  
### `<Pos>.getY()`  
- Description: This returns the y position of the Pos  
- Returns - Number: the y position  
- Example:  
```kt  
pos.getY();  
```  
  
### `<Pos>.getZ()`  
- Description: This returns the z position of the Pos  
- Returns - Number: the z position  
- Example:  
```kt  
pos.getZ();  
```  
  
### `<Pos>.subtract(pos)`  
- Description: This returns a new Pos with the current pos x, y, and z subtracted by the given pos x, y, and z  
- Parameter - Pos (`pos`): the Pos to subtract by  
- Returns - Pos: the new Pos  
- Example:  
```kt  
pos.subtract(new Pos(2, 3, 5));  
```  
  
### `<Pos>.subtract(x, y, z)`  
- Description: This returns a new Pos with the current pos x, y, and z subtracted by the given x, y, and z  
- Parameters:  
  - Number (`x`): the x subtractor  
  - Number (`y`): the y subtractor  
  - Number (`z`): the z subtractor  
- Returns - Pos: the new Pos  
- Example:  
```kt  
pos.subtract(2, 3, 5);  
```  
  
### `<Pos>.toList()`  
- Description: This returns the Pos as a List containing the x, y, and z positions in order  
- Returns - List: the Pos as a List  
- Example:  
```kt  
x, y, z = pos.toList();  
```  
  
### `<Pos>.multiply(pos)`  
- Description: This returns a new Pos with the current pos x, y, and z multiplied by the given pos x, y, and z  
- Parameter - Pos (`pos`): the Pos to multiply by  
- Returns - Pos: the new Pos  
- Example:  
```kt  
pos.multiply(new Pos(2, 3, 5));  
```  
  
### `<Pos>.multiply(x, y, z)`  
- Description: This returns a new Pos with the current pos x, y, and z multiplied by the given x, y, and z  
- Parameters:  
  - Number (`x`): the x multiplier  
  - Number (`y`): the y multiplier  
  - Number (`z`): the z multiplier  
- Returns - Pos: the new Pos  
- Example:  
```kt  
pos.multiply(2, 3, 5);  
```  
  
### `<Pos>.dotProduct(pos)`  
- Description: This returns the dot product of the current pos and the given pos  
- Parameter - Pos (`pos`): the Pos to dot product with  
- Returns - Number: the dot product  
- Example:  
```kt  
pos.dotProduct(new Pos(2, 3, 5));  
```  
  
  
  
# Recipe class  
Recipe class for Arucas.  
  
This class represents recipes in Minecraft.  
  
Import with `import Recipe from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<Recipe>.getCraftingType()`  
- Description: This returns the crafting type of the recipe  
- Returns - String: the crafting type of the recipe, for example: 'crafting', 'smelting', 'blasting'  
- Example:  
```kt  
recipe.getCraftingType()  
```  
  
### `<Recipe>.getFullId()`  
- Description: This returns the full id of the recipe  
- Returns - String: the full id of the recipe  
- Example:  
```kt  
recipe.getFullId()  
```  
  
### `<Recipe>.getId()`  
- Description: This returns the id of the recipe  
- Returns - String: the id of the recipe  
- Example:  
```kt  
recipe.getId()  
```  
  
### `<Recipe>.getIngredients()`  
- Description: This returns all the possible ingredients of the recipe  
- Returns - List: list of lists, each inner lists contains possible recipe items  
- Example:  
```kt  
recipe.getIngredients()  
```  
  
### `<Recipe>.getOutput()`  
- Description: This returns the output of the recipe  
- Returns - ItemStack: the output of the recipe  
- Example:  
```kt  
recipe.getOutput()  
```  
  
## Static Methods  
  
### `Recipe.of(recipeId)`  
- Description: This converts a recipe id into a Recipe if it's valid  
- Parameter - String (`recipeId`): the id of the recipe to convert to a Recipe  
- Returns - Recipe: the recipe instance from the id  
- Throws - Error:  
  - `'Recipe with id ... doesn't exist'`  
- Example:  
```kt  
Recipe.of('redstone_block')  
```  
  
  
# Screen class  
Screen class for Arucas.  
  
This allows you to get information about the player's current screen.  
  
Import with `import Screen from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<Screen>.getTitle()`  
- Description: Gets the title of the specific screen  
- Returns - String: the screen title as text, this may include formatting, and custom names for the screen if applicable  
- Example:  
```kt  
screen.getTitle()  
```  
  
### `<Screen>.getName()`  
- Description: Gets the name of the specific screen  
- Returns - String: the screen name, if you are in the creative menu it will return the name of the tab you are on  
- Example:  
```kt  
screen.getName()  
```  
  
  
  
# Set class  
Set class for Arucas.  
  
Sets are collections of unique values. Similar to maps, without the values.  
An instance of the class can be created by using `Set.of(values...)`  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<Set>.add(value)`  
- Description: This allows you to add a value to the set  
- Parameter - Value (`value`): the value you want to add to the set  
- Returns - Boolean: whether the value was successfully added to the set  
- Example:  
```kt  
Set.of().add('object');  
```  
  
### `<Set>.contains(value)`  
- Description: This allows you to check whether a value is in the set  
- Parameter - Value (`value`): the value that you want to check in the set  
- Returns - Boolean: whether the value is in the set  
- Example:  
```kt  
Set.of('object').contains('object');  
```  
  
### `<Set>.addAll(collection)`  
- Description: This allows you to add all the values in a collection into the set  
- Parameter - Collection (`collection`): the collection of values you want to add  
- Returns - Set: the modified set  
- Throws - Error:  
  - `'... is not a collection'`  
- Example:  
```kt  
Set.of().addAll(Set.of('object', 81, 96, 'case'));  
```  
  
### `<Set>.containsAll(collection)`  
- Description: This allows you to check whether a collection of values are all in the set  
- Parameter - Collection (`collection`): the collection of values you want to check in the set  
- Returns - Boolean: whether all the values are in the set  
- Throws - Error:  
  - `'... is not a collection'`  
- Example:  
```kt  
Set.of('object').containsAll(Set.of('object', 81, 96, 'case'));  
```  
  
### `<Set>.get(value)`  
- Description: This allows you to get a value from in the set.  
The reason this might be useful is if you want to retrieve something  
from the set that will have the same hashcode but be in a different state  
as the value you are passing in  
- Parameter - Value (`value`): the value you want to get from the set  
- Returns - Value: the value you wanted to get, null if it wasn't in the set  
- Example:  
```kt  
Set.of('object').get('object');  
```  
  
### `<Set>.clear()`  
- Description: This removes all values from inside the set  
- Example:  
```kt  
Set.of('object').clear();  
```  
  
### `<Set>.isEmpty()`  
- Description: This allows you to check whether the set has no values  
- Returns - Boolean: whether the set is empty  
- Example:  
```kt  
Set.of().isEmpty();  
```  
  
### `<Set>.toString()`  
- Description: This converts the set to a string and evaluating any collections inside it  
- Returns - String: the string representation of the set  
- Example:  
```kt  
Set.of('object').toString();  
```  
  
### `<Set>.remove(value)`  
- Description: This allows you to remove a value from the set  
- Parameter - Value (`value`): the value you want to remove from the set  
- Returns - Boolean: whether the value was removed from the set  
- Example:  
```kt  
Set.of('object').remove('object');  
```  
  
## Static Methods  
  
### `Set.unordered()`  
- Description: This creates an unordered set  
- Returns - Set: the unordered set  
- Example:  
```kt  
Set.unordered();  
```  
  
### `Set.of(values...)`  
- Description: This allows you to create a set with an arbitrary number of values  
- Parameter - Value (`values...`): the values you want to add to the set  
- Returns - Set: the set you created  
- Example:  
```kt  
Set.of('object', 81, 96, 'case');  
```  
  
  
# SphereShape class  
SphereShape class for Arucas.  
  
This class is used to create a sphere shape which can be rendered in the world.  
  
Import with `import SphereShape from Minecraft;`  
  
Fully Documented.  
  
## Members  
  
### `<SphereShape>.pos`  
- Description: This is the position of the shape  
- Type: Pos  
- Assignable: false  
- Example:  
```kt  
shape.pos;  
```  
  
## Constructors  
  
### `new SphereShape(pos)`  
- Description: This creates a new sphere shape  
- Parameter - Pos (`pos`): The position of the sphere  
- Example:  
```kt  
new SphereShape(new Pos(0, 10, 0));  
```  
### `new SphereShape(x, y, z)`  
- Description: This creates a new sphere shape  
- Parameters:  
  - Number (`x`): The x position of the sphere  
  - Number (`y`): The y position of the sphere  
  - Number (`z`): The z position of the sphere  
- Example:  
```kt  
new SphereShape(0, 10, 0);  
```  
  
## Methods  
  
### `<SphereShape>.setColour(colour)`  
- Description: This sets the colour of the shape, using a single value, this  
function also has a sibling named `setColor()` that has the same functionality  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setColour(0xFF0000);  
```  
  
### `<SphereShape>.setColour(red, green, blue)`  
- Description: This sets the colour of the shape, using three values this function  
also has a sibling named `setColor()` that has the same functionality  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setColour(34, 55, 0);  
```  
  
### `<SphereShape>.setRenderThroughBlocks(boolean)`  
- Description: This sets whether the shape should render through blocks  
- Parameter - Boolean (`boolean`): whether the shape should render through blocks  
- Example:  
```kt  
shape.setRenderThroughBlocks(true);  
```  
  
### `<SphereShape>.setZScale(zScale)`  
- Description: This sets the z scale of the shape  
- Parameter - Number (`zScale`): the z scale of the shape  
- Example:  
```kt  
shape.setZScale(3.5);  
```  
  
### `<SphereShape>.getWidth()`  
- Description: This returns the width of the shape  
- Returns - Number: the width of the shape  
- Example:  
```kt  
shape.getWidth();  
```  
  
### `<SphereShape>.setGreen(green)`  
- Description: This sets the green value of the shape, using a single value  
- Parameter - Number (`green`): the amount of green between 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setGreen(34);  
```  
  
### `<SphereShape>.setOutlineGreen(green)`  
- Description: This sets the outline green value of the shape, using a single value  
- Parameter - Number (`green`): the amount of green between 0 - 255  
- Example:  
```kt  
shape.setOutlineGreen(34);  
```  
  
### `<SphereShape>.setRed(red)`  
- Description: This sets the red value of the shape, using a single value  
- Parameter - Number (`red`): the amount of red between 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setRed(34);  
```  
  
### `<SphereShape>.getYTilt()`  
- Description: This gets the y tilt of the shape  
- Returns - Number: the y tilt  
- Example:  
```kt  
shape.getYTilt();  
```  
  
### `<SphereShape>.setPos(pos)`  
- Description: This returns the position of the shape  
- Parameter - Pos (`pos`): the position of the shape  
- Example:  
```kt  
shape.setPos(new Pos(0, 0, 0));  
```  
  
### `<SphereShape>.getOpacity()`  
- Description: This returns the opacity of the shape  
- Returns - Number: the opacity of the shape  
- Example:  
```kt  
shape.getOpacity();  
```  
  
### `<SphereShape>.centerPosition()`  
- Description: This rounds the position to the nearest block position  
- Example:  
```kt  
shape.centerPosition();  
```  
  
### `<SphereShape>.setSteps(steps)`  
- Description: This sets the number of steps the sphere will take to render  
- Parameter - Number (`steps`): The number of steps  
- Example:  
```kt  
sphere.setSteps(30);  
```  
  
### `<SphereShape>.getRed()`  
- Description: This returns the red value of the shape  
- Returns - Number: the red value of the shape  
- Example:  
```kt  
shape.getRed();  
```  
  
### `<SphereShape>.getRGBList()`  
- Description: This returns the RGB value of the shape as a list  
- Returns - List: the RGB value of the shape as a list in the form [red, green, blue]  
- Example:  
```kt  
r, g, b = shape.getRGBList();  
```  
  
### `<SphereShape>.setBlue(blue)`  
- Description: This sets the blue value of the shape, using a single value  
- Parameter - Number (`blue`): the amount of blue between 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setBlue(34);  
```  
  
### `<SphereShape>.stopRendering()`  
- Description: This stops the shape from rendering  
- Example:  
```kt  
shape.stopRendering();  
```  
  
### `<SphereShape>.setOutlinePixelWidth(width)`  
- Description: This sets the outline pixel width of the shape, using a single value  
- Parameter - Number (`width`): the width of the outline in pixels  
- Example:  
```kt  
shape.setOutlinePixelWidth(5);  
```  
  
### `<SphereShape>.setYScale(yScale)`  
- Description: This sets the y scale of the shape  
- Parameter - Number (`yScale`): the y scale of the shape  
- Example:  
```kt  
shape.setYScale(2.5);  
```  
  
### `<SphereShape>.getYScale()`  
- Description: This gets the y scale of the shape  
- Example:  
```kt  
shape.getYScale();  
```  
  
### `<SphereShape>.getSteps()`  
- Description: This gets the number of steps the sphere will take to render  
- Returns - Number: The number of steps  
- Example:  
```kt  
sphere.getSteps();  
```  
  
### `<SphereShape>.getRGBAList()`  
- Description: This returns the RGBA value of the shape as a list  
- Returns - List: the RGBA value of the shape as a list in the form [red, green, blue, opacity]  
- Example:  
```kt  
r, g, b, a = shape.getRGBAList();  
```  
  
### `<SphereShape>.getZTilt()`  
- Description: This gets the z tilt of the shape  
- Returns - Number: the z tilt  
- Example:  
```kt  
shape.getZTilt();  
```  
  
### `<SphereShape>.render()`  
- Description: This sets the shape to be rendered indefinitely, the shape will only stop rendering when the script ends or when you call the stopRendering() method  
- Example:  
```kt  
shape.render();  
```  
  
### `<SphereShape>.setZTilt(zTilt)`  
- Description: This sets the z tilt of the shape  
- Parameter - Number (`zTilt`): the z tilt  
- Example:  
```kt  
shape.setZTilt(100);  
```  
  
### `<SphereShape>.getRGB()`  
- Description: This returns the RGB value of the shape  
- Returns - Number: the RGB value of the shape as a single number in the form 0xRRGGBB  
- Example:  
```kt  
shape.getRGB();  
```  
  
### `<SphereShape>.getZScale()`  
- Description: This gets the z scale of the shape  
- Example:  
```kt  
shape.getZScale();  
```  
  
### `<SphereShape>.setXScale(xScale)`  
- Description: This sets the x scale of the shape  
- Parameter - Number (`xScale`): the x scale of the shape  
- Example:  
```kt  
shape.setXScale(1.5);  
```  
  
### `<SphereShape>.setScale(xScale, yScale, zScale)`  
- Description: This sets the scale of the shape  
- Parameters:  
  - Number (`xScale`): the x scale of the shape  
  - Number (`yScale`): the y scale of the shape  
  - Number (`zScale`): the z scale of the shape  
- Example:  
```kt  
shape.setScale(1.5, 2.5, 3.5);  
```  
  
### `<SphereShape>.setOutlineRed(red)`  
- Description: This sets the outline red value of the shape, using a single value  
- Parameter - Number (`red`): the amount of red between 0 - 255  
- Example:  
```kt  
shape.setOutlineRed(34);  
```  
  
### `<SphereShape>.setYTilt(yTilt)`  
- Description: This sets the y tilt of the shape  
- Parameter - Number (`yTilt`): the y tilt  
- Example:  
```kt  
shape.setYTilt(100);  
```  
  
### `<SphereShape>.shouldRenderThroughBlocks()`  
- Description: This returns whether the shape should render through blocks  
- Returns - Boolean: whether the shape should render through blocks  
- Example:  
```kt  
shape.shouldRenderThroughBlocks();  
```  
  
### `<SphereShape>.setWidth(width)`  
- Description: This sets the width of the shape  
- Parameter - Number (`width`): the width of the shape  
- Example:  
```kt  
shape.setWidth(10.5);  
```  
  
### `<SphereShape>.getBlue()`  
- Description: This returns the blue value of the shape  
- Returns - Number: the blue value of the shape  
- Example:  
```kt  
shape.getBlue();  
```  
  
### `<SphereShape>.setTilt(xTilt, yTilt, zTilt)`  
- Description: This sets the tilt of the shape  
- Parameters:  
  - Number (`xTilt`): the x tilt  
  - Number (`yTilt`): the y tilt  
  - Number (`zTilt`): the z tilt  
- Example:  
```kt  
shape.setTilt(100, 0, 80);  
```  
  
### `<SphereShape>.setColor(colour)`  
- Description: This sets the colour of the shape, using a single value, this  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setColor(0xFF0000);  
```  
  
### `<SphereShape>.setColor(red, green, blue)`  
- Description: This sets the colour of the shape, using three values this function  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setColor(34, 55, 0);  
```  
  
### `<SphereShape>.setOutlineBlue(blue)`  
- Description: This sets the outline blue value of the shape, using a single value  
- Parameter - Number (`blue`): the amount of blue between 0 - 255  
- Example:  
```kt  
shape.setOutlineBlue(34);  
```  
  
### `<SphereShape>.setOutlineColour(colour)`  
- Description: This sets the width of the shape, using a single value, this function  
also has a sibling named `setOutlineColor()` that has the same functionality  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setOutlineColour(0xFF00FF);  
```  
  
### `<SphereShape>.setOutlineColour(red, green, blue)`  
- Description: This sets the outline colour of the shape, using three values, this function  
also has a sibling named `setOutlineColor()` that has the same functionality  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Example:  
```kt  
shape.setOutlineColour(255, 0, 255);  
```  
  
### `<SphereShape>.getGreen()`  
- Description: This returns the green value of the shape  
- Returns - Number: the green value of the shape  
- Example:  
```kt  
shape.getGreen();  
```  
  
### `<SphereShape>.getXScale()`  
- Description: This gets the x scale of the shape  
- Example:  
```kt  
shape.getXScale();  
```  
  
### `<SphereShape>.setOutlineColor(colour)`  
- Description: This sets the width of the shape, using a single value, this function  
- Parameter - Number (`colour`): the colour, usually you would use hexadecimal, 0xRRGGBB where RR represents red from 00 - FF, GG represents green from 00 - FF, and BB represents blue from 00 - FF  
- Example:  
```kt  
shape.setOutlineColor(0xFF00FF);  
```  
  
### `<SphereShape>.setOutlineColor(red, green, blue)`  
- Description: This sets the outline colour of the shape, using three values, this function  
- Parameters:  
  - Number (`red`): the amount of red 0 - 255  
  - Number (`green`): the amount of green 0 - 255  
  - Number (`blue`): the amount of blue 0 - 255  
- Example:  
```kt  
shape.setOutlineColor(255, 0, 255);  
```  
  
### `<SphereShape>.setXTilt(xTilt)`  
- Description: This sets the x tilt of the shape  
- Parameter - Number (`xTilt`): the x tilt  
- Example:  
```kt  
shape.setXTilt(100);  
```  
  
### `<SphereShape>.getXTilt()`  
- Description: This gets the x tilt of the shape  
- Returns - Number: the x tilt  
- Example:  
```kt  
shape.getXTilt();  
```  
  
### `<SphereShape>.setOpacity(alpha)`  
- Description: This sets the opacity of the shape, using a single value  
- Parameter - Number (`alpha`): the opacity, where 255 is solid colour and 0 is no colour  
- Throws - Error:  
  - `'Colour ... is out of bounds, must be between 0 - 255'`  
- Example:  
```kt  
shape.setOpacity(34);  
```  
  
  
  
# String class  
String class for Arucas.  
  
This class cannot be constructed since strings have a literal. Strings are immutable.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<String>.uppercase()`  
- Description: This makes the string uppercase  
- Returns - String: the uppercase string  
- Example:  
```kt  
'hello'.uppercase();  
```  
  
### `<String>.lowercase()`  
- Description: This makes the string lowercase  
- Returns - String: the lowercase string  
- Example:  
```kt  
'HELLO'.lowercase();  
```  
  
### `<String>.format(values...)`  
- Description: This formats the string with the given parameters, which replace '%s' in the string  
- Parameter - Value (`values...`): the values to add, these will be converted to strings  
- Returns - String: the formatted string  
- Throws - Error:  
  - `'You are missing values to be formatted'`  
- Example:  
```kt  
'%s %s'.format('hello', 'world');  
```  
  
### `<String>.toList()`  
- Description: This makes a list of all the characters in the string  
- Returns - List: the list of characters  
- Example:  
```kt  
'hello'.toList();  
```  
  
### `<String>.matches(regex)`  
- Description: This checks if the string matches the given regex  
- Parameter - String (`regex`): the regex to check the string with  
- Returns - Boolean: true if the string matches the given regex  
- Example:  
```kt  
'hello'.matches('[a-z]*');  
```  
  
### `<String>.replaceAll(regex, replace)`  
- Description: This replaces all the instances of a regex with the replace string  
- Parameters:  
  - String (`regex`): the regex you want to replace  
  - String (`replace`): the string you want to replace it with  
- Returns - String: the modified string  
- Example:  
```kt  
'hello'.replaceAll('l', 'x');  
```  
  
### `<String>.capitalise()`  
- Description: This capitalises the first letter of the string  
- Returns - String: the capitalised string  
- Example:  
```kt  
'foo'.capitalise();  
```  
  
### `<String>.contains(string)`  
- Description: This checks if the string contains the given string  
- Parameter - String (`string`): the string you want to check for  
- Returns - Boolean: true if the string contains the given string  
- Example:  
```kt  
'hello'.contains('he');  
```  
  
### `<String>.split(regex)`  
- Description: This splits the string into a list of strings based on a regex  
- Parameter - String (`regex`): the regex to split the string with  
- Returns - List: the list of strings  
- Example:  
```kt  
'foo/bar/baz'.split('/');  
```  
  
### `<String>.strip()`  
- Description: This strips the whitespace from the string  
- Returns - String: the stripped string  
- Example:  
```kt  
'  hello  '.strip();  
```  
  
### `<String>.subString(from, to)`  
- Description: This returns a substring of the string  
- Parameters:  
  - Number (`from`): the start index  
  - Number (`to`): the end index  
- Returns - String: the substring  
- Example:  
```kt  
'hello'.subString(1, 3);  
```  
  
### `<String>.find(regex)`  
- Description: This finds all instances of the regex in the string  
- Parameter - String (`regex`): the regex to search the string with  
- Returns - List: the list of all instances of the regex in the string  
- Example:  
```kt  
'hello'.find('[a-z]*');  
```  
  
### `<String>.endsWith(string)`  
- Description: This checks if the string ends with the given string  
- Parameter - String (`string`): the string to check the string with  
- Returns - Boolean: true if the string ends with the given string  
- Example:  
```kt  
'hello'.endsWith('he');  
```  
  
### `<String>.toNumber()`  
- Description: This tries to convert the string to a number  
- Returns - Number: the number value  
- Throws - Error:  
  - `'Cannor parse ... as a number'`  
- Example:  
```kt  
'0xFF'.toNumber();  
```  
  
### `<String>.startsWith(string)`  
- Description: This checks if the string starts with the given string  
- Parameter - String (`string`): the string to check the string with  
- Returns - Boolean: true if the string starts with the given string  
- Example:  
```kt  
'hello'.startsWith('he');  
```  
  
  
  
# Text class  
Text class for Arucas.  
  
This class is used to create formatted strings used inside Minecraft.  
  
Import with `import Text from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<Text>.format(formatting)`  
- Description: This allows you to add a formatting to a text instance  
A list of formatting names can be found [here](https://minecraft.fandom.com/wiki/Formatting_codes)  
- Parameter - String (`formatting`): the name of the formatting  
- Returns - Text: the text instance with the formatting added  
- Throws - Error:  
  - `'Invalid formatting: ...'`  
- Example:  
```kt  
text.format('DARK_RED').format('BOLD');  
```  
  
### `<Text>.withHoverEvent(event, value)`  
- Description: This allows you to add a hover event to a text instance  
The possible events are: 'show_text', 'show_item', 'show_entity'  
- Parameters:  
  - String (`event`): the name of the event  
  - Value (`value`): the value associated with the event  
- Returns - Text: the text instance with the hover event  
- Throws - Error:  
  - `'Invalid action: ...'`  
- Example:  
```kt  
text = Text.of("Hello World!");  
  
// Examples of hover events  
text.withHoverEvent("show_text", Text.of("Hello world!"));  
text.withHoverEvent("show_item", Material.DIAMOND_SWORD.asItemStack());  
text.withHoverEvent("show_entity", Player.get());  
```  
  
### `<Text>.withClickEvent(event, value)`  
- Description: This allows you to add a click event to a text instance  
The possible events are: 'open_url', 'open_file', 'run_command', 'suggest_command', 'copy_to_clipboard', 'run_function'  
- Parameters:  
  - String (`event`): the name of the event  
  - String (`value`): the value associated with the event  
- Returns - Text: the text instance with the click event  
- Throws - Error:  
  - `'Invalid action: ...'`  
- Example:  
```kt  
text = Text.of("Hello World!");  
  
// Examples of click events  
text.withClickEvent("open_url", "https://youtu.be/dQw4w9WgXcQ");  
text.withClickEvent("open_file", "C:/Users/user/Desktop/thing.txt");  
text.withClickEvent("run_command", "/gamemode creative");  
text.withClickEvent("suggest_command", "/gamemode survival");  
text.withClickEvent("copy_to_clipboard", "Ooops!");  
text.withClickEvent("run_function", fun() {  
 print("Text was clicked!");});  
```  
  
### `<Text>.append(otherText)`  
- Description: This allows you to append a text instance to another text instance  
- Parameter - Text (`otherText`): the text instance to append to  
- Returns - Text: the text instance with the appended text  
- Example:  
```kt  
Text.of('Hello').append(Text.of(' world!'));  
```  
  
## Static Methods  
  
### `Text.of(string)`  
- Description: This converts a string into a text instance  
- Parameter - String (`string`): The string to convert into a text instance  
- Returns - Text: the text instance from the string  
- Example:  
```kt  
Text.of('Hello World!');  
```  
  
### `Text.parse(textJson)`  
- Description: This converts a text json into a text instance  
- Parameter - String (`textJson`): The string in json format, or a Json value itself  
- Returns - Text: the text instance from the json  
- Example:  
```kt  
Text.parse('{"text":"Hello World!","color":"white","italic":"true"}');  
```  
  
  
# Thread class  
Thread class for Arucas.  
  
This class allows you to create threads for asynchronous execution.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<Thread>.getAge()`  
- Description: This gets the age of the thread in milliseconds  
- Returns - Number: the age of the thread  
- Example:  
```kt  
Thread.getCurrentThread().getAge();  
```  
  
### `<Thread>.isAlive()`  
- Description: This checks if the thread is alive (still running)  
- Returns - Boolean: true if the thread is alive, false if not  
- Example:  
```kt  
Thread.getCurrentThread().isAlive();  
```  
  
### `<Thread>.getName()`  
- Description: This gets the name of the thread  
- Returns - String: the name of the thread  
- Example:  
```kt  
Thread.getCurrentThread().getName();  
```  
  
### `<Thread>.stop()`  
- Description: This stops the thread from executing, anything that was running will be instantly stopped  
- Throws - Error:  
  - `'Thread is not alive'`  
- Example:  
```kt  
Thread.getCurrentThread().stop();  
```  
  
## Static Methods  
  
### `Thread.freeze()`  
- Description: This freezes the current thread, stops anything else from executing on the thread  
- Example:  
```kt  
Thread.freeze();  
```  
  
### `Thread.runThreaded(function)`  
- Description: This starts a new thread and runs a function on it, the thread will   
terminate when it finishes executing the function, threads will stop automatically   
when the program stops, you are also able to stop threads by using the Thread value  
- Parameter - Function (`function`): the function you want to run on a new thread  
- Returns - Thread: the new thread  
- Example:  
```kt  
Thread.runThreaded(fun() {  
 print("Running asynchronously!");});  
```  
  
### `Thread.runThreaded(name, function)`  
- Description: This starts a new thread with a specific name and runs a function on it  
- Parameters:  
  - String (`name`): the name of the thread  
  - Function (`function`): the function you want to run on a new thread  
- Returns - Thread: the new thread  
- Example:  
```kt  
Thread.runThreaded("MyThread", fun() {  
 print("Running asynchronously on MyThread!");});  
```  
  
### `Thread.getCurrentThread()`  
- Description: This gets the current thread that the code is running on  
- Returns - Thread: the current thread  
- Throws - Error:  
  - `'Thread is not safe to get'`  
- Example:  
```kt  
Thread.getCurrentThread();  
```  
  
  
# Trade class  
Trade class for Arucas.  
  
This class represents a trade offer, and allows you to get information about it.  
  
Import with `import Trade from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<Trade>.getUses()`  
- Description: Gets the number of times the trade has been used  
- Returns - Number: the number of uses  
- Example:  
```kt  
trade.getUses();  
```  
  
### `<Trade>.getMaxUses()`  
- Description: Gets the maximum number of times the trade can be used  
- Returns - Number: the maximum number of uses  
- Example:  
```kt  
trade.getMaxUses();  
```  
  
### `<Trade>.getSpecialPrice()`  
- Description: This gets the special price which is used to adjust the price of the first buy item  
- Returns - Number: the special price  
- Example:  
```kt  
trade.getSpecialPrice();  
```  
  
### `<Trade>.getSecondBuyItem()`  
- Description: Gets the second item that the merchant will buy  
- Returns - ItemStack: the second item to buy  
- Example:  
```kt  
trade.getSecondBuyItem();  
```  
  
### `<Trade>.getPriceMultiplier()`  
- Description: Gets the price multiplier which is used to adjust the price of the first buy item  
- Returns - Number: the price multiplier  
- Example:  
```kt  
trade.getPriceMultiplier();  
```  
  
### `<Trade>.getAdjustedFirstBuyItem()`  
- Description: Gets the first item that the merchant will buy, adjusted by the price multiplier  
- Returns - ItemStack: the first item to buy  
- Example:  
```kt  
trade.getAdjustedFirstBuyItem();  
```  
  
### `<Trade>.getSellItem()`  
- Description: Gets the item that is being sold by the merchant  
- Returns - ItemStack: the item for sale  
- Example:  
```kt  
trade.getSellItem();  
```  
  
### `<Trade>.getFirstBuyItem()`  
- Description: Gets the first item that the merchant will buy  
- Returns - ItemStack: the first item to buy  
- Example:  
```kt  
trade.getFirstBuyItem();  
```  
  
  
  
# Type class  
Type class for Arucas.  
  
This class lets you get the type of a class or value.  
  
Class does not need to be imported.  
  
Fully Documented.  
  
## Methods  
  
### `<Type>.getStaticMethod(name, parameters)`  
- Description: This gets the static method of the type  
- Parameters:  
  - String (`name`): the name of the method  
  - Number (`parameters`): the number of parameters for the method  
- Returns - Function: the static method of the type  
- Example:  
```kt  
String.type.getStaticMethod('nonExistent', 0);  
```  
  
### `<Type>.getName()`  
- Description: This gets the name of the type  
- Returns - String: the name of the type  
- Example:  
```kt  
String.type.getName();  
```  
  
### `<Type>.getConstructor(parameters)`  
- Description: This gets the constructor of the type  
- Parameter - Number (`parameters`): the number of parameters for the constructor  
- Returns - Function: the constructor of the type  
- Example:  
```kt  
String.type.getConstructor(0);  
```  
  
### `<Type>.instanceOf(type)`  
- Description: This checks whether a type is a subtype of another type  
- Parameter - Type (`type`): the other type you want to check against  
- Returns - Boolean: whether the type is of that type  
- Example:  
```kt  
Type.of('').instanceOf(Number.type);  
```  
  
## Static Methods  
  
### `Type.of(value)`  
- Description: This gets the specific type of a value  
- Parameter - Value (`value`): the value you want to get the type of  
- Returns - Type: the type of the value  
- Example:  
```kt  
Type.of(0);  
```  
  
  
# World class  
World class for Arucas.  
  
This class represents worlds, and allows you to interact with things inside of them.  
  
Import with `import World from Minecraft;`  
  
Fully Documented.  
  
## Methods  
  
### `<World>.getLight(pos)`  
- Description: Gets the light level at the given position  
- Parameter - Pos (`pos`): the position of the block  
- Returns - Number: the light level  
- Example:  
```kt  
world.getLight(new Pos(0, 100, 0));  
```  
  
### `<World>.getLight(x, y, z)`  
- Description: Gets the light level at the given position  
- Parameters:  
  - Number (`x`): the x position of the block  
  - Number (`y`): the y position of the block  
  - Number (`z`): the z position of the block  
- Returns - Number: the light level  
- Example:  
```kt  
world.getLight(0, 100, 0);  
```  
  
### `<World>.getDimensionName()`  
- Deprecated: You should use 'world.getId()' instead  
- Description: This will get the id of the world  
- Returns - String: the id of the world, for example: 'overworld'  
- Example:  
```kt  
world.getDimensionName();  
```  
  
### `<World>.getClosestPlayer(entity, maxDistance)`  
- Description: This will get the closest player to another entity in the world  
- Parameters:  
  - Entity (`entity`): the entity to get the closest player to  
  - Number (`maxDistance`): the maximum distance to search for a player in blocks  
- Returns - Player: the closest player, null if not found  
- Example:  
```kt  
world.getClosestPlayer(Player.get(), 100);  
```  
  
### `<World>.getFullId()`  
- Description: This will get the full id of the world  
- Returns - String: the full id of the world, for example: 'minecraft:overworld'  
- Example:  
```kt  
world.getFullId();  
```  
  
### `<World>.getId()`  
- Description: This will get the id of the world  
- Returns - String: the id of the world, for example: 'overworld'  
- Example:  
```kt  
world.getId();  
```  
  
### `<World>.getAllEntities()`  
- Description: This will get all entities in the world  
- Returns - List: a list of all entities  
- Example:  
```kt  
world.getAllEntities();  
```  
  
### `<World>.getBlockAt(pos)`  
- Description: This function gets the block at the given coordinates  
- Parameter - Pos (`pos`): the position  
- Returns - Block: the block at the given coordinates  
- Example:  
```kt  
world.getBlockAt(new Pos(0, 100, 0));  
```  
  
### `<World>.getBlockAt(x, y, z)`  
- Description: This function gets the block at the given coordinates  
- Parameters:  
  - Number (`x`): the x coordinate  
  - Number (`y`): the y coordinate  
  - Number (`z`): the z coordinate  
- Returns - Block: the block at the given coordinates  
- Example:  
```kt  
world.getBlockAt(0, 100, 0);  
```  
  
### `<World>.getOtherPlayer(username)`  
- Description: This gets another player from the given username  
- Parameter - String (`username`): the username of the other player  
- Returns - Player: the other player, null if not found  
- Example:  
```kt  
world.getOtherPlayer('senseiwells');  
```  
  
### `<World>.getEntityFromId(entityId)`  
- Description: This will get an entity from the given entity id  
- Parameter - Number (`entityId`): the entity id  
- Returns - Entity: the entity, null if not found  
- Example:  
```kt  
world.getEntityFromId(1);  
```  
  
### `<World>.getEmittedRedstonePower(pos, direction)`  
- Description: Gets the emitted restone power at the given position and direction  
- Parameters:  
  - Pos (`pos`): the position of the block  
  - String (`direction`): the direction to check, for example 'north', 'east', 'up', etc.  
- Returns - Number: the emitted redstone power  
- Example:  
```kt  
world.getEmittedRedstonePower(new Pos(0, 100, 0), 'north');  
```  
  
### `<World>.getEmittedRedstonePower(x, y, z, direction)`  
- Description: Gets the emitted restone power at the given position and direction  
- Parameters:  
  - Number (`x`): the x position of the block  
  - Number (`y`): the y position of the block  
  - Number (`z`): the z position of the block  
  - String (`direction`): the direction to check, for example 'north', 'east', 'up', etc.  
- Returns - Number: the emitted redstone power  
- Example:  
```kt  
world.getEmittedRedstonePower(0, 100, 0, 'north');  
```  
  
### `<World>.setGhostBlock(block, pos)`  
- Deprecated: This function is dangerous, use at your own risk  
- Description: This sets a ghost block in the world as if it were a real block, may cause issues  
- Parameters:  
  - Block (`block`): the block to set  
  - Pos (`pos`): the position of the block  
- Example:  
```kt  
world.setGhostBlock(Material.BEDROCK.asBlock(), new Pos(0, 100, 0));  
```  
  
### `<World>.setGhostBlock(block, x, y, z)`  
- Deprecated: This function is dangerous, use at your own risk  
- Description: This sets a ghost block in the world as if it were a real block, may cause issues  
- Parameters:  
  - Block (`block`): the block to set  
  - Number (`x`): the x position of the block  
  - Number (`y`): the y position of the block  
  - Number (`z`): the z position of the block  
- Example:  
```kt  
world.setGhostBlock(Material.BEDROCK.asBlock(), 0, 100, 0);  
```  
  
### `<World>.getAllOtherPlayers()`  
- Description: This will get all other players in the world  
- Returns - List: a list of all other players  
- Example:  
```kt  
world.getAllOtherPlayers();  
```  
  
### `<World>.renderParticle(particleId, pos)`  
- Description: This will render a particle in the world, you can find a list of all  
the particle ids [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Particles)  
- Parameters:  
  - String (`particleId`): the id of the particle  
  - Pos (`pos`): the position of the particle  
- Throws - Error:  
  - `'Particle Invalid'`  
- Example:  
```kt  
world.renderParticle('end_rod', pos);  
```  
  
### `<World>.renderParticle(particleId, x, y, z)`  
- Description: This will render a particle in the world, you can find a list of all  
the particle ids [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Particles)  
- Parameters:  
  - String (`particleId`): the id of the particle  
  - Number (`x`): the x position of the particle  
  - Number (`y`): the y position of the particle  
  - Number (`z`): the z position of the particle  
- Throws - Error:  
  - `'Particle Invalid'`  
- Example:  
```kt  
world.renderParticle('end_rod', 10, 10, 10);  
```  
  
### `<World>.renderParticle(particleId, pos, velX, velY, velZ)`  
- Description: This will render a particle in the world with a velocity, you can find a list of all  
the particle ids [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Particles)  
- Parameters:  
  - String (`particleId`): the id of the particle  
  - Pos (`pos`): the position of the particle  
  - Number (`velX`): the velocity of the particle on the x axis  
  - Number (`velY`): the velocity of the particle on the y axis  
  - Number (`velZ`): the velocity of the particle on the z axis  
- Throws - Error:  
  - `'Particle Invalid'`  
- Example:  
```kt  
world.renderParticle('end_rod', pos, 0.5, 0.5, 0.5);  
```  
  
### `<World>.getTimeOfDay()`  
- Description: This will get the time of day of the world  
info on the time of day [here](https://minecraft.fandom.com/wiki/Daylight_cycle)  
- Returns - Number: the time of day of the world, between 0 and 24000  
- Example:  
```kt  
world.getTimeOfDay();  
```  
  
### `<World>.isThundering()`  
- Description: This will check if the world is currently thundering  
- Returns - Boolean: true if the world is currently thundering  
- Example:  
```kt  
world.isThundering();  
```  
  
### `<World>.isAir(pos)`  
- Description: Returns true if the block at the given position is air  
- Parameter - Pos (`pos`): the position of the block  
- Returns - Boolean: true if the block is air  
- Example:  
```kt  
world.isAir(new Pos(0, 100, 0));  
```  
  
### `<World>.isAir(x, y, z)`  
- Description: Returns true if the block at the given position is air  
- Parameters:  
  - Number (`x`): the x position of the block  
  - Number (`y`): the y position of the block  
  - Number (`z`): the z position of the block  
- Returns - Boolean: true if the block is air  
- Example:  
```kt  
world.isAir(0, 100, 0);  
```  
  
### `<World>.isRaining()`  
- Description: This will check if the world is currently raining  
- Returns - Boolean: true if the world is currently raining  
- Example:  
```kt  
world.isRaining();  
```  
  
### `<World>.getArea(pos1, pos2)`  
- Description: This gets a list of all block positions between the two positions  
- Parameters:  
  - Pos (`pos1`): the first position  
  - Pos (`pos2`): the second position  
- Returns - List: the list of positions  
- Example:  
```kt  
world.getArea(new Pos(0, 100, 0), new Pos(0, 100, 0));  
```  
  
### `<World>.getAreaOfBlocks(pos1, pos2)`  
- Description: This gets a list of all blocks (with positions) between the two positions  
- Parameters:  
  - Pos (`pos1`): the first position  
  - Pos (`pos2`): the second position  
- Returns - List: the list of blocks  
- Example:  
```kt  
world.getAreaOfBlocks(new Pos(0, 100, 0), new Pos(0, 100, 0));  
```


#


# Events  
  
Events are triggers for certain events that happen in the game. ClientScript provides a way to hook into these triggers to be able to run your code. You can register multiple functions to an event and they will all get called. [See here](#gameevent-class) on how to register and unregister events. Each event will run async by default but you are able to run it on the main game thread.  
  
## Available Events  
  
### `"onClientTick"`  
  
- This event is fired on every client tick  
- Cancellable: `false`  
  
### `"onHealthUpdate"`  
  
- This event is fired when the player's health changes  
- Argument - Number (`health`): The new health  
- Cancellable: `false`  
  
### `"onTotem"`  
  
- This event is fired when the player uses a totem  
- Cancellable: `false`  
  
### `"onCloseScreen"`  
  
- This event is fired when the player closes a screen  
- Argument - Screen (`screen`): The closed screen  
- Cancellable: `false`  
  
### `"onConnect"`  
  
- This event is fired when the player connects to the server  
- Argument - Player (`player`): The player entity  
- Argument - World (`world`): The world the player joined  
- Cancellable: `false`  
  
### `"onDisconnect"`  
  
- This event is fired when the player disconnects from the server  
- Cancellable: `false`  
  
### `"onOpenScreen"`  
  
- This event is fired when the player opens a screen  
- Argument - Screen (`screen`): The opened screen  
- Cancellable: `false`  
  
### `"onPickUpItem"`  
  
- This event is fired when the player picks up an item  
- Argument - ItemStack (`itemStack`): The item stack that was picked up  
- Cancellable: `false`  
  
### `"onFishBite"`  
  
- This event is fired when a fish bites the player's fishing rod  
- Argument - Entity (`entity`): The fishing bobber entity  
- Cancellable: `false`  
  
### `"onDeath"`  
  
- This event is fired when the player dies  
- Argument - Entity (`entity`): The entity that killed the player  
- Argument - Text (`message`): The death message  
- Cancellable: `false`  
  
### `"onRespawn"`  
  
- This event is fired when the player respawns  
- Argument - Player (`player`): The respawned player entity  
- Cancellable: `false`  
  
### `"onEat"`  
  
- This event is fired when the player eats something  
- Argument - ItemStack (`itemStack`): The item stack that was eaten  
- Cancellable: `false`  
  
### `"onGamemodeChange"`  
  
- This event is fired when the player changes their gamemode  
- Argument - String (`gamemode`): The new gamemode  
- Cancellable: `false`  
  
### `"onBlockBroken"`  
  
- This event is fired when the player breaks a block  
- Argument - Block (`block`): The block that was broken with the position  
- Cancellable: `false`  
  
### `"onBlockPlaced"`  
  
- This event is fired when the player places a block  
- Argument - Block (`block`): The block that was placed with the position  
- Cancellable: `false`  
  
### `"onDimensionChange"`  
  
- This event is fired when the player changes their dimension  
- Argument - World (`world`): The new world  
- Cancellable: `false`  
  
### `"onPlayerJoin"`  
  
- This event is fired when a player joins the server  
- Argument - String (`name`): The player's name  
- Cancellable: `false`  
  
### `"onPlayerLeave"`  
  
- This event is fired when a player leaves the server  
- Argument - String (`name`): The player's name  
- Cancellable: `false`  
  
### `"onEntitySpawn"`  
  
- This event is fired when an entity spawns, this does not include mobs  
- Argument - Entity (`entity`): The entity that was spawned  
- Cancellable: `false`  
  
### `"onMobSpawn"`  
  
- This event is fired when a mob spawns  
- Argument - LivingEntity (`entity`): The mob that was spawned  
- Cancellable: `false`  
  
### `"onEntityRemoved"`  
  
- This event is fired when an entity is removed  
- Argument - Entity (`entity`): The entity that was removed  
- Cancellable: `false`  
  
### `"onScriptPacket"`  
  
- This event is fired when a script packet is received from scarpet  
- Argument - List (`packet`): A list of data that was received  
- Cancellable: `false`  
  
### `"onPlayerLook"`  
  
- This event is fired when the player changes their yaw and/or pitch  
- Argument - Number (`yaw`): The new yaw  
- Argument - Number (`pitch`): The new pitch  
- Cancellable: `true`  
  
### `"onPickBlock"`  
  
- This event is fired when the player picks a block  
- Argument - ItemStack (`itemStack`): The item stack that was picked  
- Cancellable: `true`  
  
### `"onAttack"`  
  
- This event is fired when the player attacks  
- Cancellable: `true`  
  
### `"onUse"`  
  
- This event is fired when the player uses  
- Cancellable: `true`  
  
### `"onKeyPress"`  
  
- This event is fired when a key is pressed  
- Argument - String (`key`): The key that was pressed  
- Cancellable: `true`  
  
### `"onKeyRelease"`  
  
- This event is fired when a key is released  
- Argument - String (`key`): The key that was released  
- Cancellable: `true`  
  
### `"onDropItem"`  
  
- This event is fired when the player tries to drop an item  
- Argument - ItemStack (`itemStack`): The item stack that was dropped  
- Cancellable: `true`  
  
### `"onInteractItem"`  
  
- This event is fired when the player interacts with an item  
- Argument - ItemStack (`itemStack`): The item stack that was interacted with  
- Cancellable: `true`  
  
### `"onInteractBlock"`  
  
- This event is fired when the player interacts with a block  
- Argument - Block (`block`): The block that was interacted with  
- Argument - ItemStack (`itemStack`): The item stack that was interacted with  
- Cancellable: `true`  
  
### `"onInteractEntity"`  
  
- This event is fired when the player interacts with an entity  
- Argument - Entity (`entity`): The entity that was interacted with  
- Argument - ItemStack (`itemStack`): The item stack that was interacted with  
- Cancellable: `true`  
  
### `"onSendMessage"`  
  
- This event is fired when the player sends a message in chat  
- Argument - String (`message`): The message that was sent  
- Cancellable: `true`  
  
### `"onReceiveMessage"`  
  
- This event is fired when the player receives a message in chat  
- Argument - String (`uuid`): The sender's UUID  
- Argument - String (`message`): The message that was received  
- Cancellable: `true`  
  
### `"onClickSlot"`  
  
- This event is fired when the player clicks a slot  
- Argument - Number (`slot`): The slot that was clicked  
- Argument - String (`actionType`): The action that was used
- Cancellable: `true`  

### `"onAnvil"`

- This event is fired when the player anvils an item
- Argument - ItemStack (`first`): The first input
- Argument - ItemStack (`second`): The second input
- Argument - ItemStack (`result`): The result of the first and second inputs
- Argument - String (`newName`): The new name of the item stack
- Argument - Number (`levelCost`): The amount of xp levels the anvilling costs
- Cancellable: `false`    

### `"onAttackBlock"`  
  
- This event is fired when the player attacks a block  
- Argument - Block (`block`): The block that was attacked  
- Cancellable: `true`  
  
### `"onAttackEntity"`  
  
- This event is fired when the player attacks an entity  
- Argument - Entity (`entity`): The entity that was attacked  
- Cancellable: `true`
