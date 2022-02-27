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

## Logical Operators:

`&&` - This is the logical AND

`||` - This is the logical OR

`!` - This is the logical NOT

`==` - This evaluates whether two objects are equal

`>` - This evaluates whether a number is more than another

`<` - This evaluates whether a number is less than another

`>=` - This evaluates whether a number is greater than or equal to another

`<=` - This evaluates whether a number is less than or equal to another

One thing to note for AND and OR is that the left side will always be evaluated first, and if it does not evaluate to `true` in case of AND, or `false` in the case of OR, the right side will not be evalutated.

Another thing to note is that custom classes are able to override some of these operators changing their functionality, more information will be on this in the classes section.

## Comments:

You are able to make comments in your code that the compiler will ignore.

`//` - Used to comment until a line break

`/* */` - Used for multi-line comments

## Keywords:


### `{` and `}` 

- These are used to define scopes, or code blocks
- Scopes can contain multiple lines of code inside then and usually is idented to visually show it's in a different scope. Any variables initialised inside of a scope cannot be accessed outside of that scope, but variables defined outside of the scope can be accessed and assigned inside of that scope, scopes can be used independantly as well as with other statements.

Example:
```kt
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
```kt
fun doSomething() {
    print("something");
}

fun doSomethingElse(foo) {
    print(foo);
}

doSomething();
```

A thing to note is that the language is not fussy with how you format you code, in terms of new lines and spaces. So formatting like this is considered valid:

```kt
fun doSomething()
{
    if (true) print("");
}
```

### `return` 

- This is for escaping out of a function or file
- You are able to return a value, however this is not required. If there is no return statement in a function it will automatically return `null`, you can also return a value out of a file.

Examples:
```kt
fun doSomething() {
    return "something";
}

return doSomething();
```

### `if`, `else if`, and `else` 

- These are for evaluating boolean expressions
- You cannot have `else if`s and `else` without an `if`, if one of these has an expression evaluates to true the code inside of their code block will be executed, and the rest will be ignored.

Examples:
```kt
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

- These are for matching strings and numbers
- Using a switch statement is much better when you have a large number of strings or numbers to evaluate, you can have multiple values for each case. The default case is run if the inputted value matches none of the cases, but a default case is not required.

Example:
```kt
number = 4;
switch (number) {
    case 1, 2, 3 -> {
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
```kt
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
```kt
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
```kt
// this does the same as the previous for loop example, just more consise
list = [4, 5, 2, 7];
for (value : list) {
    print(value);
}
```

### `continue` 

- This allows you to return to the top of a loop

Example:
```kt
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
```kt
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

### `try` and `catch` 

- These are used to handle exceptions

- `catch` can only catch `RuntimeError`s, the parameter will contain the error's message, if errors go uncaught they will crash the program.

Example:
```kt
try {
    null();
}
catch(error) {
    print(error);
}
```

### `class` 

- This is used to define a `class`
- Classes allow for encapsulation, wrapping other objects (values) into a single object, this class defines that single object and what that object is able to do. 
- If a class has no constructors you will be able to construct that class with no parameters. Classes also allow you to define methods, or class functions.  You can overload constructors, and methods in a class by differing the number of parameters.
- You can initialise the class members in the constructor, or initialise them when you define them. If you do not define them they will default to being `null`.

Example:
```kt
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
```kt
class Example {
    var pi = 3.14;
    var name = "sensei";
}
```

### `.` 

- This is used to access members of an object
- This can be used on `class` names for `static` members or on an object for the object members.

Example:
```kt
class Example {
    var number = 10;

    fun printNumber() {
        print(this.number);
    }
}

example = new Example();

// these two do the same thing
print(example.number);
example.printNumber();
```

### `this` 

- This is used for refering to itself inside a class
- `this` is passed in internally, and you will have access to it inside a class constructor, method, or operator method, `this` allows you to refer to all of the members inside of your class, you can assign, access, or call them.

Example:
```kt
class Example {
    var number = 10;

    fun setNumber(newNumber) {
        this.number = newNumber;
    }

    fun resetNumber() {
        this.number = 10;
    }
}
``` 

### `new` 

- This is used to construct a new object
- This is used for custom classes, as the built in objects cannot be constructed, as they have literals. This will return a new instance of that object.

Examples:
```kt
class Example {
    var number = 10;
    
    Example() { }
    
    Example(number) {
        this.number = number;
    }
}

defaultExample = new Example();
myExample = new Example(20);
```

### `operator` 

- This allows you to override operator methods for an object
- An important thing to note about this is that it will be the left side's operator method that will get used, for example `a + b` would result in `a`'s plus operator getting called not `b`'s. Whereas `b + a` would result in `b`'s plus operator getting called not `a`'s
- The operators that you can override are: `+`, `-`, `*`, `/`, `^`, `<`, `<=`, `>`, `>=`, `==`, and `!`

Examples:
```kt
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
```kt
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

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

## Built-in Functions:

These are the functions that Arucas Supports:

These functions do not need any class to be called, just a regular function, Anything inside brackets are parameters and these values are used in the function to perform an action

All functions can Throw an error if you input the incorrect Value type

### `run(filePath)`

- This is used to run a `.acuras` file, you can use one script to run other scripts
- Parameter - String: as a file path 
- Returns - Value: any value that the file returns
- Throws: `"Failed to execute script..."`
- Example: `run("E:/foo/bar.acuras");`

### `runFromString(string)`

- This allows you execute code directly from a string
- Parameter - String: the code you would like to execute
- Example: `runFromString("pi = 3.14; print(pi)");`

### `stop()`

- This is used to stop a program
- Example: `stop();`

### `sleep(milliseconds)`

- This pauses your program for set amount of ms
- Parameter - Number: any number that you want to sleep for in ms
- Example: `sleep(1000);`

### `print(value)`

- This is used to print a string value to console
- Parameter - Value: any value that you want to print
- Examples: `print("Hello World");`, `print(90);`

### `input(prompt)`

- This is used to take an input from the user in the console
- Parameter - String: the prompt you want to send the user for their input
- Returns - String: the input of the user
	- Examples - `"pizza"`, `"sleep"`
- Example: `input("What's your name? ");`

### `debug(boolean)`

- This is used to enable debug mode, which just prints all returns to console
- Parameter - Boolean: whether you want it on or of
- Example: `debug(true);`

### `suppressDeprecated(boolean)`

- This is used to suppress deprecation warning printing
- Parameter - Boolean: whether you want it on or of
- Example: `suppressDeprecated(true);`

### `random(bound)`

- This gets a pseudo random integer between 0 and the bound
- Parameter - Number: the maximum bound you want (exclusive)
- Returns - Number: a random number
	- Example - `5`
- Example: `random(10);`

### `getTime()`

- This gets the current time as a string
- Returns - Number: the current time
	- Example - `00:18:00`
- Example: `getTime();`

### `getNanoTime()`

- This gets the current system time in nano seconds
- Returns - Number: the current time
- Example: `getNanoTime();`

### `len(value)`

- Returns the length of a value passed in, works with strings and lists
- Parameter - String/List/Map: any string or list or map
- Returns - Number: the length of the value
	- Example - `34`
- Throws: `Cannot pass ... into len()`
- Example: `len("What is the length of this string?");`

### `callFunctionWithList(function, parameters)`

- This allows you to call a function with a list of values as arguments, similar to `runThreaded` but not on a separate thread
- Parameters - Function, List: any function or lambda, a list of parameters (empty list if no parameters)
- Examples: `callFunctionWithList(print, ["cool"]);`

### `throwRuntimeError(message)`

- This allows you to throw a runtime error
- Parameters - String: the message for the error
- Throws: `...`
- Example: `throwRuntimeError("I'm throwing this error!");`

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

# Built-in Classes

These are classes that come with Arucas by default. You are able to use any of these values and functions!

# Value classes

This class cannot be constructed, it is the base for all other classes, every other value has these functions

## Member Functions

### `<Value>.instanceOf(valueType)`

-   This allows you to check if a value is an instance of a class
-   Parameter - String: name of a value
-   Returns - Boolean: whether the value is an instance of valueType
    -   Examples -  `true`,  `false`
-   Example:  
```kt
str = "string"; 
if (str.instanceOf("String")) { 
    print("This is a string!"); 
}
```

### `<Value>.getValueType()`

-   This gets the value type
-   Returns - String: the value type of the value
    -   Examples -  `"String"`,  `"Number"`
-   Example:  `[].getValueType();`,  `"foo".getValueType();`


### `<Value>.copy()`

-   This allows you to copy a value, this depends on the value you are copying from, some values cannot be copied so this will just return the original value
-   Returns - Value: the value you called copy from
    -   Examples -  `"foo"`,  `false`,  `[]`
-   Example:  `list = [1, 2]; newList = list.copy();`

### `<Value>.toString()`

-   This converts the current value into a string
-   Returns - String: the string representation of the value
    -   Example -  `"false"`
-   Examples:  `numberString = 9.toString();`,  `listString = [1, 2, 3].toString();`

### `<Value>.hashCode()`

- This returns the hashcode of the value, this is used inside maps to quickly identify matches
- Returns - Number: the hashcode
- Example: `"example".hashCode();`

### `<Value>.equals(other)`

- This returns whether a value is equal to another value. This equals is different to `==`, it is used inside lists and maps to determine if a value is inside. Generally you are safer using this then `==`
- Parameter - Value: another value you are comparing to
- Returns - Boolean: whether the two values are equal
- Example: `"foo".equals("bar");`

# String class

This class cannot be constructed, instead you use string literals to represent strings. Strings are immutable.

## Member Functions

### `<String>.toList()`

- This converts a string to a list of single character strings
- Returns - List: the character list of the string
	- Example -`["h", "e", "l", "l", "o", " ", "w", "o", "r", "l", "d"]`
- Example: `"hello world".toList()`

### `<String>.replaceAll(regex, replacement)`

- This allows you to remove parts of a string using regex
- Parameters - String, String: the string you want to modify, the regex, the replacement
- Returns - String: the string but with a regex replaced
	- Example - `"this is random"`
- Example: `randomString = "this/is/random"; randomString = randomString.replaceAll("/", " ");`

### `<String>.uppercase()`

- This will make the string uppercase
- Returns - String: the uppercase string
	- Example - `"HELLO WORLD"`
- Example: `randomString = "this is random"; randomString = randomString.uppercase();`

### `<String>.lowercase()`

- This will make the string lowercase
- Returns - String: the lowercase string
	- Example - `"hello world"`
- Example: `randomString = "THiS iS rANdOm"; randomString = randomString.lowercase();`

### `<String>.toNumber()`

- This will try to convert a string to a number
- Returns - Number: the number representation of a string
	- Example - `1000`
- Throws: `"Cannot parse ... as a NumberValue"`
- Example: `randomString = "1000"; randomNumber = randomString.toNumber();`

### `<String>.formatted(listOfValues)`

- This will format a string with the values you input, use `"%s"` in your string and any values will replace `"%s"` in order given in the list
- Parameter - List: the list of values you want to insert
- Returns - String: a formatted string
	- Example - `"Hi James! Have a good day!"`
- Throws: `"You are missing values to be formatted!"`
- Example: `"Hi %s! Have a %s day!".formatted(["James", "good"]);`

### `<String>.contains(otherString)`

- This will check whether the string contains another string within it
- Parameter - String: another string
- Returns - Boolean: whether the string contained the other string
- Example: `"coolwords".containsString("words");`

### `<String>.strip()`

- This removes all extra whitespaces from the string
- Returns - String: the stripped down string
	- Example: `"foo bar"`
- Example: `"foo     bar".strip();`

### `<String>.capitalise()`

- This makes the first character of the string capital
- Returns - String: the capitalised string 
	- Example: `"Foo"`
- Example: `"foo".capitalise();`

### `<String>.split(delimiter)`

- This lets you split a string into multiple strings in a list
- Parameter - String: the delimiter you want to use
- Returns - List: the list of string
	- Example: `["foo", "bar", "baz"]`
- Example: `"foo:bar:baz".split(":");`

### `<String>.subString(fromIndex, toIndex)`

- This lets you get a sub string of a string
- Parameters - Number, Number: the index of the start of the sub string, the index of the end of the substring
- Returns - String: the sub string
- Throws: `"Index out of bounds"`
- Example: `str = "foo bar"; str.subString(3, len(str));`

# Number class

This class cannot be constructed, it has a literal representation, just numbers. There are many other Number functions in the [Math class](#math-class)

## Member Functions

### `<Number>.round()`

- This will round the number to the nearest integer
- Returns - Number: a rounded number
	- Example - `10`
- Examples: `9.99.round();`, `number = 8.77; number = number.round();`

### `<Number>.ceil()`

- This will always round the number up
- Returns - Number: the number rounded down
	- Example - `10`
- Examples: `9.1.ceil();`, `number = 8.1; number = number.ceil();` 

### `<Number>.floor()`

- This will always round the number down
- Returns - Number: the number rounded up
	- Example - `10`
- Examples: `10.9.floor();`, `number = 8.77; number = number.floor();` 

### `<Number>.isNan()`

- This will evaluate whether the number is not a number
- Returns - Boolean: whether the number is not a number
	- Examples - `true`, `false`
- Example: `arccos(2).isNan();`

### `<Number>.isInfinite()`

- This will evaluate whether the number is infinite
- Returns - Boolean: whether the number is infinite
	- Examples - `true`, `false`
- Example: `(10/0).isInfinite();`

# Boolean class

This class cannot be constructed, booleans have a literal representation, just `true` or `false`. Booleans have no members, but are able to function with many operators.

# Null class

This class cannot be constructed, null has a literal representation, just `null`. Null does not have any members.

# List class

This class cannot be constructed, it has a literal representation, just `[]`.

## Member Functions

### `<List>.get(index)`

- This will get the value of an index in a list, indexes start at 0
- Parameter - Number: the index you want to get
- Returns - Value: the value at the index
	- Examples - `100`, `"this could be anything!"`, `["another list"]`
- Throws: `"Index is out of bounds"`
- Example: `["very cool list"].getIndex(0);`

### `<List>.remove(index)`

- This will remove the value of an index in a list, it will return the value you removed
- Parameter - Number: the index you want to remove
- Returns - Value: the value at the index
	- Examples - `100`, `"this could be anything!"`, `["another list"]`
- Throws: `"Index is out of bounds"`
- Example: `["very cool list"].removeIndex(0);`

### `<List>.append(value)`

- This will append a Value to the end of the list
- Parameter - Value: any value you want to add to the list
- Returns - List: the modified list
	- Example - `["foo", "bar"]`
- Example: `[].append("first!").append("second!");`

### `<List>.insert(value, index)`

- This will insert a Value into an index in the list
- Parameters - Value, Number: the value you want to insert, the index you want to insert it to
- Returns - List: the modifier list
- Throws: `"Index is out of bounds"`
- Example: `["foo", "bar"].insert("baz", 1);`

### `<List>.concat(otherList)`

- This will concatenate two lists together
- Parameter - List: the other list you want to concatenate with
- Returns - List: the modified list
	- Example - `["foo", "bar"]`
- Example: `[].concat(["first", "second"]).concat(["third"]);` 

### `<List>.contains(value)`

- This allows you to check wether a list contains a certain value
- Parameter - Value - any value you want to check
- Returns - Boolean: whether the list contains value
	- Examples - `true`, `false`
- Example: `["sensei"].contains("sensei");`

### `<List>.containsAll(otherList)`

- This will check whether a list contains all of the values in another list
- Parameter - ListValue: Exmamples - `[1, 2]`, `["foo", "bar"]`
- Returns - Boolean: whether the list contains all of the values in otherList
	- Examples: `true`, `false`
- Example: `["foo", "bar", "baz"].containsAll(["foo", "baz"]);`

### `<List>.isEmpty()`

- This will check whether the list is empty of not
- Returns - Boolean: whether the list is empty
	- Examples: `true`, `false`
- Example: `[].isEmpty();`

### `<List>.clear()`

- This will clear the list of all it's values
- Example: `["foo"].clear();`

# Map class

This class cannot be constructed, it has a literal representation, just `{}`.

## Member Functions

### `<Map>.get(key)`

- This will get the value for a key, cannot be `null`
- Parameter - Value: any value that you want to get the value for
- Returns - Value: the value of the key
	- Examples - `"foo"`, `false`, `[]`
- Throws: `"Cannot get null from a map"`
- Example: `{1 : "one"}.get(1);`

### `<Map>.getKeys()`

- This will return all the keys that are in the map
- Returns - List: a list of all the keys
	- Example - `[1, 2, 3, 4]`
- Example: `{1 : "one", 2 : "two", 3 : "three", 4 : "four"}.getKeys();`

### `<Map>.getValues()`

-  This will return all the values that are in the map
- Returns - List: a list of all the values
	- Example - `["one", "two", "three", "four"]`
- Example: `{1 : "one", 2 : "two", 3 : "three", 4 : "four"}.getValues();`

### `<Map>.put(key, value)`

- This will put a key and value into the map, cannot be null, will return the value that you put in
- Parameters - Value, Value: first parameter being the key, second being any value
- Returns - Value: the value that you inputted
	- Examples - `"foo"`, `true`, `[]`
- Throws: `"Cannot put null into a map"`
- Example: `map = {}; map.put(1, "one");`

### `<Map>.putIfAbsent(key, value)`

- This will put a key and value into the map, only if the key doesn't exist in the map already, cannot be null, will return the value that you put in
- Parameters - Value, Value: first parameter being the key, second being any value
- Returns - Value: the value that you inputted
	- Examples - `"foo"`, `true`, `[]`
- Throws: `"Cannot put null into a map"`
- Example: `map = {1, "one"}; map.putIfAbsent(1, "two");`

### `<Map>.putAll(anotherMap)`

- This allows you to put all keys and values of a map into another map 
- Parameter - Map: the map you want to merge
- Example: `map = {1 : "one"}; map.putAll({2 : "two", 3 : "three"});`

### `<Map>.remove(key)`

- This allows you to remove a key and value from a map
- Parameter - Value: the key value that you want to remove from the map
- Returns - Value: the value that you removed
	- Examples - `"foo"`, `false`, `[]`
- Throws: `"Cannot remove null from a map"`
- Example: `map = {1 : "one"}; map.remove(1);`

### `<Map>.clear()`

- This will empty the map of all it's keys and values
- Example: `map = {1 : "one", 2 : "two"}; map.clear();`

### `<Map>.isEmpty()`

- This will return whether the map is empty
- Example: `{ }.isEmpty();`

# Thread class

This class cannot be constructed, and is used to manipulate threads

## Static Member Functions

### `Thread.getCurrentThread()`

- This gets the current thread that you are currently running on
- Returns - Thread: the thread you are currently on
- Throws: `"Thread is not safe to get"`
- Example: `Thread.getCurrentThread();`

### `Thread.runThreaded(function)`

- This allows you to run a function on a different thread, this will default to giving the name `"Unnamed Arucas Thread"` to the thread
- Parameter - Function: a function that you want to run
- Returns - Thread: the new thread that you just started
- Example:
```kt
branchThread = Thread.runThreaded(fun() {
    print("This is running on a different thread!");
});
```

### `Thread.runThreaded(name, function)`

- This allows you to run a function on a different thread
- Parameters - String, Function: the you want to give the thread, a functino you want to run
- Returns - Thread: the new thread that you just started
- Example:
```kt
fun threadFunction() {
    print("This is running on a different thread!"");
}

myThread = Thread.runThreaded("myThread", threadFunction);
```

## Member Functions

This will be used for all examples:
```kt
thread = Thread.runThreaded("dummy", fun() { });
```

### `<Thread>.isAlive()`

- This allows you to check if a thread is still alive (running)
- Returns - Boolean: whether the thread is alive
- Example: `thread.isAlive();`

### `<Thread>.getAge()`

- This will return the thread's age in milliseconds, the age is the time since it started
- Returns - Number: the age of the thread
- Example: `thread.getAge();`

### `<Thread>.getName()`

- This will return the thread's name
- Returns - String: the name of the thread
- Example: `thread.getName();`

### `<Thread>.stop()`

- This will stop the thread from executing
- Throws: `"Thread is not alive"`
- Example: `thread.stop();`

# File class

This is a constructable class, the File class allows you to manipulate files

## Static Member Functions

### `File.getDirectory()`
-   This will get the current directory that the program is running in
-   Returns - File: a file with the path of the current directory
-   Example:  `File.getDirectory();`

## Constructors

### `new File(path)`

- This creates a new File value with the path given
- Parameter - String: the path of the file (that you want to access or create)
- Returns - File: the constructed File value

## Member Functions

Almost of these methods can throw errors if you are unable to modify files in a path because of your system's security settings.

This will be used for all examples:
```kt
file = new File("D:/cool/realDirectory");
```

### `<File>.getName()`

- This gets the name of the file
- Returns - String: the name of the file
- Example: `file.getName();`

### `<File>.read()`

- This will read the contents of a file
- Returns - String: the contents of the file as a string
- Throws: `"There was an error reading the file: ..."`
- Example: `file.readFile();`
- 
### `<File>.write(string)`

- This will write a string to a file
- Parameters - String: the string that you want to write
- Throws: `"There was an error writing the file: ..."`
- Example: `file.writeFile("this was saved from Arucas!");`

### `<File>.delete()`

- This will try to delete a file
- Throws: `"Could not delete file: ..."`
- Example: `file.delete();`

### `<File>.exists()`

- This will check whether a file exists in a path
- Returns - Boolean: whether the file exists
	- Example - `true`, `false`
- Example: `file.exists();`

### `<File>.getSubFiles()`

- This will return all the sub files in this file
- Returns - List: list of Files
- Throws: `"Could not find any files"`
- Example: `fileList = file .getSubFiles();`

### `<File>.createDirectory()`

- This will create directories to the specified path
- Returns - Boolean: whether the creation was successful
	- Example - `true`, `false`
- Example: `file.createDirectory();`

### `<File>.getPath()`

- This gets the relative path of the file
- Returns - String: the path of the file
- Example: `file.getPath();`

### `<File>.getAbsolutePath()`

- This gets the absolute path of the file
- Returns - String: the absolute path of the file
- Throws: `"..."`
- Example: `file.getAbsolutePath();`

### `<File>.open()`

- This tries to open the file, as if you were to click on the file
- Throws: `"An error occured while opening the file: ..."`
- Example: `file.open();`

# Math class

This class cannot be constructed, all of it's members are static

## Static Member variables

All of the Math member variables are immutable (you cannot assign to them)

### `Math.pi`

- This returns the value of `pi` - `3.14159265358979323846`

### `Math.e`

- This returns the value of `e` - `2.7182818284590452354`

### `Math.root2`

- This returns the value of `root2` - `1.41421356237309504880` 

## Static Member functions

All parameters for this class are expected to be Numbers

### `Math.round(value)`

-   This will round the number to the nearest integer
-   Returns - Number: a rounded number
    -   Example -  `10`
-   Examples:  `Math.round(9.99);`,  `number = 8.77; number = Math.round(number);`

### `Math.ceil(value)`

-   This will always round the number up
-   Returns - Number: the number rounded down
    -   Example -  `10`
-   Examples:  `Math.ceil(9.1);`,  `number = 8.1; number = Math.ceil(number);`

### `Math.floor(value)`

-   This will always round the number down
-   Returns - Number: the number rounded up
    -   Example -  `10`
-   Examples:  `Math.floor(10.9);`,  `number = 8.77; number = Math.floor(number);`

### `Math.sqrt(value)`

- This will calculate the square root of the value
- Returns - Number: the square root
	- Example - `5`
- Example: `Math.sqrt(25);`

### `Math.abs(value)`

- This returns the absolute value of the value
- Returns - Number: the absolute value
	- Example - `10`
- Example: `Math.abs(-10);`

### `Math.mod(value1, value2)`

- This returns the modulus of value1 by value2
- Returns - Number: the remainder
	- Example - `1`
- Example: `Math.mod(9, 2);`

### `Math.max(value1, value2)`

- This returns the value with the highest number
- Returns - Number: the higher number
	- Example - `25`
- Example: `Math.max(2, 25);`

### `Math.min(value1, value2)`

- This returns the value with the smaller number
- Returns - Number: the lower number
	- Example - `2`
- Example: `Math.min(44, 2);`

### `Math.clamp(value, min, max)`

- This takes the value, if it is smaller than the min then it will return the minimum value, if it is larger than the max then it will return the maximum value, if it is between them, then it will return the value
- Returns - Number: the clamped number
	- Example - `5`
- Example: `Math.clamp(2, 5, 10);`

### `Math.toRadians(value)`

-   This will take the value and convert it to radians (assuming your value was in degrees)
-   Returns - Number: the number converted to radians
    -   Example -  `3.145926`
-   Example:  `Math.toRadians(180);`

### `Math.toDegrees(value)`

-   This will take the value and convert it to degrees (assuming your value was in radians)
-   Returns - Number: the number converted to degrees
    -   Example -  `180`
-   Example:  `Math.toRandians(Math.pi);`

### `Math.log(value)`

- This will calculate the natural logarithm of a value
- Returns - Number: the natural logarithm of the value
- Example: `Math.log(7.3890560);`

### `Math.log(base, value)`

- This will calculate the logarithm with a set base of a value
- Returns - Numer: the log with base of a value
- Example: `Math.log(2, 2);`

### `Math.log10(value)`

- This will calculate the logarithm with base 10 of a value
- Returns - Number: the logarithm with base 10 of a value
- Example: `Math.log10(10);`

### `Math.sin(value)`

- This is the sine function
- Parameter - Number: any number (in radians)
- Returns - Number: the sine function of value
	- Example - `5`
- Example: `length = Math.sin(Math.pi/2);` 

### `Math.cos(value)`

- This is the cosine function
- Parameter - Number: any number (in radians)
- Returns - Number: the cosine function of value
	- Example - `5`
- Example: `length = Math.cos(Math.pi/2);` 

### `Math.tan(value)`

- This is the tangent function, or (sinθ/cosθ)
- Parameter - Number: any number (in radians)
- Returns - Number: the tangent function of value
	- Example - `5`
- Example: `length = Math.tan(Math.pi/2);` 

### `Math.arcsin(value)`

- This is the inverse sine function
- Parameter - Number: any number (in radians)
- Returns - Number: the arcsine function of value
	- Example - `1.570796`
- Example: `angle = Math.arcsin(4/5);` 

### `Math.arccos(value)`

- This is the inverse cosine function
- Parameter - Number: any number (in radians)
- Returns - Number: the arccosine function of value
	- Example - `1.570796`
- Example: `angle = Math.arccos(4/5);` 

### `Math.arctan(value)`

- This is the inverse tangent function
- Parameter - Number: any number (in radians)
- Returns - Number: the arctangent function of value
	- Example - `1.570796`
- Example: `angle = Math.arctan(4/5);` 

### `Math.cosec(value)`

- This is (1/sinθ)
- Parameter - Number: any number (in radians)
- Returns - Number: the cosec function of value
	- Example - `5`
- Example: `angle = Math.cosec(Math.pi/2);` 

### `Math.sec(value)`

- This is (1/cosθ)
- Parameter - Number: any number (in radians)
- Returns - Number: the sec function of value
	- Example - `5`
- Example: `angle = Math.sec(Math.pi/2);` 

### `Math.cot(value)`

- This is (cosθ/sinθ)
- Parameter - Number: any number (in radians)
- Returns - Number: the cot function of value
	- Example - `5`
- Example: `angle = Math.cot(Math.pi/2);` 

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

### Example code

Running a file from command line:

```kt
run("directory/filename.arucas");
```

Loops 100 times printing numbers from 1 to 100:

```kt
for (i = 1; i <= 100; i++) {
    print(i);
} 
```

Program that prints "Hello World" every second infinitely:

```kt
while (true) {
    sleep(1000);
    print("Hello World");
}
```

Iterating through a list using `foreach`:

```kt
list = ["value1", "value2", "value3", "value4", "value5"];

foreach (listVal : list) {
    print(listVal);
}
```

Basic function that takes a list and filters it for Strings:

```kt
list = [true, "foo", 9, false, null, "bar"];
stringList = [];

foreach (listVal : list) {
    if (listVal.instanceOf("String")) {
	    stringList.append(listVal);
    }
}

print(stringList);
```

Simple program that takes an input from a user and prints it back out:

```kt
name = input("What is your name? ");

print("Hi %s have a good day!".formatted(name));
```

Taking input from a user and storing it in a file as a Json:

```kt
file = new  File(getDirectory() + "/src/test/resources/code/personMap.txt");
personMap = { };

shouldReadFile = input("Would you like to try and read the file?").lowercase();

if (shouldReadFile == "y" || shouldReadFile == "yes" || shouldReadFile == "true") {
    try {
        json = Json.fromString(file.read());
        personMap = json.getValue();
        print("Successfully read file");
    }
    catch (e) {
        print("Failed to read file");
    }
}
  
while (true) {
    name = input("What is your name?");
    age = null;
    while (true) {
        age = input("How old are you?");
        try {
            age = age.toNumber();
            if (age > 100 || age < 5)
                throwRuntimeError("");
        }
        catch (e) {
            print(e);
            print("That is an invalid age!");
            continue;
        }
        break;
    }

    personMap.put(name, age);
    exit = input("Would you like to exit? (y/n)");
    if (exit == "y")
        break;
}

json = Json.fromMap(personMap);
json.writeToFile(file);

print("Saved map to file");
```

Passing lambdas as parameters:

```kt
fun runWithDelay(seconds, function) {
    milliseconds = seconds * 1000;
    sleep(milliseconds);
    function();
}

print("program started");

runWithDelay(5, fun() {
    print("lambda");
});

print("program finished");
```

Creating a schedule function:

```kt
/**
 * So here we are just making a function with parameters milliseconds (Number) and function (Function)
 * We then call the function `runThreaded` which will run our code on a separate thread
 * `runThreaded` takes in a Function and a List (this is used to pass in parameters)
 * So we just create a lambda with the parameters ms and func, and inside the lambda we tell it to
 * sleep for ms and then call the func, we also have a list which allows us to pass in the parameters
 * for ms and func. 
 */

fun schedule(milliseconds, function) {  
    runThreaded(fun() {   
        sleep(milliseconds);   
        function();   
    });  
}

/*
 Now we can test to see if it works
 */

schedule(1000, fun() {  
    print("This will print second!");  
});  
  
print("This will print first!");
```

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

# ClientScript

## Useful Links

> [Arucas' GitHub Page](https://github.com/senseiwells/Arucas)
> 
> [Arucas' Wiki Page](https://github.com/senseiwells/Arucas/wiki)
> 
> [HardCoded's Syntax Highlighter](https://github.com/Kariaro/ArucasHighlighter/releases)
> 
> [ClientScript GitHub Page](https://github.com/senseiwells/clientscript)

## What is it?

ClientScript is a feature of [EssentialClient](https://github.com/senseiwells/EssentialClient) what allows you to write scripts for the client directly into Minecraft. It extends [Arucas](https://github.com/senseiwells/Arucas) which is an interpreted language, with very similar syntax to Java using Java as it's host language, [Arucas](https://github.com/senseiwells/Arucas), has the core functionality of a programming language and ClientScript adds all the Minecraft functions.

The main purpose of ClientScript is to create modifications and player automation without having to make a mod.

## How do you use it?

You must have [EssentialClient](https://github.com/senseiwells/EssentialClient) installed, then after you have booted the game, you can navigate to the Essential Client Menu. Once you have opened this menu there will be an option to open Client Script Options, this will open up a config screen where you can manage your ClientScripts. You can create a new script (top left), and click 'Open Script' to open it, this will open a prompt asking you what program to open the file with, open it with any text editor (IntelliJ has a Highlighter for the language, you can find that [here](https://github.com/Kariaro/ArucasHighlighter/releases)). ClientScripts are stored in `.minecraft/config/EssentialClient/Scripts`.

In game, you can navigate to controls and bind `Client Script Start Selected` and `Client Script Stop Selected` to some keybinds. This will allow you to start and stop your selected scripts. You can select a script by navigating to the Client Script Options screen and ticking the checkbox. You can also start and stop scripts from here. 

If you don't want to make your own scripts that's fine, there are people who have already written scripts and who are sharing them. You will be able to find these on my [discord server](https://discord.gg/7R9SfktZxH), and also on the [clientscript GitHub page](https://github.com/senseiwells/clientscript). You can download scripts directly in-game by using the `/clientscript download` command.

# What's available in the language?

To see what's avaiable in this language please visit the [Arucas Wiki](https://github.com/senseiwells/Arucas/wiki/Arucas), this contains all the information you need about the base language. 

ClientScript then adds ontop of this language more classes and functions that allow you to control Minecraft. The information about what ClientScript adds is listed below...  

## New Value Types:
ClientScript adds some new value types for use in Minecraft.

`MinecraftClient` - The general MinecraftClient instance

`World` - The world that is/was loaded in Minecraft

`Entity` - An entity in Minecraft

`LivingEntity` - A living entity in Minecraft

`OtherPlayer` - Other players in the game

`Player` - The main player (you)

`Pos` - A position in the world (x, y, z)

`Material` - A material, all the item/block types

`Block` - A block in Minecraft

`ItemStack` - An item in Minecraft

`Recipe` - A recipe in Minecraft

`Trade` - A villager trade in Minecraft

`Text` - Strings that can be formatted for Minecraft

`Screen` - A screen instance

`MerchantScreen` - A villager screen instance

`FakeInventoryScreen` - A fake inventory screen instance

`CommandBuilder` - A builder that allows you to create commands

`BoxShape` - Boxes that can be rendered in Minecraft

`GameEvent` - Events that can be registered in Minecraft

`Json` - A json element

# General Functions

These are functions that can be called without a class or value.

### `hold()`

- This stops the script from terminating when it finishes executing
- Example: `hold();`

# MinecraftClient class

This class cannot be constructed, and it's a singleton (there is only one instance), and is used to do general things with the client.

## Static Member Functions

### `MinecraftClient.getClient()`

- This gets the MinecraftClient
- Returns - MinecraftClient: the Minecraft Client
- Example: `MinecraftClient.getClient();`

## Member Functions

This will be used for examples:
```kt
client = MinecraftClient.getClient();
```

### `<MinecraftClient>.getPlayer()`

- This gets the current player on the client
- Returns - Player: the main player
- Example: `client.getPlayer();`

### `<MinecraftClient>.getWorld()`

- This gets the current world that the client is in
- Returns - World: the current world
- Example: `client.getWorld();`

### `<MinecraftClient>.addCommand(commandNode)` 

- This allows you to register your own command in the game
- Parameters - CommandBuilder: the command builder 
- Throws: `"Expected a literal command builder as root"`
- Example:
```kt
commandBuilder = CommandBuilder.literal("example");
client.addCommand(commandBuilder);
```

### `<MinecraftClient>.pressKey(key)` 

- This allows you to simulate a key press inside of Minecraft, this will only press the key down
- Parameter - String: the key you want to press
- Throws: `"Tried to press unknown key"`
- Example: `client.pressKey("p");`

### `<MinecraftClient>.releaseKey(key)` 

- This allows you to simulate a key release inside Minecraft, this is useful for keys that only work on release. For example: `f3`
- Parameter - String: the key you want to press
- Throws: `"Tried to press unknown key"`
- Example: `client.releaseKey("f3");`

### `<MinecraftClient>.holdKey(key, milliseconds)` 

- This allows you to simulate a key being held inside Minecraft, this will press, and release the key
- Parameters - String, Number: the key you want to hold, the number of milliseconds you want it held for
- Throws: `"Tried to press unknown key"`
- Example: `client.holdKey("w", 2000);`

### `<MinecraftClient>.screenshot()`

- This allows you to take a screenshot of the game
- Example: `client.screenshot();`

### `<MinecraftClient>.playSound(soundName, volume, pitch)`

- This allows you to play a sound around the player
- Parameters - String, Number, Number: the name of the sound you want to play (list of sounds [here](https://minecraft.fandom.com/wiki/Sounds.json#Sound_events), click [show] for Java edition values, all valid sounds are in the far left column), the volume of the sound, the pitch of the sound
- Throws: `"Invalid identifier name"`
- Example: `client.playSound("entity.lightning_bolt.thunder", 1, 1);`

### `<MinecraftClient>.clearChat()`

- This allows you to clear the chat hud
- Example: `client.clearChat();`

### `<MinecraftClient>.getLatestChatMessage()` 

- This returns the latest chat message
- Returns - String: the latest chat message
	- Example: `"<senseiwells> o/"`
- Example: `client.getLatestChatMessage();`

### `<MinecraftClient>.isInSinglePlayer()`   

- Determines whether the players is in a singleplayer world
- Returns - Boolean: whether the player is in singleplayer
- Example: `client.isInSinglePlayer();`

### `<MinecraftClient>.getServerName()`

- This gets the current connected server's name that is set in the multiplayer screen
- Returns - String: the server name
	- Example: `"Minecraft Server"`
- Throws: `"Failed to get server name"`
- Example: `client.getServerName();`

### `<MinecraftClient>.getPing()`

- This gets your current ping to the server
- Returns - Number: your ping in ms
- Example: `client.getPing();`

### `<MinecraftClient>.getScriptsPath()`

- This gets the script path, where all other scripts are stored.
- Returns - String: the path of all scripts
	- Example: `"C:\Users\acer\AppData\Roaming\.minecraft\config\EssentialClient\Scripts"`
- Example: `client.getScriptsPath();`
- 
### `<MinecraftClient>.setEssentialClientRule(ruleName, value)`

- This sets the value of an EssentialClient Rule
- Parameters - String, Value: the name of the rule you want to set, the value you want to set it to
- Throws: `"Invalid ClientRule name"` and `"Cannot set that value"`
- Example: 
```kt
client.setEssentialClientRule("highlightLavaSources", false); // Can also do "false"
client.setEssentialClientRule("customClientCape", "Minecon 2011");
```

### `<MinecraftClient>.resetEssentialClientRule(ruleName)`

- This resets the value of an EssentialClient Rule
- Parameter - String: the name of the rule you want to reset
- Throws: `"Invalid ClientRule name"`
- Example: `client.resetEssentialClientRule("disableBossBar");`

### `<MinecraftClient>.getEssentialClientValue(ruleName)` 

- This gets the value of an EssentialClient Rule
- Parameter - String: the name of the rule you want to get the value of
- Returns - String: the value currently set to that rule
- Throws: `"Invalid ClientRule name"`
- Example: `client.getEssentialClientValue("overrideCreativeWalkSpeed");`

### `<MinecraftClient>.getModList()`

- This gets a list of all mod ids of the mods currently installed
- Returns - List: a list of mod ids as strings
- Example: `client.getModList();`

### `<MinecraftClient>.renderFloatingItem(itemStack)`

- This renders an item in front of the player using the totem of undying animation
- Parameter - ItemStack: the item you want to render
- Example: `client.renderFloatingItem(Material.GRASS_BLOCK.asItemStack());`

### `<MinecraftClient>.getCursorStack()`

- This returns the current ItemStack that is held by the cursor
- Returns - ItemStack: the cursor ItemStack
- Example: `client.getCursorStack();`

### `<MinecraftClient>.setCursorStack(itemStack)`

- This sets the cursor stack to an ItemStack, this will only work in FakeScreen instances
- Parameter - ItemStack: the item you want to set the cursor to hold
- Example: `client.setCursorStack(Material.GRASS_BLOCK.asItemStack());`

### `<MinecraftClient>.getClientRenderDistance()`

- This gets the current render distance you have set
- Returns - Number: the render distance
- Example: `client.getClientRenderDistance();`

### `<MinecraftClient>.setClientRenderDistance(number)`

- This sets current render distance on the client
- Parameter - Number: the render distance you want to set
- Example: `client.getClientRenderDistance();`

### `<MinecraftClient>.stripFormatting(string)`

- This removes all `§` codes from the string
- Parameter - String: the string you want to string
- Returns - String: the stripped string
- Example: `client.stripFormatting("§dHi")`

### `<MinecraftClient>.runOnMainThread(function)`

- This runs a function on the main Minecraft thread
- Parameter - FunctionValue: the function you want to run on the main thread
- Example: 
```kt
client.runOnMainThread(fun() {
	print("this is running on the main thread");
});
```

### `<MinecraftClient>.tick()`

- This ticks the MinecraftClient, this is useful if you are running something demanding on the main thread but still want to tick the client
- Example: `client.tick();`

### `<MinecraftClient>.getVersion()`

- This gets the current Minecraft version you are playing on
- Returns - String: the Minecraft Version
- Example: `client.getVersion();`

# Pos class

This class can be constructed and consists of 3 values, x, y, and z.

## Constructors

### `new Pos(x, y, z)`

- This creates a new Pos with x, y, and z
- Parameters - Number, Number, Number: x position, y position, z position
- Returns - Pos: the newly constructed Pos value

## Member Functions

This will be used for all examples:

```kt
pos = new Pos(0, 0, 0);
```

### `<Pos>.getX()`

- This gets the x position of the position value
- Returns - Number: the x position
- Example: `pos.getX();`

### `<Pos>.getY()`

- This gets the y position of the position value
- Returns - Number: the y position
- Example: `pos.getY();`

### `<Pos>.getZ()`

- This gets the z position of the position value
- Returns - Number: the z position
- Example: `pos.getZ();`

# Entity class

This class cannot be constructed but has a static method to convert a string to an instance of an Entity.

## Static Member Functions

### `Entity.of(entityIdentifier)`

- This converts an EntityId string into an entity instance
- Returns - Entity: the entity of the id
- Example: `Entity.of("minecraft:pig");`

## Member Functions

This will be used for all examples:

```kt
entity = Entity.of("item_frame");
```

### `<Entity>.isSneaking()`

- This returns whether the entity is sneaking
- Returns - Boolean: whether the entitiy is sneakng
- Example: `entity.isSneaking()`

### `<Entity>.isSprinting()`

- This returns whether the entity is sprinting
- Returns - Boolean: whether the entitiy is sprinting
- Example: `entity.isSprinting()`

### `<Entity>.isFalling()` 

- This returns whether the entity is falling 
- Returns - Boolean: whether the entitiy is falling 
- Example: `entity.isFalling()`

### `<Entity>.isOnGround()`

- This returns whether the entity is on the ground
- Returns - Boolean: whether the entitiy is on the ground
- Example: `entity.isOnGround()`

### `<Entity>.isTouchingWater()`   

- This returns whether the entity is touching water
- Returns - Boolean: whether the entitiy is touching water
- Example: `entity.isTouchingWater()`

### `<Entity>.isTouchingWaterOrRain()`

- This returns whether the entity is touching water or rain
- Returns - Boolean: whether the entitiy is touching water or rain
- Example: `entity.isTouchingWaterOrRain()`

### `<Entity>.isSubmergedInWater()`

- This returns whether the entity is submerged in water
- Returns - Boolean: whether the entitiy is submerged in water
- Example: `entity.isSubmergedInWater()`

### `<Entity>.isInLava()`

- This returns whether the entity is in lava
- Returns - Boolean: whether the entitiy is in lava
- Example: `entity.isInLava()`

### `<Entity>.isOnFire()`

- This returns whether the entity is on fire
- Returns - Boolean: whether the entitiy is on fire
- Example: `entity.isOnFire()`

### `<Entity>.getLookingAtBlock()`

- This gets the block that the entity is currently looking at
- Returns - Block: the block the entity is looking at
- Example: `entity.getLookingAtBlock();`

### `<Entity>.getLookingAtBlock(maxDistance)`

- This gets the block that the entity is currently looking at
- Parameter - Number: the max distance you want to get the block
- Returns - Block: the block the entity is looking at
- Example: `entity.getLookingAtBlock(10);`

### `<Entity>.getLookingAtPos(maxDistance)`

- This gets the position that the entity is looking at, 
- Parameter - Number: the max distance you want to get the pos
- Returns - Pos: position containing the x, y, and z
- Example: 
`pos = entity.getLookingAtPos(10);`

### `<Entity>.getEntityIdNumber()`

- This gets the entityId of the entity
- Returns - Number: the entityId
- Example: `entity.getEntityIdNumber();`

### `<Entity>.getX()`

- This gets the entity's current x position
- Returns - Number: the x position
- Example: `entity.getX();`

### `<Entity>.getY()`

- This gets the entity's current y position
- Returns - Number: the y position
- Example: `entity.getY();`

### `<Entity>.getZ()`

- This gets the entity's current z position
- Returns - Number: the z position
- Example: `entity.getZ();`

### `<Entity>.getYaw()`

- This gets the entity's current yaw
- Returns - Number: the yaw
- Example: `entity.getYaw();`

### `<Entity>.getPitch()`

- This gets the entity's current pitch
- Returns - Number: the pitch
- Example: `entity.getPitch();`

### `<Entity>.getDimension()`

- This gets the entity's current dimension
- Returns - String: the dimension
	- Examples: `"overworld"`, `"the_nether"`, `"the_end"`
- Example: `entity.getDimension();`

### `<Entity>.getBiome()`

- This gets the entity's current biome (a list of all the biome ids can be found [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Biomes))
- Returns - String: the biome
	- Examples: `plains`, `tall_birch_hills`
- Example: `entity.getBiome();`

### `<Entity>.getId()`

- This gets the entity's type as a string representation, you can find all entityNames on [Joa's Entity Property Encyclopedia](https://joakimthorsen.github.io/MCPropertyEncyclopedia/entities.html)
- Returns - String: the entity type
	- Examples: `"armor_stand"`, `"item_frame"`, `"pig"`
- Example: `entity.getId();`

### `<Entity>.getAge()`

- This gets the entity's age
- Returns - Number: the entities age
- Example: `entity.getAge();`

### `<Entity>.getCustomName()`

- This gets the entity's custom name if it has one
- Returns - String / Null: the entities custom name, null if it has none
- Example: `entity.getCustomName();` 

### `<Entity>.getEntityUuid()`

- This gets the entity's Uuid
- Returns - String: the entities Uuid
- Example: `entity.getEntityUuid();`

### `<Entity>.getDistanceTo(otherEntity)`

- This gets the entity's distance to another entity
- Returns - Number: the distance between the two entities
- Example:
```kt
world = client.getWorld();
player = client.getPlayer();
otherPlayer = world.getClosestPlayerEntity(player);
distance = player.getDistanceTo(otherPlayer);
```

### `<Entity>.getSquaredDistanceTo(otherEntity)`

- This gets the entity's squared distance to another entity
- Parameter - Entity: another entity
- Returns - Number: the squared distance between the two entities
- Example:
```kt
world = client.getWorld();
player = client.getPlayer();
otherPlayer = world.getClosestPlayerEntity(player);
squaredDistance = player.getSquaredDistanceTo(otherPlayer);
```

### `<Entity>.setGlowing(boolean)`

- This sets the entity to glowing, giving it the glowing effect on the client
- Parameter - Boolean: whether you want to disable/enable the glow effect
- Example: `entity.setGlowing(true);`

### `<Entity>.getNbt()`

- This gets the entity's Nbt data as a Map
- Returns - Map: the entity's Nbt as a map
- Example: `entity.getNbt();`

### `<Entity>.getTranslatedName()`

- This gets the entity's translated name and is properly formatted
- Returns - String: the entity's translated name
	- Example: `"Pig"`
- Example: `entity.getTranslatedName();`

### `<Entity>.getHixbox()`

- This gets the max and min positions of the entities hitbox
- Returns - List: a list of two positions, first will be the min second will be the max
- Example: `entity.getHitbox();`

### `<Entity>.collidesWith(pos, block)`

- This returns whether the entity collides with a block at a position
- Parameters - Pos, Block: the position of the block, the block
- Returns - Boolean: whether it collides
- Example: `entity,collidesWith(new Pos(0, 100, 0), Material.DIAMOND_BLOCK.asBlock());`

# LivingEntity class

This class cannot be constructed but you can get an instance of a living entity through `Entity.of()`, with entities that are living.

## Member Functions

`LivingEntity` extends `Entity`, so it inherits all methods from `Entity`

This will be used for all examples:

```kt
entity = Entity.of("pig");
```

### `<LivingEntity>.getStatusEffects()`

- This gets the LivingEntity's status effects, you can find a list of all the ids of status effects [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Effects)
- Returns - List: a list of all the status effects as strings, list can contain Null
	- Example: `["regeneration", "resistance", "fire_resistance"]`
- Example: `livingEntity.getStatusEffects();`

### `<LivingEntity>.getHealth()`

- This gets the LivingEntity's current health
- Returns - Number: the health of the entity
	- Examples: `20`, `10`
- Example: `livingEntity.getHealth();`

### `<LivingEntity>.isFlyFalling()`

- This checks whether the LivingEntity is fly falling (gliding with an elytra)
- Returns - Boolean: whether the entity is fly falling
- Example: `livingEntity.isFlyFalling();`

# OtherPlayer class

This class cannot be constructed.

## Member Functions

`OtherPlayer` extends `LivingEntity`, so it inherits all methods from `LivingEntity`, and `Entity`

This will be used for all examples:

```kt
player = Player.get();
// I am using the main player here but these functions work for otherPlayers too
```

### `<OtherPlayer>.getCurrentSlot()`

- This gets the player's current slot
- Returns - Number: the current slot number
	- Example: `0`, `4`, `8`
- Example: `player.getCurrentSlot();`

### `<OtherPlayer>.getHeldItem()`

- This gets the player's current held item
- Returns - ItemStack: the ItemStack the player is holding in their main hand
- Example: `player.getCurrentSlot();`

### `<OtherPlayer>.isInventoryFull()`

- This checks whether the player's inventory is full
- Returns - Boolean: whether the player's inventory is full
- Example: `player.isInventoryFull();`

### `<OtherPlayer>.getPlayerName()`

- This gets the player's name
- Returns - String: the player's name
	- Example: `senseiwells`
- Example: `player.getPlayerName();`

### `<OtherPlayer>.getGamemode()`

- This gets the player's current gamemode
- Returns - String: the gamemode
	- Examples: `"survival"`, `"creative"`
- Example: `player.getGamemode();`

### `<OtherPlayer>.getTotalSlots()`

- This gets the total number of slots in the player's screen
- Returns - Number: the total number of slots
- Example: `player.getTotalSlots();`

### `<OtherPlayer>.getItemForSlot(slotNum)`

- This gets an item for a slot in the player's current inventory (including other inventories)
- Parameter - Number: the slot number you want to find the item for
- Returns - ItemStack: the item in that slot
- Throws: `"That slot is out of bounds"`
- Example: `player.getItemForSlot(10);`

### `<OtherPlayer>.getItemForPlayerSlot(slotNum)`

- This gets an item for a slot in the player's inventory (excluding other inventories)
- Parameter - Number: the slot number you want to find the item for
- Returns - ItemStack: the item in that slot
- Throws: `"That slot is out of bounds"`
- Example: `player.getItemForSlot(10);`

### `<OtherPlayer>.getSlotFor(itemStack)`

- This gets a slot for an item in the player's inventory
- Parameter - ItemStack: the ItemStack you want to search for
- Returns - Number / Null: the slot of that ItemStack, returns null if it cannot find a slot
- Example: `player.getSlotFor(Material.DIAMOND.asItemStack());`

### `<OtherPlayer>.getAllSlotsFor(itemStack)`

- This gets a list of all the slots for an item in the player's inventory
- Parameter - ItemStack: the ItemStack you want to search for
- Returns - List: a list with all the slots of that ItemStack
- Example: `player.getAllSlotsFor(Material.DIAMOND.asItemStack());`

### `<OtherPlayer>.getAbilities()`

- This gets a map of all the player's abilities
- Returns - Map: a map of the abilities
	- Example: `{"invulnerable" : false, "canFly" : false, "canBreakBlocks" : true, "isCreative" : false, "walkSpeed" : 1.0, "flySpeed" : 1.2}`
- Example: `player.getAbilities();`

### `<OtherPlayer>.getLevels()`

- This gets the amount of levels the player has
- Returns - Number: the amount of levels
- Example: `player.getLevels();`

### `<OtherPlayer>.getHunger()`

- This gets the current hunger level of the player
- Returns - Number: the amount of hunger the player has
- Example: `player.getHunger();`

### `<OtherPlayer>.getSaturation()`

- This gets the current saturation level of the player
- Returns - Number: the amount of saturation the player has
- Example: `player.getSaturation();`

# Player class

This class cannot be constructed and this object refers to the main player.

## Static Member Functions

### `Player.get()`

- This gets the main player
- Returns - Player: the main player
- Example: `Player.get();`

## Member Functions

`Player` extends `OtherPlayer`, so it inherits all methods from `OtherPlayer`, `LivingEntity`, and `Entity`

This will be used for all examples:

```kt
client = MinecraftClient.getClient();
player = Player.get();
```

### `<Player>.use(type)`

- This allows you to make your player use
- Parameter - String: this must be one of three: "hold", "stop", or "once" 
- Throws: `"Must pass "hold", "stop" or "once" into use()"`
- Example: `player.use("once");`

### `<Player>.attack(type)`

- This allows you to make your player attack
- Parameter - String: this must be one of three: "hold", "stop", or "once" 
- Throws: `"Must pass "hold", "stop" or "once" into use()"`
- Example: `player.attack("hold");`

### `<Player>.jump()`

- This will make the player jump if they are on the ground
- Example: `player.jump();`

### `<Player>.setSelectedSlot(slotNum)`

- This allows you to set the slot number your player is holding
- Parameter - Number: number must be between 0 - 8
- Throws: `"Number must be between 0 - 8"`
- Example: `player.setSelectedSlot(5);`

### `<Player>.say(message)`

- This allows you to make your player send a message in chat, this includes commands
- Parameter - Value: any value you want the player to say
- Examples: `player.say("hi");`, `player.say("/gamemode creative");`

### `<Player>.message(message)`

- This allows you to send a message to your player, only they will see this
- Parameter - Value: any value you want to message the player, if you pass in Text it will be formatted
- Example: `player.message("Hello!");`

### `<Player>.messageActionBar(message)`

- This allows you to set the current message displaying on the action bar
- Parameter - Value: any value you want to message the player, if you pass in Text it will be formatted
- Example: `player.messageActionBar("Hello!");`

### `<Player>.showTitle(title, subtitle)`

- This allows you to show a title and a subtitle to the player
- Parameter - Value / Null, Value / Null: any value you want to display to the player, pass null if you don't want to diplay one of them, if you pass in Text it will be formatted
- Example: `Player.showTitle("WOW", "subtitle");`

### `<Player>.openInventory()`

- This opens the player's inventory screen
- Example: `player.openInventory();`

### `<Player>.openScreen(screen)`

- This opens a screen for the player
- Parameter - Screen: any screen that isn't handled server side
- Throws: `"Opening handled screens is unsafe"`
- Example: 
```kt
fakeScreen = client.createFakeScreen("fake", 1);
player.openScreen(fakeScreen);
```

### `<Player>.closeScreen()`

- This closes the player's current screen and returns them to the game
- Example: `player.closeScreen();`

### `<Player>.setWalking(boolean)`

- This allows you to set whether your player is holding the walk key or not
- Parameter - Boolean: whether you want them to walk
- Example: `player.setWalking(true);`

### `<Player>.setSneaking(boolean)`

- This allows you to set whether your player is holding the sneak key or not
- Parameter - Boolean: whether you want them to sneak
- Example: `player.setSneaking(true);`

### `<Player>.setSprinting(boolean)`

- This allows you to set whether your player is holding the sprinting key or not
- Parameter - Boolean: whether you want them to sprint
- Example: `player.setSprinting(true);`

### `<Player>.dropItemInHand(boolean)`

- This allows you to drop the item(s) you are currently holding in your main hand
- Parameter - Boolean: whether you want to drop the whole stack
- Example: `player.dropItemInHand(true);`

### `<Player>.dropAll(itemStack)`

- This allows you to drop all of a select item type from your inventory
- Parameter - ItemStack: the ItemStack you want to drop
- Example: `player.dropAll(Material.DIAMOND_BLOCK.asItemStack());`

### `<Player>.getSwappableHotbarSlot()`

- This returns the predicted current swappable hotbar slot
- Returns - Number: the predicted slot
- Example: `player.getSwappableHotbarSlot();` 
 
### `<Player>.swapSlots(slotNum1, slotNum2)`

- This allows you to swap 2 slots with one another
- Parameters - Number, Number: slot number, another slot number
- Throws `"That slot is out of bounds"`
- Example: `player.swapSlots(13, 46);`

### `<Player>.swapPlayerSlotWithHotbar(slotNum)`

- This allows you to swap a slot in the player's inventory with your hotbar
- Parameter - Number: the slot you want to swap
- Throws: `"That slot is out of bound"`
- Example: `player.swapPlayerSlotWithHotbar(15);`

### `<Player>.shiftClickSlot(slotNum)`

- This allows you to shift click a slot
- Parameters - Number: a slot number
- Throws `"That slot is out of bounds"`
- Example: `player.shiftClickSlot(9);`

### `<Player>.clickSlot(slotNum, clickType, slotAction)`

- This allows you to click a slot with either right or left click and a slot action
- Parameters - Number, String, String: the slot number, either 'left' or 'right' click, the type of action, 'click', 'shift_click', 'swap', 'middle_click', 'throw', 'drag', 'double_click'.
- Throws: `"Invalid clickData must be \"left\" or \"right\""`, `"Invalid slotActionType, see Wiki"`, or `"That slot is out of bounds"`
- Example: `player.clickSlot(9, "left", "double_click");`

### `<Player>.getCurrentScreen()`

- This gets the current screen the player is in
- Returns - Screen / Null: the screen that the player is in, if the player is not in a screen, returns Null
- Example: `player.getCurrentScreen();`

### `<Player>.dropSlot(slotNum)`

- This allows you to drop the items in a slot
- Parameter - Number: a slot number
- Example: `player.dropSlot(14);`

### `<Player>.swapHands()`

- This swaps the player's main and off hand
- Example: `player.swapHands();`

### `<Player>.swingHand(isOffHand)`

- This players the player's hand swinging animation
- Parameter - Boolean: whether the swing should be the offhand
- Example: `player.swingHand(true);`

### `<Player>.look(yaw, pitch)`

- This allows you to manipulate where your player is looking
- Parameters - Number, Number: the yaw (between -180 - 180), and the pitch (between -90 - 90)
- Example: `player.look(-76.2, 80.1);`

### `<Player>.lookAtPos(x, y, z)`

- This makes your player look towards a block position
- Parameters - Number, Number, Number: x position, y position, and z position
- Example: `player.lookAtPos(0.0, 0.0, 0.0);`

### `<Player>.lookAtPos(pos)`

- This makes your player look towards a block position
- Parameters - Pos: the position value
- Example: `player.lookAtPos(new Pos(0, 0, 0);`

### `<Player>.fakeLook(yaw, pitch, direction, duration)`

- This makes the player 'fake' look in a direction, this can be used to place blocks in unusual orientations without moving the camera.
- Paramters - Number, Number, String, Number: yaw, pitch, direction (north, south, etc...), duration in ticks
- Example: `player.fakeLook(0, 0, "up", 100);`

### `<Player>.craft(recipe)`

- This allows you to craft a recipe, this can be 2x2 or 3x3
- Parameter - List: a list of ItemStacks making up the recipe you want to craft (must include air)
- Throws: `"Recipe must either be 3x3 or 2x2"` or `"The recipe must only include items"` or `"You must be in a crafting table to craft a 3x3"`
- Example:
```kt
oakItem = Material.OAK_PLANKS.asItemStack();
airItem = Material.AIR.asItemStack();
player.craft([
    oakItem, oakItem, oakItem,
    oakItem, airItem, oakItem,
    oakItem, oakItem, oakItem
    // Chest crafting recipe
]);
```

### `<Player>.craftRecipe(recipe)`

- This allows you to craft a predefined recipe.
- Parameter - Recipe: a recipe
- Throws: `"Must be in a crafting GUI"`
- Example:
`player.craftRecipe(Recipe.OAK_PLANKS);`

### `<Player>.stonecutter(itemInput, itemOutput)`

- This allows you to use the stonecutter
- Parameters - ItemStack, ItemStack: the item you want to input, the item you want to output
- Returns - Boolean: returns false if the player doesn't have the inputItem, returns true if crafting was successful
- Throws: `"Not in stonecutter gui"` or `"Recipe does not exist"`
- Example: `player.stonecutter(Material.STONE.asItemstack(), Material.STONE_BRICKS.asItemStack());`

### `<Player>.anvil(predicate1, predicate2)`

- This allows you to combine two items in an anvil
- Parameters - Function, Function: a function determining whether the first ItemStack meets a criteria, function determining whether the second ItemStack meets a criteria
- Returns - Boolean / Number: whether the anvilling was successful, if the player doesn't have enough levels it will return the cost of the anvilling
- Throws: `Not in anvil gui"` or `""Invalid function parameter""`
- Example:
```kt
// Enchant a pickaxe with mending
player.anvil(
    // Predicate for pick
    fun(item) {
        // We want a netherite pickaxe without mending
        if (item.getItemId() == "netherite_pickaxe") {
            hasMending = item.getEnchantments().getKeys().contains("mending");
            return !hasMending;
        }
        return false;
    },
    // Predicate for book
    fun(item) {
        // We want a book with mending
        if (item.getItemId() == "enchanted_book") {
            hasMending = item.getEnchantments().getKeys().contains("mending");
            return hasMending;
        }
        return false;
    }
);
```

### `<Player>.anvilRename(name, predicate)`

- This allows you to name an item in an anvil
- Parameters - String, Function: the name you want to name it to, function determining whether the ItemStack meets a criteria
- Returns - Boolean / Number: whether the anvilling was successful, if the player doesn't have enough levels it will return the cost of the anvilling
- Throws: `"Not in anvil gui"` or `"Invalid function parameter"`
- Example: 
```kt
// Rename any shulker box
player.anvilRename("Rocket Box",
    fun(item) {
        isShulker = item.getItemId().containsString("shulker_box"));
        return isShulker;
    }
);
```

### `<Player>.logout(message)`

- This forces the player to leave the world
- Parameter - String: the message you display on the disconnect screen
- Example: `player.logout("You've been lazy!")`

### `<Player>.spectatorTeleport(entity)`

- This lets you to teleport to any entity as long as you are in spectator mode
- Parameter - Entity: the entity you want to teleport to, this must be an actual entity on the server
- Example:
```kt
firstEntity = client.getWorld().getAllEntities().get(0);
player.spectatorTeleport(firstEntity);
```

### `<Player>.interactWithEntity(entity)`

- This allows a player to interact with an entity without have to click on the entity
- Parameter - Entity: the entity you want to interact with
- Example: 
```kt
allEntities = client.getWorld().getAllEntities();
foreach (entity : allEntities) {
    if (entity.getId() == "villager" && player.getSquaredDistanceTo(entity) < 5) {
        player.interactWithEntity(entity);
        break;
    }
}
```

### `<Player>.attackEntity(entity)`

- This makes a player attack an entity without having to be looking at or clicking on the entity
- Parameter - Entity: the entity you want to attack
- Example:
```
allEntities = client.getWorld().getAllEntities();
foreach (entity : allEntities) {
    if (entity.getId() == "villager" && player.getSquaredDistanceTo(entity) < 5) {
        player.attackEntity(entity);
        break;
    }
}
```

### `<Player>.getLookingAtEntity()`

- This gets the entity that the player is currently looking at
- Returns - Entity / Null: the entity that the player is currently looking at, can be Null if there is no Entity
- Example: `player.getLookingAtEntity();`

### `<Player>.interactBlock(x, y, z, direction)`

- This allows you to interact with a block at a position and direction
- Parameters - Number, Number, Number, String: x position, y position, z position, and direction (north, south, etc...)
- Example: `player.interactBlock(0, 100, 0, "down");`

### `<Player>.interactBlock(pos, direction)`

- This allows you to interact with a block at a position and drection
- Parameters - Pos, String: position, and direction (north, south, etc...)
- Example: `player.interactBlock(new Pos(0, 100, 0), "down");`

### `<Player>.interactBlock(posX, posY, posZ, direction, blockX, blockY, blockZ, insideBlock)`

- This allows you to interact with a block at a position and drection
- Parameters - Number, Number, Number, String, Number, Number, Number, Boolean: x position, y position, z position, and direction (north, south, etc...), block x position, block y position, block z position, whether you are inside the block
- Example: `player.interactBlock(0, 100, 0, "down", 0, 100, 0, false);`

### `<Player>.interactBlock(playerPos, direction, blockPos, insideBlock)`

- This allows you to interact with a block at a position and drection
- Parameters - Pos, String, Pos, Boolean: position, and direction (north, south, etc...), block position, whether you are inside the block
- Example: 
```kt
pos = new Pos(0, 100, 0);
player.interactBlock(pos, "down", pos, false);`
```

### `<Player>.attackBlock(x, y, z, direction)`

- This allows you to attack a block at a position and direction
- Parameters - Number, Number, Number, String: x position, y position, z position, and direction (north, south, etc...)
- Example: `player.attackBlock(0, 100, 0, "down");`

### `<Player>.attackBlock(pos, direction)`

- This allows you to attack a block at a position and drection
- Parameters - Pos, String: position, and direction (north, south, etc...)
- Example: `player.attackBlock(new Pos(0, 100, 0), "down");`

### `<Player>.updateBreakingBlock(x, y, z)`

- This allows you to update your block breaking progress at a position
- Parameters - Number, Number, Number: x position, y position, z position
- Example: `player.updateBreakingBlock(0, 100, 0, "down");`

### `<Player>.updateBreakingBlock(pos)`

- This allows you to update your block breaking progress at a position
- Parameters - Pos: position of the block
- Example: `player.updateBreakingBlock(new Pos(0, 100, 0), "down");`

### `<Player>.getBlockBreakingSpeed(block)`

- This calculates the speed at which the player would break a block with their current hand
- Paratmeter - Block: the block you want to get the breaking speed for
- Example: `player.getBlockBreakingSpeed(Material.OAK_LOG.asBlock());`

# FakeEntity class

This class can be constructed.

## Constructors

### `new FakeEntity(entity, world)`

- This creates a new instance of a FakeEntity which allows you to spawn in a fake entity on the client.
- Parameters - Entity, World: the entity (type) that you want to spawn, the current world
- Throws: `"Entity could not be created"`
- Example: 
```kt
new FakeEntity(Entity.of("pig"), MinecraftClient.getClient().getWorld());
```
- Extra Info:
	- You cannot create fake players...

# Members

This will be used for all examples:

```kt
client = MinecraftClient.getClient();
fakeEntity = new FakeEntity(Entity.of("pig"), client.getWorld());
```

### `<FakeEntity>.entity`

- This is the entity that is being faked
- Value Type: Entity
- Assignable: false
- Example: `fakeEntity.entity;`

### `<FakeEntity>.world`

- This is the world of the entity
- Value Type: World
- Assignable: false
- Example: `fakeEntity.world;`

### `<FakeEntity>.pos`

- This is the position of the entity
- Value Type: Pos
- Assignable: false
- Example: `fakeEntity.pos;`

### `<FakeEntity>.bodyYaw`

- This is the body yaw of the entity
- Value Type: Number
- Assignable: false
- Example: `fakeEntity.bodyYaw;`

### `<FakeEntity>.yaw`

- This is the yaw of the entity
- Value Type: Number
- Assignable: false
- Example: `fakeEntity.yaw;`

### `<FakeEntity>.pitch`

- This is the pitch of the entity
- Value Type: Number
- Assignable: false
- Example: `fakeEntity.pitch;`

## Member Functions


### `<FakeEntity>.setWorld(world)`

- This sets the current world for the entity
- Parameter - World: the world you want to set
- Example: `fakeEntity.setWorld(client.getWorld());`

### `<FakeEntity>.setPos(x, y, z, interpolation)`

- This sets the entity's position interpolating the movement (moving in steps)
- Parameters - Number, Number, Number, Number: x position, y position, z position, the number of interpolation steps
- Example: `fakeEntity.setPos(0, 100, 0, 5);`

### `<FakeEntity>.setPos(pos, interpolation)`

- This sets the entity's position interpolating the movement (moving in steps)
- Parameters - Pos, Number: the position, the number of interpolation steps
- Example: `fakeEntity.setPos(new Pos(0, 100, 0), 5);`

### `<FakeEntity>.setPos(x, y, z)`

- This sets the entity's position with no interpolation
- Parameters - Number, Number, Number: x position, y position, z position
- Example: `fakeEntity.setPos(0, 100, 0);`

### `<FakeEntity>.setPos(pos)`

- This sets the entity's position with no interpolation
- Parameter - Pos: the position
- Example: `fakeEntity.setPos(new Pos(0, 100, 0));`

### `<FakeEntity>.setYaw(yaw, interpolation)`

- This sets the entity's head yaw with interpolation
- Parameters - Number, Number: the yaw, the number of interpolation steps
- Example: `fakeEntity.setYaw(100, 3);`

### `<FakeEntity>.setYaw(yaw)`

- This sets the entity's head yaw with no interpolation
- Parameter - Number: the yaw
- Example: `fakeEntity.setYaw(100);`

### `<FakeEntity>.setBodyYaw(bodyYaw, interpolation)`

- This sets the entity's body yaw with interpolation
- Parameters - Number, Number: the yaw, the number of interpolation steps
- Example: `fakeEntity.setBodyYaw(100, 3);`

### `<FakeEntity>.setBodyYaw(bodyYaw)`

- This sets the entity's body yaw with no interpolation
- Parameter - Number: the yaw
- Example: `fakeEntity.setBodyYaw(100);`

### `<FakeEntity>.setPitch(pitch, interpolation)`

- This sets the entity's pitch with interpolation
- Parameters - Number, Number: the pitch, the number of interpolation steps
- Example: `fakeEntity.setPitch(100, 3);`

### `<FakeEntity>.setPitch(pitch)`

- This sets the entity's pitch with no interpolation
- Parameter - Number: the pitch
- Example: `fakeEntity.setPitch(100);`


### `<FakeEntity>.updatePosAndRotation(pos, yaw, pitch, interpolation)`

- This sets the entity's pos, yaw, and pitch with interpolation
- Parameter - Pos, Number, Number, Number: the position, the yaw, the pitch, and the number of interpolation steps
- Example: `fakeEntity(new Pos(0, 100, 0), 0, 0, 4);`

### `<FakeEntity>.updatePosAndRotation(pos, yaw, pitch)`

- This sets the entity's pos, yaw, and pitch without interpolation
- Parameter - Pos, Number, Number: the position, the yaw, the pitch
- Example: `fakeEntity(new Pos(0, 100, 0), 0, 0);`

### `<FakeEntity>.spawn()`

- This spawns the entity into it's world
- Example: `fakeEntity.spawn();`

### `<FakeEntity>.despawn()`

- This removes the entity from it's world
- Example: `fakeEntity.despawn();`

# CommandBuilder class

This class cannot be constructed.

## Static Member Functions

### `CommandBuilder.fromMap(map)`

- This is the suggested way to write commands as it is easier in general for people to read and understand, this parses a map into a command.
- Parameter - Map: the command map
- Returns - CommandBuilder: the command from the map
- Example:
```kt
effectCommandMap = {
   "name" : "effect",
   "subcommands" : {
       "give" : {
           "<targets> <effect>" : {
               "" : fun(target, effect) {
                   // do something
               },
               "<seconds>" : {
                   "" : fun(target, effect, second) {
                       // do something
                   },
                   "<amplifier>" : {
                       "" : fun(target, effect, second, amplifier) {
                           // do something
                       },
                       "<hideParticle>" : {
                           "" : fun(target, effect, second, amplifier, hideParticle) {
                               // do something
                           }
                       }
                   }
               }
           }
       },
       "clear" : {
           "" : fun() {
               // do something
           },
           "<targets>" : {
               "" : fun(target) {
                   // do something
               },
               "<effect>" : {
                   "" : fun(target, effect) {
                       // do something
                   }
               }
           }
       }
   },
   "arguments" : {
       "targets" : { "type" : "Entity" },
       "effect" : { "type" : "Effect", "suggests" : ["effect1", "effect2"] },
       "seconds" : { "type" : "Integer", "min" : 0, "max" : 1000000 },
       "amplifier" : { "type" : "Integer", "min" : 0, "max" : 255 },
       "hideParticle" : { "type" : "Boolean" }
   }
};
effectCommand = CommandBuilder.fromMap(effectCommandMap);
``` 
- Extra info: 
	- This way of making a command makes it possible to have a tree and have proper argument types. In the first map you must include `"name"`  with a string value representing the name of the command, and it must also include `"subcommands"` and `"arguments"`, both with a key of a map.
	- The subcommands map can contain branches for the command tree, this is made by having a string as a key, you can have multiple subcommands in a single string as long as they are separated by a ` ` (space), for example: `"sub1 sub2 sub3"`, this then has a value of a map which can contain an empty string as a key which must have a function as the value which will be the function that gets executed then the command is run.
	- Functions must contain the right amount of parameters that correspond to the command, the arguments of the command will be passed into the function.
	- You are able to create arguments by surrounding the string in `<>`, for example: `<arg1>`, the name inside the `<>` must be defined in the `"arguments"` map in the root map, the name would be the key and the value must contain a map of the attributes of the argument. This map must contain `"type"` with the value of a string which is parsed as the argument type (see below for all argument types), and it can contain `"suggests"` which must have a list as its value. All the things inside the list will be suggests to the player when they type the command with the argument.
	- Argument Types: 
		- `"PlayerName"` - this suggests to the main player all names of those online
		- `"Word"` - this can take any String without spaces
		- `"GreedyString"` - this can take any String including those with spaces, slashes, etc.
		- `"Double"` - this can only take double values (decimal values), this can also have a `"min"` and `"max"` attribute in the argument map
		- `"Integer"` - this can only take integer values (whole numbers), this can also have a `"min"` and `"max"` attribute in the argument map
		- `"Boolean"` - this can only take either `true` or `false`
		- `"ItemStack"` - this suggests ItemStacks and can only take an ItemStack values
		- `"Block"` - this suggests Blocks and can only take Block values
		- `"Entity"` - this suggests entities and can only take Entity values
		- `"BlockPos"` - this suggests block pos and can ony take Pos values
		- `"Pos"` - this suggests pos and can only take Pos values
		- `"Effect"` - this suggests effects and can only take effect values (converted to string)
		- `"Particle"` - this suggests particles and can only take particle values (converted to string)
		- `"RecipeId"` - this suggests all recipe ids and can only take recipe ids
		- `"EntityId"` - this suggests all entity ids and can only take entity ids
		- `"EnchantmentId"` - this suggests all enchantment ids and can only take enchantment ids
	- If you have an unknown argument type it will throw an error.

# GameEvent class

This class can be constructed and is responsible for registering GameEvents.

## Static Member Functions

### `GameEvent.cancel()`

- This will try to cancel an event if called inside of an event. Not every event can be cancelled, again check the [Script Event wiki page](https://github.com/senseiwells/EssentialClient/wiki/ClientScript---Events) for more information
- Throws: `"Cannot cancel event outside of a cancellable event"`
- Example:
```kt
new GameEvent("onAttack", fun() {
    // This prevents you from attacking in-game
    GameEvent.cancel();
}, true);
```
- Extra Info:
	- The event you use this function is **must** be cancellable for this to work.

### `GameEvent.unregisterAll()`

- This unregisters all GameEvents from being called.
- Example: `GameEvent.unregisterAll();`


## Constructors

### `new GameEvent(eventName, function, cancellable)`

- This creates a new instance of a GameEvent which will run on an event that happens in-game. This is determined by the name see the [Script Event wiki page](https://github.com/senseiwells/EssentialClient/wiki/ClientScript---Events) for all the events.
- Parameters - String, Function, Boolean: the name of the event, the function you want to run on the event, whether the event should be cancellable (able stop the event from running)
- Throws: `"No such event '...'"`
- Example: 
```kt
new GameEvent("onUse", fun() { 
    print("You tried to use something!");
}, true);
```
- Extra Info:
	- If the event is cancellable the event will run on the main game thread, for example, if you call `sleep(...)` it will pause the whole game.

### `new GameEvent(eventName, function)`

- This creates a new instance of a GameEvent which will run on an event that happens in-game. This is determined by the name see the [Script Event wiki page](https://github.com/senseiwells/EssentialClient/wiki/ClientScript---Events) for all the events. This sets the event to not be cancellable.
- Parameters - String, Function: the name of the event, the function you want to run on the event
- Throws: `"No such event '...'"`
- Example: 
```kt
new GameEvent("onUse", fun() { 
    print("You tried to use something!");
}, false);
```

## Member Functions

This will be used for all examples:

```kt
attackEvent = new GameEvent("onAttack", fun() {
    print("You attacked!");
}, true);
```

### `<GameEvent>.register()`

- This registers your game event so it will actually be called when the event happens.
- Example: `attackEvent.register();`

### `<GameEvent>.isRegistered()`

- This checks if the current GameEvent instance is registered to be called.
- Returns - Boolean: whether the event is registered
- Example: `attackEvent.isRegistered();`

### `<GameEvent>.unregister()`

- This removes the GameEvent from being registered and being called.
- Returns - Boolean: whether the game was registered
- Example: `attackEvent.unregister();`

# World class

This class cannot be constructed.

## Member Functions

This will be used for all examples:

```kt
client = MinecraftClient.getClient();
world = client.getWorld();
```

### `<World>.getBlockAt(x, y, z)`

- This gets the Block in a World at set coordinates
- Parameters - Number, Number, Number: x position, y position, z position
- Returns - Block: the block at that position
- Example: `world.getBlockAt(0, 100, 0);`

### `<World>.getBlockAt(pos)`

- This gets the Block in a World at set coordinates
- Parameters - Pos: the position you want to get the block from
- Returns - Block: the block at that position
- Example: `world.getBlockAt(new Pos(0, 100, 0));`

### `<World>.getAllEntities()`

- This gets all of the Entities in a World
- Returns - List: a list of all the Entities in a World
- Example: `world.getAllEntities();`

### `<World>.getEntityFromId(entityId)`

- This gets an Entity from an entityId
- Parameter - Number: an entityId
- Returns - Entity / Null: the Entity from the entityId, if no entity exists under that Id then it returns Null
- Example: `world.getEntityFromId(12);`

### `<World>.getOtherPlayer(playerName)`

- This gets a OtherPlayer from their username
- Parameter - String: the player's username
- Returns - OtherPlayer / Null: the OtherPlayer under the playerName, if the OtherPlayer doesn't exist then it will return Null
- Example: `world.getOtherPlayer("senseiwells");`

### `<World>.getAllOtherPlayers()`

- This will get all OtherPlayers in the world
- Returns - List: a list of all OtherPlayers
- Example: `world.getAllOtherPlayers();`

### `<World>.getClosestPlayer(entity, maxDistance)`

- This will get the closest player to another entity in the world
- Parameters - Entity, Number: the entity you want to check from, the max distance you want to check (in blocks)
- Returns - OtherPlayer / Player / Null: it will get the closest player, if it's the main player it will return Player, if there are no players it can return Null
- Example: `world.getClosestPlayer(client.getPlayer(), 20);`

### `<World>.getDimensionName()`

- This will get the dimension name of the world
- Returns - String: the dimension name
	- Example: `"overworld"`, `"the_nether"`, `"the_end"`
- Example: `world.getDimensionName();`

### `<World>.isRaining()`

- This will check whether it is raining in the world
- Returns - Boolean: whether it is raining
- Example: `world.isRaining();`

### `<World>.isThundering()`

- This will check whether it is thundering in the world
- Returns - Boolean: whether it is thundering 
- Example: `world.isThundering();`

### `<World>.getTimeOfDay()`

- This will get the time of day, info on the time of day [here](https://minecraft.fandom.com/wiki/Daylight_cycle)
- Returns - Number: the time of day (0 - 23999)
- Example: `world.getTimeOfDay();`

### `<World>.renderParticle(particleName, x, y, z)`

- This will render a partilce in the world, you can find a list of all the particle ids [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Particles)
- Parameters - String, Number, Number, Number: the name of the particle, x position, y position, z position
- Throws: `"Particle Invalid"` or `"Invalid identifier name"`
- Example: `world.renderParticle("end_rod", 0, 100, 0);`

### `<World>.renderParticle(particleName, pos)`

- This will render a partilce in the world, you can find a list of all the particle ids [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Particles)
- Parameters - String, Pos: the name of the particle, the position of the particle
- Throws: `"Particle Invalid"` or `"Invalid identifier name"`
- Example: `world.renderParticle("end_rod", new Pos(0, 100, 0));`

### `<World>.renderParticle(particleName, pos, xVelocity, yVelocity, zVelocity)`

- This will render a partilce in the world, you can find a list of all the particle ids [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Particles)
- Parameters - String, Pos, Number, Number, Number: the name of the particle, the position of the particle, x velocity, y velocity, z velocity
- Throws: `"Particle Invalid"` or `"Invalid identifier name"`
- Example: `world.renderParticle("end_rod", new Pos(0, 100, 0), 100, 0, 20);`

### ~~`<World>.setGhostBlock(block, x, y ,z)`~~

- **This function is deprecated, this is a dangerous function be careful with how you use it...**
- This sets a ghost block in the world
- Parameters - Block, Number, Number, Number: the block you want to set, x position, y position, z position
- Example: `world.setGhostBlock(Material.BEDROCK.asBlock(), 0, 100, 0);`

### ~~`<World>.setGhostBlock(block, pos)`~~

- **This function is deprecated, this is a dangerous function be careful with how you use it...**
- This sets a ghost block in the world
- Parameters - Block, Pos: the block you want to set, the position
- Example: `world.setGhostBlock(Material.BEDROCK.asBlock(), new Pos(0, 100, 0));`

### `<World>.isAir(x, y, z)`

- Returns whether the block at a position is air
- Parameters - Number, Number, Number: x position, y position, z position
- Returns - Boolean: whether the block is air
- Example: `world.isAir(0, 100, 0);`

### `<World>.isAir(pos)`

- Returns whether the block at a position is air
- Parameters - Pos: the position
- Returns - Boolean: whether the block is air
- Example: `world.isAir(new Pos(0, 100, 0));`

### `<World>.getEmittedRedstonePower(x, y, z, direction)`

- Gets the emitted restone power at a position and direction
- Parameters - Number, Number, Number, String: x position, y position, z position, the direction as a string ("north", "south", etc...)
- Returns - Number: the emitted redstone power level
- Example: `world.getEmittedRedstonePower(0, 100, 0, "up");`

### `<World>.getEmittedRedstonePower(pos, direction)`

- Gets the emitted restone power at a position and direction
- Parameters - Pos, String: the position, the direction as a string ("north", "south", etc...)
- Returns - Number: the emitted redstone power level
- Example: `world.getEmittedRedstonePower(new Pos(0, 100, 0), "up");`

### `<World>.getLight(x, y, z)`

- This gets the current light level at a position
- Parameters - Number, Number, Number: x position, y position, z position
- Returns - Number: the light level
- Example: `world.getLight(0, 100, 0);`

### `<World>.getLight(pos)`

- This gets the current light level at a position
- Parameters - Pos: the position
- Returns - Number: the light level
- Example: `world.getLight(new Pos(0, 100, 0));`
- 
# Material class

This class cannot be constructed but you are able to create instances of it by using it's static member `of`

## Static Members

### `Material.<MaterialId>`

- The material class has many static members... too many to actually list here, but every single material is a static member. All the static members are the id's of the materials but capitalised. These can then be used to create blocks or items, and compare them without having to use strings.
- Value Type - Material
- Assignable: false
- Examples: `Material.OAK_PLANKS;`, `Material.ARROW;`, `Material.GOLD_INGOT;`, `Material.AIR;`

### `Material.ALL`

- This member is a list that contains all materials in the game
- Value Type - List: containing materials
- Assignable: false
- Example: `Material.ALL;`

## Static Member Functions

### `Material.of(string)`

- This converts a string into a material type if it's valid
- Parameter - String: the name of the material
- Returns - Material: the material representation of that string
- Example: `Material.of("oak_planks");`

## Member Functions

### `<Material>.getId()`

- This gets the material id (name) of the Material, you can find all material names on [Joa's Item Property Encyclopedia](https://joakimthorsen.github.io/MCPropertyEncyclopedia/items.html), this is the same as ItemStack ids.
- Returns - String: the id of the Material
	- Example: `"grass_block"`, `"diamond_pickaxe"`
- Example: `Material.GRASS_BLOCK.getId();`

### `<Material>.asItemStack()`

- This gets the ItemStack of the material
- Returns - ItemStack: the itemstack with that material
- Example: `Material.GRASS_BLOCK.asItemStack();`

### `<Material>.asBlock()`

- This gets the Block of the material
- Returns - Block : the block with that material
- Example: `Material.GRASS_BLOCK.asBlock();`

### `<Material>.getTranslatedName()`

- This gets the translated name of the Material
- Returns - String: the translated name
- Example: `Material.GRASS_BLOCK.getTranslatedName();`

# ItemStack class

This class cannot be constructed but does have a static method to convert materials to ItemStacks

## Static Member Functions

### `ItemStack.of(material)`

- This gets an ItemStack from a Material, alternatively you can use `<Material>.asItemStack()`
- Parameter - Material: the material of the ItemStack
- Returns - ItemStack: the new ItemStack
- Example: `ItemStack.of(Material.GLASS);`

## Member Functions

This will be used for all examples:

```kt
client = MinecraftClient.getClient();
itemStack = ItemStack.of(Material.GRASS_BLOCK);
```

### `<ItemStack>.getMaterial()`

- This gets the material of the ItemStack
- Returns - Material: the material of the ItemStack
- Example: `itemStack.getMaterial();`

### `<ItemStack>.getId()`

- This gets the item id (name) of the ItemStack, you can find all itemNames on [Joa's Item Property Encyclopedia](https://joakimthorsen.github.io/MCPropertyEncyclopedia/items.html)
- Returns - String: the id of the ItemStack
	- Example: `"grass_block"`, `"diamond_pickaxe"`
- Example: `itemStack.getId();`

### `<ItemStack>.getCount()`

- This gets the number of items in the stack
- Returns - Number: the amount of items in the stack
- Example: `itemStack.getCount();`

### `<ItemStack>.getDurability()`

- This gets the durability of the ItemStack
- Returns - Number: the durability, this will return 0 if it doesn't have durability
- Example: `itemStack.getDurability();`

### `<ItemStack>.getMaxDurability()`

- This gets the maximum possible durability for that ItemStack
- Returns - Number: the max durability
- Example: `itemStack.getMaxDurability();`

### `<ItemStack>.getEnchantments()`

- This gets the enchantments of an ItemStack, you can find a list of all the ids of enchantments [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Enchantments)
- Returns - Map: a map of the enchantments and there levels (String : Number), will return an empty map if there are no enchantments
	- Example: `{"mending" : 1, "unbreaking" : 2}`
- Example: `itemStack.getEnchantments();`

### `<ItemStack>.isBlockItem()`

- This checks if the item is a block item (can be placed as a block)
- Returns - Boolean: whether it is a block item
- Example: `itemStack.isBlockItem();`

### `<ItemStack>.asBlock()`

- This gets the Block from an ItemStack
- Returns - Block: the block of the ItemStack
- Throws: `"Item cannot be converted to block"`
- Example: `itemStack.asBlock();`

### `<ItemStack>.isStackable()`

- This checks whether the ItemStack is stackable
- Returns - Boolean: whether it's stackable
- Example: `itemStack.isStackable();`

### `<ItemStack>.getMaxCount()`

- This gets the maximum stack count that ItemStack can hold
- Returns - Number: the max count
- Example: `itemStack.getMaxCount();`

### `<ItemStack>.getCustomName()`

- This gets the custom name for the ItemStack
- Returns - String: the custom name
- Example: `itemStack.getCustomName();`

### `<ItemStack>.isNbtEqual(otherItemStack)`

- This checks whether the NBT tags of an ItemStack is equal to another
- Parameter - ItemStack: the ItemStack you want to compare
- Returns - Boolean: whether the NBT is equal
- Example: `itemStack.isNbtEqual(Material.GRASS_BLOCK.asItemStack());`

### `<ItemStack>.getNbt()`

- This will get a map of the Nbt of the item
- Returns - Map: a map of all the item Nbt
	- Example: `{"BlockEntityTag" : {"Items" : [ {"Slot" : 0, "id" : "minecraft:spruce_planks", "Count" : 64} ] } }`
- Example: `itemStack.getNbt();`

### `<ItemStack>.getTranslatedName()`

- This gets the translated name of the ItemStack
- Returns - String: the translated name
- Example: `itemStack.getTranslatedName();`

### `<ItemStack>.getMiningSpeedMultiplier(block)`

- This gets the mining speed multiplier of the item on the block
- Parameter - Block: the block you want to get the mining speed multiplier of
- Returns - Number: the multiplier number
- Example: `itemStack.getMiningSpeedMultiplier(Material.GRASS_BLOCK.asBlock());`

### `<ItemStack>.setCustomName(name)`

- This allows you to set a custom name for an ItemStack
- Parameter - String / Text: the string you want to set the name as, or the text which allows you to format it
- Returns - ItemStack: the ItemStack but with the custom name
- Example: `itemStack.setItemLore("Custom Name!");`

### `<ItemStack>.setItemLore(textList)`

- This allows you to set lore for an ItemStack
- Parameter - List: a list of text you want to add, each index in the list will be a new line in the lore
- Returns - ItemStack: the ItemStack but with the lore
- Throws: `"List must contain only Text"`
- Example: `itemStack.setItemLore(Text.of("Fancy"));`

# Recipe class

This class cannot be constructed but you are able to create instances of it by using it's static member `of`

## Static Members

### `Recipe.<RecipeId>`

- The material class has many static members... too many to actually list here, but every single recipe is a static member. All the static members are the id's of the recipes but capitalised.
- Value Type - Recipe
- Assignable: false
- Examples: `Recipe.OAK_PLANKS;`, `Recipe.REDSTONE_BLOCK;`, `Recipe.PISTON;`

### `Recipe.ALL`

- This member is a list that contains all recipes in the game
- Value Type - List: containing recipes
- Assignable: false
- Example: `Recipe.ALL;`

## Static Member Functions

### `Recipe.of(string)`

- This converts a string into a material type if it's valid
- Parameter - String: the recipe id
- Returns - Recipe: the recipe with that id
- Example: `Recipe.of("redstone_block");`

## Member Functions


### `<Recipe>.getId()`

- This gets the id of the recipe
- Returns - String: the recipe id
- Example: `recipe.getId();`

### `<Recipe>.getCraftingType()`

- This gets the crafting type of the recipe
- Returns - String: the crafting type
	- Examples: `"crafting"`, `"smelting"`, `"blasting"`
- Example: `Recipe.GOLD_BLOCK.getCraftingType();`

### `<Recipe>.getOutput()`

- This gets the outputted ItemStack from the recipe
- Returns - ItemStack: the outputted item
- Example: `Recipe.GOLD_BLOCK.getOutput();`

### `<Recipe>.getIngredients()`

- This gets a list of list of ItemStacks being the ingredients of a recipe
- Returns - List: the list contains a lists of ItemStacks
- Example: `Recipe.CHEST.getIngredients();`
```
// This would be an example of the list so you can visualise it
// The lists inside of the list contain all posible items that could go in that slot
// In the case of a chest it's every type of wood plank:
[
    [OAK_PLANK, BIRCH_PLANK, SPRUCE_PLANK...], [OAK_PLANK...], [OAK_PLANK...],
    [OAK_PLANK...], [AIR], [OAK_PLANK...],
    [OAK_PLANK...], [OAK_PLANK...], [OAK_PLANK...]
]
``` 

# Block class

This class cannot be constructed but does have a static method to convert materials to Blocks.

## Static Member Functions

### `Block.of(material)`

- This gets an Blockfrom a Material, alternatively you can use `<Material>.asBlock()`
- Parameter - Material: the material of the Block
- Returns - Block: the new Block
- Throws: `"Material cannot be converted to block"`
- Example: `Block.of(Material.GLASS);`

## Member Functions

This will be used for all examples:

```kt
block = Block.of(Material.GRASS_BLOCK);
```

### `<Block>.getId()`

- This gets the block id (name) of the Block
- Returns - String: the id of the Block
	- Example: `"grass_block"`, `"diamond_block"`
- Example: `block.getId();`

### `<Block>.isBlockEntity()`

- This checks whether the block is a block entity
- Returns - Boolean: whether it is a block entity
- Example: `block.isBlockEntity();`

### `<Block>.isTransparent()`

- This checks if the block is transparent
- Returns - Boolean: whether the block is transparent
- Example: `block.isTransparent();`

### `<Block>.asItemStack()`

- This gets the ItemStack representation of the block
- Returns - ItemStack: the ItemStack representation of the block
- Example: `block.asItemStack();`

### `<Block>.getBlastResistance()`

- This gets the Blocks blast resistance
- Returns - Number: the blast resistance of the block
- Example: `block.getBlastResistance();`

### `<Block>.getBlockProperties()`

- This gets the block properties of the Block, you can find a list of all block properties [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Block_states)
- Returns - Map: map of properties, empty map if there are no properties
	- Example: `{"waterlogged" : true, "age" : 25, "type" : "double"}`
- Example: `block.getBlockProperties();`

### `<Block>.hasBlockPosition()`

- This will return whether the block has a block position or not
- Returns - Boolean: whether the block has a position
- Example: `block.hasBlockPosition();`

### `<Block>.getPos()`

- This will get the position of the block
- Returns - Pos / Null: the position of the block, Null if it doesn't have a position
- Example: `block.getPos();`

### `<Block>.getX()`

- This will get the x position of the block
- Returns - Number / Null: the x position of the block, Null if it doesn't have a position
- Example: `block.getX();`

### `<Block>.getY()`

- This will get the y position of the block
- Returns - Number / Null: the y position of the block, Null if it doesn't have a position
- Example: `block.getY();`

### `<Block>.getZ()`

- This will get the z position of the block
- Returns - Number / Null: the z position of the block, Null if it doesn't have a position
- Example: `block.getZ();`

### `<Block>.getTranslatedName()`

- This gets the translated name of the block
- Returns - String: the translated name
- Example: `block.getTranslatedName();`

### `<Block>.isSolidBlock()`

- This returns whether the block is solid
- Returns - Boolean: whether the block is solid
- Throws: `"Block does not have position"`
- Example: `block.isSolidBlock();`

### `<Block>.rotateYClockwise()`

- This rotates the block state 90 degrees clockwise on Y axis
- Returns - Block: the rotated block
- Example: `block.rotateYClockwise();`

### `<Block>.rotateYCounterClockwise()`

- This rotates the block state 90 degrees anticlockwise on Y axis
- Returns - Block: the rotated block
- Example: `block.rotateYCounterClockwise();`

### `<Block>.mirrorFrontBack()`

- This mirrors the block state front to back
- Returns - Block: the mirrored block
- Example: `block.mirrorFrontBack();`

### `<Block>.mirrorLeftRight()`

- This mirrors the block state left to right
- Returns - Block: the mirrored block
- Example: `block.mirrorLeftRight();`

### `<Block>.isFluid()`

- This checks whether the block is a fluid block
- Returns - Boolean: whether the block is a fluid
- Example: `block.isFluid();`

### `<Block>.isFluidSource()`

- This checks whether the block is a fluid source
- Returns - Boolean: whether the block is a fluid source
- Example: `block.isFluidSource();`

### `<Block>.isReplaceable()`

- This checks whether the block can be replaced
- Returns - Boolean: whether the block is replaceable
- Example: `block.isReplaceable();`

### `<Block>.getHardness()`

- This gets the block's hardness value
- Returns - Number: the block's hardness value
- Example: `block.getHardness();`

### `<Block>.sideCoversSmallSquare(direction)`

- This checks whether the block covers a small square on a side
- Parameter - String: direction ("north", "south", etc...)
- Returns - Boolean: whether it covers a small square
- Throws: `"Block does not have position"`
- Example: `block.sideCoversSmallSquare("north");`

### `<Block>.isSideSolidFullSquare(direction)`

- This checks whether the block's side is a full solid square
- Parameter - String: direction ("north", "south", etc...)
- Returns - Boolean: whether it's side is a full solid square
- Throws: `"Block does not have position"`
- Example: `block.isSideSolidFullSquare("north");`

### `<Block>.isSpawnable()`

- This returns whether a block type can be spawned on by a zombie
- Returns - Boolean: whether it's spawnable
- Throws: `"Block does not have position"`
- Example: `block.isSpawnable();`

### `<Block>.isSpawnable(entity)`

- This returns whether a block type can be spawned on by an entity type
- Parameter - Entity: the entity you want to test, can spawn on the block
- Returns - Boolean: whether it's spawnable
- Throws: `"Block does not have position"`
- Example: `block.isSpawnable();`

### `<Block>.getLuminance()`

- This gets the light level that the block emits
- Returns - Number: the light level
- Example: `block.getLuminance();`

# BoxShape class

This class can be constructed and is responsible for rendering boxes on the client.

## Constructors

### `new BoxShape(pos1, pos2)`

- This creates a BoxShape with 2 positions
- Parameters - Pos, Pos: position of corner 1, position of corner 2
- Returns - BoxShape: the newly constructed BoxShape

### `new BoxShape(x1, y1, z1, x2, y2, z2)`

- This creates a BoxShape with 2 positions
- Parameters - Number, Number, Number, Number, Number, Number: x of corner 1, y of corner 1, z of corner 1, x of corner 2, y of corner 2, z of corner 2
- Returns - BoxShape: the newly constructed BoxShape

### `new BoxShape(pos)`

- This creates a BoxShape with pos at 2 positions (1x1 cube)
- Parameters - Pos: position of box
- Returns - BoxShape: the newly constructed BoxShape

### `new BoxShape(x, y, z)`

- This creates a BoxShape with x, y, z at 2 positions (1x1 cube)
- Parameters - Number, Number, Number: x of box, y of box, z of box
- Returns - BoxShape: the newly constructed BoxShape

## Members

This will be used for all examples:

```kt
box = new BoxShape(0, 100, 0);
```

### `<BoxShape>.pos1`

- This is the position of corner 1
- Value Type: Pos
- Assignable: false
- Example: `box.pos1;`

### `<BoxShape>.pos2`

- This is the position of corner 2
- Value Type: Pos
- Assignable: false
- Example: `box.pos2;`

## Member Functions

### `<BoxShape>.setPos1(pos)`

- This sets the value of position 1
- Parameter - Pos: the new position
- Example: `box.setPos1(new Pos(1, 100, 0));`

### `<BoxShape>.setPos2(pos)`

- This sets the value of position 2
- Parameter - Pos: the new position
- Example: `box.setPos2(new Pos(0, 100, 1));`

### `<BoxShape>.setColour(red, green, blue)` or `<BoxShape>.setColor(red, green, blue)`

- This sets the colour of the main faces of the box
- Parameters - Number, Number, Number: red value between 0-255, green value between 0-255, blue value between 0-255
- Throws: `"Colours must be between 0 and 255"`
- Example: `box.setColour(40, 30, 20);`

### `<BoxShape>.setOpacity(opacity)`

- Sets the opacity of the main faces of the box
- Parameter - Number: opacity value between 0-255
- Throws: `"Colours must be between 0 and 255"`
- Example: `box.setOpacity(200);`

### `<BoxShape>.setOutlineColour(red, green, blue)` or `<BoxShape>.setOutlineColor(red, green, blue)`

- This sets the colour of the outline of the box
- Parameters - Number, Number, Number: red value between 0-255, green value between 0-255, blue value between 0-255
- Throws: `"Colours must be between 0 and 255"`
- Example: `box.setOutlineColour(40, 30, 20);`

### `<BoxShape>.setOutlinePixelWidth(width)`

- Sets the outline width of the outline of the box
- Parameter - Number: the pixel width of the outline
- Example: `box.setOutlinePixelWidth(10);`

### `<BoxShape>.setRenderThroughBlocks(boolean)`

- Sets whether the box should render through blocks
- Parameter - Boolean: whether it should render through blocks
- Example: `box.setRenderThroughBlocks(true);`

### `<BoxShape>.getRed()`

- Gets the red value of the main faces
- Returns: Number: the red value
- Example: `box.getRed();`

### `<BoxShape>.getGreen()`

- Gets the green value of the main faces
- Returns: Number: the green value
- Example: `box.getGreen();`

### `<BoxShape>.getBlue()`

- Gets the blue value of the main faces
- Returns: Number: the blue value
- Example: `box.getBlue();`

### `<BoxShape>.getOpacity()`

- Gets the opacity value of the main faces
- Returns: Number: the opacity value
- Example: `box.getOpacity();`

### `<BoxShape>.getOutlineRed()`

- Gets the red value of the outline
- Returns: Number: the red value
- Example: `box.getOutlineRed();`

### `<BoxShape>.getOutlineGreen()`

- Gets the green value of the outline
- Returns: Number: the green value
- Example: `box.getOutlineGreen();`

### `<BoxShape>.getOutlineBlue()`

- Gets the blue value of the outline
- Returns: Number: the blue value
- Example: `box.getOutlineBlue();`

### `<BoxShape>.getOutlinePixelWidth()`

- Gets the pixel width of the outline
- Returns: Number: the pixel width
- Example: `box.getOutlinePixelWidth();`

### `<BoxShape>.shouldRenderThroughBlocks()`

- Gets whether the box should render through blocks
- Returns: Boolean: whether the box should render through blocks
- Example: `box.shouldRenderThroughBlocks();`

### `<BoxShape>.render()`

- Sets the box for rendering and will be rendered on the client until script stops or `stopRendering` is called
- Example: `box.render();`

### `<BoxShape>.stopRendering()`

- Removes the box for rendering
- Returns - Boolean: whether the box was rendering
- Example: `box.stopRendering()`

# Text class

This class cannot be constructed but you can get instances from it's static methods.

## Static Member Functions

### `Text.of(string)`

- This converts a string into a plain text with that string
- Parameter - String: the string you want to the text to have
- Returns - Text: the text representation of that string
- Example: `Text.of("Example Text");`

### `Text.parse(textJson)`

- This converts a textJson to text
- Parameter - String: a json that represents a text
- Returns - Text: the text of the json
- Example: `Text.parse("{\"text\":\"A\",\"color\":\"white\",\"italic\":\"true\"}");`

This will be used for all examples:

```kt
client = getMinecraftClient();
text = client.textFromString("CLICK ME");
```

### `<Text>.format(formatting)`

- This allows you to format text for Minecraft, list of formatting names can be found [here](https://minecraft.fandom.com/wiki/Formatting_codes)
- Parameter - String: the formatting name, it must be the name of the format
- Returns - Text: the formatted text
- Throws: `"Invalid formatting: ..."`
- Example: `text.format("DARK_RED").format("BOLD");`

### `<Text>.withClickEvent(event, string)`

- This allows you to style your text with a click event
- Parameters - String, String: the event name, the value associated with the event
	- Examples: `"open_url", "https://google.com"`, `"open_file", "C:/Users/user/Desktop/thing.txt"`, `"run_command", "/gamemode creative"`, `"suggest_command", "/gamemode survival"`, `"copy_to_clipboard", "This is your clipboard now :)"`
- Throws: `"Invalid action: ..."`
- Returns - Text: the styled text
- Example: `text.withClickEvent("open_url", "https://youtu.be/dQw4w9WgXcQ");`

### `<Text>.append(otherText)`

- This allows you to append two texts together
- Parameter - Text: a different text you want to append
- Returns - Text: the appended text
- Example: `text.append(client.textFromString(" NOW!"));`

# Screen class

This class cannot be constructed

## Member Functions

This will be used for all examples:

```kt
player = Player.get();
screen = player.getCurrentScreen();
```

### `<Screen>.getName()`

- This gets the Screen's name
- Returns - String: the screen's name, if you are in the creative menu it will return the name of the tab you are on
	- Examples: `"Anvil"`, `"Furnace"`, `"Credits"`, `"Merchant"`
- Throws: `"Screen was null"`
- Example: `screen.getName();`

### `<Screen>.getTitle()`

- This gets the Screen's title
- Returns - String: the screen's title
	- Example: `"Crafting"`, `"Ender Chest"`, `"Cleric"`
- Throws: `"Screen was null"`
- Example: `screen.getTitle();`

# FakeInventoryScreen class

The class can be constructed and it extends `Screen` so it inherits all of Screen's methods

## Constructors

### `new FakeInventoryScreen(name, rows)`

- This creates a new fake inventory screen instance with a name and set amount of rows between 1-6
- Parameters - String, Number: the title of the screen, the number of rows between 1-6
- Returns - FakeInventoryScreen: the newly constructed instance

## Member Functions

This will be used for all examples:

```kt
client = getMinecraftClient();
fakeScreen = new FakeInventoryScreen("example", 3);
```

### `<FakeInventoryScreen>.onClick(function)`

- This lets you define what happens when the player clicks inside of this gui
- Parameter - Function: the function that you want to happen when the player clicks
	- this functions has Parameters - ItemStack, Number, String: the item that was clicked, the slot that was clicked, and the action
- Example:
```kt
fakeScreen.onClick(fun(item, slot, action) {
   print("Item: %S, Slot: %s, Action: %s".formatted([item, slot, action]);
});
```

### `<FakeInventoryScreen>.setStackForSlot(slotNum, itemStack)`

- This lets you set the ItemStack for a slot in the FakeScreen
- Parameters - Number, ItemStack: the slot number, the item you want to put there
- Example: 
```kt
customItem = client.itemFromString("oak_planks").setCustomName("Cool");
fakeScreen.setStackForSlot(0, customItem);
```

### `<FakeInventoryScreen>.getStackForSlot(slotNum)`

- This lets you get the ItemStack that is in a slot
- Paramter - Number: the slot number
- Example: `fakeScreen.getStackForSlot(0);`

# MerchantScreen class

This class cannot be constructed.

## Member Functions

All of these functions can throw: `"Currently not in MerchantScreen..."`

This will be used for all examples:

```kt
player = Player.get();
screen = player.getCurrentScreen();
if (!screen.instanceOf("MerchantScreen")) return;
```

### `<MerchantScreen>.getTradeList()`

- This gets a list of all the merchant's trades
- Returns - List: list of Trades
- Example: `screen.getTradeList();`

### `<MerchantScreen>.getTradeListSize()`

- This gets the size of the list of merchant's trades
- Returns - Number: the number of trades
- Example: `screen.getTradeListSize();`

### `<MerchantScreen>.getVillagerLevel()`

- This gets the level of the villager
- Returns - Number: the level of the villager
- Throws: `"Merchant isn't a villager"`
- Example: `screen.getVillagerLevel();`

### `<MerchantScreen>.getVillagerProfession()`

- This gets the profession of the villager as a string
- Returns - String: the profession of the villager
	- Example: `"armorer"`, `"mason"`, `"weaponsmith"`
- Throws: `"Merchant isn't a villager"`
- Example: `screen.getVillagerProfession();`

### `<MerchantScreen>.tradeIndex(index)`

-  This allows you to trade with a villager at a certain index
-  Parameter - Number: the index of the trade you want to trade
-  Throws:  `"Not in merchant gui"`
-  Example:  `screen.tradeIndex(2);`

### `<MerchantScreen>.getIndexOfTradeItem(itemStack)`

-  This gets the index of an ItemStack in a villagers trade list
-  Parameter - ItemStack: the ItemStack that you want the index of
-  Returns - Number / Null: the index of the trade, can return null if the villager doesn't have the trade
-  Throws:  `"Not in merchant gui"`
- Example: `screen.getIndexofTradeItem(Material.ENCHANTED_BOOK.asItemStack());`

### `<MerchantScreen>.getTradeItemForIndex(index)`

-  This gets an ItemStack of an index in a villagers trade list
-  Parameter - Number: the index of the trade you want the ItemStack for
-  Returns ItemStack: the ItemStack at the index
-  Throws:  `"That trade is out of bounds"`  or  `"Not in merchant gui"`
- Example: `screen.getTradeItemForIndex(2);`

### `<MerchantScreen>.doesVillagerHaveTrade(itemStack)`

-  This checks whether a villager has a trade or not
-  Parameter - ItemStack: the ItemStack that you want to check
-  Returns - Boolean: whether the villager has a trade for that ItemStack
-  Throws:  `"Not in merchant gui"`  or  `"That trade is out of bounds"`
-  Example:  `screen.doesVillagerHaveTrade(Material.DIAMOND_PICKAXE.asItemStack());`

### `<MerchantScreen>.isTradeDisabled(index)`

-  This checks whether a villager's trade is disabled
-  Parameter - Number: the index of the trade you want to check
-  Returns - Boolean: whether the trade is disabled
-  Throws:  `"Not in merchant gui"`  or  `"That trade is out of bounds"`
-  Example:  `screen.isTradeDisabled(4);`

### `<MerchantScreen>.getPriceForIndex(index)`

-  This gets the price of the trade at an index
-  Parameter - Number: the index of the trade
-  Returns - Number: the price of the trade
-  Throws:  `"Not in merchant gui"`  or  `"That trade is out of bounds"`
-  Example:  `screen.getPriceForIndex(1);`

### `<MerchantScreen>.selectTrade(index)`

- This selects a trade at an index
- Paramter - Number: the index of the trade
- Throws: `"Not in merchant gui"`
- Example: `screen.selectTrade(1);`

### `<MerchantScreen>.clearTrade()`

- This clears the selected trade
- Throws: `"Not in merchant gui"`
- Example: `screen.clearTrade();`

### `<MerchantScreen>.isTradeSelected()`

- This checks whether a trade is currently selected
- Returns - Boolean: whether a trade is currently selected
- Example: `screen.isTradeSelected();`

### `<MerchantScreen>.tradeSelected()`

- This trades the currently selected trade
- Throws: `"Not in merchant gui"`
- Example: `screen.tradeSelected();`

### `<MerchantScreen>.tradeSelectedAndThrow()`

- This trades the currently selected trade and throws the result
- Throws: `"Not in merchant gui"`
- Example: `screen.tradeSelectedAndThrow();`

# Trade class

This class cannot be constructed.

## Member Functions

This will be used for all examples:

```kt
player = Player.get();
screen = player.getCurrentScreen();
if (!screen.instanceOf("MerchantScreen")) return;
trade = screen.getTradeList().get(0);
```

### `<Trade>.getSellItem()`

- This gets the item that the villager is selling
- Returns - ItemStack: the item for sale
- Example: `trade.getSellItem();`

### `<Trade>.getFirstBuyItem()`

- This gets the first item that the villager wants to buy
- Returns - ItemStack: the item that the villager wants to buy
- Example: `trade.getFirstBuyItem();`
- 
### `<Trade>.getAdjustedFirstBuyItem()`

- This gets the first item that the villager wants to buy with adjusted amount
- Returns - ItemStack: the item that the villager wants to buy with adjusted amount
- Example: `trade.getAdjustedFirstBuyItem();`

### `<Trade>.getSecondBuyItem()`

- This gets the second item the villager wants to buy
- Returns - ItemStack: the second item that the villager wants to buy
- Example: `trade.getSecondBuyItem();`

### `<Trade>.getMaxUses()`

- This gets the max uses the trade can be traded for
- Returns - Number: the max uses
- Example: `trade.getMaxUses();`

### `<Trade>.getUses()`

- This gets the current amount of times the trade has been used since last reset
- Returns - Number: the number of uses
- Example: `trade.getUses();`

### `<Trade>.getSpecialPrice()`

- This gets the spectial price which is used to adjust the first buy item, lower this is the lower the price is
- Returns - Number: the special price
- Example: `trade.getSpectialPrice();`

### `<Trade>.getPriceMultiplier()`

- This gets the price multiplier which is used to adjust the first buy item
- Returns - Number: the price multiplier
- Example: `trage.getPriceMultiplier();`

# Json Class

This class cannot be directy constructed, but it does have it's own Json value.

## Static Member Functions

### `Json.fromString(string)`

- This converts a string into a Json provided it is formatted correctly
- Parameter - String: the string that you want to parse into a Json
- Returns - Json: the Json parsed form the string
- Throws: `"Json could not be parsed"`
- Example: `Json.fromString("{\"sensei\":10}");`

### `Json.fromList(list)`

- This converts a list into a Json, an important thing to note is that any values that are not Numbers, Booleans, Lists, Maps, or Null will use their `toString()` member to convert them to a string. 
- Parameter - List: the list you want to convert
- Returns - Json: the Json from the list
- Example: `Json.fromList(["sensei", "foo", "bar"]);`

### `Json.fromMap(map)`

- This converts a map into a Json, an important thing to note is that any values that are not Numbers, Booleans, Lists, Maps, or Null will use their `toString()` member to convert them to a string. 
- Parameter - Map: the map you want to convert
- Returns - Json: the Json from the map
- Example: `Json.fromMap({"foo" : ["bar", "baz"]});`

## Member Functions

This will be used for all examples:

```kt
json = Json.fromString("{\"foo\": 10, \"baz\": 5}");
```

### `<Json>.getValue()`

- This converts the Json back into a Value
- Returns - String, Number, Boolean, List, Map, Null: the Value parsed from a Json
	- Example: `{"foo" : 10, "baz" : 5}`
- Example: `json.getValue();`

### `<Json>.writeToFile(file)`

- This writes the Json to a file
- Parameter - File: the file you want to write to
- Throws: `"There was an error writing the file: ..."`
- Example: `json.writeToFile(new File("D:/cool/realDirectory"))`

## Events

Events are on a separate wiki page, see [here](https://github.com/senseiwells/EssentialClient/wiki/ClientScript---Events)

## Example Code

Example Code is on a separate wiki page, see [here](https://github.com/senseiwells/EssentialClient/wiki/ClientScript---Example-Code)

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

# Forbidden Magic:

These are classes and functions that are kinda unnecessary and complicated (brigadier), but are here for the more advanced scripters who want to use it.

# CommandBuilder class (continued)

## Static Member Functions

### `CommandBuilder.literal(string)`

- This creates a CommandBuilder with a literal string name
- Parameter - String: the name of the command/subcommand
- Returns - CommandBuilder: the CommandBuilder with literal name
- Example: `CommandBuilder.literal("examplecommand");`

### `CommandBuilder.argument(name, type)`

- This creates a CommandBuilder with an argument 
- Parameter - String, String: the name of the command/subcommand, the argument type
- Returns - CommandBuilder: the CommandBuilder with argument
- Example: `CommandBuilder.argument("examplearg", "ItemStack");`

### `CommandBuilder.argument(string, type, suggests)`

- This creates a CommandBuilder with an argument 
- Parameter - String, String, List: the name of the command/subcommand, the argument type, list of suggested strings for the argument
- Returns - CommandBuilder: the CommandBuilder with argument
- Example: `CommandBuilder.argument("examplearg", "Word". ["suggestion1", "2", "foo"]);`

## Member Functions

This will be used for all examples:

```kt
literal = CommandBuilder.literal("example");
argument = CommandBuilder.argument("argument", "Boolean");
argument2 = CommandBuilder.argument("otherArgument", "Entity");
```

### `<CommandBuilder>.then(subCommandBuilder)`

- This adds a child CommandBuilder to your command builder
- Parameter - CommandBuilder: the sub command builder
- Returns - CommandBuilder: the original command builder
- Example: `literal.then(argument.then(argument2));`

### `<CommandBuilder>.executes(function)`

- This adds a function to the current command builder
- Parameter - Function: the function you want to run when the command is executed at this builder
- Returns - CommandBuilder: the original command builder
- Example: `literal.executes(fun() { print("example command was run"); });`

### `<CommandBuilder>.requires(predicate)`

- This adds a predicate to the command meaning a function that returns either true of false
- Parameter - Function: the predicate of whether the command should be allowed to be used
- Returns - CommandBuilder: the original command builder
- Example: 
```
literal.requires(fun() { 
    return Player.get().getGamemode() == "creative";
});
```

- Effect Command Example:
```kt
root = literal("effect");

root.then(
    literal("give").then(
        argument("targets", "PlayerName").then(
            argument("effect", "Potion").executes(fun (playerName, potion) {
                // give playerName potion
            }).then(
                argument("seconds", "Integer").executes(fun (playerName, potion, seconds) {
                    // give playerName potion for seconds
                }).then(
                    argument("amplifier", "Integer").executes(fun (playerName, potion, seconds, amplifier) {
                        // give playerName potion for seconds with amplifier
                    }).then(
                        argument("hideParticles", "Boolean").executes(fun (playerName, potion, seconds, amplifier, hideParticles) {
                            // give playerName potion for seconds with amplifier and hideParticles
                        })
                    )
                )
            )
        )
    )
)
root.then(
    literal("clear").executes(fun () {
        // clears own effect
    }).then(
        argument("targets", "PlayerName").executes(fun (playerName) {
            // clears playerName effect
        }).then(
            argument("effect", "Potion").executes(fun (playerName, potion) {
                // clears potion from playerName
            })
        )
    )
)
```

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

# Events

Events are triggers for certain events that happen in the game. ClientScript provides a way to hook into these triggers to be able to run your code. You can register multiple functions to an event and they will all get called. [See here](https://github.com/senseiwells/EssentialClient/wiki/ClientScript#gameevent-class) on how to register and unregister events. Each event will run async by default but you are able to run it on the main game thread.

## Available Events

This will be used for examples:
```kt
client = MinecraftClient.getClient();
```

### `"onClientTick"`

- This event gets called every client tick
- Cancellable: false
- Example:
```kt
onTickEvent = new GameEvent("onClientTick", fun() {
    // Code
});
```

### `"onHealthUpdate"`

- This event gets called when the player's health is updated
- Parameter - Number: the players health
- Cancellable: false
- Example:
```kt
onHealthEvent = new GameEvent("onHealthUpdate", fun(health) {
    // Code
});
```

### `"onTotem"`

- This event gets called when a totem is used
- Cancellable: false
- Example:
```kt
onTotemEvent = new GameEvent("onTotem", fun() {
    // Code
});
```

### `"onPickBlock"`

- This event gets called when you pick a block (middle click)
- Parameter - ItemStack: the item you picked
- Cancellable: false
- Example:
```kt
onPickBlockEvent = new GameEvent("onPickBlock", fun(itemStack) {
    // Code
});
```

### `"onCloseScreen"`

- This event gets called when you close a screen
- Parameter - Screen: the screen you closed
- Cancellable: false
- Example:
```kt
onCloseScreenEvent = new GameEvent("onCloseScreen", fun(screen) {
    // Code
});
```

### `"onConnect"`

- This event gets called when you connect to a world
- Parameter - Player, World: the main player, the current world
- Cancellable: false
- Example:
```kt
onConnectEvent = new GameEvent("onConnect", fun(player, world) {
    // Code
});
```

### `"onDisconnect"`

- This event gets called when you disconnect a world
- Cancellable: false
- Example:
```kt
onDisconnectEvent = new GameEvent("onDisconnect", fun() {
    // Code
});
```

### ~~`"onCommand"`~~

- **This event is deprecated and will be removed in a future release**, the old command system has now been replace with the `CommandBuilder`
- This event gets called when you enter a command
- Parameter - String, List: the name of the command, the command arguments
- Cancellable: false
- Example:
```kt
onCommandEvent = new GameEvent("onCommand", fun(command, args) {
    // Code
});
```

### `"onOpenScreen"`

- This event gets called when you open a screen
- Parameter - Screen: the opened screen
- Cancellable: false
- Example:
```kt
onOpenScreenEvent = new GameEvent("onOpenScreen", fun(screen) {
    // Code
});
```

### `"onPickUpItem"`

- This event gets called when you pick up an item
- Parameter - ItemStack: the item you picked up
- Cancellable: false
- Example:
```kt
onPickUpItemEvent = new GameEvent("onPickUpItem", fun(itemStack) {
    // Code
});
```

### `"onFishBite"`

- This event gets called when a fish bites your fishing rod
- Parameter - Entity: the fishing bobber
- Cancellable: false
- Example:
```kt
onFishBiteEvent = new GameEvent("onFishBite", fun(fishBobber) {
    // Code
});
```

### `"onDeath"`

- This event gets called when you die
- Parameter - Entity / Null, Text: the entity that killed you, null if none, the message that will print
- Cancellable: false
- Example:
```kt
onDeathEvent = new GameEvent("onDeath", fun(entity, message) {
    // Code
});
```

### `"onRespawn"`

- This event gets called when you respawn
- Parameter - Player: the new main player
- Cancellable: false
- Example:
```kt
onRespawnEvent = new GameEvent("onRespawn", fun(player) {
    // Code
});
```

### `"onEat"`

- This event gets called when you eat something
- Parameter - ItemStack: the item you ate
- Cancellable: false
- Example:
```kt
onEatEvent = new GameEvent("onEat", fun(itemStack) {
    // Code
});
```

### `"onGamemodeChange"`

- This event gets called when you change gamemode
- Parameter - String: the gamemode
- Cancellable: false
- Example:
```kt
onGamemodeChangeEvent = new GameEvent("onGamemodeChange", fun(newGamemode) {
    // Code
});
```

### `"onBlockBroken"`

- This event gets called when you break a block
- Parameter - Block: the block being broken (contains the position)
- Cancellable: false
- Example:
```kt
onBlockBrokenEvent = new GameEvent("onBlockBroken", fun(block) {
    // Code
});
```

### `"onDimensionChange"`

- This event gets called when you change dimension
- Parameter - World: the new world you are in
- Cancellable: false
- Example:
```kt
onDimensionChangeEvent = new GameEvent("onDimensionChange", fun(newWorld) {
    // Code
});
```

### `"onPlayerJoin"`

- This event gets called when another player joins the game
- Parameter - String: the name of the player
- Cancellable: false
- Example:
```kt
onPlayerJoinEvent = new GameEvent("onPlayerJoin", fun(name) {
    // Code
});
```

### `"onPlayerLeave"`

- This event gets called when another player leaves the game
- Parameter - String: the name of the player
- Cancellable: false
- Example:
```kt
onPlayerLeaveEvent = new GameEvent("onPlayerLeave", fun(name) {
    // Code
});
```

### `"onAttack"`

- This event gets called when you attack
- Cancellable: true
- Example:
```kt
onAttackEvent = new GameEvent("onAttack", fun() {
    // Code
}, true);
```

### `"onUse"`

- This event gets called when you use
- Cancellable: true
- Example:
```kt
onUseEvent = new GameEvent("onUse", fun() {
    // Code
}, true);
```

### `"onKeyPress"`

- This event gets called when you press a key
- Parameter - String: key you pressed
- Cancellable: true
- Example:
```kt
onKeyPressEvent = new GameEvent("onKeyPress", fun(key) {
    // Code
}, true);
```

### `"onKeyRelease"`

- This event gets called when you release a key
- Parameter - String: key you released
- Cancellable: true
- Example:
```kt
onKeyReleaseEvent = new GameEvent("onKeyRelease", fun(key) {
    // Code
}, true);
```

### `"onDropItem"`

- This event gets called when you drop an item
- Parameter - ItemStack: the item you dropped
- Cancellable: true
- Example:
```kt
onDropItemEvent = new GameEvent("onDropItem", fun(itemStack) {
    // Code
}, true);
```

### `"onInteractItem"`

- This event gets called when you iteract with an item
- Parameter - ItemStack: the itemStack you interacted with
- Cancellable: true
- Example:
```kt
onInteractItemEvent = new GameEvent("onInteractItem", fun(itemStack) {
    // Code
}, true);
```

### `"onInteractEntity"`

- This event gets called when you interact with an entity
- Parameter - Entity, ItemStack: the entity you interacted with, the player's hand item
- Cancellable: true
- Example:
```kt
onInteractEntityEvent = new GameEvent("onInteractEntity", fun(entity, itemStack) {
    // Code
}, true);
```

### `"onSendMessage"`

- This event gets called when you send a message
- Parameter - String: the message you sent
- Cancellable: true
- Example:
```kt
onSendMessageEvent = new GameEvent("onSendMessage", fun(message) {
    // Code
}, true);
```

### `"onReceiveMessage"`

- This event gets called when you receive a message
- Parameter - String: message
- Cancellable: true
- Example:
```kt
onReceieveMessage = new GameEvent("onReceiveMessage", fun(message) {
    // Code
}, true);
```

### `"onClickSlot"`

- This event gets called when you click a slot
- Parameter - Number: the slot number
- Cancellable: true
- Example:
```kt
onClickSlotEvent = new GameEvent("onClickSlot", fun(slotNum) {
    // Code
}, true);
```

### `"onAttackBlock"`

- This event gets called when you attack a block
- Parameter - Block: the block you attacked (contains pos)
- Cancellable: true
- Example:
```kt
onAttackBlockEvent = new GameEvent("onAttackBlock", fun(block) {
    // Code
}, true);
```

### `"onAttackEntity"`

- This event gets called when you attack an entity
- Parameter - Entity: the entity you are attacking
- Cancellable: true
- Example:
```kt
onAttackEntityEvent = new GameEvent("onAttackEntity", fun(entity) {
    // Code
}, true);
```

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

# Example Code

## Mining Junk

This is a very simple script that throws out all the junk items you don't want to pick up when you are mining.
```kt
player = Player.get();

// List of item names you want to throw away
stuffToThrow = [
    Material.STONE.asItemStack(),
    Material.DIRT.asItemStack(),
    Material.COBBLESTONE.asItemStack(),
    Material.GRAVEL.asItemStack()
];

while (true) {
    foreach (item : stuffToThrow) {
        player.dropAll(item);
    }
    sleep(50); // looping every 50 ms is a bit overkill, you can tone this down
}

```

## Finding Obsidian

This is a more complex script that checks an area around the player and highlights any obsidian blocks. This could be useful for example when making a quarry and needing to manually clear obsidian.
```kt
class SingleBoxManager {
    var boxes = { };

    fun clearBoxes() {
        foreach (box : this.boxes.getValues()) {
            box.stopRendering();
        }
        this.boxes.clear();
    }

    fun addPosition(x, y, z) {
        boxPos = new Pos(x, y, z);
        if (!this.boxes.getKeys().contains(boxPos)) {
            box = new BoxShape(boxPos);
            box.setOutlinePixelWidth(0);
            box.setOpacity(50);
            box.setRenderThroughBlocks(true);
            box.render();
            this.boxes.put(boxPos, box);
        }
    }

    fun removePosition(x, y, z) {
        boxPos = new Pos(x, y, z);
        box = this.boxes.remove(boxPos);
        if (box != null) {
            box.stopRendering();
        }
    }
}

client = MinecraftClient.getClient();
boxManager = new SingleBoxManager();
shouldRun = false;
searchRadius = 64;
fromY = 0;
toY = 64;

fun findObsidian() {
    player = Player.get();
    world = client.getWorld();
    x = player.getX().floor();
    y = player.getY().floor();
    z = player.getZ().floor();
    for (i = x - searchRadius; i < x + searchRadius; i++) {
        for (j = fromY; j < toY; j++) {
            for (h = z - searchRadius; h < z + searchRadius; h++) {
                block = world.getBlockAt(i, j, h);
                if (block.getMaterial() == Material.OBSIDIAN) {
                    boxManager.addPosition(i, j, h);
                }
                else {
                    boxManager.removePosition(i, j, h);
                }
            }
        }
    }
}

findObsidianCommand = {
    "name" : "findObsidian",
    "subcommands" : {
        "find" : {
            "" : findObsidian,
            "start" : {
                "" : fun() {
                    print("Started searching for obsidian");
                    shouldRun = true;
                }
            },
            "stop" : {
                "" : fun() {
                    print("Stopped searching for obsidian");
                    shouldRun = false;
                }
            }
        },
        "clear" : {
            "" : fun() {
                boxManager.clearBoxes();
            }
        },
        "radius <radius>" : {
            "" : fun(radius) {
                if (radius > 128) {
                    print("Warning radius of over 128 will take a long time!");
                }
                searchRadius = radius;
            }
        },
        "height <from> <to>" : {
            "" : fun(from, to) {
                fromY = from;
                toY = to;
            }
        }
    },
    "arguments" : {
        "radius" : {
            "type" : "Integer",
            "min" : 1,
            "max" : 512,
            "suggests" : [64, 128, 256]
        },
        "from" : {
            "type" : "Integer",
            "min" : -64,
            "max" : 319,
            "suggests" : [0, -64]
        },
        "to" : {
            "type" : "Integer",
            "min" : -64,
            "max" : 319,
            "suggests" : [64, 128]
        }
    }
};

client.addCommand(CommandBuilder.fromMap(findObsidianCommand));

// This is so when we break a block of Obsidian it stops highlighting the position
blockBreakEvent = new GameEvent("onBlockBroken", fun(block) {
    if (block.getMaterial() == Material.OBSIDIAN) {
        boxManager.removePosition(block.getX(), block.getY(), block.getZ());
    }
});

blockBreakEvent.register();

while (true) {
    if (shouldRun) {
        findObsidian();
    }
    // We check all obsidian then take a 1 second break
    sleep(1000);
}

hold();
```

