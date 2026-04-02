## Problem
Given an array of numbers, return the count of elements strictly less than 0

## Observations
- Elements can be infinite or not numbers
- Argument can be anything

## Approaches
### Approach 1: Using regular for loop
### Approach 2: Using .filter() method of javascript
### Approach 3: Using .reduce() method

## Codes
### Using regular for loop
```javascript
function countNegatives(arr) {
  // implement your solution here
  if (!Array.isArray(arr))
    return false;
  if (arr == null)
    return 0;
  let count = 0;
  for (let num of arr) {
    if (typeof num !== 'number' || !Number.isFinite(num))
        return false;
    if (num < 0)
      count++;
  }
  return count;
}
```
### Using filter()
```javascript
function countNegatives(arr) {
  // implement your solution here
  if (!Array.isArray(arr))
    return false;
  if (!arr.every(num => typeof num === 'number' && Number.isFinite(num)))
    return false;
  return arr.filter(num => num < 0).length;
}
```
### Using reduce()
```javascript
function countNegatives(arr) {
  // implement your solution here
  if (!Array.isArray(arr))
    return false;
  if (!arr.every(num => typeof num === 'number' && Number.isFinite(num)))
    return false;
  return arr.reduce( (count, num) => count + (num < 0 ? 1 : 0), 0)
}
```

## New Learnings
- isFinite() function → checks if the number is finite
- typedef num === 'number' → checks if the input is number
- Array.isArray(arr) → checks if the passed input is an array or not.

## Pitfalls
- Look for infinite and inputs other than numbers
- Look out for non-array inputs
