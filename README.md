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


## Style Guide
- Select clear and descriptive names for your variables and functions. This makes it easier for you and others to quickly grasp the functionality of your program.
- Use snake_case for variable and function names
- Separate function definitions with two blank lines to clearly distinguish between them.
- Add a signle blank line between logical sections within a functiohn to group related lines of code together.

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
---
*Created by Claire*
