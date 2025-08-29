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
## 📌 5. Mirror Words

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


