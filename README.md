# [In complete]
# Functional Programming in JavaScript 

## Functional Programming
You can find a lot of articles, blogs & finally [wikipedia](https://en.wikipedia.org/wiki/Functional_programming) to understand about this. According to me, functional programming is programming pattern followed with certain practices. 

It is a [declarative programming](https://en.wikipedia.org/wiki/Declarative_programming) paradigm. 

> Collection of simple functional blocks to build application with immutation, purity.

Simple understanding from mathematics:

```f(x,y) = x + y``` is just a function to add two numbers. 

- It does not change state (inputs)
- It derives only output from inputs
- It does only what is needed, no additional task

Let's create another function which can add 3 numbers. 

Something like this ``` f(x,y,z) = x + y + z ```. 

Nope, I would suggest consider reusing existing ```f(x,y)```. 

How can I reuse to add 3 numbers? 

```f1(x,y,z) = f(x,f(y,z)) or f(f(x,y),z)```

Example: 
```f1(1,2,3) => f(f(1,2),3) => f(3,3) => 6```

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
 
 ## Functional programming with JavaScript
  
Javascript is well known interpreted programming language and changed the software industry lot in 2018. Everything is a function in javascript. It has new API methods which extends jsvascript to support functional programming. 

Before starting functional programming with javascript. Lets get familiarize with new API methods in javascript.

Array.prototype methods, refer for more in [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype).

- reduce
- map
- filter
- every
- some
- etc..

Best site to learn these all is [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype)

Think we have dataset before starting the simple problem.

#### Practial

Lets get start with simple problem, processing numbers in array.

Assume the below array to solve all problems.

```javascript
const numbers = [12,14,23,40,6,78,90,100,123];
```

##### Problem statements:

1. Find maximum in numbers array?
1. Find sum of numbers?
1. Get all odd numbers?
1. Get sqrt of each from number from numbers array?

We will solve the problems in different ways gradually.

###### Find maximum in numbers array

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

_Solution 3_: Use Array.prototype.reduce, if you want to learn about reduce, please read in [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

```javascript
const reducer = (max, currentValue) => max < currentValue ? currentValue : max;
console.log(numbers.reduce(reducer));
```
In this soultion, we have removed for or forEach loop, reduce takes callback function and does recursion operation. reducer is a callback function which is invoked with two arguments, first argument is result of previous call, second argument is the current position value.

i.e) max is tha accumulator, numbers[i] is the currentValue from previous examples.

This is then way, you start thinking in functional programming way by removing avoidable variables, logic. 
