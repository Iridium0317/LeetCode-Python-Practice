# LeetCode Python Practice

![Language](https://img.shields.io/badge/Language-Python3-blue)
![Status](https://img.shields.io/badge/Status-Active-success)

This repository serves as a coding journal and a sandbox for my daily algorithmic practice, random picks, and contest problems.

> **Note**: This is a supplementary repo for experimental solutions. My structured study plans (e.g., LeetCode 75) are maintained in a separate repository.

## Tech Stack & Focus
- **Language**: Python 3 (Transitioning from C++/C)
- **Focus**: Pythonic implementation, Standard Library mastery, and Code Readability.
- **Tools**: VS Code with LeetCode extension.

## Study Methodology: Spaced Repetition

My workflow involves two stages:

1.  Implementation (Phase 1): 
    - Focus on solving the problem and passing test cases.
    - Initial commit with a working solution.
    
2.  Retrospection (Phase 2): 
    - Revisit the solution after a few days.
    - Write Takeaways and complexity analysis in the file's docstrings.
    - Refactor code to be more "Pythonic" or optimize time/space complexity.

## Progress Tracker (Notable Problems)

| ID | Problem | Diff | Code | Takeaways|
| :---: | :--- | :---: | :---: | :--- |
| 0001 | [Two Sum](https://leetcode.com/problems/two-sum/) |   |  |   |
| 0020 | [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) |   |   |   |
| ... | ... | ... | ... | ... |


## Style Guide (PEP 8)
- Select clear and descriptive names for your variables and functions. This makes it easier for you and others to quickly grasp the functionality of your program.
- Use snake_case for variable and function names
- Separate function definitions with two blank lines to clearly distinguish between them.
- Add a signle blank line between logical sections within a functiohn to group related lines of code together.
- 变量定义 和 后续逻辑 之间空一行。
- 预处理（Edge cases check） 和 主逻辑 之间空一行。
- 核心算法（比如 while/for 循环） 结束后，和 return 语句 之间空一行。
```python
def solve_problem(nums, target):
    if not nums:
        return []

    result = []
    seen = set()

    for x in nums:
        complement = target - x
        if complement in seen: 
            result.append((x, complement))
        seen.add(x)

    result.sort()
    return result
```
- if x is not None 写 if x == None: 虽然也能跑，但在面试中会被认为“不地道”。
- 逗号后面要加空格 ✅ nums = [1, 2, 3]
- 专业写法：
```python
for i, num in enumerate(nums):
    print(i, num)

# 做反转链表、排序或者数组内部交换元素时，千万别像 Java/C 那样搞个 temp 变量
nums[i], nums[j] = nums[j], nums[i]

# 空的容器（list, dict, string）和数字 0 都会自动被视为 False。不需要显式去比大小。
# 应用场景： 所有的栈 (Stack)、队列 (Queue)、数组判空逻辑。
# ❌
if len(stack) > 0:
    # do something
if len(nums) == 0:
    return
# ✅
if stack:  # 只要 stack 里有东西，就是 True
    # do something

if not nums: # 只要 nums 是空的，就是 True
    return

# 创建一个 rows * cols 的全 0 矩阵，只要一行
# 这里用 _ 表示“我不关心这个循环变量叫什么”，这也是一个很好的编码习惯。当这个i没有实际意义的时候
rows, cols = 3, 4
grid = [[0] * cols for _ in range(rows)]

# 当这个i没有实际意义的时候
x, _ = get_point()
# 意思就是：第一个值给 x，第二个值丢垃圾桶，我不关心
print(x)

# 同时遍历两个数组
for val1, val2 in zip(list1, list2):

```

## Study Notes:
- 必须用 for 循环, 当你明确知道要循环多少次，或者要遍历一个容器（数组、字符串、链表）时。
- 必须用 while 循环, 当你不知道要循环多少次，只知道停止条件时。
- Nonetype: x = None. The **None** value can serve as a sort of placeholder for when we need to create a variable before we know what value it needs to have. 先挖个坑，之后再填上


<img width="1566" height="999" alt="image" src="https://github.com/user-attachments/assets/9a42679f-04fa-4352-a52f-b8f702589328" />


### String
- isupper(), islower(), isdigit() # 全为数字, s.lower() #全变小写, s.upper(), s.strip() #去除前后空格, s.lstrip #去除左边空格, s.rstrip(), swapcase() #大写变小写，小写变大写, replace(old, new) # s.replace("l","E"), split()
```python
s = "Hello World"
len()
s.count("H") #1
isupper()
islower
```

### Array
- 用index读非常快，查询、插入、删除非常慢，连续存储
<img width="1618" height="1000" alt="image" src="https://github.com/user-attachments/assets/6a326f11-e2a4-461b-b4ef-9413f74e653d" />

### LinkedList
<img width="1922" height="1000" alt="image" src="https://github.com/user-attachments/assets/bcd711d2-1213-4e49-ac78-7fbdaa823a79" />

### List 数据类型：
A list might have an int, float, str, or even another list inside of it. int, float and str are immutable.
1. name_of_list = [initial_value] * size  2. name_of_list = [] #define an empty list
2. name_of_list.append(), name_of_list.remove() #只删除一次, x = name_of_list.pop() #删除最后一个元素并返回  name_of_list.pop(index)
3. list1.extend(list2) #把list2加到list1里     combined = list1 + list2
4. idx = name_of_list.index(element) #返回第一个element的index
5. name_of_list.insert(index, element)
6. max(name_of_list, min(name_of_list), sum(name_of_list), name_of_list.reverse(), name_of_list.clear() name_of_list[start:end]
7. b = [Expression for x in list]   b = [ExpressionA if Condition else ExpressionB for x in List]  b = [Expression for x in List if Condition] #遍历 list，只有满足条件的 x 才会被处理并塞进新列表。不满足的直接丢掉
 

### Dictionary
- 数据类型：name_of_dict = {key1:value1,} 无序， Key必须唯一且不可变。 快速查找、映射、计数
- 1. for key in dict.keys(): 2. for value in name_of_dict.values(): 3. for key, value in dict.items(): 4. dict.pop(key) #删除的是pair, dict.clear()  len(dict)   del dict[key] # 删除pair 但是不返回值
- 1. keys must be immutable types; Values can be mutable or immutable
  2. empty_dict = {}
  3. final_grades = {} final_grades.[key1] = value1 
  4. visited = {} #这是空字典 visited = set() #这是空集合
  5. Nested Dict：处理复杂数据结构、图论（Graph）和树（Tree）的高频工具
```python
from collections import defaultdict

# 定义一个无限套娃的字典（树状结构）
def recursive_dict():
    return defaultdict(recursive_dict)

tree = recursive_dict()

# 不需要初始化！直接赋值！
tree['user1']['address']['city'] = 'LA'
tree['user1']['score'] = 100

print(tree['user1']['address']['city']) # 输出 LA
```
  6. .get()：“如果找不到这个 Key，别返回 None，给我返回一个 0 (或者其他默认值)。”  count = my_dict.get(key, 0)
    <img width="602" height="407" alt="image" src="https://github.com/user-attachments/assets/9c5d1436-3d96-4ef9-83be-57e5bb45cf83" />

### Tuple () 
- 有序，不可变，存储不希望被修改的数据。 len(), max(), min()
- 可哈希 可以作为 字典的 Key 或者 集合 的元素，场景：DFS/BFS 记录坐标 visited.add((x, y))，DP 记忆化 memo[(i, j)]。
- 可以直接把 Tuple 里的值赋给多个变量。 场景： 坐标处理、交换数值。
```python
point = (3, 5)
x, y = point
```
- 定义只有一个元素的 Tuple，必须加逗号，否则是 int/str。


### Set：
- {1, "a", 2}或set() 无序，元素唯一且不可变。去重，判断元素是否存在
- .add(), .remove(), len(), max(), min()
- 1. 交集 set1 & set2 2. 并集 set1 | set2 3. 差集 set1 - set2 4. 对称差集 set1 /\ set2 两个集合中不共有的元素

### Hash Map
- search、insert、delete快，没法通过索引访问
- set 用来去重和找不同：s = set(nums) #把nums里的重复元素去除了；x in s # 速度O（1）
- set的数学运算 1. 交集 set1 & set2 2. 并集 set1 | set2 3. 差集 set1 - set2
- Dictionary 用来查找 谁 在哪里
- Counter 统计 出现次数
```python
from collections import Counter
nums = [1, 2, 2, 3, 3, 3]
counts = Counter(nums) 
```

### Queued 队列
- FIFO
### Stack 栈
### Heap 堆
### Tree 树
---
*Created by Claire*
