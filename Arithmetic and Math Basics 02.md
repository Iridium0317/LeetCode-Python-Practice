# 263. 丑数 – Ugly Number

**Problem**  
An **ugly number** is a positive integer whose prime factors are limited to `2`, `3`, and `5`.

Given an integer `n`, return `true` *if* `n` *is an **ugly number***.

**Example**

```text
Input: n = 6
Output: true
Explanation: 6 = 2 × 3

Input: n = 1
Output: true
Explanation: 1 has no prime factors, therefore all of its prime factors are limited to 2, 3, and 5.

Input: n = 14
Output: false
Explanation: 14 is not ugly since it includes the prime factor 7.
```

**Constraints:**
*   -2^31 <= n <= 2^31 - 1

## My Understanding

### Solution
```python
class Solution:
    def canMakeArithmeticProgression(self, arr: List[int]) -> bool:
        arr.sort() #O(N log N)
        b = [] #O(N)
        for i in range(len(arr)-1): #O(N)
            b.append(arr[i+1]-arr[i])

        return max(b) ==min(b) #O(N) + O(N)

# class Solution:
#     def canMakeArithmeticProgression(self, arr: List[int]) -> bool:
#         arr.sort()
#         diff = arr[1] - arr[0]

#         for i in range(1, len(arr) - 1):
#             if arr[i+1] - arr[i] != diff:
#                 return False
                
#         return True            
```
**Note**

*   Time Complexity: $O(log N)$
*   Space Complexity: $O(1)$


---

# 1015. Smallest Integer Divisible by K

**Problem**  
Given a positive integer `k`, you need to find the length of the **smallest** positive integer `n` such that `n` is divisible by `k`, and `n` only contains the digit `1`.

Return *the length of* `n`. If there is no such `n`, return `-1`.

**Note:** `n` may not fit in a 64-bit signed integer.

**Example**

```text
Input: k = 1
Output: 1
Explanation: The smallest answer is n = 1, which has length 1.

Input: k = 2
Output: -1
Explanation: There is no such positive integer n divisible by 2.

Input: k = 3
Output: 3
Explanation: The smallest answer is n = 111, which has length 3.
```

**Constraints:**
*   1 <= k <= 10^5

## My Understanding

### Solution
```python
class Solution:
    def smallestRepunitDivByK(self, k: int) -> int:
        if k % 2 == 0 or k % 5 == 0:
            return -1
            
        remainder = 0
        
        for length in range(1, k + 1):
            remainder = (remainder * 10 + 1) % k
            if remainder == 0:
                return length
                
        return -1         
```
**Note**

*   Time Complexity: $O(K)$
*   Space Complexity: $O(1)$

