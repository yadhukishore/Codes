# 1979. Find Greatest Common Divisor of Array

``` javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findGCD = function(nums) {
 const gcd=(a,b)=>{
    if(b===0)return a;
    else return gcd(b,a%b); 
 }
 return gcd(Math.max(...nums),Math.min(...nums));
};
```
