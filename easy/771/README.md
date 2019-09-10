## Jewels and Stones (돌에서 보석 찾기)

You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

보석 인 돌의 종류를 나타내는 줄 J와 당신이 가진 돌을 나타내는 S가 주어집니다. S의 각 문자는 당신이 가진 돌의 유형입니다. 당신은 보석이 얼마나 많은 돌인지 알고 싶습니다.

J의 문자는 구별되며 J 및 S의 모든 문자는 문자입니다. 문자는 대소 문자를 구분하므로 "a"는 "A"와 다른 유형의 돌로 간주됩니다.

Example 1:

```
Input: J = "aA", S = "aAAbbbb"
Output: 3
```

Example 2:

```
Input: J = "z", S = "ZZ"
Output: 0
```

Note:

 * S and J will consist of letters and have length at most 50.
 * The characters in J are distinct.

Solution: 

```javascript
/**
 * @param {string} J
 * @param {string} S
 * @return {number}
 */
var numJewelsInStones = function(J, S) {
  const set = new Set();
  
  J.split('').map((c, i) => {
    if (!set.has(c)) set.add(c);
  })
  
  let num = 0;
  
  S.split('').map((c, i) => {
    if (set.has(c)) num += 1;
  })
  
  return num;
};
```
