# 1502. Can Make Arithmetic Progression From Sequence

**Problem**  
A sequence of numbers is called an arithmetic progression if the difference between any two consecutive elements is the same.

Given an array of numbers `arr`, return `true` *if the array can be rearranged to form an **arithmetic progression**. Otherwise, return* `false`.

**Example**

```text
Input: arr = [3,5,1]
Output: true
Explanation: We can reorder the elements as [1,3,5] or [5,3,1] with differences 2 and -2 respectively, between each consecutive elements.

Input: arr = [1,2,4]
Output: false
Explanation: There is no way to reorder the elements to obtain an arithmetic progression.
```

**Constraints:**
*   2 <= arr.length <= 1000
*   -106 <= arr[i] <= 106

**My Understanding**

**Solution**
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
Time Complexity: $O(N log N)$
Space Complexity: $O(N)$
--
# 2485. Find the Pivot Integer

**Problem**  
Given a positive integer `n`, find the **pivot integer** `x` such that:

The sum of all elements between `1` and `x` inclusively equals the sum of all elements between `x` and `n` inclusively.

Return *the pivot integer* `x`. If no such integer exists, return `-1`. It is guaranteed that there will be at most one pivot index for the given input.

**Example**

```text
Input: n = 8
Output: 6
Explanation: 6 is the pivot integer since: 1 + 2 + 3 + 4 + 5 + 6 = 21 and 6 + 7 + 8 = 21.

Input: n = 1
Output: 1
Explanation: 1 is the pivot integer since: 1 = 1.

Input: n = 4
Output: -1
Explanation: It can be proved that no such integer exist.
```

**Constraints:**
*   1 <= n <= 1000


**My Understanding**

**Solution**

```python
class Solution:
    def pivotInteger(self, n: int) -> int:
        num = (n * n + n) / 2  # 这里得到的是 float
        x = num ** 0.5      # 或者 math.sqrt(num)

        if x.is_integer():
            return int(x)
        else:
            return -1
        # return int(x) if x.is_integer() else -1
```

**Note**
Time Complexity: $O(1)$
Space Complexity: $O(1)$
--
# 9. Palindrome Number

**Problem**  
Given an integer `x`, return `true` *if `x` is a **palindrome**, and `false` otherwise*.

An integer is a **palindrome** when it reads the same forward and backward.
*   For example, `121` is a palindrome while `123` is not.

**Example**

```text
Input: x = 121
Output: true

Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

**Constraints:**
*   -231 <= x <= 231 - 1
**My Understanding**

**Solution**

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False

        if x<=9:
            return True
        
        original = x
        reversed_num = 0
        
        while x > 0:
            digit = x % 10
            reversed_num = reversed_num * 10 + digit # * 10 就是十进制世界里的“左移操作”
            x = x // 10 #向右移了一位
            
        return original == reversed_num
        # s = str(x)
        # left = 0 
        # right = len(s)-1
        # while left<right:
        #     if s[left]!=s[right]:
        #         return False
        #     else:
        #         left+=1
        #         right-=1
        # return True

        # s = str(x)
        # # s[::-1] 会创建一个倒序的新字符串
        # return s == s[::-1]
```

**Note**
Solution1: 
Time Complexity: $O(\log_{10} x)$
Space Complexity: $O(1)$
Solution2:
Time Complexity: $O(\log_{10} x)$
Space Complexity: $O(\log_{10} x)$
--

