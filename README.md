# Big Words Java Script



### Primitive types: 
``` javascript
 boolean,  number, undefined, symbol, string, null. 
```



### Single Thread 

![alt text](execution_context.png "Logo Title Text 1")


### Associative 

```javascript 
var a =  2, b = 3, c =4;
a = b = c;

console.log(a);

result iguals 4. 
```
[Link](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) to search precedence

### Equanlity and comparesions

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness



### JSON and Object Literals 

Object literals exemple
```javascript
var objectLiteral = {
   firstName : "Caio",
   age : 18
}
```
JSON -> JavaSript Object Notation

```json
{
 "firstName" : "Caio",
 "age" : 18
}
```

tranformome object literal to JSON 
```javascript 
console.log(JSON.stringfy(objectLiteral));
````

### Function

- Function are objects
- Function and object are passed by reference. primitive types are passed by value
- var belongs the execution context
```javascript

var teste = "global"

function print(){
    this.teste = "in method printf";
    console.log(teste);
}


print();

console.log(teste);

//out put
//in method printf
//global

```

### Immediately Invoked Functions Expressions 

```javascript
(function(name){
   console.log(name);
})();
```


### bind , call , apply

```javascript
var person = {
    firstname: 'John',
    lastname: 'Doe',
    getFullName: function() {
        
        var fullname = this.firstname + ' ' + this.lastname;
        return fullname;
        
    }
}

var logName = function(lang1, lang2) {

    console.log('Logged: ' + this.getFullName());
    console.log('Arguments: ' + lang1 + ' ' + lang2);
    console.log('-----------');
    
}

var logPersonName = logName.bind(person);
logPersonName('en','en');

logName.call(person, 'en', 'es');
logName.apply(person, ['en', 'es']);

```


### function borrowing

```javascript

var person = {
    firstname: 'John',
    lastname: 'Doe',
    getFullName: function() {
        
        var fullname = this.firstname + ' ' + this.lastname;
        return fullname;
        
    }
}

var person2 = {
    firstname: 'Jane',
    lastname: 'Doe'
}

console.log(person.getFullName.apply(person2));
```


### function constructor 


```javascript
var car = new Car()
```

- The name javascript was choised just because to atract java developers. 
- function constructors is just a normal function that is used to construct objects 
the variable 'this' points a new empty object and that object is returned from the function
automatically


### Prototype

- That variable can be only use in "function constructor" (key word new )
- You can add value to a prototy any time, and all objects you recive that object. 


```javascript
function Person(firstname, lastname) {
 
    console.log(this);
    this.firstname = firstname;
    this.lastname = lastname;
    console.log('This function is invoked.');
    
}

Person.prototype.getFullName = function() {
    return this.firstname + ' ' + this.lastname;   
}

var john = new Person('John', 'Doe');
console.log(john);

var jane = new Person('Jane', 'Doe');
console.log(jane);

Person.prototype.getFormalFullName = function() {
    return this.lastname + ', ' + this.firstname;   
}

console.log(john.getFormalFullName());
`
```
## Opertator == and ===

```javascript
var a = 1
var b = new Number(1);
a == b // true
a === b // false, it compares the type
```

# Arrays 

- Arrays are object 
```javascript
Array.prototype.myCustomFeature = 'cool!';

var arr = ['John','Jane', 'Jim' ];

// avoid it because it show the object "myCustomFeature"
for(var prop in arr){

}

//use it 
for (let index = 0; index < array.length; index++) {
    const element = array[index];
    
}

```

### Create vs New 

- "Object.create" create a object in the prototype. Ex Object.create(Pearson) =  object.prototype = new Pearson();
-  "new" Create a object with the prototype type "Object".

```javascript 
// polyfill
if (!Object.create) {
  Object.create = function (o) {
    if (arguments.length > 1) {
      throw new Error('Object.create implementation'
      + ' only accepts the first parameter.');
    }
    function F() {}
    F.prototype = o;
    return new F();
  };
}

var person = {
    firstname: 'Default',
    lastname: 'Default',
    greet: function() {
        return 'Hi ' + this.firstname;   
    }
}

var john = Object.create(person);
john.firstname = 'John';
john.lastname = 'Doe';
console.log(john);
```





### Polyfill

- code that adds a feature whitch the engine may lack


### Syntactic Sugar 

- A diferente way to type something that doesn't change how it works under the hood

one exemple is the class in ECS6 

```javascript
class Manager extends Person{
    constructor(director){
        super(director)
    }
} 
```
extends =  object.prototype;


### typeof and instanceof
```javascript
type of b // String

var e = new Pearson('Jane')
e instance of Pearson() // true, searching in the prototyes

type of null // bug returns object
```

