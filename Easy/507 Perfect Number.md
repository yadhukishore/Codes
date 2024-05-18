# 507.Perfect Number
## `O(n) solution`
```javascript
/**
 * @param {number} num
 * @return {boolean}
 */
var checkPerfectNumber = function(num) {
    if (num <= 0) return false;

let sum=0;
    for (let i = 1; i < num; i++) {
        if(num%i===0)
        {
            sum+=i;
        }
    }
  return  sum===num;
};
```

`Optimised:-`
```javascript
var checkPerfectNumber = function(num) {
    if (num <= 1) return false; // Perfect numbers are greater than 1

    let sum = 1; // Start with 1 because 1 is a divisor of every number

    // Loop from 2 to the square root of num
    for (let i = 2; i <= Math.sqrt(num); i++) {
        if (num % i === 0) {
            sum += i;
            if (i !== num / i) {// then paired divisor found it will also update the sum
                sum += num / i;
            }
        }
    }

    return sum === num;
};

// Example usage:
console.log(checkPerfectNumber(28)); // Output: true
console.log(checkPerfectNumber(7));  // Output: false


```
### Output
```
Initial sum: 1
Found divisor: 2, updated sum: 3
Found paired divisor: 14, updated sum: 17
Found divisor: 4, updated sum: 21
Found paired divisor: 7, updated sum: 28
Final sum of divisors: 28
Is 28 a perfect number? true
Initial sum: 1
Final sum of divisors: 1
Is 7 a perfect number? false
```
