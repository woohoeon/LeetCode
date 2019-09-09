## Non-decreasing Array (감소하지 않는 Array)

Given an array with n integers, your task is to check if it could become non-decreasing by modifying at most 1 element.

We define an array is non-decreasing if array[i] <= array[i + 1] holds for every i (1 <= i < n).

정수가 n 인 배열이 주어지면 최대 1 개의 요소를 수정하여 감소하지 않을 수 있는지 확인해야합니다.

array [i] <= array [i + 1]이 모든 i (1 <= i <n)에 대해 유지되는 경우 배열이 감소하지 않는 것으로 정의합니다.

Example1 :

```
Input: [4,2,3]
Output: True
Explanation: You could modify the first 4 to 1 to get a non-decreasing array.
```

Example2 :

```
Input: [4,2,1]
Output: False
Explanation: You can't get a non-decreasing array by modify at most one element.
```

Note:

The n belongs to [1, 10,000].

Solution: 

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var checkPossibility = function(nums) {
  const acc = nums.slice()
  const len = nums.length
  let count = 0
  
  const addCount = (arr) => {
    count += 1
    const result = arr.every((num, index) => {
      const next = index === len - 1 ? null : arr[index + 1]
      return !(next !== null && num > next)
    })
    if (!result) {
      count += 1
    }
  }

  return nums.every((num, index) => {
    const next = index === len - 1 ? null : acc[index + 1]
    const prev = index === 0 ? null : acc[index - 1] 
    if (prev === null && num > next) {
      acc[index] = next
      addCount(acc.slice(index, len))
    }
    if (next !== null && prev !== null && num > next) {
      if (prev > next) {
        acc[index + 1] = num
      }
      if (prev < next) {
        acc[index] = next  
      }
      addCount(acc.slice(index, len))
    }
    return count < 2
  })
};
```
