# 2455.Average Value of Even Numbers That Are Divisible by Three

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var averageValue = function(nums) {
    let sum=0;
    let count=0;
    for(let n of nums ){
        if(n%6===0){
            sum+=n;
            count++;
        }
    }
    if(sum===0){
        return sum;
    }else{
       return Math.floor(sum / count);
    }
};

```
