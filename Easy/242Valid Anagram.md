## Easy way:-

```javascriprt
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    let sVal = s.split('').sort().join('');
    let tVal = t.split('').sort().join('');
    if(sVal===tVal){
        return true;
    }else{
        return false;
    }
};
```

## Using map:-

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
if(t.length !== s.length) return false;
const count={};
for (let c of s){
    count[c]=(count[c]||0)+1;
}
for (let c of t){
    if(!count[c]) return false;
    count[c]--;
}
return true;
};
```
