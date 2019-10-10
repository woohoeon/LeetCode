##  Excel Sheet Column Title (엑셀 시트 열 제목)

Given a positive integer, return its corresponding column title as appear in an Excel sheet.

양의 정수가 주어지면 Excel 시트에 나타나는 해당 열 제목을 반환하십시오.

For example:

```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
    ...
```    

Example 1:

```
Input: 1
Output: "A"
```

Example 2:

```
Input: 28
Output: "AB"
```

Example 3:

```
Input: 701
Output: "ZY"
```

Solution: 

```javascript
/**
 * @param {number} n
 * @return {string}
 */
var convertToTitle = function(n) {
  if (n < 27) {
    return String.fromCharCode(((n - 1) % 26) + 65);
  }
  return (
    convertToTitle(Math.floor((n - 1) / 26)) +
    String.fromCharCode(((n - 1) % 26) + 65)
  );
};
```
