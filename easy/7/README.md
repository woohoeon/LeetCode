## Reverse Integer (역 정수)

Given a 32-bit signed integer, reverse digits of an integer.

32 비트 부호있는 정수가 주어지면 정수의 반대 자릿수입니다.

Example 1:

```
Input: 123
Output: 321
```

Example 2:

```
Input: -123
Output: -321
```

Example 3:

```
Input: 120
Output: 21
```

Note:

Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

32 비트 부호있는 정수 범위 [-231, 231-1] 내의 정수만 저장할 수있는 환경을 처리한다고 가정합니다. 이 문제의 목적을 위해, 역 정수가 오버 플로우 될 때 함수가 0을 리턴한다고 가정하십시오.

Solution: 

```javascript
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
  const process = (x, last, acc) => x > 0 ? 
    process(Math.floor(x / 10), x % 10, (acc * 10) + last) :
    (acc * 10) + last;
  
  const result = process(Math.abs(x), 0, 0);
  
  if (0x7FFFFFFF < result) return 0;
  
  return x < 0 ? result * -1 : result;
};
```
