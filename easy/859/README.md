## Buddy Strings (두 개의 문자만 바꾸어 A와 B가 같은지 확인하기)

Given two strings A and B of lowercase letters, return true if and only if we can swap two letters in A so that the result equals B.

두 개의 소문자 문자열 A와 B가 주어지면 결과를 B와 같도록 A에서 두 문자를 바꿀 수있는 경우에만 true를 반환합니다.
 

Example 1:

```
Input: A = "ab", B = "ba"
Output: true
```

Example 2:

```
Input: A = "ab", B = "ab"
Output: false
```

Example 3:

```
Input: A = "aa", B = "aa"
Output: true
```

Example 4:

```
Input: A = "aaaaaaabc", B = "aaaaaaacb"
Output: true
```

Example 5:

```
Input: A = "", B = "aa"
Output: false
 ```

Note:

1. 0 <= A.length <= 20000
2. 0 <= B.length <= 20000
3. A and B consist only of lowercase letters.


Solution: 

```javascript
/**
 * @param {string} A
 * @param {string} B
 * @return {boolean}
 */
var buddyStrings = function(A, B) {
  const aLen = A.length,
        bLen = B.length;
  
  if (aLen !== bLen || aLen < 2 || bLen < 2) return false;
  
  if (aLen === 2) return A[0] === B[1] && B[0] === A[1];
  
  const setA = new Set(A.split(''));
  const setB = new Set(B.split(''));
  
  if (setA.size !== setB.size) return false;
  
  if (A === B) return setA.size < aLen
  
  const a = A.split('')
  const b = B.split('')
  
  const { a: defA, b: defB } = a.reduce((acc, val, i) => {
    if (val !== b[i]) {
      acc.a.push(val)
      acc.b.push(b[i])
    }
    return acc;
  }, { a: [], b: [] });
  
  
  if (defA.length === 2) return defA[0] === defB[1] && defA[0] === defB[1];
  
  return defA.length === 0;
};
```
