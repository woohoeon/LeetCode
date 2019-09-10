## Third Maximum Number (세 번째 최대 수)

Given a non-empty array of integers, return the third maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).

비어 있지 않은 정수 배열이 주어지면이 배열의 세 번째 최대 숫자를 반환하십시오. 존재하지 않으면 최대 수를 반환하십시오. 시간 복잡도는 O (n)이어야합니다.

Example 1:

```
Input: [3, 2, 1]

Output: 1

Explanation: The third maximum is 1.
```

Example 2:

```
Input: [1, 2]

Output: 2

Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
```

Example 3:

```
Input: [2, 2, 3, 1]

Output: 1

Explanation: Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
```

Solution: 

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var thirdMax = function(nums) {
  const { third, first } = nums.reduce(({ set, first, second, third }, num, i) => {
    if (set.has(num)) return { set, first, second, third };
    
    if (first === null || first < num) {
      third = second;
      second = first;
      first = num;
    } else if (second === null || second < num) {
      third = second;
      second = num;
    } else if (third === null || third < num) {
      third = num;
    } 
    
    set.add(num);
    
    return { set, first, second, third };
  }, {
    set: new Set(),
    first: null,
    second: null,
    third: null
  });
  
  return third === null ? first : third;
};
```

or 

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var thirdMax = function(nums) {
  const set = new Set();
  
  let first = null,
      second = null,
      third = null;
  
  nums.map((num, i) => {
    if (set.has(num)) return;
    if (first === null || first < num) {
      third = second;
      second = first;
      first = num;
    } else if (second === null || second < num) {
      third = second;
      second = num;
    } else if (third === null || third < num) {
      third = num;
    } 
    set.add(num);
  });
  
  return third === null ? first : third;
};
```
