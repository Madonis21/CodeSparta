```
Interview Questions


Num of island problem

DFS

grid = [
  [1,1,0,0,0],
  [1,1,0,0,0],
  [0,0,1,0,0],
  [0,0,0,1,1]
]

def numIslands(grid):
    rows = len(grid)
    cols = len(grid[0])

    def traverse(grid, i, j):
        if (i < 0 or j < 0 or i > rows - 1 or j > cols -1):
            return
        if grid[i][j] == 1:
            grid[i][j] = 0

    numOfIslands = 0
    for i in range(0, rows - 1):
        for j in range(0, cols - 1):
            if grid[i][j] == 1:
                numOfIslands += 1
                grid[i][j] = 0
                traverse(grid, i + 1, j)
                traverse(grid, i - 1, j)
                traverse(grid, i, j - 1)
                traverse(grid, i, j + 1)
    
    return numOfIslands


Flood Fill
BFS


image = [
  [1,1,1],
  [1,1,0],
  [1,0,1]
]
sr = 1
sc = 1
newColor = 2


[
  [2,2,2],
  [2,2,0],
  [2,0,1]
]

from collections import deque

def flood_fill(image, sr, sc):

    row_len = len(image)
    # 3
    col_len = len(image[0])

    directions = [(1, 0), (0, 1), (-1 , 0), (0, -1)]

    queue = deque()
    queue.append((sr, sc))
    # queue = [(1,1)]
    while queue:
        row, col = queue.popleft() # 1,1
        for dr, dc in directions:
            #1, 0
            if row + dr >= 0 and row + dr < row_len and col + dc >=0 and col + dc < col_len:
                if image[row + dr][col + dc] == 1:
                    queue.append((row + dr, col + dc))
                    image[row + dr][col + dc] = 2




    return image

print(flood_fill(image, sr, sc))
