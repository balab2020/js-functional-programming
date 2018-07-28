# Functional Programming in JavaScript 

## Functional Programming
Functional programming is a [declarative programming](https://en.wikipedia.org/wiki/Declarative_programming) paradigm. Everything is treated as function in mathematics way and it does exactly only one action at a time. You can read more about it in [wikipedia](https://en.wikipedia.org/wiki/Functional_programming). It is not new now. It was introduced along with Object Oriented Programming.

> Collection of simple functional blocks to build application with immutation, purity.

Simple understanding from mathematics:

```f(x,y) = x + y``` is just a function to add two numbers. 

- f(x,y) does not change state (inputs)
- f(x,y) derives only output from inputs
- f(x,y) does only one action

Let's create another function which can add 3 numbers. 

Something like this ``` f(x,y,z) = x + y + z ```. 

Nope, I would suggest consider reusing existing ```f(x,y)```. 

How can I reuse to add 3 numbers? 

```f1(x,y,z) = f(x,f(y,z)) or f(f(x,y),z)```

Example: 
```f1(1,2,3) => f(f(1,2),3) => f(3,3) => 6```

Similarly we can think of creating basic mathematical operations as functions:

Addition : ```f(x,y) = x + y;```

Subtraction : ```s(x,y) = x - y;```

Greater than: ```gt(x,y) = x > y;```

Less Than: ```lt(x,y) = x < y;```

Equal: ```eq(x,y) = x == y;```

Not: ```not(x) = !x;```

AND: ```and(x,y) = x && y;```

ifElse: ```ifElse(cond,ifAns, elseAns) = cond ? ifAns : elseAns;```

function: ```fn(f,a,b) = function(a,b){
  return f(a,b);
};```

..etc

Instead of writing logical, we need to just use these basic mathematical functions to get output;

For example, If you have two numbers x & y and need to sum them if x greater than y otherwise subtract y from x.

How do you do:

```
const x = 1, y =2;
if(x > y)
  print(x+y);
else
  print(x-y);
```

In functional programming, you need to think of calling functions to do this.
```
const x=1, y=2;
ifElse(gt(x,y),f(x,y), s(x,y));
```
Let us understand the execution of fp way:

Stage 1: ifElse(gt(x,y),f(x,y), s(x,y))

Stage 2: ifElse(gt(1,2), f(1,2), s(1,2));

Stage 3: ifElse(1>2, 1+2, 1-2);

Stage 4: ifElse(false, 3, -1);

Stage 5: false ? 3 : -1;

Stage 6: -1 is output

It is as same as writing if else by ourself. But you can see lot of reusabilty of having function being called to perform some action than repeating the same for every need. It will be more readable if you start thinking from functional programming way. We will do more hands on this after understanding few supported new API in javascript.

### Principals of funtional programming:

- #### First class or Higher order function

A function which takes functions as arguments and returns a function which can process inputs and produces the desired out. It basically curries the inputs function to produce the desired function.

- #### Pure function
  A function has no side effects in the system. It is created & used for simple purpose. It never changes / mutates state, global   variables. It never logs anything, does CRUD operations with DB, IO devices..etc.
  
- #### Immutation
Function should not modify any global scope variables, inputs. It should produce new value / object instead. This is strict rule followed in functional programming. 

If you remove function from the system, the side effect is zero except it's processing logic.

- #### Recursion
  Looping with function to get desired result.
  
  - [x] I am done with theoary, lets talk about real time examples.
 
 ## Process collection in JS : Advanced JS programming 
  
Javascript supports new prototype methods with Array which helps to implement functional programming without using any frameworks. We will understand few them here before starting with functional programming with javscript.

Array.prototype methods
- reduce
- map
- filter
- every
- some
- etc.. refer for more in [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype).

We can learn more theory from internet. Let start solving simple problems using them.

### Hands on / Practical

#### Problem: Process array of number.

Lets assume below is dataset/input to the problem.
```javascript
const numbers = [12,14,23,40,6,78,90,100,123];
```

###### Find max number from given array

_Solution 1_: Create a function which takes numbers array as argument and iterates it to find the maximum number in the array.

```javascript   
function max(numbers){
    var max = numbers[0];
    for(var i = 1 ; i < numbers.length ; i++){
      if(input[i] > max) {
        max = input[i];
      }
    }
    return max;
 }   
   console.log(max(numbers));
```
This works really perfect but we have introduced some new variables like max, i and using for loop. All these can be avoided.

_Solution 2_: Use Array.prototype.forEach to avoid for loop.

```javascript   
function max(numbers){
    var max = 0;
    numbers.forEach(function findMax(number){
      if(max < number)
        max = number;
    });
    return max;
 }   
 console.log(max(numbers));
```
In this solution, we just replaced for loop with forEach which takes function as argument and uses it to process each item in array.

Improvements:
- we don't introduce & maintain variable like i
- we use callback function to process the array

_Solution 3_: Use Array.prototype.reduce, if you want to learn about reduce, please read in [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

```javascript
const reducer = (max, currentValue) => max < currentValue ? currentValue : max;
console.log(numbers.reduce(reducer));
```
In this soultion, we have removed for or forEach loop, reduce takes callback function and does recursion operation. reducer is a callback function which is invoked with two arguments, first argument is result of previous call, second argument is the current position value.

i.e) max is tha accumulator, numbers[i] is the currentValue from previous examples.

Improvements:
- don't need to have any global/local variables
- result derieved from function callbacks in recursion way.
- reducer becomes pure function & reusable

This is the way you start thinking in functional programming way. Functions are used to derived output from inputs. 

###### Find sum of all numbers from given array

We can solve this problem with for loop, Array.prototype.forEach. I would rather show you the solution directly using reduce.

```javascript
const add = function(a,b) {
  return a + b;
}
const sum = numbers.reduce(add,0);
```
- Add is simple function just return sum of 2 input numbers as arguments.
- Second argument 0 is initial seed to process first time.

###### Filter all odd numbers from given numbers array

_Solution 1_: Use forEach to filter odd numbers.
```javascript
const odds = []
numbers.forEach( function(number) {
  if(number % 2 == 1)
    odds.push(number);
});
```

_Solution 2_: Use Array.prototype.filter
```javascript
const isOdd = function (n){
  return n % 2 == 1;
};
const odds = numbers.filter(isOdd);
```
filter API helps to filter item from array which satisfies the given condition. filter takes callback function and return result array.

###### Get square root of all the numbers from given input array

_Solution 1_: Use forEach to filter odd numbers.
```javascript
const sqrtNumbers = []
numbers.forEach(function(number) {
 sqrtNumbers.push(Math.sqrt(number));
});
```

_Solution 2_: Use Array.prototype.map
```javascript
const sqrtNumbers = numbers.map(Math.sqrt);
```
Array.prototype.map creates new array from input array by using given function.


I hope, we got fair understanding with javascript API to process the collection. We should be able to understand when to use map, reduce, filter..etc to keep modules simple.

Let get started thinking make functions to replace operators, comparators..etc
