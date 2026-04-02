## Smallest number
```javascript
function findSmallest(arr) {
  // your solution here
  if (!Array.isArray(arr)) return false;
  if (!arr.every(ele => typeof ele === 'number' && Number.isFinite(ele))) return false;
  if (arr.length == 0) return null;
  if (arr.length == 1) return arr.at(0);
  return arr.reduce((smallest, ele) => ele = (ele < smallest) ? ele : smallest, arr[0]);
}
```

## Largest Number
```javascript
function findLargest(arr) {
  // your solution here
  if (!Array.isArray(arr)) return false;
  if (arr.length == 0 || arr == null) return null;
  if (!arr.every(ele => typeof ele === 'number' && Number.isFinite(ele))) return false;
  return Math.max(...arr);
}
```