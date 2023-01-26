## Curry functions in js

- currying - is an advanced techniques of working with functions not only used in js but also in other programming languages.
- def - currying is transformation of functions from callable as f(a,b,c) into callable as f(a)(b)(c)
- currying doesn't calls a function, it trsnaforms it.

###### basically f(a,b,c) --> f(a)-> g(b) -> h(c) 

example - 

```javascript
function curry(f){
	return function(a){
  	return function(b){
    	return f(a,b);
    }
  }
}

function sum(a,b){
	return a+b;
}

const curriedFunction = curry(sum);
console.log("curriedFunction result is:", curriedFunction(2)(3));
```

## Implement curry function

- requiremnets of curry function
1. curry() should return a function
2. The returned function should
   2.1. If number of arguments matches the original function , return the final result
   2.2. Otherwise return a function which expects the missing arguments, as this function needs to be curried as well. 

/* function curry(f){
  return function(a){
    return function(b){
      return f(a,b);
    }
  }
} */

##### implement curry function

```javascript
function curry(func){
	return function curried(...args){
  //If enough args , then calls the function
  // If not enough arguments , bind the arguments and wait for the next ones
  	console.log(this, "this");
    if(args.length>=func.length){
			return func.apply(this, args);
    }
    else{
    	return curried.bind(this, ...args)
    }
  }
}


function sum(a,b){
	return a+b;
}

const curriedFunction = curry(sum);
console.log("curriedFunction result is:", curriedFunction(2)(3));
```

##### Implement infinite currying

```javascript
function sum(a) {
  return function(b){
    if(!b){
        return a;
    }
    return sum(a+b);
  }
}
console.log(sum(1)(2)(3)(4)(5)(6)());  //21
```