#### Array.prototype.filter()

- The filter() method creates a shallow copy of a portion of a given array, filtered down to just the elements from the given array that pass the test implemented by the provided function.
_______________________________________________________________________

##### example
```
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const filteredResult = words.filter(word => word.length>5);
console.log("filteredResult:", filteredResult);
```
_______________________________________________________________________

#### polyfill for filter

```
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

 function myFilter(callback) {
  //Store the new array
  const result = [];
  for (let i = 0; i < this.length; i++) {
    //call the callback with the current element, index, and context.
    //if it passes the text then add the element in the new array.
    if (callback(this[i])) {
      result.push(this[i]);
    }
  }
  
  //return the array
  return result
}

Array.prototype.myFilter = myFilter;

const filteredResult = words.myFilter((word) => word.length>5);
console.log("filteredResult:", filteredResult);
```