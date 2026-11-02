#

### two pointers:

- is a technic where we use two indexes moves through an array to solve problem efficiently.

instead of using nested loops

O(n2)


solve this in O(n);

```javascript
left=0;
right=arr.length-1;
```



### Basic Pattern:

```javascript

left=0;
right=arr.length-1;

while(left < right)
{
    left++;
    right--;
}
```


### example -> Reverse an array:

```javascript
arr=[1, 2, 3, 9, 5];


const result=arrayReverse(arr);

console.log(arr);

function arrayReverse(arr){
  left=0;
  right=arr.length-1;

  while(left< right){

    [arr[left],arr[right]]=[arr[right],arr[left]];
    
    left++;
    right--;
  }

  return arr;
}

```
output:
[5,4,3,2,1]


Complexity:

O(n)
O(1)


### palindrome:



```javascript

onst str="madam";

const result=checkPalindrome(str);

if(result)
{
  console.log("Given string is palindrome")
}else{
    console.log("Given string is not palindrome")

}

function checkPalindrome(str){
  left=0;
  right=str.length-1;

  console.log(right);
  while(left < right){
    // if()
    if(str[left] != str[right]){
      return false;
    }
    
    left++;
    right--;
  }

  return true;
}

```


Complexity:
O(n)
O(1)


### Two sum - Sorted array

Note: For unsorted array ,map functionality is used.


```javascript


nums = [1, 2, 3, 4, 6]
target = 7

// const result=checkTotal(nums,target);
const result=checkTotal(nums,target);


console.log(nums[result[0]],nums[result[1]]);

function checkTotal(nums,target){
    left=0;

   right=nums.length-1;

  while(left<right){
    sum=nums[left] + nums[right];


    if(sum===target){
      return [left,right];
    }

    if(sum < target){ // if the sum is less than target then move one postion to right
      left++;
    }else{  // if the sum is greater than target then move one postion to left
      right--;
    }
  }
  return null;
}
```

output:

1 6


Complexity:

O(n)
O(1)


Important: Middle value is skipped due to it is already matched one left and right combination




### Important Rule:


Pattern 1 -> Opposite directions

left ->
<- right 

Pattern 2 -> Same Direction:


left ->
right ->


### Move zeros:


```javascript


const arr=[0, 1, 0, 3, 12];


const result=moveArray(arr);

console.log(result);

function moveArray(arr){
// console.log(arr);
  let left=0;

  for(let right=0;right < arr.length;right++){
    if(arr[right] !== 0){
      // console.log('if',arr[right]);
      [arr[left],arr[right]]=[arr[right],arr[left]];
      left++;
    }
  }

  return arr;
}

```

output:

[ 1, 3, 12, 0, 0 ]


Note:
if not zero, it is changed the position from left to right of zero and right to left of non zero.


Complexity:
Time:  O(n)
Space: O(1)


### remove Duplicates from sorted array:


```javascript

const arr=[1, 1, 2, 2, 3];

const result=removeDuplicates(arr);

console.log(result);


function removeDuplicates(arr){
  let slow=0;

  for(let fast=1; fast < arr.length;fast++){

    if(arr[fast] !== arr[slow]){
      
      slow++;
      arr[slow]=arr[fast];
    }
  }

  // return slow+1;// it returns the unique array values. // 3
  return arr.slice(0,slow+1); // it returns the unique array. // [ 1, 2, 3 ]
}

```

output:
[ 1, 2, 3 ]



### Container With Most Water
This is an important interview problem.
[1, 8, 6, 2, 5, 4, 8, 3, 7]
 ↑                       ↑
 L                       R

You calculate the area between the two pointers and move the pointer with the smaller height.

This is a classic example where understanding why the pointer moves is more important than memorizing code.