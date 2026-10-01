# Basics


### Time Complexity

- number of operation increases when input size n increases.


```javascript
function(arr){
    console.log(arr[0]);
}
```

- When array contains 10 or 1million, we process 1 element.

Therefore:

- Time= O(1)


1 item - 1 work
10 item - 1 work
10000 item - 1 work
100000 item - 1 work




### space complexity:

- how much additional memory an algorithm need as n grows.


```
function sum(arr){
    let total=0;

    for(let i=0;i< arr.length;i++){
       console.log(arr[0]) ;
    }
}
```


1 item - 1 work
10 item - 10 work
10000 item - 10000 work
100000 item - 100000 work


So

Space = O(1)
Time=O(n)


### O(1) -- Constant

- the number of operations doesnot depends on n.

```javascript

function getFirst(arr){
    
    return arr[0];
}


```


n=1 -> 1 operations
n=10 -> 1 operations
n=1000 -> 1 operations
n=10000 -> 1 operations


Therefore:

Time: O(1)
Space:O(1)

### O(n) -- Linear

- The work grows proportionally with the input

function printArry(arr){
    for(let i=0;i< arr.lenght;i++){
        console.log(arr[i]);
    }
}


n=1 -> 1 operations
n=10 -> 10 operations
n=1000 -> 1000 operations
n=10000 -> 10000 operations


Therefore:

Time: O(n)
Space:O(n)



### Quadratic $O(n^2)$:


- Happens in nested loops

```javascript
function printPairs(arr){
    for(let i=0;i< arr.length;i++){
        for(let j=0;j< arr.length;j++){
            console.log(arr[i],arr[j]);
        }
    }
}
```


n=10 -> 100
n=100 -> 10000
n=1000 -> 1000000

### O(log n) - logarithmetic

- important for `Binary search`

Suppose we have
1 2 3 4 5 6 7 8 9


instead of checking every element, we repeatedly divided the search area

10 elements
5 elements
2/3 elements
1 elements


Time:
O(log n)

### O(n log n):

- important for `Merge sort` and `Quick sort`

arr.sort((a,b) => a- b );

- Process n element accross n levels.



## Arrays:

- stores multiple values into the ordered collection.

const arr=[1,2,3,4,5];


console.log(arr[0]);


time complexity: o(1);


### Important Array Operations:


Operations | Example | Typical complexity
---- | ----- | ----
Access | arr[2] | O(1)
Search | find a value | O(n)
Update | arr[5]=100 | O(1)
Push | add at end  | O(1)*
pop | Remove at end | O(1)
unshift | Add at beginning | O(n)
shit | remove at beginning  | O(n)
Insert Middle | splice | O(n)
Delete middle | Slice | O(n)


push() is typically O(1) amortized in JavaScript arrays.

### traversing an array:


const arr=[10,20,30,40,50];


for(i=0;i<arr.length;i++){
    console.log(arr[i]);
}



time: O(n)
space: O(1)





