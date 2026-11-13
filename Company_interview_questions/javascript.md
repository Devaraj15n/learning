## Staplets:(10-11-2026)



#### find non Duplicate Array count:

```javascript
const str=[1,2,3,4,1,2,5,6];

const result=findNonDuplicateArray(str);

console.log(result);

function findNonDuplicateArray(str){
    let result=0;
    
    let map=new Map();
    for(let num of str){
        map.set(num,(map.get(num) || 0) +1);
    }

    for(let [num,count] of map){ // this is very important

        if(count <= 1){
            result++;
        }
    }

    return result;

}

```



## Platform Science technologies India private limited (12-11-2026):

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




### Loop the value without touching the special characters:


```javascript

// console.log(/[a-z]/i.test("a")); // Alpabets
// console.log(/[0-9]/.test("9")); // Numbers
// console.log(/[^a-z0-9]/.test("%")); //Special characters
// console.log(/[A-Z/]/.test("Z")); // Upper characters
// console.log(/[a-z]/.test("a")); // Lower characters


const str="@D#e$v%a!r^a&";

const result=loopCharacter(str);

console.log(result);


function loopCharacter(str){

    let chars=str.split("");
    let letters=[];
    for(let char of chars){
        if(/[a-z]/i.test(char)){
            letters.push(char);
        }
    }

    letters.sort((a,b)=>a.localeCompare(b)); // sort the characters

    let index=0;
    for(let i =0;i< chars.length;i++){
        if(/[a-z]/i.test(chars[i])){
            console.log(chars[i]);
            chars[i]=letters[index++];
        }
    }

    return chars.join("");

}

```