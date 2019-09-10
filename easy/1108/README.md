## Defanging an IP Address (IP 주소 분리)

Given a valid (IPv4) IP address, return a defanged version of that IP address.

A defanged IP address replaces every period "." with "[.]".

유효한 (IPv4) IP 주소가 제공되면 해당 IP 주소의 축소 된 버전을 반환하십시오.

각 IP 주소는 "."기간마다 바뀝니다. "[.]"와 함께.
 
Example 1:

```
Input: address = "1.1.1.1"
Output: "1[.]1[.]1[.]1"
```

Example 2:

```
Input: address = "255.100.50.0"
Output: "255[.]100[.]50[.]0"
```


Solution: 

```javascript
/**
 * @param {string} address
 * @return {string}
 */
var defangIPaddr = function(address) {
    return address.replace(/\./gi, '[.]');
};
```
