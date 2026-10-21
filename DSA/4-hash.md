# Hash Map and Hash Set:



### 1. Hash Map

- Stores data as key -> Value pairs

```javascript

const map=new Map();

map.set("name","Deva");
map.set("age",29);



console.log(map.get("name"));
console.log(map.get("age"));


```

### 2. Important Map Methods:


set()
get()
has()
delete()
size()
clear()


set():
- Add/update a value
map.set("name","Deva");
get()
- get the value
map.get(name);
has()
- check the key exists
map.has("name");
delete()
- delete the key

map.delete("name");

size()
- get number of entries
map.size();
clear()
- Remove ecerything
map.clear();


```javacript
const map=new Map();

map.set("name","Deva");
map.set("age",29);



console.log(map.get("name"));
console.log(map.get("age"));

console.log(map.has("name"));
console.log(map.delete("name"));

console.log(map.get("name"));


console.log(map.size);

console.log(map.clear());

console.log(map.size);



```
output:

```
Deva
29
true
true
undefined
1
undefined
0


```


### 3. Map Complexity:

set() -> O(1)
get() -> O(1)
has() -> o(1)
delete() -> O(1)


### 4. Hash Set

- Stores Unique values.


const set= new Set();

set.add(10);
set.add(20);
set.add(10);

console.log(set);


**Result:**
```
Set(2) { 10, 20 }
```


### 5. Important set Methods.

add()
has()
delete()
size()
clear()



```javascript
const set= new Set();

set.add(10);
set.add(20);
set.add(10);

console.log(set);
console.log(set.has(10));
console.log(set.delete(10));

console.log(set);
console.log(set.size);
console.log(set.clear());
console.log(set)

```

output:
```
Set(2) { 10, 20 }
true
true
Set(1) { 20 }
1
undefined
Set(0) {}

```

### 6. Set Complexity

add() -> O(1) average
has() -> O(1) average
delete -> O(1) average


### 7. Map vs Set


-   |    Map     |    Set
-- | -- | --
Stores  | Key + value |  Values
Duplicate | key are unique | values are unique
Main use | lookup/frequency | Uniqueness/existence


### 8.  frequency Counter:



```javascript

function frequency(arr){
    const map=new Map();
    for(const item of arr){
      map.set(item,(map.get(item) || 0) + 1)
    }
  return map;
}
let result=frequency([10, 20, 10, 30, 20, 10]);


for(const [number,count] of result){
  console.log(`${number} appease ${count} times` )
}

```

Output:

```bash
10 appease 3 times
20 appease 2 times
30 appease 1 times

```

**Complexity:**

Time-O(n)
Space - 0(n)


### 9. Find Duplicates using set

```javascript

const arr = [1, 2, 3, 1, 4, 2];

const result=duplicate(arr);

if(result){
  console.log("Array has duplicates");
}else{
    console.log("Array does not has duplicates");

}


function duplicate(arr){
  const set=new Set();
  for (const item of arr){
    if(set.has(item)){
      return true;
    }
    set.add(item);
    
  }
  return false;
}


```

Output:
Array has duplicates

Complexity:
Time-O(n)
Space - O(n)

### 10. Remove Duplicates.

```javascript
const arr = [1, 2, 2, 3, 4, 4];

const result=[...new Set(arr)];

console.log(result);

```
### 11. Two Sum (very Important):

```javascript


const arr=[2,5,11,15];
const total=7;

const result=calculateTotal(arr,total);

console.log(`${arr[result[0]]} and ${arr[result[1]]} is ${total}` )

function calculateTotal(arr,total){
  const map=new Map();
  for(let i=0;i<arr.length;i++){
    let complement =total - arr[i];

    if(map.has(complement)){
      return [map.get(complement),i] // value,index
    }
  
    map.set(arr[i],i); // value,index
  }

  return [];
}

```
**Output:**
2 and 5 is 7

this is very important:
```bash
let complement =total - arr[i];
```
