# Javascript101 

## 1. Variables 

1. Variables are containers which stores some values.
2. Variables are case-sensitive.
3. Variables are loosly typed. (we do not use int,boolean,float,long,etc to store values , this is done in strongly typed languages such as java,c++,etc)
4. **var** is the keyword used to declare variables.
5. Assign value to the variable using =(equal to) operator.

### Rules for constructing a variable

1. Names containes $,letters,digits and underscores.
2. Variable name can be of any length.
3. Names can begin with letter,$ and underscore.
4. Reserved words like (true,switch,if else,etc) cannot be used.

## 2. Datatypes

Variables in Javascript are "dynamically typed". There are 8 types of datatype in Javascript.
Primitive datatype (which can store one value at a time), Composite datatype (which can store multiple value), 
special types

### 1. Integer 

Integer can be any of integer type or floating type. Range of integer lies between -(2<sup>53</sup>-1) to 2<sup>53</sup>-1.

```javascript
int val = 12;
int val = 124;
int val = 124.56;
int val =  0;
int val = -0;
int val = Infinity;
int val = -Infinity;
int val = NaN; //Not a number
```
### 2. String

Anything betwwen single quotes(''),double quotes("") and back tick(``) is a string 

```javascript
var name1 = "Germany";
var name2 = 'Denmark';
var name = `France`;
var combine = name1 + name2;
var isboolean = "true";// It's a string
var isint = "1";// It's a string 
```

### 3. Boolean

Returns two values either true or false

```javascript
var s1=true;
var s2=false;
```
### 4. BigInt

BigInt type was recently added to the language to represent integers of arbitrary length.
A BigInt value is created by appending n to the end of an integer.

```javascript
var val1 = 9999865n;
var val2 = BigInt(999865);
//9999865n
```
### 5. undefined

The meaning of undefined is “value is not assigned”.

```javascript
var val1 ; // Automatically assigned undefined
var val2 = undefined; // It is not recommended to use undefined , use null instead
```
### 6. null

It’s just a special value which represents “nothing”, “empty” or “value unknown”.

```javascript
var val1 = null;
```
### 7. Object 

1. Access the object using dot notation or array.
2. Array notation is useful when you have space in your properties name.
3. Use delete operator to delete property or method.
4. Fetch all the keys using Object.keys().
5. Convert Object to string using JSON.stringify(obj) and string to object using JSON.parse(string).

***Object Literal***
```javascript
var obj1 = {
    name:"Adam",
    age:24,
    greetings:function(){
        return "Hello Adam";
    }
}

var obj2.name = "Prat";
var obj2.age = 24;

var obj4;
obj4["age"] = 44;
obj4["name"] = "Chris";
```
***Object Constructor***
```javascript
var obj6 = new Object();
obj6.name = "Ralph";
```

***Object Create***
```javascript
var obj7 = {name:"raplh"};
var objnew = Object.create(obj7);

//Access to the properties is not possible bcz it contains space
var obj8 = {name : "Ralph" , full name: "Ralph Norman" };
//Uncaught SyntaxError: Unexpected identifier
//In order to cope up with this we use array to assign value
var obj8["full name"] = "Ralph Norman";

//Fetch the keys in object
Object.keys(obj8);

//Delete properties
delete obj8.name;

//Convert object to string
var obj9 = {name : "Shaun"};
var str = JSON.stringify(obj9);

//Convert string to object
JSON.parse(str);

```
### 8. Symbol 

ES6 introduced a new primitive type for javascript : Symbols. 
Each time symbol function is called a unique symbol is returned.

```javascript
var s1 = Symbol("Hi");
var s2 = Symbol("Hi");

s1 === s2 
//false cz unique value is returned

var obj = {};
var s2 = Symbol();
obj.name = "Gram";
obj[s2] = "abc@gmail.com" //use array format to assign value , dot notation wont work
Object.keys(obj);
//only name is returned

```

## 2. typeof Operator

1. The typeof operator is used to get datatypes of its operand.
2. It always return string value.

```javascript 
typeof(typeof 1);
//"string" cz typeof 1 is a "number" which is a string

typeof !!(-1);
//"boolean" cz !!(-1) is true 

typeof function(){}
//"function" considered as firstclass object

typeof new Date();
//"object" where ever new keyword is used its an object

typeof [];
//"object"

typeof null;
//"object"

typeof NaN;
//"number"

typeof undefined;
//"undefined"
```

## 3. Type Coercion 

Type coercion is converting one datatype to another.

Coersion are of two type :-
1. Explicit - Conversion using built-in types
2. Implicit - Conversion arent obivious but done by the compiler

```javascript
//Explicit Coersion
Number(4)
//4
Number(undefined);
//NaN
Number(NaN)
//NaN
Number(null);
//0
Number("hello")
//NaN
Number(true)
//1
Number(false)
//0
Number([])
//0
Number(["44"])
//44
Number(["55"."66"])
//NaN

//Other than these everything is true in Boolean
Boolean(false);
//false
Boolean(0);
//false
Boolean(On);
//false
Boolean(null);
//false
Boolean(undefined);
//false
Boolean(NaN)
//false

//Implicit Coersion
"Hello" + "world";
//"Helloworld"
100 + "Hello"
//"100Hello" converts everthing into string
100 + null + 20 + "word"
//Either side is not string then check with Number()
//100 + Number(null)+20 + "word"
//100 + 0 + 20 + "word"
//"120word"
100+200+undefined+"word"
//"NaNword"
var x ={};
x+"hey";
//"[object Object]hey"
```

## 4. Equality Comparision

1. Abstract Equality Comparision 
Example :- 100 == "100"

2. Strict Equality Comparision
Example :- 100 === "100"

3. Object.is() :- Strict Comparision + cover all the edge cases

```javascript
100 == "100"
true
//It compare values irrespective of there datatypes
true == "true"
false

100 === "100"
false

//two scenario where === fails 

0 === -0
true
NaN === NaN
false

Object.is(0,-0);
//false
Object.is(NaN,NaN);
//true
Object.is(100,"100");
//false
```
## 5a. Arithmatic Operator

 / , + , - , * , % , ++ , -- are all arthematic operator

```javascript
//postincrement
var i = 10;
i++;
//10
i;
//11

//preincrement
var y = 10;
++y;
//11

```
## 5b. Comparison Operator

== , === , != , !== , > , < , >= , <= are all comparison operator.

```javascript
10 !== 10 
//false
10 !== "10"
//true
10 != "10"
//false

"hello" > "Hello"
//true
//Compare ascii value of the first character
h.charCodeAt()
104 
104>72
//true
```
## 5c. Logical Operator

&& , || , ! are logical operator

```javascript
var x = 10;
var y = 11;

x || y
// if x is true , it will never execute y 
// But if x is false , it will go y and execute it
//10 

var k = [] || "hey";
k;
//[]

//It checks boolean of the given operand
Boolean([])
//true , so return [] when || is used

var j = 0 || "hey";
j;
//"hey"


var o = true || "hey";
//Either both value must be true or both should be false
//true
```

## 5d. Assignment Operator

= , += , /= , %= , -= , *= are assignment operator

```javascript
var a = 10 
a+=10;
a
//20
```

## 5e. Ternary Operator

Special operatory that assign value to a variable based on the condition.
Short form of if-else

```javascript 
var name = "nik";

var isAvailable = name === "nik" ? "present" : "absent";
isAvailable
//"present"
```

## 6. Conditional Statement

1. ***if statement***
```javascript
var k = 10;
if(k)
{
    console.log("okay");
}
//okay
```

2. ***if else statement***
```javascript
var k = 0;
if(k)
{
    console.log("okay");
}
else
{
    console.log("not okay");
}
//not okay
```
3. ***if else if statement***
```javascript
var k = "A";
if(k==="A")
{
    console.log("A");
} 
else if(k==="B")
{
    console.log("B");
}
else
{
    console.log("C");
}
//A
```

4. ***switch case***
```javascript
var num = 2;
var day;
switch(num)
{
    case 0:
    day = "Monday";
    break;
    case 1:
    day = "Tuesday";
    break;
    default:
    day = "Anyday"; 
}
//Anyday 
```
## 7. var, const and let keywords

1. ***var***
var is a global scoped
There are issues associated with variable declared with var ie ***Hoisting*** 
That take all the variable to the top 

```javascript
console.log(x)
var x = 10;
//undefined
//cz it take variable declaration on the top ie 
//var x
//console.log(x) //undefined
//x = 10;
```
2. ***let***
let was introduced to resolve this hoisting issue.
let is block scoped
let can br upadated but not redeclared.

```javascript
var k=10;
if(k)
{
var s = "string";
}
console.log(s);
//string is printed cz s is global scoped

let k= 10;
if(k)
{
let s= "string";
}
console.log(s);
//Error is thrown cz s is in if block 


var k = 20;
var k = 10; // k redeclared work with var
k
//10

let o = 10;
let o = 40; // o redeclared will throw error
```

3. **const***
const resolve  hoisting issue.
const is block scoped
const cannot be upadated and redeclared except objects

```javascript
const name = "patt"
const name = "frank" //Will throw error cz redeclared

const obj = {name = "kash"};
obj.name = " karl";
//This will work cz we are updating just the properties not the reference

const obj = {} // this will throw error bcz already declared
```



## Arrays

Array is an object which can store multiple values of different types.
Array can be initialized using two ways Array literal and Array constructer.

```javascript 
//Array literals
var arr = [];
arr
//[]
var arr = [10,12,14,15];
arr
//[10,12,14,15]
var arr = [1,'a','b',5];
arr
//[1,'a','b',5]

//Array contructor
var arr1 = new Array();

arr1[0] = "Pam";
arr1
//["Pam"]

//array with particular length
var arr2 = new Array(4);

arr2.length();
//4

arr2[0]=0;
arr2[1]=1;
arr2[2]=2;
arr2[3]=3;
arr2
//[0,1,2,3]

//Directly pass the value
var arr5 = new Array(1,"a","b",5);

arr5
//[1,"a","b",5]
```

***Array methods***
1. push - Add the element at last

```javascript
var a = [1,2,4,5];
a.push(6);
//return lenght of the array 5
a
//[1,2,4,5,6]
```
2. pop - Remove element at last

```javascript
var a = [1,2,4,5];
a.pop();
//6 return the value at the end
a
//[1,2,4,5]
```

3. shift - Remove element from the front

```javascript
var a = [1,2,4,5];
a.shift();
//1
a
//[2,4,5]
```

4. unshift - Add element at front

```javascript
var a = [1,2,4,5];
a.unshift(8);
//5 length of the array
a
//[8,1,2,4,5]
```

5. splice - Add and remove element from particular index

```javascript 
var x = [1,2,4,5,6,7];
x.splice(1,2);
//Starting from 1st index delete 2 numbers
//[2,4]
x
//[1,5,6,7]

x = [1,2,4,5,6,7];
x.splice(4,0,15);
//If we have 0 as 2nd parameter that means we have nothing to remove and add 15 to 4th index
//[]
x
//[1,2,4,5,15,6,7]


























