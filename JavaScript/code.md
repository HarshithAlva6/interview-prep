* Brendan Eich in 1995 - ECMA standards, called ECMAScript

* ECMAScript 5 (ES5) added new features to the Just-In-Time JavaScript language and modified some of the existing ones. To keep the old code working, most such modifications are off by default. You need to explicitly enable them with a special directive: **use strict**.
* JavaScript is *Object-oriented language* built around prototype model, from which properties are inherited by objects.
In classical OOP languages, classes inherit data from other classes. In prototype-based languages, objects inherit data from objects, i.e., an object has access to all the properties of its prototype by means of inheritance.
This is because every object in JavaScript has an internal [[Prototype]] attribute which contains a reference to its prototype. b = Object.create(a)
**Prototype Chain:** A list of prototypes whose first item is the prototype of o, and any subsequent item is the prototype of the previous item, and the last item is simply null.
* Properties defined on an object shadow properties available on its prototype. This is formally referred to as *property shadowing*. 
* When we read a property from object, and it’s missing, JavaScript automatically takes it from the prototype. In programming, this is called *prototypal inheritance*. This is assigned using ___proto___
* **Variables:** _boxes_ for data, where if value is changed, data replaced. camelCase and case-sensitive, $ and _ can also be variable names. var, let, const
* **Data Types:** number, NaN, Infinity, BigInt, string ["",'',`${}`], boolean, null, undefined, symbol(NO CHAR) are primitive data type, unlike Objects(special)
* **Operator:** typeof value
* **Interaction:** alert, prompt(input), confirm(question)
* **Type Conversions:** String, Number(automatic in mathematical expressions), Boolean("0"/" "/1 is true)
* **Operators:** % is remainder, || (OR), && (AND), ! (NOT), ?? (Null) Logical Operators
alert(2 + 2 + '1' ); // "41" and not "221"
alert('1' + 2 + 2); // "122" and not "14"
alert( 6 - '2' ); // 4, converts '2' to a number
Unary: + converts values into number. Eg: let apples = "3"; alert(+apples); // 3
Chained assignment from right to left(a=b=c=5). Increment/Decrement(++/--)
* **Comparison:** Strings in lexographiccal order. If different types, conversion of value to numbers.
* **Statements:** If-else, Conditional(?), while, for, break exits loop continue exits current iteration of loop, switch-case
* **Functions:** Declaration has arguments as parameters, Global, Outer, Local Variables. Function expression is function assigned to variable. Can also be created using arrow functions.
CallBack functions -  Pass a function (as parameter) and expect it to be “called back” later if necessary (based on conditions?)

* **Objects:** File cabinet analogy. use Object(). Dot property to access values. Square brackets for multiword properties. key types converted to strings. Also use _in_ operator. While variables create COPY, Objects create COPY of reference.
To create copy, have to do for each property onto new Object. 
Object.assign(dest, src) to move properties
Therefore: let clone = Object.assign({}, user)
For nested Objects: let clone = structuredClone(user) 
Functions that are properties of an object are called methods. If this function wants to access another property, we use **this** on RHS.
* **Garbage Collection:** Reachability - Root values and values that are reference away. Garbage Collector is background process which runs automatically to remove Objects (when reference is overwritten) or delete Object. 
Mark-and-sweep: roots are marked,then its references are marked. All objects not marked are sweeped/removed.
* **Constructors:** A function preceded by _new_ is assigned to Object.
Use **this** on LHS to ensure the Object has this property.

* **Hoisting:** JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution
* **Promise:** Special JavaScript object that links the “producing code” and the “consuming code” together.
* **DOM:** Host environment provides objects and functions in addition to JS. HTML backbone is tags -> objects. 
document.body is object representing <body> tag

**Built-in objects -** Number, Math, Date, String, Error, Function, Boolean
**Data Type -** Number, BigInt, String, Boolean, Null, Undefined and Symbol
**JavaScript Object Notation (JSON)** is a standard text-based format for representing structured data based on JavaScript object syntax. Converting between objects and text using JSON.parse() and JSON.stringify()
