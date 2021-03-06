# 63. Unique Paths II

A robot is located at the top-left corner of a `m x n` grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and space is marked as `1` and `0` respectively in the grid.

## Example 1:
![robot1.jpg](/src/robot1.jpg)
```
Input: obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
Output: 2
Explanation: There is one obstacle in the middle of the 3x3 grid above.
There are two ways to reach the bottom-right corner:
1. Right -> Right -> Down -> Down
2. Down -> Down -> Right -> Right
```

## Example 2:
![robot2.jpg](/src/robot2.jpg)
```
Input: obstacleGrid = [[0,1],[0,0]]
Output: 1
```

## Constraints:
- `m == obstacleGrid.length`
- `n == obstacleGrid[i].length`
- `1 <= m, n <= 100`
- `obstacleGrid[i][j]` is `0` or `1`.

# Solution
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        if obstacleGrid[0][0] == 1:
            return 0
        obstacleGrid[0][0] = -1
        n, m = len(obstacleGrid), len(obstacleGrid[0])
        for j in range(1, m):
            if obstacleGrid[0][j] == 1:
                break
            obstacleGrid[0][j] = -1
        for i in range(1, n):
            if obstacleGrid[i][0] == 1:
                break
            obstacleGrid[i][0] = -1
        for i in range(1, n):
            for j in range(1, m):
                if obstacleGrid[i][j] != 1:
                    if obstacleGrid[i-1][j] != 1 and obstacleGrid[i][j-1] != 1:
                        obstacleGrid[i][j] = obstacleGrid[i-1][j] + obstacleGrid[i][j-1]
                    elif obstacleGrid[i-1][j] == 1:
                        obstacleGrid[i][j] = obstacleGrid[i][j-1]
                    elif obstacleGrid[i][j-1] == 1:
                        obstacleGrid[i][j] = obstacleGrid[i-1][j]
        return -obstacleGrid[n-1][m-1] if obstacleGrid[n-1][m-1] != 1 else 0
```
Simple Dynamic Programming.
