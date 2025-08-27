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

## 📌 Example Problem: Two Sum
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

