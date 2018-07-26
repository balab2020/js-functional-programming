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
  
Javascript is well known interpreted programming language and changed the software industry lot in 2018. Everything is a function in javascript. It has new API methods to support functional programming. 

Before starting functional programming with javascript. Lets get started with new stuff

- reduce
- map
- filter
- every
- some
- etc..

Best site to learn these all is [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype)

Think we have dataset before starting the simple problem.

#### Practial

```javascript
const numbers = [12,14,23,40,6,78,90,100,123];
```

##### Problem statements:

1. find maximum in number?
1. find sum of numbers?
1. get odd numbers?
1. get sqrt of each from number?

```javascript
   //find maximum in number?
   function max(input){
        var max = input[0];
        for(var i = 1 ; i < input.length ; i++)
        {
            if(input[i] > max)
            {
              max = input[i];
            }
        }
      return max;
   }
   //find sum of numbers?
   function sum(input){
      var sum = 0;
      for(i=0;i<input.length;i++)
        sum += input[i];
      return sum;
   }
   //get odd numbers?
   function getOdds(input){
     var odds = [];
     for(i=0; i<input.length;i++) {
        if(input[i] % 2 === 1)
            odds.push( input[i] );
     }
   }  
   //get sqrt of each from number?
   function sqrt(input) {
      var sqrts = [];
      for(i=0; i<input;i++)
         sqrts.push(Math.sqrt(input[i]));
      return sqrts;
   }
```

If you solved all problem statement with given dataset, you may be arrived at the proposed solution.

if yes, it is good to see  you are logically solving the problem.

Lets think differently :)
