### Q1. Reverse a string

let str="Staples";



function reverseString(){
   let result='';
        for(let i=str.length-1;i >= 0 ; i--){
            result +=str[i];
        }

        return result;
}



console.log(reverseString(str));

### Q2. Find duplicate elements in an array

let str=[1, 2, 3, 2, 4, 1];


function findDUplicates(str){
    let seen=new Set();
    let duplicate=new Set();
    for(let num of str){
        if(seen.has(num)){
            duplicate.add(num);
        }else{
            seen.add(num)
        }
    }
    return [...duplicate]
}

console.log(findDUplicates(str));


### Remove duplicate elements from an array


Using Set:
const str=[1, 2, 2, 3, 3];


function removeDuplicates(str){
    return [...new Set(str)];
}


console.log(removeDuplicates(str));  



using for loop:


const str=[1, 2, 2, 3, 3];


function removeDuplicates(str){
    let result=[];

    for(let num of str){
        if(!result.includes(num)){
            result.push(num)
        }
    }

    return result;
}


console.log(removeDuplicates(str));



### Find character frequency in a string

const str="javascript";


function charfrequency(str){
    let map=new Map();
    for(let char of str){
        map.set(char,(map.has(char) || 0) + 1);
    }

    return map;
}

console.log(charfrequency(str));

Map(9) {
  'j' => 1,
  'a' => 2,
  'v' => 1,
  's' => 1,
  'c' => 1,
  'r' => 1,
  'i' => 1,
  'p' => 1,
  't' => 1
}

### Implement debounce

```javascript
function debounce(callback,delay){
    let timer='';

    return function(...args){
        clearTimeout(timer);
         timer=setTimeout(()=>{
                callback(...args)
        },delay);
    }
}


function searchValue(str){
    console.log(str);
}

const debounceSearch=debounce(searchValue,200);

debounceSearch("javascript");

```





```javascript
const str="aabbccddea";


const result=checkPalindromeArrange(str);
console.log(result);


function checkPalindromeArrange(str){

    const map=new Map();
    for(let char of str){
        map.set(char,(map.get(char) || 0) + 1)
    }
    let oddValue=0;
    let left='';
    let middle='';
    for(let [char,count] of map){

        if(count % 2 !==0){
            oddValue++;
            middle=char
        }

        left += char.repeat(Math.floor(count /2 ));

    }

    let right=left.split("").reverse().join("");

    if(oddValue > 1){
        console.log("Given string is not able to make the palindrome");
        return false;
    }
    return left + middle + right;

}


```


### Plalindrome:

```javascript
const str='madam';


const result=checkPalindrome(str);

if(result){
    console.log("Given string is palindrome!");
}else{
    console.log("Given string is not palindrome!");
}

function checkPalindrome(str){
    const reverse=str.split("").reverse().join("");
    if(reverse===str){
        return true;
    }
    return false;

}

```
### Using Two Pointers:

```javascript
const result=checkPalindrome(str);

if(result){
    console.log("Given string is palindrome!");
}else{
    console.log("Given string is not palindrome!");
}

function checkPalindrome(str){
    let left=0;
    let right=str.length -1;


    while(left < right){

        if(str[left] != str[right]){
            return false;
        }

        left++;
        right--;
    }
    return true;


}
```


**Regex:**

console.log(/[a-z]/i.test("a")); // Alpabets

console.log(/[0-9]/.test("9")); // Numbers

console.log(/[^a-z0-9]/.test("%")); //Special characters

console.log(/[A-Z/]/.test("Z")); // Upper characters

console.log(/[a-z]/.test("a")); // Lower characters




