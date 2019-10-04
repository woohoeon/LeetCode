## MissingInteger

Find the smallest positive integer that does not occur in a given sequence.

Write a function:

function solution(A);

that, given an array A of N integers, returns the smallest positive integer (greater than 0) that does not occur in A.

For example, given A = [1, 3, 6, 4, 1, 2], the function should return 5.

Given A = [1, 2, 3], the function should return 4.

Given A = [−1, −3], the function should return 1.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [−1,000,000..1,000,000].
Copyright 2009–2019 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or disclosure prohibited.

Solution: 

```javascript
function solution(A) {
    // write your code in JavaScript (Node.js 8.9.4)
    let arr = new Array(A.length);
    
    A.map((n, i) => {
        if (n > 0 && arr[n] === undefined) {
            arr[n] = 1;
        }
    });
    
    let ans = null;
    
    arr.some((n, i) => {
        if (i > 0 && n === undefined) {
            ans = i;
            return true;
        }
        return false;
    });
    
    return ans === null ? arr.length : ans;
}

```
