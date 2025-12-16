# 🚀 LeetCode JavaScript Solutions & Coding Challenges

This repo contains my **JavaScript coding snippets**.  
It is designed to help developers **learn problem-solving** and **prepare for coding interviews**.

## 📂 Categories
- Arrays (Two Sum, Maximum Subarray, Rotate Array...)
- Strings (Valid Palindrome, Anagram, Substring...)
- Linked List (Reverse LL, Detect Cycle...)
- Dynamic Programming (Climbing Stairs, Coin Change...)
- Other coding challenges from LeetCode & interviews

## 🔥 Why this repo?
- ✅ Copy-paste friendly **JavaScript snippets**  
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
function intersection(arr1, arr2){
    // let result = []     -> 1 solution 
    // for(let num of arr1){
    //     if(arr2.includes(num)){
    //         result.push(num)
    //     }
    // }
    // return result


    // let newSet = new Set(arr1)  -> 2 solution
    // let result = []
    // for(let num of arr2){
    //     if(newSet.has(num)){
    //         result.push(num)
    //     }
    // }
    // return result

    // return arr1.filter((num) => arr2.includes(num))  -> 3 solution

    let result = []
    let sortArr1 = arr1.sort((a, b) => a - b)
    let sortArr2 = arr2.sort((a, b) => a -b)
    let i =0
    let j =0
    
    while(i < sortArr1.length && j < sortArr2.length){
        let isSame = sortArr1[i] === sortArr2[j]
        if(isSame){
            result.push(sortArr1[i])
            i++
            j++
        }else if(sortArr1[i] < sortArr2[j]){
            i++
        }else{
            j++
        }
    }
    return  result
}
console.log(intersection(arr1, arr2))
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

function capitalizeWords(str){
    let result = ""
    for(let word of str.split(" ")){
           word = word[0].toUpperCase() + word.slice(1).toLowerCase()
           result+= word + " "
    }
    return result.trim()
}
console.log(capitalizeWords(str))
```
## 📌 22. Remove Specific Characters
```javascript
let obj = { string: "hello world", charsToRemove: "lo" }
// Output: "he wrd"


function removeChars(obj){
    const {string, charsToRemove} = obj
    let result= ''
    
    for(let chars of string){
        if(charsToRemove.includes(chars)){
            chars = ""
        }else{
            result += chars
        }
    }
    return result
}
console.log(removeChars(obj))
```
## 📌 23. Truncate String
```javascript
let obj = { string: "This is a long sentence", maxLength: 10 }
// Output: "This is a..."

function turncate(obj){
    const {string, maxLength} = obj
    let strlen = string.length
    
    let result = ""
    
    for(let char of string){
      if(string.length > maxLength){
          result = string.slice(0, maxLength) + "..."
      }else{
          result += char
      }
    }
    return result
}
console.log(turncate(obj))
```
## 📌 24. Merge Two Objects
```javascript
let  obj= { obj1: { a: 1, b: 2 }, obj2: { b: 3, c: 4 } }
// Output: { a: 1, b: 3, c: 4 }


function mergeTwoObject(obj){
    let {obj1, obj2} = obj
    // return {...obj1, obj2}   ---> solution: 1
    // return Object.assign({}, obj1, obj2) ---> solution: 2
    
    let result = {...obj1}
    for(let key in obj2){
        if(result[key]){
            result[key] = obj2[key]
        }else{
            result[key] = obj2[key]
        }
    }
    return result
}
console.log(mergeTwoObject(obj))
```
## 📌 25. Filter Object Properties
```javascript
let input = { obj: { a: 1, b: 2, c: 3, d: 4 }, keep: ["a", "c"] }
// Output: { a: 1, c: 3 }

function filterKey(input){
    const {obj, keep} = input
    return keep.reduce((acc, key) => {
        if(obj[key]) acc[key] = obj[key]
        return acc
    }, {})
}
console.log(filterKey(input))
```
## 📌 26. Group By Property
```javascript
let arr = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 },
  { name: "Charlie", age: 25 }
]
// Output: {
//   "25": [{ name: "Alice", age: 25 }, { name: "Charlie", age: 25 }],
//   "30": [{ name: "Bob", age: 30 }]
// }


function groupByProperty(input){
    let result = {}
    return input.reduce((acc, obj)=>{
        if(!acc[obj.age]){
            acc[obj.age] = []
        }
        acc[obj.age].push(obj)
        return acc
    }, {})
    
}
console.log(groupByProperty(arr))
```
## 📌 27. Some special case
```javascript
  console.log(null == undefined);
// If x is null and y is undefined, or vice-versa → return true. (No further coercion happens. (ECMA-262 spec))


// Strict Equality (===) checks both value & type
  console.log(null === undefined);  
// Output: false
// Because null is of type "object" and undefined is of type "undefined"
// Different types → strictly not equal


// Loose Equality (==) allows coercion but has special rules
console.log(null == 0);           
// Output: false
// null only equals undefined (special case), not any number


console.log(undefined == 0);      
// Output: false
// undefined also only equals null, not a number


// Explicit conversion using Number()
console.log(Number(null));        
// Output: 0
// null is treated as "empty" → converts to 0


console.log(Number(undefined));   
// Output: NaN
// undefined cannot be converted to a valid number → gives NaN

```
## 📌 28. When Objects used as a key
```javascript

let obj = {};
obj[{}] = "first";
obj[{}] = "second";
console.log(obj);

//{ '[object Object]': 'second' }
```
## 📌 29. Deep Clone Object
```javascript
let obj = { a: 1, b: { c: 2 } }
// Output: { a: 1, b: { c: 2 } } 

function deepClone(obj){
    if(typeof obj !== "object" || obj === null){
        return obj
    }
    let copy = Array.isArray(obj) ? [] :{}
    for(let key in obj){
        if(typeof obj[key] === "object" && obj[key] !== null){
            copy[key] = deepClone(obj[key])
        }else{
            copy[key] = obj[key]
        }
    }
    return copy
}
console.log(deepClone(obj))
```
## 📌 30. Flatten Object
```javascript
let obj =  { a: 1, b: { c: 2, d: { e: 3 } } }
// Output: { "a": 1, "b.c": 2, "b.d.e": 3 }

function flattenObj(obj){
    let stack = [{value:obj, parentKey:""}]
    let result = {}
    while(stack.length){
        const {value, parentKey} = stack.pop()
        
        for(let key in value){
            let combineKey = parentKey ? `${parentKey}.${key}` : key
            
            if(typeof value[key] === "object" && value[key] !== null){
                stack.push({value:value[key], parentKey:combineKey})
            }else{
                result[combineKey] = value[key]
            }
        }
    }
    return result
}
console.log(flattenObj(obj))
```

## 📌 31. Convert Array to Object
```javascript
let arr = [["name", "Alice"], ["age", 25], ["city", "New York"]]
// Output: { name: "Alice", age: 25, city: "New York" }

function convertIntoObj(arr){
    return arr.reduce((acc, item)=>{
         const [key, value] = item
         acc[key] = value
        return acc
    }, {})
}
console.log(convertIntoObj(arr))
```
## 📌 32. Find Object in Array
```javascript
let obj = { 
  array: [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" },
    { id: 3, name: "Charlie" }
  ],
  property: "id",
  value: 2
}
// Output: { id: 2, name: "Bob" }

function findObjById(obj){
    const {array, property, value} = obj
    return array.reduce((acc, item) =>{
        if(item[property] === value){
            acc = {...item}
        }
        return acc
        
    }, {})
}
console.log(findObjById(obj))
```

## 📌 32. Sort Objects by Property
```javascript
let obj = {
  array: [
    { name: "Charlie", age: 30 },
    { name: "Alice", age: 25 },
    { name: "Bob", age: 35 }
  ],
  property: "age"
}

// Output: [
//   { name: "Alice", age: 25 },
//   { name: "Charlie", age: 30 },
//   { name: "Bob", age: 35 }
// ]

function sortByProperty(obj){
    const {array, property} = obj
    return array.sort((a, b) => a[property] - b[property])
}
console.log(sortByProperty(obj))
```
## 📌 33. Convert CSV to Array of Objects
```javascript
let input = "name,age,city\nAlice,25,New York\nBob,30,San Francisco"
// Output: [
//   { name: "Alice", age: "25", city: "New York" },
//   { name: "Bob", age: "30", city: "San Francisco" }
// ]

function csvToArrObj(input){
    let result = []
    let keys = input.split("\n")[0].split(",")
    let values = input.split("\n").slice(1)
    
    for(let value of values){
        let splitValue = value.split(",")isPalindrom
        let obj = {}
        
        for(let i = 0; i < splitValue.length; i++){
             obj[keys[i]] = splitValue[i]
        }
        
        result.push(obj)
    }
    return result
}
console.log(csvToArrObj(input))
```
## 📌 34. Convert Array of Objects to CSV
```javascript
let arr = [
  { name: "Alice", age: "25", city: "New York" },
  { name: "Bob", age: "30", city: "San Francisco" }
]
// output = "name,age,city\nAlice,25,New York\nBob,30,San Francisco"

function arrToIntoCSV(arr){
    let keys = Object.keys( arr[0]).join(",")
    let values = ""
    for(let {name, age, city} of arr){
         values += `${name},${age},${city}` + "\n"
    }
    return keys + "\n" + values
}
console.log(arrToIntoCSV(arr))
```

## 📌 35. Scoping
```javascript
Arrow function → this is lexical, not tied to the object.
Normal function → this depends on the call-site.

let x = 10;
const foo = {
  x: 20,
  bar: () => console.log(this.x),
  baz: function () {
    console.log(this.x);
  }
};

foo.bar();  // undefined
foo.baz();  //20
```
## 📌 36. Longest Unique Substring
```javascript
let str = "abcabcbb"
// Output: 3 ("abc")


function findlongestSubStrWithoutRepeating(str){
    let left = 0 // it will track unique str
    let maxLen = 0 // unique str length
    
    let newSet = new Set()  // hold unique str
    let longestStr = ""   // longest string
    
     for(let right =0; right < str.length; right++){
        let currentChar = str[right]
        while(newSet.has(currentChar)){// check if duplicate
             newSet.delete(str[left]) // remove first duplicate
             left++   // now it track only unique str
        } 
        newSet.add(currentChar) // add only unique value
        
        let strLen = right - left+1
        if(strLen > maxLen){
            maxLen = strLen
            longestStr = str.slice(left, right+1)  // 1 for include last value
        }
    }
    return{
        maxLen,
        longestStr
    }
}
console.log(findlongestSubStrWithoutRepeating(str))
```
## 📌 37. Merge Objects
```javascript
let a = { user: { name: "Monu", skills: ["JS"] } };
let b = { user: { age: 26, skills: ["React"] } };

// output { user: { name: 'Monu', skills: [ 'JS', 'React' ], age: 26 } }

function mergeTwoObjects(obj1, obj2) {
  let result = { ...obj1 };
  for (let key in obj2) {
    if (Array.isArray(obj2[key]) && Array.isArray(result[key])) {
      result[key] = [...result[key], ...obj2[key]];
    } else if (
      typeof obj2[key] === "object" &&
      obj2[key] !== null &&
      typeof result[key] === "object"
    ) {
      result[key] = mergeTwoObjects(result[key], obj2[key]);
    } else {
      result[key] = obj2[key];
    }
  }
  return result;
}
console.log(mergeTwoObjects(a, b));
```
## 📌 38. Check if number is Prime
```javascript
let num = 9

// A prime number is a natural number greater than 1 that is divisible only by 1 and itself.
// ✅ Prime → 2, 3, 5, 7, 11, 13
// ❌ Not Prime → 1 (special case), 4 (divisible by 2), 9 (divisible by 3)

function isPrime(num){
    if( num <= 1) return false
    if(num === 2) return true
    for(let i=2; i <= Math.sqrt(num); i++){
         if(num % i === 0){
             return false
         }
    }
    return true
}
console.log(isPrime(num))
```
## 📌 39. Remove duplicate numbers
```javascript

let arr = [1,1,2,2,3,3,4]
// Output: [1,2,3,4]

function removeDuplicateArr(arr){
    let left = 0 // slow track
    for(let right=1; right < arr.length; right++){
        if(arr[left] !== arr[right]){
            left++
            arr[left] = arr[right]
        }
    }
     return arr.slice(0, left + 1);
}
console.log(removeDuplicateArr(arr))
```
## 📌 40. Remove Duplicate into string
```javascript
let str = "banana"
// Output: "ban"

function makeStrUnique(str){
    // return [...new Set(str)].join("")    -> (1) solution
    
    let obj={}          
    for(let char of str){
        obj[char] = (str[char] || 0) +1
    }
    return Object.keys(obj).join("")
}
console.log(makeStrUnique(str))
```
## 📌 41. Find Second Largest Number
```javascript
let arr = [10, 5, 8, 20, 15]
// Output: 15

function findSecondLarestNumber(arr){
    // arr.sort((a, b) => b -a)     -> 1 solution
    // return arr[1]
    
    if(arr.length < 2) return null
    
    let firstMax = -Infinity
    let secondMax = -Infinity
    for(let num of arr){
        if(num > firstMax){
            secondMax = firstMax
            firstMax = num
        }else if(num > secondMax && num < firstMax){
            secondMax = num
        }
    }
    return {firstMax, secondMax}
}
console.log(findSecondLarestNumber(arr))
```
## 📌 42. Rotate Array by K Steps
```javascript
// 7. Rotate Array by K Steps

let nums = [1,2,3,4,5,6,7], k = 3
// Output: [5,6,7,1,2,3,4]

function rotateArrByKStep(nums, k){
    // let firstSlice = nums.slice(0, k+1) // include -> exclude value
    // let lastSlice = nums.slice(k+1) // skip kth value
    // return lastSlice.concat(firstSlice)
    
    while(k !== 0){
        let lastEl = nums.pop()
        k--
        nums.unshift(lastEl)
    }
    return nums 
}
console.log(rotateArrByKStep(nums, k))
```
## 📌 43. Find Missing Number
```javascript
let arr = [1,2,4,5,6] 
// (range is 1 to 6)
// Output: 3

function findMissingNumber(arr){
    // let n = arr.length +1
    // let actualSum = n * (n +1)/2
    // let expectedSum = arr.reduce((acc, num) => acc += num, 0)
    // return actualSum - expectedSum
    
    
    let min = Math.min(...arr)
    let max = Math.max(...arr)
    for(let i=min; i <= max; i++){
        if(!arr.includes(i)){
            return i
        }
    }
}
console.log(findMissingNumber(arr))
```
## 📌 44. Convert Array of Objects to Object by ID
```javascript
let arr =[
  { id: 1, name: "Monu" },
  { id: 2, name: "Daksh" }
]

// output {
//   1: { id: 1, name: "Monu" },
//   2: { id: 2, name: "Daksh" }
// }

function groupObjectOfArr(arr){
    // let result = {}   ---> 1. solution
    // for(let item of arr){
    //     if(!result[item.id]){
    //         result[item.id] =[]
    //     }
    //     result[item.id].push(item)
    // }
    // return result

    
    return arr.reduce((acc, item)=>{
        if(!acc[item.id]){
            acc[item.id] = []
        }
        acc[item.id].push(item)
        return acc
    }, {})
}
console.log(groupObjectOfArr(arr))
```
## 📌 45. String Compression
```javascript
let str = aabcccccaaa
let str = abc

// output "a2b1c5a3"
// output  "abc"

function stringCompress(str) {
    let count = 1;
    let result = "";

    for (let i = 1; i < str.length; i++) {
        if (str[i] === str[i - 1]) {
            count++;
        } else {
            result += str[i - 1] + count;
            count = 1;
        }
    }
    // Add last char
    result += str[str.length - 1] + count;

    // Return compressed only if smaller
    return result.length < str.length ? result : str;
}
console.log(stringCompress(str)
```
## 📌 46. Valid Parentheses
```javascript
let  s = "({[]})"
// output: true


function isValidParentheses(s){
    let obj = {
        "{":"}",
        "(":")",
        "[":"]"
    }
    
    let parenthesArr = []
    for(let parenthes of s){
        if(obj[parenthes]){
            parenthesArr.push(parenthes)
        }else{
            let lastParenthes = parenthesArr.pop()
            if(obj[lastParenthes] !== parenthes){
                return false
            }
        }
    }
    return parenthesArr.length ===0
}
console.log(isValidParentheses(s))
```
## 📌 47. Remove All Adjacent Duplicates
```javascript
let s = "abbaca"
// Expected Output:
// "ca"

function removeAdjacentEl(s){
    let stack = []
    for(let char of s){
        if(stack.length && stack[stack.length -1] === char){
            stack.pop()
        }else{
            stack.push(char)
        }
    }
    return stack
}
console.log(removeAdjacentEl(s))
```
## 📌 48. Group Anagrams
```javascript
let strs = ["eat","tea","tan","ate","nat","bat"]

// Expected Output:
// [["eat","tea","ate"],["tan","nat"],["bat"]]

function groupAnagram(arr){
    let obj = arr.reduce((acc, item) =>{
        let sortedWord = item.split("").sort().join("")
        if(!acc[sortedWord]){
            acc[sortedWord] = []
        }
        acc[sortedWord].push(item)
        return acc
    },{})
    return Object.values(obj)
}
console.log(groupAnagram(strs))
```
## 📌 49. Find All Substrings of a String
```javascript
let s = "abc"
// Expected Output:
// ["a","b","c","ab","bc","abc"]

function findAllSubstrings(s){
    let result = []
    for(let i=0; i < s.length; i++){
        let substr = ""
        for(let j=i; j < s.length; j++){
            substr += s[j]
            result.push(substr)
        }
    }
    return result.sort((a, b) => a.length -b.length)  
}
console.log(findAllSubstrings(s))
```
## 📌 50. Deep Clone Without Reference
```javascript
const obj = { name: "Monu", address: { city: "Delhi" } };

function deepClone(obj){
    // return structuredClone(obj)
    
    if(typeof obj !== "object" || obj === null){
        return obj
    }
    let copy = Array.isArray(obj) ? [] : {}
    for(let key in obj){
        if(typeof obj[key] === "object" && obj[key] !== null){
            copy[key] =  deepClone(obj[key])
        }else{
            copy[key] = obj[key]
        }
    }

    return copy
}
console.log(deepClone(obj))
```
## 📌 51. Remove Null or Undefined Keys
```javascript
function removeNullUndefined(obj) {
  return Object.keys(obj).reduce((acc, key) => {
    if (obj[key] !== null && obj[key] !== undefined) {
      acc[key] = obj[key];
    }
    return acc;
  }, {});
}
```
## 📌 51. Compare deep object
```javascript
const obj1 = { a: 1, b: { c: 2 } };
const obj2 = { a: 1, b: { c: 2 } }

function deepCompare(obj1, obj2) {
  // base case: primitive values
  if (obj1 === obj2) return true;
  
  // check null or non-object
  if (typeof obj1 !== "object" || typeof obj2 !== "object" || obj1 === null || obj2 === null) {
    return false;
  }
  if (Object.keys(obj1).length !== Object.keys(obj2).length) return false;
  for (let key in obj1) {
    if (!deepCompare(obj1[key], obj2[key])) {
      return false;
    }
  }
  return true;
}
console.log(deepCompare(obj1, obj2))
```
## 📌 52. Find Max Value in Object
``` javascript
const scores = { Monu: 85, Daksh: 92, Rahul: 78 };
// output : { name: 'Daksh', score: 92 }

function findMaxScore(obj) {
  let score = -Infinity;
  let name = "";
  for (let key in obj) {
    if (obj[key] > score) {
      score = obj[key];  
      name = key;       
    }
  }
  return { name, score };
}
console.log(findMaxScore(scores));
```
## 📌 53. Convert Object to Query String
```javascript
const obj = { name: "Monu", age: 26, city: "Delhi" };
//"name=Monu&age=26&city=Delhi"

function queryString(obj){
    //  return Object.keys(obj).map((key) => `${key}=${obj[key]}`).join("&")
    
    let result= ''
    let objLength = Object.keys(obj).length
    let i = 0
    
    for(let key in obj){
         result += `${key}=${obj[key]}`
         if(i < objLength -1){
             result += "&"
         }
         i++
    }
    return result    
}
console.log(queryString(obj))
```
## 📌 54. Map vs WeakMap in JavaScript (garbage collection)
```javascript
// =======================================
// Example: Map vs WeakMap in JavaScript
// =======================================

// --- Using Map ---
let obj1 = { name: "Monu" };
const map = new Map();

// Setting an object as a key in Map
map.set(obj1, "I am stored in Map");

// Now we remove the reference from variable
obj1 = null;

// Object is still accessible because Map holds a strong reference
console.log("Map key still exists:", map.keys().next().value); 
// Output: { name: "Monu" }
// Explanation: Map prevents garbage collection as long as the key exists inside it.

// --- Using WeakMap ---
let obj2 = { name: "Daksh" };
const weakMap = new WeakMap();

// Setting an object as a key in WeakMap
weakMap.set(obj2, "I am stored in WeakMap");

// Remove the reference from variable
obj2 = null;


console.log("WeakMap dont have key now",  weakMap.has(obj2)) // false

// In WeakMap, the key becomes eligible for garbage collection
// Because WeakMap only holds a *weak reference* to the object

// You CANNOT iterate keys of a WeakMap, so no weakMap.keys() like Map.
// If garbage collector runs, the entry will be removed automatically.
```
## 📌 55. JavaScript type coercion / truthy-falsy values
```javascript

!!"something" → convert values into boolean.

Non-empty string = true.
thats why !!"false" == !!"true" → true,

but "false" == "true" → false.

console.log(!!"false" == !!"true");    // true
console.log("false" == "true");       // false

// ![]  --> this will be treated like truthy value with have ! at starting
console.log([] == ![]);               // true
```
## 📌 56. Enumerable key + inherited keys + non-enumerable key + hidden key
```javascript
let obj = { a: 1, b: 2 };

for (let key in obj) {
  console.log(key);   // for...in = enumerable + inherited keys
}

console.log(Object.keys(obj));              // enumerable own properties
console.log(Object.getOwnPropertyNames(obj)); // all own properties (enumerable + non-enumerable +  hidden)


All own properties (enumerable + non-enumerable / hidden)
Object.defineProperty(obj, "hiddenProp", {
  value: 42,
  enumerable: false
});

console.log(Object.getOwnPropertyNames(obj));


Inherited properties
let parent = { c: 3 };
let child = Object.create(parent);
child.a = 1;      // adding a in child


use for ... in loop and you will see ("c", "a")

Object.keys(child) → only ["a"].
console.log(Object.getPrototypeOf(child));  only ["c"]  inherited
```
## 📌 57. Unique Objects in Array
```javascript
let arr =[{id: 1, name: "A"}, {id: 2, name: "B"}, {id: 1, name: "C"}]

// output :[{id: 1, name: "A"}, {id: 2, name: "B"}]

function findUniqueObj(arr){
    let map = new Map()
    
    for(let obj of arr){
        if(!map.has(obj.id)){
            map.set(obj.id, obj)
        }
    }
    return Array.from(map.values(map))
}
console.log(findUniqueObj(arr))
```
## 📌 57. Sweap Two numbers without using third variable
```javascript
let a = 10;
let b = 20;

// first Approach
a = a +b
b = a - b
a = a - b
console.log(a, b)  // 20, 10


// Second Approach
[a, b] = [b, a]
console.log(a, b)// 20, 10
```
## 📌 58. Function vs Block Scope with var
```javascript
function test() {
  console.log(a);
  if (true) {
    var a = 10;
  }
  console.log(a);
}
test();  // undefined, 10


==== Explanation ====
function test() {
  var a; // hoisted to top (initialized as undefined)

  console.log(a); // <-- a is declared, but not yet assigned
  if (true) {
    a = 10; // assignment happens here
  }
  console.log(a);  // 10 assign here now
}

```
## 📌 59. Shadowing Inside Function
```javascript

var name = "Global";
function printName() {
  console.log("1:", name);
  var name = "Local";
  console.log("2:", name);
}
printName();


==== Explanation ====
function printName() {
  var name;  // declaration hoisted, value = undefined

  console.log("1:", name); // at this point, it's undefined
  name = "Local";          // assignment happens here
  console.log("2:", name); // now it's "Local"
}


⚡ Reason
var is function-scoped, not block-scoped.
When var name is declared inside printName, it shadows the global name.
Due to hoisting, the local name exists from the top of the function, but starts as undefined.
That’s why you don’t see "Global" inside the function at all.

```
## 📌 60. Check Palindrome Number in Array Form(Two pointer)
```javascript
let digits = [1, 2, 3, 2, 1]
// Output: true

function checkPlaindrom(arr){
    let left =0
    let right = arr.length -1
    while(left < right){
        if(arr[left] !== arr[right]){
            return false
        }
        left++
        right--
    }
    return true
}
console.log(checkPlaindrom(digits))
```
## 📌 61. Subtract One from Array Number
```javascript
let digits = [1, 0, 0]
// Output: [9, 9]

function subtractOne(digits){
    for(let i = digits.length -1; i >= 0; i--){
        if(digits[i] >0){  // digits greater then 0 , subtract
            digits[i]--
            break
        }else{
            digits[i] = 9  // if current digit ===0 then replace this with 9
        }
    }
    if(digits[0] === 0){
        digits.shift()  // remove [ 0, 9, 9 ]  first zero
    }
   return digits
}
console.log(subtractOne(digits))
```
## 📌 62. Plus One
```javascript
let arr =[9, 9]
// output [1, 0, 0]

function plusOne(arr){
    for(let i = arr.length-1; i >=0; i--){
        if(arr[i] < 9){
            arr[i] += 1
            return arr
        }else{
            arr[i] = 0
        }
    }
    arr.unshift(1)
    return arr
}
console.log(plusOne(arr))
```
## 📌 63. Add Two Numbers in Array Form
```javascript
let num1 = [2, 7, 4], num2 = [5, 6, 4]
// Output : [8, 3, 8]

function sumOfArr(arr1, arr2){
    let result = []
    let carry = 0
    
    let i = arr1.length -1
    let j = arr2.length -1
    
    while(i >=0 || j >=0 || carry > 0){
        let x =  i >=0 ?  arr1[i]  :0
        let y = j >=0 ? arr2[j] : 0
        
        let sum = x + y + carry
        result.unshift(sum % 10)
        carry = Math.floor(sum / 10)
        i--
        j--
    }
    return result
}
console.log(sumOfArr(num1, num2))
```
## 📌 64. Subarray with Given Sum
```javascript

let nums = [1, 4, 20, 3, 10, 5], target = 33
  // [20,3,10]

function findSunArr(arr, target){
    let left = 0   // slow pointer
    let currentSum = 0
    
    for(let right=0; right < arr.length; right++){
        currentSum += arr[right]
        while(currentSum > target && left <= right){
            currentSum -= arr[left]
            left++
        }
        if(currentSum === target){
            return {found:true, result:arr.slice(left, right+1)}
        }
    }
    return {found:false, result:[]}
}
console.log(findSunArr(nums, target))
```
## 📌 65. Majority Element (> n/2 times)
```javascript
let arr = [2,2,1,1,1,2,2]
// Output: 2

function findMajorityElement(arr){
    let obj = {}
    for(let num of arr){
        obj[num] = (obj[num] || 0) +1
        
        if(obj[num] > arr.length / 2){
            return num
        }
    }
    return null
}
console.log(findMajorityElement(arr))
```
## 📌 66. Find duplicate values
```javascript

let arr = [4,3,2,7,8,2,3,1]
// Output: [2,3]

function duplicate(arr){
    let result = []
    let obj = {}
    
    for(let num of arr){
        obj[num] = (obj[num] || 0) +1
    }
    for(let key in obj){
        if(obj[key]  >= 2){
            result.push(+key)
        }
    }
    return result
}
console.log(duplicate(arr))
```
## 📌 67. find a string is valid
```javascript
let str = "A man, a plan, a canal: Panama"  
// Output: true

function isPalindrom(str){
    let validStr = ""
    for(let char of str){
        if((char >= "a" && char <= "z") || (char >= "A"&& char <= "Z")){
            validStr += char.toLowerCase()
        }
    }
    
    let left =0;
    let right = validStr.length -1
    while(left < right){
        if(validStr[left] !== validStr[right]){
            return false
        }
        left++
        right--
    }
    return true
}
console.log(isPalindrom(str))
```
## 📌 68. Generate Range of Numbers
```javascript
let obj = { start: 5, end: 10 }
// Output: [5, 6, 7, 8, 9, 10]

function generateNumber(obj){
    let {start, end} = obj

    // let size = end -start+1
    // return Array.from({length:size}, (_, index) => start+index)
    
      let result = []
      for(let i = start; i <= end; i++){
          result.push(i)
      }
     return result
}
console.log(generateNumber(obj))
```
## 📌 69. Find the Deepest Key in a Nested Object
```javascript
let obj = {a: 1, b: {c: 2, d: {e: 3}}}
// Output: "e"


function deepKey(obj){
    
    let stack = [{node:obj, key:null}]
    let deepestKey = null;
    while(stack.length){
        const {node, key} = stack.pop()
        for(let k in node){
            if(typeof node[k] === "object" && node[k]){
                stack.push({node:node[k], key:k})
            }else{
                deepestKey = k
            }
        }
    }
    return deepestKey
}
console.log(deepKey(obj))
```
## 📌 70. Group Words by Their Length
```javascript
let arr =["cat", "dog", "elephant", "lion", "tiger"]
// Output: {3: ["cat", "dog"], 8: ["elephant"], 4: ["lion"], 5: ["tiger"]}

function groupWordByLength(arr){
    return arr.reduce((acc, word)=>{
        let wordLength = word.length
        if(!acc[wordLength]){
            acc[wordLength] = []
        }
        acc[wordLength].push(word)
        return acc
    },{})    
}
console.log(groupWordByLength(arr))
```
## 📌 71. Find All Distinct Palindromic Substrings
```javascript
let str ="abaaa"
// Output: ["a", "aa", "aaa", "aba", "b"]


function findAllPalinfromSubStr(str){
    
    function isPalindrom(substr){
        let left = 0
        let right = substr.length -1
        while(left < right){
            if(substr[left] !== substr[right]){
                return false
            }
            left++
            right--
        }
        return true
    }
    
    
    let result = new Set()
   for (let i = 0; i < str.length; i++) {
        for (let j = i; j < str.length; j++) {
            let subStr = str.slice(i, j + 1);
            if (isPalindrom(subStr)) {
                result.add(subStr);
            }
        }
    }
    return [...result] 
}
console.log(findAllPalinfromSubStr(str))
```
## 📌 72. Nested Promises
```javascript
Note: if there is resolved promise inside then, so it will replace first resolved promise value

Promise.resolve("first")
  .then(res => {
    return Promise.resolve("second");
  })
  .then(res => console.log(res)); // second
```
## 📌 73. Find Subarray with Given Sum
```javascript
let arr = [1, 2, 3, 7, 5];
let target = 12;
// Output: [2,3,7]

function findSubArr(arr, target){
    let left =0
    let sum = 0
    
    for(let right =0; right < arr.length; right++){
         sum += arr[right]
         while(sum > target && left <= right){
             sum -= arr[left]
             left++
         }
         if(sum === target){
             return arr.slice(left, right+1)
         }
    }
    return []
}
console.log(findSubArr(arr, target))
```
## 📌 74. Rearrange Array Alternating Positive & Negative
```javascript

let arr =[1, 2, -3, -4, -5, 6, -7]
// Output: [1, -3, 2, -4, 6, -5, -7]

function rearrange(arr){
    let pos = arr.filter((num)=> num > 0)
    let negs = arr.filter((num) => num < 0)
    let result = []
    
    let i = 0
    let j = 0

    while(i < pos.length && j < negs.length ){
          if(i < pos.length) result.push(pos[i++])
          if(j < negs.length) result.push(negs[j++])
    }
    return result
}
console.log(rearrange(arr))
```
## 📌 75. Maximum Sum Subarray (Kadane’s Algorithm)
```javascript

let arr = [-2,1,-3,4,-1,2,1,-5,4]
//{ maxSum: 6, subArray: [4, -1, 2, 1] }

function findMaxSubArray(arr){
    let maxSum = arr[0]
    let currentSum = arr[0]
    
    let start =0
    let end = 0
    let tempStart = 0
    
    for(let i=1; i < arr.length; i++){
        if(arr[i] > currentSum + arr[i]){
            currentSum = arr[i]
            tempStart = i
        }else{ 
            currentSum += arr[i]
        }
        if(currentSum > maxSum){
            maxSum = currentSum
            start = tempStart
            end = i
        }
    }
    return {
        maxSum,
        subArr: arr.slice(start, end+1)
    }
}
console.log(findMaxSubArray(arr))
```
## 📌 76. Smallest Subarray with Sum ≥ Target
```javascript
let arr = [2,3,1,2,4,3], target = 7

// Output: 2 ([4,3])
function smallestSubArrayWithTargetSum(arr, target){
    let minLength = Infinity
    let currentSum = 0
    let result = []
    let left = 0
    
    for(let right =0; right < arr.length; right++){
         currentSum += arr[right]
         while(currentSum >= target){
             if(right - left + 1 < minLength){
                 minLength = right - left +1
                 result = arr.slice(left, right+1)
             }
             currentSum -= arr[left]
             left++
         }
    }
    return{
        minLength,
        result
    }
}
console.log(smallestSubArrayWithTargetSum(arr, target))
```
## 📌 77. Hoisting 
```javascript
When Js run/execute it goes through with two steps
1. Memory creation phase (place where we have hosting there)
2. Code execution phase

console.log(name)   // undefined
var name = "Dev"  

console.log(getName)    // dev
function getName(){  
 return "Dev"  
}
```
## 📌 78. Function inside block scope
```javascript

'use strict';
if (true) {
  function test() {
    console.log("inside");
  }
}
test(); // ❌ ReferenceError



if (true) {
  function test() {
    console.log("inside");
  }
}
test();  // inside
```
## 📌 79. Class hoisting
```javascript

let obj = new Person();  // ❌ ReferenceError
class Person {}

Note: Classes never hoist
```
## 📌 80. Hoisting
```javascript
var x = 5;
var x;
console.log(x);

Note:-

var x;   // declared (initialized with undefined by default)
x = 5;   // then assigned
var x;   // ignored, because it's already declared
```
## 📌 80. var hoisting conflict
```javascript
foo();
var foo = function() {
  console.log("var func");
};
function foo() {
  console.log("declaration func");
}
foo();

output:-
declaration func
var func

📌 Important Notes:


Function declarations are hoisted with their full body.
var declarations are hoisted but only with undefined.
If both functions are with same → function declaration wins initially, but later reassignment by var will overwrite it.
```
## 📌 81. Conversion rule (ECMAScript spec)
```javascript

console.log(+"");   // Number("") --> 0
console.log(+null); // Number(null)  --> 0
console.log(+undefined); // Number(undefined)  


// + use Number(...) for conversion
```
## 📌 82. Array to number
```javascript
console.log(+[]);      
// [] is object → primitive conversion
// [].toString() → ""
// +"" → Number("")
// → 0


console.log(+["5"]);  
// ["5"].toString() → "5"
// +"5" → Number("5")
// → 5


console.log(+[1,2,3]); 
// [1,2,3].toString() → "1,2,3"
// +"1,2,3" → Number("1,2,3")
// → NaN (not a valid number)
```
## 📌 82. Array to number
```javascript
**Case 1: []**
console.log([] == 0);
// [] is object → ToPrimitive → [].toString()
// [].toString() → "" (empty string)
// "" == 0 → Number("") == 0
// 0 == 0 → true


// Case 2: [null]
console.log([null] == 0);
// [null] is object → ToPrimitive → [null].toString()
// [null].toString() → ""   (null is empty string in array join)
// "" == 0 → Number("") == 0
// 0 == 0 → true


// Case 3: [undefined]
console.log([undefined] == 0);
// [undefined] is object → ToPrimitive → [undefined].toString()
// [undefined].toString() → ""   (undefined is empty string in array join)
// "" == 0 → Number("") == 0
// 0 == 0 → true


// Case 4: [1]
console.log([1] == 1);
// [1] is object → ToPrimitive → [1].toString()
// [1].toString() → "1"
// "1" == 1 → Number("1") == 1
// 1 == 1 → true


// Case 5: [1,2]
console.log([1,2] == "1,2");
// [1,2] is object → ToPrimitive → [1,2].toString()
// [1,2].toString() → "1,2"
// "1,2" == "1,2" → true


// Case 6: [[]]
console.log([[]] == 0);
// [[]] → ToPrimitive → [[]].toString()
// [[]].toString() → ""  (inner [] → "")
// "" == 0 → Number("") == 0
// 0 == 0 → true
```
## 📌 83. Scoping
```javascript

var x = 1;
let x = 2;
console.log(x);

🔍 Reason:
You cannot redeclare the same variable with var and let in the same scope.
Since var x = 1; is already declared, writing let x = 2; causes a compile-time error.
```
## 📌 84. Scoping
```javascript

"use strict" (new browser ES6+ modules default)
try {
  throw new Error();
} catch (e) {
  function hello() { return "hi"; }
}
console.log(typeof hello);   // undefined


// no strict mode (old browser)
try {
  throw new Error();
} catch (e) {
  function hello() { return "hi"; }
}
console.log(typeof hello);   // function


🔍 Reason:
In strict mode (ES6+ modules default), function declarations inside a block (catch, if, for, etc.) are block-scoped.
So function hello() exists only inside the catch block and is not accessible outside.

When you do console.log(typeof hello), it checks in the outer/global scope, where hello is not defined → result is "undefined".
```
## 📌 85. Event loop starvation trap (microtask starvation)
```javascript
setTimeout(() => console.log("T"), 0);

Promise.resolve().then(function loop() {
  console.log("P");
  Promise.resolve().then(loop);
});

//output:
P
P
P
P
... (infinite)


//Global Execution

setTimeout(..., 0) schedules a macrotask (in the Timer phase).

Promise.resolve().then(loop) schedules a microtask.

//Event Loop Rule
Microtasks always run before moving to the next macrotask.
So the event loop first executes loop().

//Inside loop()
Logs "P".
Schedules another microtask loop (via Promise.resolve().then(loop)).

//Infinite Recursion in Microtask Queue
After one loop() finishes, another loop() is already waiting in the microtask queue.
This cycle repeats endlessly.
The microtask queue never becomes empty.

//Why setTimeout("T") never executes
The event loop cannot move to the macrotask queue (where setTimeout lives) until the microtask queue is completely empty.
Since the recursive promise keeps filling the microtask queue, "T" is starved forever.
```
## 📌 86. Explicit Coercion Snippets (guess the output)
```javascript
console.log(String(null));         
console.log(String(undefined));     
console.log(String(Symbol("x")));   

console.log(Boolean(null));         
console.log(Boolean(undefined));     
console.log(Boolean(Symbol("x")));   

console.log(Number(null));         
console.log(Number(undefined));     
console.log(Number(Symbol("x")));  


// String conversion
console.log(String(null));          // ?
console.log(String(undefined));     // ?
console.log(String(Symbol("x")));   // ?

// Number conversion
console.log(Number(""));            // ?
console.log(Number("   "));         // ?
console.log(Number("123abc"));      // ?
console.log(Number(true));          // ?
console.log(Number(false));         // ?
console.log(Number(null));          // ?
console.log(Number(undefined));     // ?

// Boolean conversion
console.log(Boolean("false"));      // ?
console.log(Boolean(""));           // ?
console.log(Boolean("0"));          // ?
console.log(Boolean(0));            // ?
console.log(Boolean([]));           // ?
console.log(Boolean({}));           // ?

// parseInt / parseFloat edge cases
console.log(parseInt("08"));        // ?
console.log(parseInt("0xF"));       // ?
console.log(parseInt("Infinity"));  // ?
console.log(parseFloat("123.45abc")); // ?

// Weird coercion mix
console.log(+true);                 // ?
console.log(+false);                // ?
console.log(+null);                 // ?
console.log(+undefined);            // ?
console.log(+"   ");                // ?

// Explicit object → primitive coercion
console.log(String([1,2,3]));       // ?
console.log(Number([1,2,3]));       // ?
console.log(Number([]));            // ?
console.log(Number({}));            // ?
console.log(Boolean([].toString())); // ?


// Empty arrays and strings
console.log([] + []);           // ?
console.log([] + {});           // ?
console.log({} + []);           // ?
console.log([1] + [1]);         // ?

// Boolean + Number coercion
console.log(true + true);       // ?
console.log(true + false);      // ?
console.log(false + false);     // ?
console.log(!!"false" == true); // ?

// null, undefined with +
console.log(null + 1);          // ?
console.log(undefined + 1);     // ?
console.log(null == 0);         // ?
console.log(undefined == null); // ?

// String + Number coercion
console.log("5" + 3);           // ?
console.log("5" - 3);           // ?
console.log("5" * "2");         // ?
console.log("5" / "2");         // ?

// Weird equality checks
console.log([] == ![]);         // ?
console.log("0" == false);      // ?
console.log(0 == "");           // ?
console.log(0 == []);           // ?
console.log("0" == []);         // ?

// Object / Array coercion with +
console.log([] + null + 1);     // ?
console.log([1,2] + [3,4]);     // ?
console.log(+[]);               // ?
console.log(+{});               // ?
console.log(+[[]]);             // ?
console.log(+[1,2,3]);          // ?

```

## 📌 87. Create a maskEmail function
```javascript
Input:
"monu.daksh@gmail.com"
Expected Output:
"m*****h@gmail.com"

function encrptEmail(email){
     let [username, domain] = email.split("@")
     
     let firstchar = username[0]
     let lastchar = username[username.length - 1]
     
     let hiddin = "*".repeat(username.length -2)
     return `${firstchar}${hiddin}${lastchar}${ "@" +  domain}`
}
console.log(encrptEmail(str))

```


## 📌 88. 
Implement a function storeData(obj) that stores objects in an array.
If a new object has the same id, replace the old one with the latest.
```javascript

storeData({id: 1, name: 'Monu'})
storeData({id: 2, name: 'Daksh'})
storeData({id: 1, name: 'Updated Monu'})

// Expected stored data:
[
  {id: 1, name: 'Updated Monu'},
  {id: 2, name: 'Daksh'}
]

let store = [];

function storeData(obj) {
  const index = store.findIndex(item => item.id === obj.id);
  if (index !== -1) {
    // Replace old object
    store[index] = obj;
  } else {
    // Add new object
    store.push(obj);
  }
  return store;
}

// Test:
console.log(storeData({ id: 1, name: "Monu" }));
console.log(storeData({ id: 2, name: "Daksh" }));
console.log(storeData({ id: 1, name: "Monu Updated" }));
```

## 📌 89. Create a Rate Limiter
```javascript
Implement a function that limits how many times a function can be called per second.

function rateLimiter(fn, limit, interval) {
  // Store timestamps of function calls
  const calls = [];

  return function (...args) {
    const now = Date.now();

    // Remove timestamps older than interval
    while (calls.length && now - calls[0] > interval) {
      calls.shift();
    }

    // Check if limit reached
    if (calls.length < limit) {
      calls.push(now); // record this call
      fn(...args);     // execute function
    } else {
      console.log("Rate limit exceeded. Try again later.");
    }
  };
}

// Example function to test
function sayHello(name) {
  console.log(`Hello, ${name}!`);
}

// Limit sayHello to 2 calls per 1000ms (1 second)
const limitedHello = rateLimiter(sayHello, 2, 1000);

// Test
limitedHello("Monu"); //  runs
limitedHello("John"); //  runs
limitedHello("Dev");  //  ignored (rate limit)
setTimeout(() => limitedHello("Alice"), 1100); //  runs after 1.1s


```

## 📌 90. Track Login Attempts
```javascript
Write a function loginTracker(userId) that stores how many times a user logs in.
Each call increases the count and returns the total.

function loginTracker() {
  const userLogins = {};

  return function(userId) {
    if (!userLogins[userId]) {
      userLogins[userId] = 0;
    }

    userLogins[userId]++;
    return userLogins[userId];
  };
}

// Example usage:
const trackLogin = loginTracker();

console.log(trackLogin("monu")); // 1
console.log(trackLogin("daksh")); // 1
console.log(trackLogin("monu")); // 2
console.log(trackLogin("monu")); // 3
console.log(trackLogin("daksh")); // 2

```
## 📌 91. Implement Retry Logic
```javascript

// retry(fn, n)
// fn → async function that might fail
// n  → number of retry attempts
async function retry(fn, n) {
  let lastError;

  for (let i = 0; i < n; i++) {
    try {
      //  Try running the async function
      return await fn();
    } catch (err) {
      //  If it fails, store the error and log retry info
      lastError = err;
      console.log(`Attempt ${i + 1} failed. Retrying...`);
    }
  }

  //  All attempts failed → throw last error
  throw lastError;
}


// Example: Simulated API that randomly fails
async function unstableAPI() {
  const success = Math.random() > 0.7; // 30% success chance
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (success) resolve(" Success!");
      else reject(" Failed!");
    }, 500);
  });
}

// Try calling with retry logic
retry(unstableAPI, 3)
  .then(res => console.log("Result:", res))
  .catch(err => console.error("Final Error:", err));
```
## 📌 91. Implement Retry Logic
```javascript

async function retry(fn, retries) {
  for (let attempt = 1; attempt <= retries; attempt++) {
    try {
      // Try to execute the function
      const result = await fn();
      return result; //  Success, return result
    } catch (err) {
      console.log(`Attempt ${attempt} failed.`);
      if (attempt === retries) {
        throw err; //  Last attempt failed, throw error
      }
      // Otherwise, continue to next attempt
    }
  }
}

// Example async function that may fail randomly
async function fetchData() {
  if (Math.random() < 0.7) { // 70% chance to fail
    throw new Error("Network error!");
  }
  return "Data fetched successfully!";
}

// Usage
retry(fetchData, 3)
  .then(res => console.log(res))
  .catch(err => console.log("All attempts failed:", err.message));


```
## 📌 93. Countdown Timer
```javascript
function countdown(count){
    let remaining = count
    let intervalId = setInterval(()=>{
        
        if(remaining > 0){
            console.log(`Time left: ${remaining} seconds`);
            remaining--
        }else{
            console.log("Time's up!");
            clearInterval(intervalId)
        }
    }, 1000)
}
countdown(10)
```
## 📌 94. Delay Function Using Promise
```javascript
function delay(ms){
    return new Promise((resolve)=> setTimeout(resolve, ms))
}

async function run(){
    console.log("start")
    await delay(2000)
    console.log("Executed after 2 seconds!");
}
run()
```

## 📌 95. Transform Nested User Data
```javascript
let obj = { 
  name: "Monu", 
  details: { age: 25, city: "Delhi" } 
}

output:
{
  name: "Monu",
  age: 25,
  city: "Delhi"
}

function unmergeObj(obj) {
  let result = {}

  for (let key in obj) {
    if (typeof obj[key] === "object" && obj[key] !== null) {
      Object.assign(result, unmergeObj(obj[key]))
    } else {
      result[key] = obj[key]
    }
  }
  return result
}
console.log(unmergeObj(obj))
```
## 📌 95. Merge Users and Orders by ID
```javascript
users = [{id:1,name:"Monu"},{id:2,name:"Daksh"}]
orders = [{userId:1,product:"Laptop"},{userId:2,product:"Phone"}]

Output:
[
  {id:1,name:"Monu",product:"Laptop"},
  {id:2,name:"Daksh",product:"Phone"}
]

function mergeArrs(arr1, arr2){
    return arr1.reduce((acc, obj)=>{
        let matched = arr2.find((_obj) => _obj.userId === obj.id)
        if(matched){
            acc.push({...obj, product: matched.product})
        }
        return acc
    }, [])
}
console.log(mergeArrs(users, orders))
```
## 📌 96. Replace All Nested String Values
```javascript

let obj ={
  name: "monu",
  details: { city: "delhi", country: "india" }
}

Output:
{
  name: "MONU",
  details: { city: "DELHI", country: "INDIA" }
}

function modifiedObj(obj){
    let result = {}
    for(let key in obj){
        if(typeof obj[key] === "object" && obj[key] !== null){
            result[key] = modifiedObj(obj[key])
        }else{
            result[key] = obj[key].toUpperCase()
        }
    }
    return result
    
}
console.log(modifiedObj(obj))
```
## 📌 97. Modify Data & Keep Latest Timestamp
```javascript
let arr =[
  { user:"A", login:"10:00" },
  { user:"A", login:"10:10" },
  { user:"B", login:"09:00" }
]

// Output:
// [
//   { user:"A", login:"10:10" },
//   { user:"B", login:"09:00" }
// ]

function updateLatest(arr){
    return arr.reduce((acc, obj)=>{
        let existingIndex = acc.findIndex((o)=> o.user === obj.user)
        if(existingIndex !== -1){
            acc[existingIndex] = obj
        }else{
            acc.push(obj)
        }
        return acc
    }, [])
    
}
console.log(updateLatest(arr))
```
## 📌 98. Remove Duplicate Objects Based on Key
```javascript
arr = [
  { id: 1, name: "A" },
  { id: 1, name: "X" },
  { id: 2, name: "B" }
]

output:
[
  { id: 1, name: "X" },
  { id: 2, name: "B" }
]

function removeDuplicate(arr){
    const map = new Map()
    for (let item of arr) {
        map.set(item.id, item)
    }
    return [...map.values()]
}
```
## 📌 99. Insert Element After Every Nth Index
```javascript
let arr = [1,2,3,4,5,6]
let item = "X"
let n = 2

output: 
// [1,2,"X",3,4,"X",5,6]

function insertAfterEveryN(arr, item, n){
    let result = []
    let count = 0
    
    for(let num of arr){
        result.push(num)
        count++
        if(count === n){
            result.push(item)
            count =0
        }
    }
    return result
}
console.log(insertAfterEveryN(arr, item, n))
```
## 📌 100. Add Missing Keys to Objects
```javascript
arr = [{ name: "A" }, { name: "B", age: 20 }]
defaultKeys = { age: 0 }

output:
[{ name: "A", age: 0 }, { name: "B", age: 20 }]



function addMissingKeys(arr, defaultKeys){
    return arr.reduce((acc, item) => {
        let missingKey = Object.keys(defaultKeys)[0];
        if (!(missingKey in item)) {
            acc.push({ ...item, ...defaultKeys });
        } else {
            acc.push(item);
        }
        return acc;
    }, []);
}
```
## 📌 101. Replace Duplicate Characters with Count
```javascript

let str = "banana"
//"b1a3n2"

function countChars(str){
    let map = {}
    let result = ""
    
    for(let char of str){
        map[char] = (map[char] || 0) +1
    }
    
    let newSet = new Set()
    for(let char of str){
        if(!newSet.has(char)){
            result += char + map[char]
            newSet.add(char)
        }
    }
    return result
}
console.log(countChars(str))
```
## 📌 102. Swap every two characters
```javascript

let str = "abcdef"
// Output: "badcfe"

function swapTwoChar(str){
    let result = ""
    
    for(let i =0; i < str.length; i+=2){
        let first = str[i]
        let second = str[i+1]
        
        if(second !== undefined){
            result += second + first
        }else{
            result += first
        }
    }
    
    return result
}

console.log(swapTwoChar(str))
```
## 📌 103. Merge employee + department + salary records
```javascript
let emp = [{id:1,name:"A"}]
let dept = [{id:1,dept:"IT"}]
let sal = [{id:1,salary:50000}]

output:-
//[{id:1,name:"A",dept:"IT",salary:50000}]

function mergeArr(arr1, arr2, arr3){
    return arr1.reduce((acc, curr)=>{
        let d = arr2.find((_d)=> _d.id === curr.id)
        let s = arr3.find((_s)=> _s.id === curr.id)
        
        acc.push({
            ...curr,
            ...d,
            ...s
        })
        return acc
        
    }, [])
}

console.log(mergeArr(emp, dept, sal))
```
## 📌 104. Flatten nested categories
```javascript

let arr = [{id:1,children:[{id:2},{id:3}]}]

output:
// [1, 2, 3]

function flattenArr(arr){
    return arr.reduce((acc, curr)=>{
         acc.push(curr.id)
         if(Array.isArray(curr.children)){
            acc.push(... flattenArr(curr.children))
         }
         return acc
    }, [])
}
console.log(flattenArr(arr))
```
## 📌 105. Find placeholder and replace
```javascript

let template = "Hi {{name}}, your score is {{score}}"
let data = {name:"Monu",score:90}

output:
//"Hi Monu, your score is 90"

function replacePlaceHolderWithValue(str, obj){
    for(let key in obj){
        let placeholder = `{{${key}}}`
        str = str.replace(placeholder, obj[key])
    }
    return str
}
console.log(replacePlaceHolderWithValue(template, data))
```
## 📌 106. Create Groups of Consecutive Numbers
```javascript

let arr = [1,2,3,7,8,10,11,12]
// Output: [[1,2,3],[7,8],[10,11,12]]

function groupConsecutiveArr(arr){
    let subArr = [arr[0]]
    let result = []
    
    for(let i=1; i <= arr.length-1; i++){
        if(arr[i] - arr[i -1] === 1){
             subArr.push(arr[i])
        }else{
             result.push(subArr)
             subArr =[ arr[i]]
        }
    }
    
    result.push(subArr)
    return result
    
}
console.log(groupConsecutiveArr(arr))
```
## 📌 107. Highlight Changed Keys (Diff Two Objects)
```javascript

let old = {a:1, b:2, c:3};
let updated = {a:1, b:5, d:10}

// Output:
// {changed:["b"], removed:["c"], added:["d"]}

function checkDiff(obj1, obj2){
    let result = {
        changed:[],
        removed:[],
        added:[]
    }
    
    for(let key in obj1){
        if(!(key in obj2)){
            result.removed.push(key)
        }else if(obj1[key] !== obj2[key]){
            result.changed.push(key)
        }
    }
    
    for(let key in obj2){
        if(!(key in obj1)){
            result.added.push(key)
        }
    }
    return result
}
console.log(checkDiff(old, updated))
```
## 📌 108. Rename Keys Based on Mapping
```javascript

let obj = {fname:"Monu", age:25}
let mapping = {fname:"firstName"}
// Output: {firstName:"Monu", age:25}


function mapObj(obj1, obj2){
    let result = {}
    
    for(let key in obj1){
        if(obj2.hasOwnProperty(key)){
            result[obj2[key]] = obj1[key]
        }else{
            result[key] = obj1[key]
        }
    }
    return result
}
console.log(mapObj(obj, mapping))
```
## 📌 109. Swap First and Last Letter of Every Word
```javascript
let str = "coding is fun"
// Output: "goding si nuf"


function swapfirstTwoLetters(str){
    let splitStr = str.split(" ")
    let result = []
    
    for(let word of splitStr){
        let first = word[0]
        let last = word[word.length -1]
        let middle = word.slice(1, -1)
       result.push(last + middle + first)
    }
    return result.join(" ")
}
console.log(swapfirstTwoLetters(str))
```
## 📌 110. Interleave Two Strings Character-Wise
```javascript
let str1 = "abc"
let str2 = "XYZ"
// Output: "aXbYcZ"

function interleaveTwoString{
    let i =0
    let j =0
    
    let result = ""
    
    while(i < str1.length || j < str2.length){
        if( i < str1.length){
            result += str1[i++]
        }
        
        if(j < str2.length){
            result += str2[j++]
        }
    }
    return result
}
console.log(interleaveTwoString(str1, str2))
```
## 📌 111. Extract Characters Between Two Symbols
```javascript
let str = "start[hello]end"
// Output: "hello"

function extractStr(str){
    let startIndex = str.indexOf("[")
    let endIndex = str.indexOf("]")
    return str.slice(startIndex+1, endIndex)
}
console.log(extractStr(str))
```
## 📌 112. Create Frequency String (sorted alphabetically)
```javascript
let str = "babaac"
// Output: "a3b2c1"

function sortAlphabetically(str){
    let freq = {} // { b: 2, a: 3, c: 1 }
    
    for(let char of str){
        freq[char] = (freq[char] || 0) +1
    }
     let result = Object.keys(freq).sort().map((key)=> key + freq[key]).join("")
     return result
}
console.log(sortAlphabetically(str))
```
## 📌 113. Capitalize Every Character After Special Symbol
```javascript
let str = "hello#world$monu"
// Output: "hello#World$Monu"

function capEveryCharAfterSymbol(str){
    let result = ""
    let shouldCap = false
    
    for(let i =0; i < str.length; i++){
        char = str[i]
        
        let isLetter = (char >= "a" && char <= "z" || char >= "A" && char <= "Z")
        
        if(!isLetter){
            result += char
            shouldCap = true
        }else if(shouldCap){
            result += char.toUpperCase()
            shouldCap = false
        }else{
            result += char.toLowerCase()
        }
    }
    return result
    
}
console.log(capEveryCharAfterSymbol(str))
```
## 📌 113. Find First Word With Unique Characters
```javascript
let str = "apple car moon ball"
// Output: "car"


function findFirstWordWithUniqueChar(str){
    let words = str.split(" ")
    
    for(let word of words){
        let freq = {}
        let unique = true
        
        for(let char of word){
            freq[char] = (freq[char] || 0) +1
            if(freq[char] > 1){
                unique = false
                break 
            }
        }
        if(unique) return word
    }
    return ""
}

console.log(findFirstWordWithUniqueChar(str))
```
## 📌 114. Move All Increasing Pairs Before Decreasing Ones
```javascript

let arr = [4, 1, 5, 2, 9, 7]
// Pairs: (4>1)=dec, (1<5)=inc, (5>2)=dec, (2<9)=inc, (9>7)=dec
// Expected Output: inc pairs first → [1,5,2,9,4,1,5,2,9,7]

function increasingOrder(arr){
    let inc = []
    let dec = []
    
    for(let i=0; i < arr.length; i++){
        let a = arr[i]
        let b = arr[i+1]
        
        if(a < b){
            inc.push(a, b)
        }else if(a > b){
            dec.push(a, b)
        }
    }
    return [...inc, ...dec]
}
console.log(increasingOrder(arr))
```
## 📌 115. Reverse Only Elements at Odd Indexes
```javascript
let arr = [10,20,30,40,50,60]
// Odd indexes → 20,40,60
// Expected Output: [10,60,30,40,50,20]

function reverseOddIndex(arr){
    let odds = []
    
    for(let i =0; i < arr.length; i++){
        if(i % 2 !==0){
            odds.push(arr[i])
        }
    }
    
    odds.reverse()
    
    let idx = 0
    
    for(let i =0; i < arr.length; i++){
         if(i % 2 !== 0){
             arr[i] = odds[idx++]
         }
    }
    return arr
}
console.log(reverseOddIndex(arr))
```
## 📌 116. Replace digits with
```
javascript
let str ="a1b2c3"

// Output: "a#b#c#"

function replaceDigits(str){
    return str.split("").reduce((acc, val)=> {
          if(!isNaN(val)){
              acc += "#"
          }else{
              acc += val
          }
        return acc
        
    }, "")
}
console.log(replaceDigits(str))
```
## 📌 117. Sum numbers in string
```
javascript

let str ="ab12cd3"
// Output:15

function sumNumbersInString(str){
    let sum = 0
    let temp = ""
    
    for(let char of str){
        if(!isNaN(char)){
            temp+= char
        }else{
            sum += Number(temp)
            temp=""
        }
    }
    return sum + Number(temp)
}
console.log(sumNumbersInString(str))
```




