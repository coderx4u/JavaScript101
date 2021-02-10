# Javascript 

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
### 8. Object 

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

## 5. Comparision Operator

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
























