# react_training_ass2

Why are Closures Useful in JavaScript?
----------------------------------------

Closures are useful because they allow a function to access variables from an enclosing scope even after that scope has finished executing. This can be particularly useful for creating private variables or functions and for maintaining state in asynchronous code.

Example Use Case:

function createCounter() {
    let count = 0; // Private variable
    return function() {
        count += 1;
        return count;
    };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3

In this example, the count variable is private to the createCounter function, and only the returned function has access to it. This allows the count to be incremented while keeping the actual count variable hidden from the outside.


When Should You Choose to Use let or const?
-----------------------------------------------

	•	let: Use let when you need to declare a variable that can be reassigned. It is block-scoped, meaning it is only accessible within the block it is defined in.
 
 let x = 10;
x = 20; // Reassignment is allowed

	•	const: Use const when you need to declare a variable that should not be reassigned. It is also block-scoped. However, if the variable is an object or an array, its properties or elements can still be changed.

 const y = 10;
// y = 20; // This will cause an error because reassignment is not allowed

const obj = { key: 'value' };
obj.key = 'newValue'; // This is allowed


Common Mistake Related to Hoisting
-------------------------------------
A common mistake related to hoisting is assuming that let and const are hoisted in the same way as var. While var declarations are hoisted to the top of their scope and initialized with undefined, let and const declarations are hoisted but not initialized, leading to a ReferenceError if accessed before the declaration.

console.log(a); // undefined
var a = 10;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 10;

To fix this, always declare let and const variables before using them:

let b = 10;
console.log(b); // 10

Outcome of console.log() Statements
-------------------------------------

const arr = [1, 2];

function foo1(arg) {
  arg.push(3);
}
foo1(arr);
console.log(arr); // [1, 2, 3]

function foo2(arg) {
  arg = [1, 2, 3, 4];
}
foo2(arr);
console.log(arr); // [1, 2, 3]

function foo3(arg) {
  let b = arg;
  b.push(3);
}
foo3(arr);
console.log(arr); // [1, 2, 3, 3]

function foo4(arg) {
  let b = arg;
  b = [1, 2, 3, 4];
}
foo4(arr);
console.log(arr); // [1, 2, 3, 3]

# Explanation:

	1.	After foo1(arr);
	•	The foo1 function takes arg and pushes 3 into it. Since arg is a reference to arr, the original array is modified.
	•	console.log(arr); // [1, 2, 3]
	2.	After foo2(arr);
	•	The foo2 function reassigns arg to a new array [1, 2, 3, 4]. However, this does not affect the original arr because arg is a local variable in foo2.
	•	console.log(arr); // [1, 2, 3]
	3.	After foo3(arr);
	•	The foo3 function creates a new reference b that points to the same array as arg and pushes 3 into it. This modifies the original array.
	•	console.log(arr); // [1, 2, 3, 3]
	4.	After foo4(arr);
	•	The foo4 function creates a new reference b that initially points to the same array as arg, but then b is reassigned to a new array [1, 2, 3, 4]. This reassignment does not affect the original array.
	•	console.log(arr); // [1, 2, 3, 3]

 




