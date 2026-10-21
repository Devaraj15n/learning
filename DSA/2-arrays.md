
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
space: O(1) -  Single variable(i)



const arr=[10,20,30,40,50];

result=[];
for(i=0;i<arr.length;i++){
    result.push(arr[i]);
}


time: O(n)
space: O(n) -  multiple values in single value - So memory increase(result).


### Find Maximum:


```javascript
function max(arr){
  let max_var=arr[0];

  for(i=1;i< arr.length;i++){
    if(arr[i] > max_var){
      max_var=arr[i];
    }
  }

  return max_var;

}


console.log(max([30,50,10,5,25]));
```

Time: 0(n)
Space : 0(1)


### reverse an Array:

Simple approach:


```javascript   

    function reverseArray(arr){
        arr.reverse();
    }
```

`Need to analysis this`:

```javascript


function reverseArray(arr){
  let left=0;
  let right=arr.length - 1;

  while(left < right){
    [arr[left],arr[right]]=[arr[right],arr[left]];
    left++;
    right--;
  }

  return arr;
}


console.log(reverseArray([1,2,3,4,5,6]))

```

complexity:
Time:O(n)
Space:O(1);


The loop runs approximately n / 2 times.

while(left < right){
    [arr[left],arr[right]]=[arr[right],arr[left]];
    left++;
    right--;
  }


Technically:
n/2

But in Big-O We ingore constants

So O(n/2) -> O(n)


**Why Space O(1):**

let left=0;
let right=arr.length - 1;

    - two variables
    - How many loops executed, you didn't create the new variables.



# Interview questions to practice.
Find maximum element
Find minimum element
Find sum of array
Reverse an array
Find second largest
Check if array is sorted
Remove duplicates
Move all zeroes to the end