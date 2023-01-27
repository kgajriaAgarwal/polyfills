### Array.prototype.map()

The map() method creates a new array populated with the results of calling a provided function on every element in the calling array.
_______________________________________________________________________________________________________________________________________

example -

const arr = [1,2,3,4];

const doubledArr = arr.map(el => el * 2)
console.log("doubledArr:", doubledArr);

__________________________________________________________________________________________________________________________________________

### polyfill for map method

```
function myMap(cb){
	var result = [];
  for(var i= 0 ; i < this.length ; i++){
  	result.push(cb(this[i]));
  }
  return result;
}

Array.prototype.myMap = myMap;

var arr  = [1,2,3,4,5];

const myMapResult = arr.myMap(el => el*2);
console.log("myMapResult:", myMapResult);

// output:
// "myMapResult:", [2, 4, 6, 8, 10]
```