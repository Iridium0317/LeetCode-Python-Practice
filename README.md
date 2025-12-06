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
for i, num in enumerate(nums): #适用于所有可迭代对象，
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
### 1. 列表 / 数组 (List) —— 最常用
| 函数/语法 | 用法示例 | 时间复杂度 | 面试场景 / 备注 |
| :--- | :--- | :--- | :--- |
| `sort()` | `nums.sort()` | $O(N \log N)$ | 原地排序，不返还新数组。改变原有的顺序。 |
| `sorted()` | `res = sorted(nums)` | $O(N \log N)$ | 返回新数组，原数组不变。 |
| `append()` | `stack.append(x)` | $O(1)$ | 栈顶入栈。 |
| `pop()` | `x = stack.pop()` | $O(1)$ | 栈顶出栈（删除最后一个）。 |
| 切片反转 | `nums[::-1]` | $O(N)$ | 快速反转数组或字符串。[start : stop : step] |
| 初始化 | `arr = [0] * n` | $O(N)$ | 初始化固定长度的数组（如 DP 数组）。 |
| 二维数组 | `[[0]*n for _ in range(m)]` | $O(M \cdot N)$ | 千万别写 `[[0]*n]*m` (那是浅拷贝 Bug)。 |

### 2. 字符串 (String) —— 不可变
| 函数/语法 | 用法示例 | 时间复杂度 | 面试场景 / 备注 |
| :--- | :--- | :--- | :--- |
| `join()` | `"".join(list)` | $O(N)$ | 将列表转为字符串。比 `+=` 快得多。 |
| `split()` | `s.split(" ")` | $O(N)$ | 将字符串按空格切成列表。 |
| `strip()` | `s.strip()` | $O(N)$ | 去除首尾空格。 |
| `isdigit()` | `char.isdigit()` | $O(1)$ | 判断是否为数字字符 '0'-'9'。 |
| `isalnum()` | `char.isalnum()` | $O(1)$ | 判断是否为字母或数字（验证回文串常用）。 |
| `ord()` | `ord('a')` -> 97 | $O(1)$ | 字符转 ASCII 码。 |
| `chr()` | `chr(97)` -> 'a' | $O(1)$ | ASCII 码转字符。 |

### 3. 字典 (Dict) & 集合 (Set) —— 哈希表
| 函数/语法 | 用法示例 | 时间复杂度 | 面试场景 / 备注 |
| :--- | :--- | :--- | :--- |
| `get()` | `d.get(key, 0)` | $O(1)$ | 安全取值。如果你不确定 key 存不存在，用这个。 |
| `keys()` | `d.keys()` | $O(N)$ | 获取所有键。 |
| `values()` | `d.values()` | $O(N)$ | 获取所有值。 |
| `items()` | `d.items()` | $O(N)$ | 同时获取键和值：`for k, v in d.items():` |
| `set()` | `s = set(nums)` | $O(N)$ | 数组去重 / 快速查找。 |
| `add()` | `s.add(x)` | $O(1)$ | 往集合里加元素。 |
| `x in s` | `if x in visited:` | $O(1)$ | 哈希查找核心。比 list 查找快得多。 |

### 4. 队列 & 堆 (Collections & Heapq) —— 需 import
| 模块 | 函数/语法 | 时间复杂度 | 面试场景 / 备注 |
| :--- | :--- | :--- | :--- |
| Deque | `q = deque()` | - | 双端队列，BFS 必备。 |
| | `q.append(x)` | $O(1)$ | 右进。 |
| | `q.popleft()` | $O(1)$ | 左出（千万别用 list 的 pop(0)）。 |
| Heapq | `heapify(list)` | $O(N)$ | 把乱序数组变成堆。 |
| | `heappush(h, x)` | $O(\log N)$ | 往堆里加元素。 |
| | `heappop(h)` | $O(\log N)$ | 弹出最小值。 |
| Counter | `Counter(nums)` | $O(N)$ | 词频统计神器。返回一个字典。 |
| Defaultdict| `d = defaultdict(int)` | $O(1)$ | 访问不存在的 key 不会报错，自动赋默认值 0。 |

### 5. 数学 & 循环 (Math & Loop)
| 函数/语法 | 用法示例 | 面试场景 / 备注 |
| :--- | :--- | :--- |
| 无穷大 | `float('inf')`, `float('-inf')` | 初始化最小值/最大值时用。 |
| 绝对值 | `abs(-5)` -> 5 | 碰撞问题、距离计算。 |
| 商和余 | `divmod(10, 3)` -> `(3, 1)` | 同时拿到商和余数。 |
| 带索引遍历 | `for i, x in enumerate(nums):` | 不要写 `range(len())` 了。 |
| 双数组遍历 | `for a, b in zip(list1, list2):` | 同时遍历两个数组。 |
| 倒序循环 | `range(n-1, -1, -1)` | 从后往前遍历（DP 或 栈题目常用）。 |

| 符号 | 例子 | 作用 |
| :--- | :--- | :--- |
| `//` 整除 (Floor Div) | `7 // 2 = 3` | 用于“砍掉尾巴”或“求行号”。 |
| `%` 取模 (Mod) | `7 % 2 = 1` | 取余数，用于“判断奇偶”、“循环下标”、“取个位数”。 |
| `divmod` 同时求 | `divmod(7, 2) = (3, 1)` | 两个一起求，写代码更简洁。 |
- 必须用 for 循环, 当你明确知道要循环多少次，或者要遍历一个容器（数组、字符串、链表）时。
- 必须用 while 循环, 当你不知道要循环多少次，只知道停止条件时。
- Nonetype: x = None. The **None** value can serve as a sort of placeholder for when we need to create a variable before we know what value it needs to have. 先挖个坑，之后再填上


<img width="1566" height="999" alt="image" src="https://github.com/user-attachments/assets/9a42679f-04fa-4352-a52f-b8f702589328" />

### 常用的函数
### String
- isupper(), islower(), isdigit() # 全为数字, s.lower() #全变小写, s.upper(), s.strip() #去除前后空格, s.lstrip #去除左边空格, s.rstrip(), swapcase() #大写变小写，小写变大写, replace(old, new) # s.replace("l","E"), split()
```python
s = "Hello World"
len()
s.count("H") #1
isupper()
islower()
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
数据类型：name_of_dict = {key1:value1,} 无序， Key必须唯一且不可变。 快速查找、映射、计数
1. for key in dict.keys(): 2. for value in name_of_dict.values(): 3. for key, value in dict.items(): 4. dict.pop(key) #删除的是pair, dict.clear()  len(dict)   del dict[key] # 删除pair 但是不返回值

   
1. keys must be immutable types; Values can be mutable or immutable
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
- 1. 交集 set1 & set2    2. 并集 set1 | set2     3. 差集 set1 - set2     4. 对称差集 set1 /\ set2 两个集合中不共有的元素

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

### Queued 队列 -> BFS 
- FIFO 先进先出， 双端队列：两边都可进/出
- <img width="4000" height="873" alt="image" src="https://github.com/user-attachments/assets/766f4266-1c1c-408b-ba4f-a3f063936d8c" />
- List 需要移动整个数组，增加或删除会比较慢 !!!严禁使用 list 配合 pop(0)
    - list.pop(0) 的时间复杂度是 O(N)

- deque 双端 增加或删除非常快 max(q) #O(N), min(q) #O(N), len(q) #O(1)
    - deque.popleft() 的时间复杂度是 O(1)
    - from collections import deque,
    - 先进先出 搭配使用 append(), popleft() 进队：q.append(x) 出队：val = q.popleft()  或 appendleft(), pop()
    - BFS模板： queue = collections.deque([root])
    - 如果需要在队列/栈中频繁获取最大/最小值，不能直接用 max() 函数


### Stack 栈 ->DFS
- FILO 先进后出
- 一般使用List .append(), .pop(), max() min() len()
    - 进栈：stack.append(x)
    - 出栈：val = stack.pop()
    - 查看栈顶（栈里面的最后一个元素）：stack[-1]

### Heap 堆
大堆 Max Heap（最顶端的是最大值），小堆 Min Heap（最顶端的是最小值）
前k个最大/小值

- from heapq import heapify, heappush, heappop
- heapify() #默认返回小堆 O(N)， heappush() #O(logN), heappop() #O(logN), nlargest() #前n个最大的值 O(NlogK), nsmallest()
- 
```python
a = [1, 2, 3]
heapify(a) #小堆
heappush(a, 4) #[1, 2, 3, 4]
heappop(a) #1 [2, 3, 4]
nlargest(2,a) # [4, 3]
nsmallest(2,a) # [2, 3]

Python 没有大顶堆。必须把数字取反 (乘 -1) 存进去，取出来的时候再乘 -1 变回来
import heapq
# 想要大顶堆存 [1, 5, 3]
max_heap = []
heapq.heappush(max_heap, -1)
heapq.heappush(max_heap, -5)
heapq.heappush(max_heap, -3)

# 现在的堆是 [-5, -3, -1] (实际上是小顶堆，但绝对值最大的是5)
# 取出最大值：
val = -heapq.heappop(max_heap) # 取出 -5，变回 5
print(val)
```
### Tree 树 -> BFS, DFS, BST - Binary Search Tree
- 重要概念：节点、根节点、叶子节点，
    - 高度Height：该节点到叶子节点的最长路径 常用 后序遍历 Bottom-Up 拿到左右孩子高度，取 max(left, right) + 1，等左右孩子都算完了（左右），最后才能算你自己（中）
      ```python
      def get_height(node):
        if not node: return 0
        
        # 1. 先去问左孩子 (左)
        left_height = get_height(node.left)
        
        # 2. 再去问右孩子 (右)
        right_height = get_height(node.right)
        
        # 3. 最后算我自己 (中)
        # 我自己的高度 = 最高的那个孩子 + 我自己这1层
        return max(left_height, right_height) + 1
      ```
    - 深度Depth：从根节点到该节点的边数 常用 前序遍历 Top-Down (往下传参数 depth + 1)
      ```python
        # 这里的 depth 是父节点传给我的
        def get_depth(node, current_depth):
            if not node: return
            
            # 1. 先处理自己（比如打印：我是第几层）
            print(f"节点 {node.val} 的深度是 {current_depth}")
            
            # 2. 再往下传 (depth + 1)
            get_depth(node.left, current_depth + 1)
            get_depth(node.right, current_depth + 1)
      ```
  <img width="703" height="126" alt="image" src="https://github.com/user-attachments/assets/8926f8f1-a2a9-4ca2-a7e1-84a7e0a30d69" />

    - 层：
    - 树的高度：根节点的高度
- 二叉树：每个节点最多有两个叉
    - 满二叉树(perfect binary tree)：除了叶子节点，每个节点都有左右两个子节点，节点总数一定是2^k - 1
    - 完全二叉树（complete binary tree): 上满下左，适合用数组/堆存储，下标关系 left = 2*i + 1, right = 2*i + 2
- 二叉树的遍历：指的是根节点的处理时机
- 二叉搜索树 (BST):  左 < 根 < 右。中序遍历 = 有序数组。
  <img width="3161" height="1000" alt="image" src="https://github.com/user-attachments/assets/aa95a7c7-7d06-4b14-ba1e-9941c6a29717" />

### 递归 vs 迭代 (Recursion vs Iteration) 
#### 递归 Recursion
```python
def dfs(node):
    if not node: return  # 终止条件 (底)
    
    # 逻辑处理...
    
    dfs(node.left)   # 甩锅给左边
    dfs(node.right)  # 甩锅给右边
```
- 很像数学归纳法
- 缺点 爆栈 (Stack Overflow)： 每次“甩锅”都要占用一点系统内存（系统栈）。如果层数太深（比如树有 10 万层），内存直接爆掉，程序崩溃。
#### 迭代 Iteration
```python
# 手动维护一个栈，不依赖系统
stack = [root] 
while stack:
    node = stack.pop()
    # 逻辑处理...
    if node.right: stack.append(node.right)
    if node.left:  stack.append(node.left)
```
- 使用循环 (for 或 while)，stack 或者queue
- 不会爆栈，但是容易出错
- 数列递推 / 累加
- 动态规划 (Tabulation): 其实就是 迭代 + 填表。
思维：从最小的基础（Base Case）开始，填好 dp[0]，然后填dp[1]，一直填到 dp[n]
。
---
*Created by Claire*
