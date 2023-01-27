### Array.prototype.forEach()

- The forEach() executes the callback function on each and every element of the array.

##### example -
```
const arr = [1,2,3,4];
arr.forEach(el => console.log(el*2));
```

#### polyfill forEach
```
const arr = [1,2,3,4];
  
function myForEach(callback){
	for(var i =0;i<this.length;i++){
  	callback(this[i]);
  }
}

Array.prototype.myForEach = myForEach;

arr.myForEach(el => console.log(el*2))

/* arr.forEach(el => console.log(el*2)); */
```