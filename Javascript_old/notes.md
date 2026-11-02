#


## Javascipt:

- High Level
- Dynamically typed Programming language.
- make interactive web applications.


```bash

const name="Devaraj";
console.log(`Hello ${name}`);

```

### diff between var,let and const


| Feature       | var      | let   | const |
| ------------- | -------- | ----- | ----- |
| Scope         | Function | block | block |
| Redecleration | YES      | NO    | NO    |
| Reassignment  | YES      | YES   | NO    |
| Hoisted       | YES      | YES   | YES   |


### diff between == and ===

== performs before type convertion before comparison

=== checks value and type

```bash

    5 == "5" //true
    5 === "5" // false


```


**Interview answer:**

== Compares value after coercion

=== compares value without implicit type conversion.


### Null vs undefined:

undefined:
- variable is declared but is not assigned any value.

```javascript
 let variable;
    console.log(variable); // undefined
```

null:
- intentionally make the value is null

```javascript
    let variable = null;
     console.log(variable); // null
```

### Javascript data types:

Primitive and non primitive data types

#### Primitive data Types:

```
Number 
String
Boolean
null
undefined
BigInt
Symbol

```


Example:


```
var number = 1243; //number
var name ="Deva"; //string
var isBoolean= true; //boolean
var declare; // undefined
var value=null; // null
let bigInt=123n; // Bigint
```


#### Non Primitive Data types

```
Object
Array
Functions
```


### Hoisting


- behaviour in javascript which move the variable,function , class and import declarations
-  to top of their containing scope.
- before the code executes.




```javascript
console.log(a);

var a=10;
```

**During Hoisting:**

```javascript

 var a;
 console.log(a);

 a =10;

 //output: //undefined

```


**For let and const:**

```javascript
    console.log(a);
    let a=10;
```


```output
ERROR!
/tmp/8Y1yrLZCAA/main.js:7
console.log(a);
            ^

ReferenceError: Cannot access 'a' before initialization
    at Object.<anonymous> (/tmp/8Y1yrLZCAA/main.js:7:13)
    at Module._compile (node:internal/modules/cjs/loader:1781:14)
    at Object..js (node:internal/modules/cjs/loader:1913:10)
    at Module.load (node:internal/modules/cjs/loader:1505:32)
    at Function._load (node:internal/modules/cjs/loader:1309:12)
    at wrapModuleLoad (node:internal/modules/cjs/loader:254:19)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:171:5)
    at node:internal/main/run_main_module:36:49

Node.js v22.23.2

```

- for let and const is in TDZ(Temporal Dead Zone).



### Scope
- Scope determines where a variable can be accessed.


```javascript

function test(){
    let message="Hello deva";

    console.log(message);
}

test();


console.log(message); //Error

```

Common scopes:
- block scope.
- function scope.
- Global Scope.



### What is a function:
- Resuable block of code.


```javascript

function add(a,b){
    return a+b;
}

console.log(add(10,20));
```


### function Declaration vs Function Definition

Function Declaration:

- Use the `function` keyword.
- Can be hoisted


    ```
    add();

    function add(){

    }
    // it is working fine 

    ```


```javascript
function add(a,b){
    return a+b;
}
```

Function Expression:
- Use the named function.
- variable follows var/let/const rules.


```javascript

const add= function(a,b){
    return a+b;
}

```




### 10. Arrow function:
- Shorter syntax for function.


Normal:
function(a,b){
    return a=b;
}


arrow:

const add = (a,b)=>{
    return a+b;
}

Even shorter:

const add =(a,b) => a+b;


**Note:** arrow function doesnot have their own `this`.



### 11. Callback function:

- Callback is a function passed to another function as an argument.
- Used with asynchronous operations


```javascript
function done(){
    console.log("Done");
}


function greet(name,callback){
    console.log(`Hello ` + name );

    callback();    
}



greet("Deva",done);
```

### 12. map()

- creates a new array transforming every element


```javascript

const numbers=[1,2,3,4,5];

const result=numbers.map(num=>num * 2);

console.log(result)
```

### 13. filter();

- filter creates a new array with satisfy the condition.

```javascript

const numbers=[1,2,3,4,5];

const result=numbers.filter(num => num > 2);


console.log(result);

// [3,4,5]
```


```javascript

const numbers=[1,2,3,4,5];

const result=numbers.filter(num => num + 2);


console.log(result);

```

1+2=3,
num = 1 → 1 + 2 = 3
num = 2 → 2 + 2 = 4
num = 3 → 3 + 2 = 5
num = 4 → 4 + 2 = 6
num = 5 → 5 + 2 = 7

filter() receives:

3
4
5
6
7

These are all truthy values, so every element is kept.

it give same value:
[1,2,3,4,5]

it is due to truthy values




num - 2

const result = numbers.filter(num => num - 2);

console.log(result);

1 - 2 = -1  → truthy
2 - 2 =  0  → falsy
3 - 2 =  1  → truthy
4 - 2 =  2  → truthy
5 - 2 =  3  → truthy


[1, 3, 4, 5]


filter() doesn't care that you used + or -. It cares whether the returned value is truthy or falsy.


Falsy values:

```javascript
false
0
-0
0n
""
null
undefiuned
Nan

```

Truthy Values:

```javascript
1
-1
"hello"
{}
[]

```


### 14. reduce
- reduce and array into the single element


const numbers=[1,2,3,4];


const result=numbers.reduce((sum,num)=>{
   return sum+ num;
},0);

console.log(result)

output: 10

0 in the above is start value of sum

### 15. Destructing:

- Allows to extract values from objects and array


```
const user={
    name:"Deva",
    age:10
};


const {name,age}=user;

console.log(name);
console.log(age);

```

```javascript
const numbers=[10,20,30];


const [first,second]=numbers;


console.log(first);
console.log(second);
```




### 16. spread operator:

- expand values.



Array:

```javascript

const arr1=[1,2,3];

const result=[arr1,4,5];

console.log(result); // [ [ 1, 2, 3 ], 4, 5 ]

const result=[...arr1,4,5];

console.log(result); // [  1, 2, 3 , 4, 5 ]

```


**Object:**


```javascript
const user:{
    name:"Deva",
    age:20
};


const updateUser={
    ...user,
    age:36
};

console.log(updateUser);

// output:

{name:"Deva",age:36};



```
**Important:** Age 36 overwrite the age 20. If last update user has 20 means, it is changed to 20.

```javascript

const user:{
    name:"Deva",
    age:36
};


const updateUser={
    ...user,
    age:20
};

console.log(updateUser);

// output:

{name:"Deva",age:20};

```
last one updated/overwrite the properties.


### 17. rest operator:

- collect remaining values.


```javascript


    function add(...numbers){
        return numbers.reduce((sum,num)=>{

        },0);
    }


    add(1,2,3,4,5);


    shorter syntax:

    function add(...numbers){
        return numbers.reduce((sum,num)=> sum + num,0);
    }

```


### 18. optional chaining:(?.)

- optional chaining (?.) allows you to safely access properties.


```

const user={
  name:"Deva",
  age:24,
  address:{
    city:"gobi"
  }
};

console.log(user.address.city);



```

if address is not in the array, it is gives `Error!`.



if city is not present it is gives the `undefined`



```
user?.address?.city
```

if the address doesnot have the properties it gives `undefined`.

### 19. Nullish Coalescing(??):

?? provides a default value when the left side value is null or undefined


```javascript

const name = null ?? "Guest";

```


const count = 0 || 10;

const count = 0 ?? 10;


### 20. closure:(`important`)

- Closure happens when a inner function remembers variables the outer variable of the outer function.
- even after the outer function has finished executing.


```javascript

function counter(){
    count=0;

    console.log("count-inside",count); // count-inside 0

    return function(){
        count++;
        return count;
    }
}


const increment=counter();

console.log(increment()); //1
console.log(increment()); //2
console.log(increment()); //3

```

### 21. What is `this`?


`this` acts as a reference to the object.


```javascript
const person={
  name:'Deva',

  greet(){
    console.log(this.name);
  }
};


person.greet(); // here this refers to person



class Person{
  constructor(name){
    this.name=name;
  }
  
}


const user=new Person("Devaraj"); // here this refers to user

```


### 22. call(),apply() and bind();

- used to control `this` value when calling functions.

```javascript
const user={
    name: "Deva"
};


function greet(age){
    console.log(this.name,age);
}



greet.call(user,25); // Deva 25
greet.apply(user,[25]); // Deva 25
const newFunction = greet.bind(user,25);


newFunction(); // Deva 25


```

call -> calls immediately, arguments is value.
apply -> calls immediately, arguments is array.
bind -> returns a new function (It is resued).


### 23. Promise:

- Perform the asynchronous operation.

```javascript
const promise= new Promise((resolve,reject)=>{
  const status =false;

  if(status){
    resolve("success");
  }else{
    reject("Error");
  };
});


promise
.then(result => console.log(result))
.catch(error => console.log(error));

```



### 24. async/await

- cleaner way to work with promises.

```javascript

async function getUser(){
   const resonse= await fetch('/users');

  const data= await resonse.json();

  console.log(data);
}



getUser();


// Async/await use the try/catch handling

async function getUser(){
  try{
    const response=await fetch('/users');
    const data=response.json();
    return data;
    
  }catch(error){
    console.error(error);
  }
}


```

### 25. promise.all()

- runs multiple promises concurrently and waits for all exeuction.
- if one rejects, returned promise is rejected immediately.



```javascript
try{
 
  const results = await Promise.all([
    Promise.resolve("Success"),
    Promise.resolve("Success")
  ]);

  console.log("results",results);
}catch(error){
  console.error("error",error);
}


//results [ 'Success', 'Success' ]



try{
 
  const results = await Promise.all([
    Promise.resolve("Success"),
    Promise.reject("error")
  ]);

  console.log("results",results);
}catch(error){

  console.error("error",error);

}

//error error


```



#### Promise.allSettled():

- waits for all promise to finish, whether it is fullfilled or rejected.

```javascript
try{
    const results=await Promise.allSettled([
      Promise.resolve("Success"),
      Promise.reject("Error"),
      Promise.resolve("Success")
    ]);

  console.log(results);
}
catch(error){
  console.log("error",error);
}



````


***Result:***

```bash
[
    {status:'fulfilled',value:'Success'},
    {status:'rejected',value:'Error'}
    {status:'fulfilled',value:'Success'}
]

```


#### promise.race();


- returns the result of `first promise either - whether it fulfills or reject`

```javascript

const first = new Promise(reject=>
  setTimeout(() => 
    reject("First"),200)
  );

const second = new Promise(resolve => setTimeout(()=>
  resolve("Second"),500)
);

const results=await Promise.race([first,second]);

console.log(results)


```

**output:**
First



```javascript

const first = new Promise(reject=>
  setTimeout(() => 
    reject("First"),200)
  );

const second = new Promise(resolve => setTimeout(()=>
  resolve("Second"),100)
);

const results=await Promise.race([first,second]);

console.log(results)


```

**output:**
Second

#### promise.any();


- returns the result of `first promise to fulfill`. if All rejected, it is rejected.

```javascript
const result=await Promise.any([
  Promise.resolve("Success1"),
  Promise.reject("Error"),
  Promise.resolve("Success")
]);


console.log(result);

**output:**
Success1


```

first resolve is `Success1`


```javascript

const result=await Promise.any([
  Promise.reject("Success1"),
  Promise.reject("Error"),
  Promise.resolve("Success2")
]);


console.log(result);

output:
Success2

```

here first resolve is `Success2`

```javascript

const result=await Promise.any([
  Promise.reject("Success2"),
  Promise.reject("Error"),
  Promise.reject("Success3")
]);


console.log(result);

output:
[AggregateError: All promises were rejected] {
  [errors]: [ 'Success2', 'Error', 'Success3' ]
}

```

If all reject, it is showning aggregateError.



promise.all - all fullfills.

promise.allsettled - executes all with rejects too

promise.race() - first one either rejects or approve

promise.any() - first one (either rejects or approve).


### 26. Event Loop:
 
 - single threaded.
 - handle the aysnchronous operation using the event loop


order:
1.synchronous.
2.Promise callback.
3. Timer callback.


```javascript


console.log('A');


setTimeout(() =>{
  console.log('B')
},200);

setTimeout(() =>{
  console.log('D')
},100);


Promise.resolve().then(()=>
    console.log("F")
  );


Promise.resolve().then(()=>{
  console.log("promise A");

  Promise.resolve().then(()=>{
    console.log("promise B");
  });
});

Promise.resolve().then(()=>{
    console.log("promise D");
  });

console.log('C');

```


output:

```bash
A
C
F
promise A
promise D
promise B
D
B

```


### 29. Debouncing

- delays execution until the user stops execution


```bash
j
ja
java
javas
javasc
javascr
javascri
javascrip
javascript

```
- waits until the user stops typing.

```javascript

function debounce(callback,delay){
  let timer;

  return function(..args){
    clearTimeout(timer);

    timer=setTimeout(()=>{
      callback(..args);
    },delay)
  }
}

```


```javascript
function searchApi(query){
  console.log("Api called with",query);
}

const debouncedSearch=debounce(searchApi,500);

debouncedSearch("h");
debouncedSearch("he");
debouncedSearch("hel");
debouncedSearch("hell");
debouncedSearch("hello");


```

output:

Api called with hello



### 30.  Throttling

 - limit the executes of function on specific time.


```javascript

function throttle(callback) {
  let lastTimer = 0;

  return function () {
    const now = Date.now();

    if (now - lastTimer >= 200) {
      callback();
      lastTimer = now;
    }
  };
}

function sayHello() {
  console.log("Button is clicked!");
}

const data = throttle(sayHello);

data();
data();
data();
data();
data();
data();
data();
data();
data();


```

**output:**

Button is clicked!

