# 🚀 LeetCode JavaScript Solutions & Coding Challenges

This repo contains my **LeetCode solutions** and **JavaScript coding snippets**.  
It is designed to help developers **learn problem-solving** and **prepare for coding interviews**.

## 📂 Categories
- Arrays (Two Sum, Maximum Subarray, Rotate Array...)
- Strings (Valid Palindrome, Anagram, Substring...)
- Linked List (Reverse LL, Detect Cycle...)
- Dynamic Programming (Climbing Stairs, Coin Change...)
- Other coding challenges from LeetCode & interviews

## 🔥 Why this repo?
- ✅ Copy-paste friendly **JavaScript snippets**  
- ✅ Structured by **topic & difficulty**  
- ✅ Beginner-friendly + Interview-ready  

## 📌 1. Example Problem: Two Sum
```javascript
// Problem: Given an array of numbers, return indices of the two numbers that add up to target.

function twoSum(nums, target) {
  const map = new Map();
  for (let i = 0; i < nums.length; i++) {
    let diff = target - nums[i];
    if (map.has(diff)) return [map.get(diff), i];
    map.set(nums[i], i);
  }
}
console.log(twoSum([2,7,11,15], 9)); // [0,1]

```
## 📌 2. Rearrange Digits to Form Largest Number
```javascript
// 👉 Rearrange digits of n to form the largest possible number.

Input: n = 34091
Output: 94310

function makeLargestNumber(n){
    let digits = []
    let result = 0
    
    while(n > 0){
        digits.push(n % 10)
        n = Math.floor(n / 10)
    }
    digits.sort((a, b) => b -a)
    
    for(let d of digits){
        result = result * 10 + d
    }
    return result
    
}
console.log(makeLargestNumber(n))
```
## 📌 3. Count Unique Pairs with Given Difference
```javascript
// 👉 function to Count Unique Pairs with Given Difference

Input: nums = [1, 5, 3, 4, 2], k = 2
Output: { pairs: [ [ 1, 3 ], [ 3, 5 ], [ 2, 4 ] ], count: 3 }

function getPairs(nums, k){
    let count =0
    let pairs = []
    
    let newSet = new Set(nums)
    for(let num of nums){
        if(newSet.has(num+k)){
            pairs.push([num, num+k])
            count++
        }
    }
    return{pairs, count}
}

console.log(getPairs(nums, k))
```
## 📌 4. Replace Every Vowel with Next Alphabet
```javascript
// 👉 function to Replace Every Vowel with Next Alphabet

let str = "hello world"
Expected Output: "hfllp wprld"
Replace vowels: a→b, e→f, i→j, o→p, u→v.

function replaceEveryVowelwithNextAlphabet(str){
    let vowels = "aeiouAEIOU"  
    let result = ""
    
    for(let char of str){  
        if(vowels.includes(char)){  
            result += String.fromCharCode(char.charCodeAt(0)+ 1)
        }else{
            result += char
        }
    }
    return result
}

console.log(replaceEveryVowelwithNextAlphabet(str))
```
## 📌 5. Consecutive Number Sum
```javascript
// 👉 Problem: Given an array of integers, find the longest consecutive increasing subsequence sum

let arr = [3, 2, 1, 2, 3, 4, 1]
output: 10  // 1+2+3+4

function sumeOfConsecutiveArr(arr){
    let sortedArr = [...new Set(arr)].sort((a, b)=> a -b)
    let longestArr = []
    let currentArr = [sortedArr[0]]
    
    for(let i=1; i < sortedArr.length; i++){
        if(sortedArr[i] - sortedArr[i -1] ===1){
            currentArr.push(sortedArr[i])
        }else{
            if(currentArr.length > longestArr.length){
                longestArr = currentArr
            }
            currentArr = sortedArr[i]
        }
    }
    
    if(currentArr.length > longestArr.length){
        longestArr = currentArr
    }
    return longestArr.reduce((acc, sum) => acc += sum, 0)
}

console.log(sumeOfConsecutiveArr(arr))

```
## 📌 6. Mirror Words

```javascript
// 👉 Problem: Given a string, return true if every word in the string is a palindrome when reversed.

let str = "madam racecar noon";
output: true

function areAllWordsPalindrome(sentence) {
    return sentence.split(" ").every(
        word => word === word.split("").reverse().join("")
    );
}

console.log(areAllWordsPalindrome(str)); 

```
## 📌 7. Reverse an Array (in-place)
```javascript

let arr = [1, 2, 3, 4, 5]
// Output: [5, 4, 3, 2, 1]


function reverseArr(arr){
    let right = arr.length -1
    let left = 0
    while(left < right){
        [arr[left], arr[right]] = [arr[right], arr[left]]
        left++
        right--
    }
    return arr
}
console.log(reverseArr(arr))
```


## 📌 8. Remove Duplicates (in-place)
```javascript
let arr = [1,2,2,3,4,4,5]
// output [1, 2, 3, 4, 5]  

//👉 In-place work only when array is sorted

function removeDuplicate(arr){
    let slow =0 // track unique arr
    for(let fast =1; fast < arr.length; fast++){
        if(arr[fast] !== arr[slow]){
            slow++
            arr[slow] = arr[fast]
        }
    }
    return arr.slice(0, slow+1) 
}

console.log(removeDuplicate(arr))
```

## 📌 9. Flatten Nested Array
```javascript
let arr = [1, [2, 3], [4, [5, 6]]]
// Output: [1, 2, 3, 4, 5, 6]

//👉 function to flatten nested array

function flattenArr(arr){
    return arr.reduce((acc, item) =>{
        if(Array.isArray(item)){
            acc.push(...flattenArr(item))
        }else{
            acc.push(item)
        }
        return acc
    }, [])
}
console.log(flattenArr(arr))
```

## 📌 10. Group Elements by Type
```javascript

let arr = [1, "a", 2, "b", 3]
// Output: { numbers: [1, 2, 3], strings: ["a", "b"] }

function groupElement(arr){
    return arr.reduce((acc, item)=>{
        if(typeof item === "number"){
            acc.numbers.push(item)
        }else{
            acc.strings.push(item)
        }
        return acc
        
    }, {numbers:[], strings:[]})
}
console.log(groupElement(arr))
```
## 📌 11. Intersection of Arrays (Two Pointer)
``` javascript
let obj ={ array1: [1, 2, 3, 4], array2: [3, 4, 5, 6] }
// Output: [3, 4]

function interSectionArr(obj){
    const {array1:arr1, array2:arr2} = obj
    
    let sortedArr1 = arr1.sort((a, b) => a - b)
    let sortedArr2 = arr2.sort((a, b) => a - b)
    
    let i =0
    let j = 0
    
    let result = []
    
    while( i < sortedArr1.length && j < sortedArr2.length){
         let isSame = sortedArr1[i] === sortedArr2[j]
         if(isSame){
             result.push(sortedArr1[i])
              i++
              j++
         }else if(sortedArr1[i] < sortedArr2[j]){
             i++
         }else{
             j++
         }
    }
    return result
}
console.log(interSectionArr(obj))
```
## 📌 12. Chunking an Array
```javascript
let obj = { array: [1, 2, 3, 4, 5, 6, 7], size: 3 }
// Output: [[1, 2, 3], [4, 5, 6], [7]]


function chunkArr(obj){
    let {array, size} = obj
    let i = 0
    let result = []
    
    while(i < array.length){
        let subArr = array.slice(i, i+size)
        result.push(subArr)
        i+=size
    }
    return result
}
console.log(chunkArr(obj))
```
## 📌 13. Find Pairs with Sum (Two Pointer)
```javascript
let obj= { array: [2, 4, 5, 3, 1, 6], targetSum: 7 }
// Output: [[2, 5], [4, 3], [1, 6]]


function findSumPair(obj){
    const {array, targetSum} = obj
    let sortedArr = array.sort((a, b)=> a -b) 
    
    let left = 0
    let right = sortedArr.length -1
    let result = []
    
    while(left < right){
        let currentSum = sortedArr[left] + sortedArr[right]
        if(currentSum === targetSum){
            result.push([sortedArr[left], sortedArr[right]])
            left++
            right--
        }else if(currentSum < targetSum){
            left++
        }else{
            right--
        }
    }
    return result
}
console.log(findSumPair(obj))
```
## 📌 14. Generate Range of Numbers (Without using loop)
```javascript
let obj = { start: 5, end: 10 }
// Output: [5, 6, 7, 8, 9, 10]

function generateRange(obj){
    const {start, end} = obj
    let size = end - start +1
    return Array.from({length:size}, (_, i)=> start+i)
}
console.log(generateRange(obj))
```

## 📌 15. Convert to Camel Case
```javascript
let str = "hello_world_example"
// Output: "helloWorldExample"


function convertIntoCamelCase(str){
    let result = []
    let makeUpper = false
    
    for(let char of str){
        if(char === "_"){
            makeUpper = true
            continue
        }
        if(makeUpper){
            result.push(char.toUpperCase())
            makeUpper = false
        }else{
            result.push(char)
        }
    }
    return result.join("")
}
console.log(convertIntoCamelCase(str))
```
## 📌 15. Convert into snake case
```javascript
let str = "helloWorldExample"
// Output: "hello_world_example"


function convertIntoSnakeCase(str){
    return str.split("").reduce((acc, char)=>{
        if(char === char.toUpperCase()){
            acc += "_" + char
        }else{
            acc += char
        }
        return acc
    }, "")
}

console.log(convertIntoSnakeCase(str))
```
## 📌 16. Count Character Occurrences
```javascript
let obj = { string: "hello", char: "l" }
// Output: 2

function charCount(obj){
    const {string, char} = obj
    return string.split(char).length - 1
}
console.log(charCount(obj))
```
## 📌 17. Trim Whitespace
```javascript
let str = "  hello world  "
// Output: "hello world"

function trimStr(str){
    let left = 0
    let right = str.length -1
    
    while(str[left] === " " && left <= right){
        left++
    }
    while(str[right] === " " && right >= left){
        right--
    }
    return str.slice(left, right+1)
}
console.log(trimStr(str))
```

## 📌 18. Extract Domain from URL
```javascript
let str = "https://www.example.com/path"
// Output: "example.com"

function extractURL(str){
      return new URL(str).hostname.split("www.")[1]
}
console.log(extractURL(str))

```

## 📌 19. Find Longest Word
```javascript
let str = "The quick brown fox jumps"
// Output: "quick"

function longestStr(str){
    return str.split(" ").sort((a, b)=> b.length - a.length)[0]
}
console.log(longestStr(str))
```
## 📌 20. Reverse Words in a String
```javascript
let str = "Hello World"
// Output: "olleH dlroW"


function reverseStrWords(str){
// return str.split(" ").map((word) => word.split("").reverse().join("")).join(" ")
   let result = ""
   
   for(let word of str.split(" ")){
        result += word.split("").reverse().join("")+" "
   }
   return result.trim()
}

console.log(reverseStrWords(str))
```
## 📌 21. Check Anagrams
```javascript
 let obj ={ string1: "listen", string2: "silent" }
// Output: true


function checkAnagram(obj){
    const {string1, string2} = obj
    
    if(string1.length !== string2.length){
        return false
    }
    let obj1 = {} //{ l: 1, i: 1, s: 1, t: 1, e: 1, n: 1 }
    let obj2 = {}
    
    for(let char of string1){
        obj1[char] = (obj1[char] || 0) +1
    }
    
    for(let char of string2){
        obj2[char] = (obj2[char] || 0) +1
    }
    
    for(let char in obj2){
        if(obj1[char] !== obj2[char] ){
            return false
        }
    }
    return true
}
console.log(checkAnagram(obj))
```
## 📌 21. Convert to Title Case
```javascript
let str = "the quick brown fox"
// Output: "The Quick Brown Fox"

function capitalizeWords()(str){
    let result = ""
    for(let word of str.split(" ")){
           word = word[0].toUpperCase() + word.slice(1).toLowerCase()
           result+= word + " "
    }
    return result.trim()
}
console.log(convertFirstCap(str))
```

