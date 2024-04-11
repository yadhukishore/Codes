# 2427. Number of Common Factors
`Method 1`
```javascript
/**
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
var commonFactors = function(a, b) {
    let count=0;
    let n=Math.min(a,b);
    for(let i = 0;i<=n;i++){
        if(a%i===0 && b%i === 0){
            count++;
        }
    }
return count;
};

```

`Method-2`
```javascript

/**
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
var commonFactors = function(a, b) {
let count = 0;
let aFactor = new Set();
for(let i = 0 ; i <= a ; i++){
    if(a%i===0)aFactor.add(i);
}

for(let j = 0 ; j<=b  ; j++){
    if(aFactor.has(b/j))count++
}
return count;

};
```
