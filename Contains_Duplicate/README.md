# 🧠 NeetCode 150 - Contains Duplicate  
 Difficulty: Easy  
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

I like to ask these questions as if I am in an interview.

---

## Intuition
Basically, We need to check if a number shows up more than once in a list. 
There are multiple ways to do this:
- **Brute Force:** Check every number against every other number.  
- **Sorting:** Sort the list and check if any two numbers next to each other are the same.  
- **Set:** Use a set to track what we have seen so far and check quickly if a number repeats.
---
# Approach 1: Nested Loops(Brute force)
### Steps
1. Loop through every element i in the array.  
2. For each i, loop through every element j that comes after it.  
3. If nums[i] equals nums[j], return True.  
4. If no pair matches, return False.

### Time Complexity
O(n^2)  
because we compare every pair of numbers.

### Space Complexity
O(1)  
Not using any extra data structure.

### Python Code
```python
def containsDuplicate_bruteforce(nums: List[int]) -> bool:
    for num_1 in range(len(nums)):
        for num_2 in range(num_1 + 1, len(nums)):
            if nums[num_1] == nums[num_2]:
                return True
    return False
```

## Approach 2: Sorting(Better than bruteforce) 
1. Sort the array.
2. Loop through the array.
3. if the current number and previous number are equal, return True.
4. Otherwise, False after checking all pairs.


### Time Complexity
O(n log n)  
Sorting takes longer than a set. 

### Space Complexity
O(1)  


### Python Code
```python

def containsDuplicate_sorting(nums: List[int]) -> bool:
    nums.sort()
    for i in range(1, len(nums)):
        if nums[i] == nums[i - 1]:
            return True
    return False

```

## Approach 3: Using a Set( Optimized) 
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
