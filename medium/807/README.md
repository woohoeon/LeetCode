##  Max Increase to Keep City Skyline (도시 스카이 라인을 유지하기위한 최대 증가)

In a 2 dimensional array grid, each value grid[i][j] represents the height of a building located there. We are allowed to increase the height of any number of buildings, by any amount (the amounts can be different for different buildings). Height 0 is considered to be a building as well. 

At the end, the "skyline" when viewed from all four directions of the grid, i.e. top, bottom, left, and right, must be the same as the skyline of the original grid. A city's skyline is the outer contour of the rectangles formed by all the buildings when viewed from a distance. See the following example.

What is the maximum total sum that the height of the buildings can be increased?

2 차원 어레이 그리드에서, 각각의 값 그리드 [i] [j]는 그곳에 위치한 건물의 높이를 나타낸다. 우리는 건물 수에 관계없이 건물의 높이를 얼마든지 늘릴 수 있습니다 (건물마다 금액이 다를 수 있음). 높이 0도 건물로 간주됩니다.

마지막으로 그리드의 네 방향, 즉 위, 아래, 왼쪽 및 오른쪽에서 볼 때 "스카이 라인"은 원래 그리드의 스카이 라인과 같아야합니다. 도시의 스카이 라인은 멀리서 볼 때 모든 건물에 의해 형성된 사각형의 외부 윤곽입니다. 다음 예를 참조하십시오.

건물 높이를 늘릴 수있는 최대 총계는 얼마입니까?

```
Example:
Input: grid = [[3,0,8,4],[2,4,5,7],[9,2,6,3],[0,3,1,0]]
Output: 35
Explanation: 
The grid is:
[ [3, 0, 8, 4], 
  [2, 4, 5, 7],
  [9, 2, 6, 3],
  [0, 3, 1, 0] ]

The skyline viewed from top or bottom is: [9, 4, 8, 7]
The skyline viewed from left or right is: [8, 7, 9, 3]

The grid after increasing the height of buildings without affecting skylines is:

gridNew = [ [8, 4, 8, 7],
            [7, 4, 7, 7],
            [9, 4, 8, 7],
            [3, 3, 3, 3] ]
```

Solution: 

```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var maxIncreaseKeepingSkyline = function(grid) {
  const top = []
  const left = []
  
  grid.map((row, i) => {
    row.map((cell, ci) => {
      if (top[ci] === undefined || top[ci] < cell) {
        top[ci] = cell
      }
      if (left[i] === undefined || left[i] < cell) {
        left[i] = cell
      }
    })
  })

  let count = 0
  
  grid.map((row, i) => {
    row.map((cell, ci) => {
      if (top[ci] > cell && left[i] > cell) {
        if (top[ci] > left[i]) {
          count += (left[i] - cell)
        } else {
          count += (top[ci] - cell)
        }
      }
    })
  })
  
  return count
};
```
