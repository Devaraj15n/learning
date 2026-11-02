# Typescript Learning

### What is typescript

- Typescript is programming lanuguage
- Developed by Microsoft
- that adds `static typing` in javascript

### Program

Javascript:

```javascript

function add(a,b){
    return a + b;
}

console.log(add(10,"TEST"))

```

Typescript:

```typescript

function add(a:number,b:String){
    return a + b;
}

console.log(add(10,"test"));

```

### Datatypes:

```bash
Number:

let number:number=10;

String:

let a:String="TEST";

Boolean:

let isArray:boolean=true;


Array:

let array:number[]=[1,2,3];

let array1:Array<String>=["a","b","c"];


Tuple:

Fixed length with specify types


let tuple:[number,String]=[10,"Deva"];

console.log(tuple);

Enum:

enum Status {
    Approved,
    Rejected,
    Pending
};

let currentStatus:Status=Status.Pending;
console.log(currentStatus);

any:

Disable the type checking

let data:any="TEST"
data=10;
data="Deva";

console.log(data);

unknown:

Safer alternative to any

let value:unknown="String";


if(typeof(value)=='string'){
    console.log(value.toUpperCase());
}
```




### 3. Type Interface

let city="chennai";

let number=10;

Dont need to specify the type manually.

### 4. Functions

Parameter and Return types:


```bash

function greet(name:string,title:string):string{
    return `Hello ${name}`;
}

```

Optional Parameters:

```bash
function greet(name:string,title?:string){
    return title ? `${title} ${name}` : name;
}

```

Default Parameters:

```bash

function greet(name:string,title:string='MR.'){
    return ${title} ${name};
}

```

### 5.Objects


```bash
let employees={
    name:string;
    age:number;
}={
    name:"Deva".
    age:10
};

```

### 6. Type Aliases

```bash
type Employee = {
    name:string;
    age:number;
    email:string;
}

const emp:Employee = {
    name:"Deva",
    age:10,
    email:"devaraj7city@gmail.com"
};

```

### 7. Interface:

```typescript

interface User={
    id:number;
    name:string;
    email:string;
};

const user:User={
    id:1,
    name:"Deva",
    email:"Devaraj7city@gmail.com"
};



```

#### Interface Extension:

```typescript
interface Employee extends User{
    department:string
}

```

### 8. Union Types

```typescript
let id: string | number;

id=10;
id="Deva";

```


### 9. Union Types with Status


```typescript

type claimStatus= "submitted" | "approved" | "denied";


let status: claimStatus;

status="submitted";
status="approved";
status="denied";

# error

status="pending";

```


### Optional Properties
? this property is optional

```typescript

inteface User={
    id:number,
    name: string,
    email?: string
}

const user: User={
    id: 1,
    name: "Deva"
}

```



### Generics

```typescript

function getData<T>(data:<T>): T{
    return data;
}

const result = getData<string>("Deva");

const numberResult=getData<number>(100);

```

