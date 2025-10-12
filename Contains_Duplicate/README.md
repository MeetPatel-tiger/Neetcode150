# 🧠 NeetCode 150 – Contains Duplicate  
 **LeetCode #217** | Difficulty: 🟢 Easy  
 **Topics:** Arrays | Hashing | Sorting  

---

## Problem Statement  
Given an integer array nums, return **true** if any value appears **at least twice** in the array,  
and **false** if every element is distinct.

---
## Clarifying Questions
Before writing code, I asked:
1. What is the range of input size?
2. Can numbers be negative?
3. Should we change the input array or leave it as is?
4. What should we return if the array is empty or has only one number?

I like to solve this problems as if I am in an interview.

---

## Intuition
We only need to check if a value shows up more than once.  
A set is perfect for this because it lets you fast lookups and stores only unique items.  
If we ever find a number that already exists in the set, we can return True.  
If we finish the loop without finding duplicates, return False.

---

## Approach 1: Using a Set 
1. Create an empty set called seen.
2. Loop through each number in nums.
3. If the number is already in seen, return True.
4. Otherwise, add it to seen.
5. If you finish looping without finding a duplicate, return False.

### Time Complexity
O(n)  
We check each number once.

### Space Complexity
O(n)  
In the worst case, the set stores every number.

### Python Code
```python

def containsDuplicate(nums: List[int]) -> bool:
    seen = set()
    for x in nums:
        if x in seen:
            return True
        seen.add(x)
    return False
