# JS Basics

## JS data types

1. undefined
2. null
3. boolean
4. string -> Cannot be changed by the notation <str>[0] = newstring 5. symbol
5. bigint
6. number
7. object
8. array

**Obs:. Use camelCase to declare variable names in js**

## Declaration of variables

1. var <myvar>:
   Can be accidentaly overwritten in the code;
   var is declared globally, or locally if declared inside a function.
2. let <myvar>:
   Inside a block, statement, or expression, its scope is limited to
   that block, statement, or expression.
3. const <myvar>:
   Not reassigned;
   Bbjects (including arrays and functions) assigned to a variable using const are still mutable.

```javascript
Const eg.:

const s = [5, 6, 7];        // s = [5, 6, 7]
s = [1, 2, 3];              // Will result in an error
s[2] = 45;                  // Will not result in an error
console.log(s);             // [5, 6, 45]
```

## Escaping Literals

1. Using backslash(\\) before quotes(")
2. All escaping char are in the table below

| CODE | OUTPUT          |
| ---- | --------------- |
| \'   | single quote    |
| \"   | double quote    |
| \\\  | backslash       |
| \n   | new line        |
| \r   | carriage return |
| \t   | tab             |
| \b   | word boundary   |
| \f   | form feed       |

## Arrays

Data collection in format square brackets format: ["string", 1237]

### Tips and tricks below

```javascript
Get the last item of an array

const arr = []
arr.at(-1)      // returns the last element
```

```
Most used methods to do manipulation of arrays

push(): Used to append data in a array on last position.
pop(): Used to remove the last data in a array.
shift(): Used to remove the first data in a array.
unshift(): Used to append data in a array on first position.
```

## OOP and Classes

### Constructor

Its the initializer of a class, needed to be provided to instantiate a new obj

It is convention to precede the name of a private variable with an underscore (\_). However, the practice itself does not make a variable private.

```javascript
class UpperName {
   constructor(param) {
      this._param = param
   }

   // Getter
   get param() { return this._param }

   // Setter
   set param(newvalue) { this._param = newvalue }
}

// to set new value using getter
const test = new UpperName("param");
console.log(test) // "param"
test.param = 10
console.log(test.param) // 10
```

## Object/Object literals

### Properties and values

```javascript
const cat = {
   name: "Whiskers",
   "total of legs": 4,
   tail": 1,
   enemies: ["Water", "Dogs"]
};
```

### Access the object props with dot notation or bracket notation

The bracket notation is used when access the prop with a variable or with a "divided string" prop

```javascript
cat.name;

let name;
cat[name];

cat["name of cat"];
```

### Tips and tricks below

```javascript
// Verify if a prop exists in an obj

obj.hasOwnProperty(propName)
```

```javascript
// Remove a prop of an obj

delete obj.prop
```

```javascript
// Add prop with dot and square notation

obj.newprop = <value>
obj[newprop] = <value>
```

```javascript
// JS provides a function to not allow changes in a obj: Object.freeze(myObj)

let obj = {
   name:"FreeCodeCamp",
   review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad";
obj.newProp = "Test";
console.log(obj); // { name: "FreeCodeCamp", review: "Awesome" }
```

## Functions

### Declaration

```javascript
function name(param) {
   return // If you do not specify the return, js function will return a undefined value
}
```

### Scopes

Its possible to have two variables(global and local) with the same name.
When you do this, the local var takes precedence over the global.

### Rest parameter

Use the Rest(...) parameter with function parameters to use a function with undefined
number of parameters

```javascript
function howMany(...args) {
   return "You have passed " + args.length + " arguments.";
}
```

## Arrow functions

1. Used to write concise anonymous function (functions without a name)
2. Can receive a simple parameter or a default parameter

```javascript
const myFunc = (param="default value if param is undefined") => {
   const myVar = "value";
   return myVar;
}

```

## Comparison operators

1. Equality operator ==
2. Strict equality operator ===
3. Inequality operator !=
4. Strict inequality op. !==

**Obs:. When we use the strict operators, js compare data type and data value.**

## Loops

1. while
2. for
3. do while

## Variables conversion

1. The parseInt() function parses a string and returns an integer.
2. parseInt(string, radix); -> radix: which specifies the base of the number in the string

```javascript
const a = parseInt("007"); // a = 007
```

## Ternary operator

1. Basic syntax: is a == b ? "Equal" : "Not Equal"
2. Can be used with one or multiple conditions like if/else if/else

```javascript
num > 0 ? "positive" : num < 0 ? "negative" : "zero"
```

## Spread operator (...arr)

### Used to return a unpacked array

```javascript
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);
```

The spread operator only works in-place, like in an argument to a function or
in an array literal.

**The following code will not work:**

```javascript
const spreaded = ...arr;
```

## Destructuring

### Special syntax for neatly assigning values taken directly from an object.

```javascript
const user = { name: 'John Doe', age: 34 };
const { name, age } = user;

// A little bit more complex
const user = {
   johnDoe: {
      age: 34,
      email: 'johnDoe@freeCodeCamp.com'
   }
};

const { johnDoe: { age: userAge, email: userEmail }} = user;
```

### ES6 makes easy to destructuring arrays also

```javascript
const [a, b] = [1, 2, 3, 4, 5, 6]; // a = 1; b = 2;
const [a, b,,, c] = [1, 2, 3, 4, 5, 6]; // a = 1; b = 2; c = 5;
```

### Tips and tricks below

### Destructuring assignment with the Rest parameter to performe an effective array.slice()

```javascript
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7]; a = 1; b = 2; arr = [3,4,5,7]
```

### Destructuring an object sent to a function parameter

```javascript
const profileUpdate = ({ name, age, nationality, location }) => {}

profileUpdate(obj)
```

## Modules

### type = module allow a JS file to use import and export modules

```javascript
<script type="module" src="filename.js"></script>
```

### Use export to share a code block

```javascript
export const add = (x, y) => {
   return x + y;
}

// or

const add = (x, y) => {
   return x + y;
}

export { add };
```

### If you have more functions in the same file to export use

```javascript
const add = (x, y) => {
   return x + y;
}

const subtract = (x, y) => {
   return x - y;
}

export { add, subtract };
```

### To import from a module use

```javascript
import { add, subtract } from "./filepath.js;
```

To import all from a module use \* notation

```javascript
import \* as myMathModule from "./math_functions.js";
```

### Export default

Since export default is used to declare a fallback value for a module or file, you can only have one value be a default export in each module or file. Additionally, you cannot use export default with var, let, or const

```javascript
export default function add(x, y) {
   return x + y;
}
```

### Import default

The imported value, add, is not surrounded by curly braces. You can use any name here when importing a default.

```javascript
import add from "./math_functions.js";
```

## Promise

A promise in JavaScript is exactly what it sounds like - you use it to make a promise to do something, usually asynchronously.

A promise has three states

1. Pending
2. Fulfilled
3. Rejected

Basic promise:

```javascript
const myPromise = new Promise((resolve, reject) => {});
```

Handle a fulfilled promise with then

```javascript
myPromise.then(result => {});
```

Handle a reject promise with catch

```javascript
myPromise.catch(error => {});
```

## Regex

Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching.

### One way to test a regex in js is using the method .test()

```javascript
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr); // true
```

### Matching a string with different possibilities with OR operator (|)

```javascript
myRegex = /yes|no|maybe/
```

### Flags

Reference: https://javascript.info/regexp-introduction

Flag i

```
Case insensitive
```

Flag g

```
All matches
```

Flag m

```
Multiline mode
```

Flag s

```
Enables “dotall” mode, that allows a dot . to match newline character \n
```

Flag u

```
Enables full Unicode support
```

Flag y

```
“Sticky” mode: searching at the exact position in the text
```

### Extract matches

To extract strings use the method .match()

```javascript
"Hello, World!".match(/Hello/); //["Hello"]
```

To find more than the first match use the flag g

```javascript
let testStr = "Repeat, Repeat, Repeat";
let repeatRegex = /Repeat/g;
testStr.match(repeatRegex); // ['Repeat', 'Repeat', 'Repeat']
```

**Obs about flags: You can have more than 1 flag by regex**

### Match anything with wildcard period (.)

The wildcard character . will match any one character.

```javascript
let humStr = "I'll hum a hummmmmmmmmm song";
let huRegex = /hu./;
huRegex.test(humStr); // true because have one or more "hu." words
```

### Match single char with mult possibilities

Character classes allow you to define a group of characters you wish to match by placing them inside square ([ and ]) brackets.

For example, if I need to find "bag", "big", "bug" but not "bog. I can create the regex /b[aiu]/

```javascript
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex);        // big
bagStr.match(bgRegex);        // bag
bugStr.match(bgRegex);        // bug
bogStr.match(bgRegex);        // null
```

### Match letters and numbers of alphabet

Inside a character set, you can define a range of characters to match using a hyphen character: -

```javascript
let catStr = "cat";
let batStr = "bat";
let matStr = "mat";
let bgRegex = /[a-e]at/;
```

It is possible to do with numbers also.

```javascript
let jennyStr = "Jenny8675309";
let myRegex = /[a-z0-9]/ig;
jennyStr.match(myRegex);
```

### Negated character sets

Used to specify which characters I dont want to find using the ^

```javascript
/[^aeiou]/gi      // will match all non vowels
```

### Matching beginning string patterns

Outside of a char set the ^is used to search for patterns at the beginning of strings

```javascript
let firstString = "Ricky is first and can be found.";
let firstRegex = /^Ricky/;
firstRegex.test(firstString);          // true

let notFirst = "You can't find Ricky now.";
firstRegex.test(notFirst);             // false
```

### Match ending string patterns

To search the end of strings using the dollar sign character $ at the end of the regex.

```javascript
let theEnding = "This is a never ending story";
let storyRegex = /story$/;
storyRegex.test(theEnding);         // true

let noEnding = "Sometimes a story will have to end";
storyRegex.test(noEnding);          // false
```

### Match characters that occur one or more times

You can use the + character to check if that is the case

```javascript
let regex = /a+/g          // Will find and return ["a"]
```

### Match characters that occur zero or more times

The character to do this is the asterisk or star: \*

```javascript
let goRegex = /go*/;
```

### Lazy match

Regular expressions are by default greedy, so the match would return ["titani"]. It finds the largest sub-string possible to fit the pattern.

However, you can use the ? character to change it to lazy matching. "titanic" matched against the adjusted regex of /t[a-z]\*?i/ returns ["ti"].

```javascript
const titanic = "titanic"
const mregex = /t[a-z]*?i/

console.log(titanic.match(mregex))  // ["ti"]
```

### Character classes

#### Match the alphabet with \w

\w is a short mode to find [A-Za-z0-9_]

```javascript
let shortHand = /\w/;
```

#### Match non alphanumeric with \W

\W is a short mode to find [^a-za-z0-9_]

```javascript
let shortHand = /\W+/;
```

#### Match all numbers

The shortcut to look for digit characters is \d, is the same to use [0-9]

#### Match all non numbers

The shortcut to look for non digit characters is \D, is the same to use [^0-9]

#### Match white spaces

You can search for whitespace using \s, which is a lowercase s. This pattern not only matches whitespace, but also carriage return, tab, form feed, and new line characters. You can think of it as similar to the character class [ \r\t\f\n\v].

#### Match non white spaces

Search for non-whitespace using \S, which is an uppercase s. This pattern will not match whitespace, carriage return, tab, form feed, and new line characters. You can think of it being similar to the character class [^ \r\t\f\n\v].

### Specify a quantity of letters to match

#### Specify Upper and Lower Number of Matches

You can specify the lower and upper number of patterns with quantity specifiers. Quantity specifiers are used with curly brackets ({ and }). You put two numbers between the curly brackets - for the lower and upper number of patterns.

for example: /a{3,5}h/

```javascript
let A4 = "aaaah";
let A2 = "aah";
let multipleA = /a{3,5}h/;
```

#### Specify Only the Lower Number of Matches

You can specify the lower and upper number of patterns with quantity specifiers using curly brackets.
For example: /ha{3,}h/

```javascript
let A4 = "haaaah";
let A2 = "haah";
let A100 = "h" + "a".repeat(100) + "h";
let multipleA = /ha{3,}h/;
multipleA.test(A4);
multipleA.test(A2);
multipleA.test(A100);
```

#### Specify Exact Number of Matches

You can specify the lower and upper number of patterns with quantity specifiers using curly brackets.

```javascript
let A4 = "haaaah";
let A3 = "haaah";
let A100 = "h" + "a".repeat(100) + "h";
let multipleHA = /ha{3}h/;
multipleHA.test(A4);
multipleHA.test(A3);
multipleHA.test(A100);
```

#### Check for All or None

You can specify the possible existence of an element with a question mark, ?. This checks for zero or one of the preceding element. You can think of this symbol as saying the previous element is optional.

```javascript
let american = "color";
let british = "colour";
let rainbowRegex= /colou?r/;
rainbowRegex.test(american);
rainbowRegex.test(british);
```

### Check For Mixed Grouping of Characters

Sometimes we want to check for groups of characters using a Regular Expression and to achieve that we use parentheses ().
If you want to find either Penguin or Pumpkin in a string, you can use the following Regular Expression: /P(engu|umpk)in/g

```javascript
let testStr = "Pumpkin";
let testRegex = /P(engu|umpk)in/;
testRegex.test(testStr);
```

### Remove Whitespace from Start and End

```javascript
let hello = "   Hello, World!  ";
let wsRegex = /^\s+|\s+$/g;
let result = hello.replace(wsRegex, "");
```
