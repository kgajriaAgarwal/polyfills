reduce() method

The reduce() method executes a user-supplied "reducer" callback function on each element of the array, in order, passing in the return value from the calculation on the preceding element. The final result of running the reducer across all elements of the array is a single value.

The first time that the callback is run there is no "return value of the previous calculation". If supplied, an initial value may be used in its place. Otherwise the array element at index 0 is used as the initial value and iteration starts from the next element (index 1 instead of index 0).
____________________________________________________________________________
//REDUCE EXAMPLES...
//reduce for aggregation
//arr.reduce(reducer, initialValue)

//reduce method take 4 args
//arr.reduce(acc, cval, cindx , arr)

//EXAMPLE 1
//example of aggregation 
const arr = [1,2,3];
const res = arr.reduce((acc, cval)=> {
	return acc += cval
  }, 4);
  
console.log(res);

___________________________________________________________________________

//EXAMPLE 2
//Summing an Array of Numeric Properties
const lineItems = [
  { description: 'Eggs (Dozen)', quantity: 1, price: 3, total: 3 },
  { description: 'Cheese', quantity: 0.5, price: 5, total: 2.5 },
  { description: 'Butter', quantity: 2, price: 6, total: 12 }
];

//find the total
const total = lineItems.reduce((acc, cval) => { return acc += cval.total}, 0)
console.log("total is :", total);

____________________________________________________________________________

//EXAMPLE 3
//Find the Maximum Value
const dates = [
  '2019/06/01',
  '2018/06/01',
  '2019/09/01', // This is the most recent date, but how to find it?
  '2018/09/01'
]

const maxDate = dates.reduce((acc, cval)=> acc > cval? acc : cval);
console.log("maxDate:", maxDate);
___________________________________________________________________________________________

//EXAMPLE 4
//Grouping Values
const characters = [
  { name: 'Jean-Luc Picard', age: 59 },
  { name: 'Will Riker', age: 29 },
  { name: 'Deanna Troi', age: 29 }
];
//expected o/p: How do you return a map that contains how many characters have a given age? For example, the correct output on the above array would be { 29: 2, 59: 1 }.

const groupCharacters = characters.reduce((acc, cval)=>{
	if(!acc[cval.age]){
  	acc[cval.age] = 1;
  }else{
  	acc[cval.age]++;
  }
  return acc;
}, {});

console.log("groupCharacters:", groupCharacters);
______________________________________________________________________________________________

//EXAMPLE 5
//Summing Values in an Object Array Using Array Reduce JavaScript
const obj = [{n: 5}, {n: 9}, {n: 13}, {n: 25}, {n: 40}]

const resultObjSum = obj.reduce((acc, cval)=> { return acc += cval.n}, 0);
console.log("resultObjSum:", resultObjSum);
_________________________________________________________________________________________________

//EXAMPLE 6
//Flattening an Array of Arrays With Reduce Method
let mulArray = [[3, 5], [1, 7], [12, 9], 14];

const flatMulArr = mulArray.reduce((acc, cval) => {
	return acc.concat(cval);
}, [] );

console.log("flatMulArr:", flatMulArr);
___________________________________________________________________________________________________

//EXAMPLE 7
//Counting Instances in an Object Using Array Reduce in JavaScript
const myCars = ['Mercedes-Benz', 'Jeep', 'Ferrari', 'Lamborghini', 'Mercedes-Benz', 'BMW', 'Ferrari'];

const countInstances = myCars.reduce((acc, cval) =>{
	if(!acc[cval]){
  	acc[cval] = 1;
  }else{
  	acc[cval]++;
    }
  return acc;
}, {})

console.log("countInstances:", countInstances);
___________________________________________________________________________________________________

//EXAMPLE 9
//Grouping Objects With Array Reduce in JavaScript

let student = [
  { name: 'David', age: 23, hobby: 'fishing' },
  { name: 'Rachel', age: 25, hobby: 'cooking' },
  { name: 'Rahul', age: 22, hobby: 'fishing' }
];

 const groupingObjs = student.reduce((acc, cval)=>{
  /* const arr = []; */
  if(!acc[cval.hobby]){
    acc[cval.hobby] = []
  }
    acc[cval.hobby].push(cval)
  return acc;
}, {});

console.log("groupingObjs:", groupingObjs); 

output expected:
"Running fiddle"
"groupingObjs:", 
{
  cooking: [{
  age: 25,
  hobby: "cooking",
  name: "Rachel"
  }],
  fishing: [{
  age: 23,
  hobby: "fishing",
  name: "David"
  }, {
  age: 22,
  hobby: "fishing",
  name: "Rahul"
  }]
}
___________________________________________________________________________________________________

//EXAMPLE 10
//Removing Duplicates With Array Reduce
let array = [2, 5, 7, 5, 12, 9, 7, 5, 4, 3, 5, 2, 4, 15];

const uniqueArr = array.reduce((acc, cval)=>{
	if(acc.indexOf(cval)=== -1){
   acc.push(cval);
  }
  return acc;
}, [])

console.log("uniqueArr:", uniqueArr);

//O/p : "uniqueArr:", [2, 5, 7, 12, 9, 4, 3, 15]
___________________________________________________________________________________________________

//EXAMPLE 11
//find average
const euros = [29.76, 41.85, 46.5];

const findAverage = euros.reduce((acc, cval)=>  {
	 acc += cval;
  /* console.log("acc:", acc, "acc:", acc) */;
	return (acc/euros.length);
}, 0)

console.log("findAverage:", findAverage.toFixed(2))
___________________________________________________________________________________________________

//EXAMPLE 12
//Creating a Tally with the Reduce Method In JavaScript​

const fruitBasket = ['banana', 'cherry', 'orange', 'apple', 'cherry', 'orange', 'apple', 'banana', 'cherry', 'orange', 'fig' ];

const createTally = fruitBasket.reduce((acc, cval) => {
	if(!acc[cval]){
  	acc[cval] = 1
  }else{
  	acc[cval] = acc[cval] +1;
  }
  return acc;
},{})

console.log("createTally:", createTally);

☁️ "Running fiddle"
"createTally:", {
  apple: 2,
  banana: 2,
  cherry: 3,
  fig: 1,
  orange: 3
}
___________________________________________________________________________________________________

//EXAMPLE 13

/* More often than not, information is nested in more complicated ways. For instance, lets say we just want all the colors in the data variable below. */

const data = [
  {a: 'happy', b: 'robin', c: ['blue','green']}, 
  {a: 'tired', b: 'panther', c: ['green','black','orange','blue']}, 
  {a: 'sad', b: 'goldfish', c: ['green','red']}
];

//['blue','green','green','black','orange','blue','green','red']

const dataArr = data.map(el => el.c);
console.log("dataArr:", dataArr);
VM105:12 dataArr: (3) [Array(2), Array(4), Array(2)]0: (2) ['blue', 'green']1: (4) ['green', 'black', 'orange', 'blue']2: (2) ['green', 'red']length: 3[[Prototype]]: Array(0)

const res = dataArr.reduce((acc, cval) => acc.concat(cval), [])
console.log("res:", res);
VM760:2 res: (8) ['blue', 'green', 'green', 'black', 'orange', 'blue', 'green', 'red']

___________________________________________________________________________________________________

//EXAMPLE 14

/* Piping with Reduce
An interesting aspect of the reduce method in JavaScript is that you can reduce over functions as well as numbers and strings. */

/* Let’s say we have a collection of simple mathematical functions. these functions allow us to increment, decrement, double and halve an amount. */

function increment(input) { 
	return input + 1;
}

function decrement(input) { 
	return input - 1; 
}

function double(input) { 
	return input * 2; 
}

function halve(input) {
	return input / 2; 
}

//For whatever reason, we need to increment, then double, then decrement an amount.

/* You could write a function that takes an input, and returns (input + 1) * 2 -1. The problem is that we know we are going to need to increment the amount three times, then double it, then decrement it, and then halve it at some point in the future. We don’t want to have to rewrite our function every time so we going to use reduce to create a pipeline. */

/* A pipeline is a term used for a list of functions that transform some initial value into a final value. Our pipeline will consist of our three functions in the order that we want to use them. */

let pipeline = [increment, double, decrement];
/* Instead of reducing an array of values we reduce over our pipeline of functions. This works because we set the initial value as the amount we want to transform. */

const result = pipeline.reduce(function(total, func) {
  return func(total);
}, 1);

console.log("result:", result) // 3
/* Because the pipeline is an array, it can be easily modified. If we want to decrement something three times, then double it, decrement it , and halve it then we just alter the pipeline. */

/* var pipeline = [

  increment,
  
  increment,
  
  increment,
  
  double,
  
  decrement,
  
  halve
  
]; */

_____________________________________________________________________________________________________________________________________________________

//EXAMPLE 15
//segregation using reduce method
const arr1 =  [1.1, 1.2, 1.3, 2.2, 2.3, 2.4, 4.5, 4.6, 7.2, 7.7];
//expected o/p : 
/*
{
1: [1.1, 1.2, 1.3],
2: [2.2, 2.3, 2.4]
}
*/

const segregate = arr1.reduce((acc, cval)=> {
	const  floored_key = Math.floor(cval);
  /* console.log("acc[floored_key]:", acc[floored_key]) */;
  if(!acc[floored_key]){
  	console.log("acc[floored_key]:", acc[floored_key]);
  	acc[floored_key] = [];
    console.log("acc[floored_key]: after::", acc[floored_key]);
  }
  acc[floored_key].push(cval);
  return acc;
  
}, {})

console.log(segregate);

_____________________________________________________________________________________________________________________________________________________________

//POLYFILL FOR REDUCE
/**
 * Read FAQs section on the left for more information on how to use the editor
**/
/**
* Do not change the function name
**/

Array.prototype.customReduce  = function customReduce(callback, initialValue) {
  // DO NOT REMOVE
  'use strict'; 
    
    //test case 1:
    if(this === undefined || this === null){
      throw TypeError("reduce emethod cannot be implemented on undefined or null");
    }
    
    console.log("typeof callback", typeof callback, arguments);
    
    //test case 2
    if(!callback || typeof callback !== "function"){
      throw TypeError("callback should be a function");
    }
    
    //test case 3(incase this.length is 0)
    if(!this.length){
      //there is no initaial value && no arr length also , throw Error
      if(arguments.length < 2){
        throw TypeError("reduce cannot  be implemneted on an empty array with no initial value");
      }
      if(arguments.length === 2 ){
       return initialValue;
      }
    }
    
    //if the arr is not empty
    var k = 0; // for mainitaing the ARR INdex
    var acc = initialValue;
    
    //arr.length
    if(arguments.length < 2){
    	acc= this[k++];
    }
    
    //arr.length, initailvalue 
    while(k<this.length){
    	acc = callback(acc, this[k], k, this)
      k++;
    }
    
    return acc;
}


var arr = [1,2,3];

function sum(acc , cval){
  return acc+cval;
};

var result = arr.customReduce(sum);
console.log("result is :", result);
