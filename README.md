# JavaScript Functional Programming - In complete

## Functional Programming
You can find a lot of articles, blogs & finally [wikipedia](https://en.wikipedia.org/wiki/Functional_programming) to understand about this. According to me, functional programming is programming pattern followed with certain practices.

> Building collection of functional blocks to process something without changing the state & with purity.

Simple understanding from mathematics:

> f(x,y) = x + y, f1(x,y,z) = f(x, f(y,z)) => x + y + z

f(x,y) takes two arguments and returns some. It is pure function whick takes 2 arguments & returns the sum.


You come around lot terminologies in this programming paradigm. Like below,
- Higher order or First classfunctions
- Pure Functions
- Immutation

##### Higher order functions
It is function which takes one or more functions as arguments and returns function which process inputs.

For example:
if you want to calculate the power of 2 for given input x.

##### Pure Functions
A function can be called with the same inputs at anytime, you should get the same result always.
  * No side-effects (don't change input, does only what is expected).
  * Don't change outside variables (don not change global scope values, inputs).
  * Don’t read from or write to a database (simple functional block).

```js
const Add = (a,b) => a + b;
```

##### Impure functions
  * Can have side effects.
  * Can change the outside variable.
  * May deal with external resources.

```js
Add (a,b) {
  const result = a + b;
  console.log(`Add(${a}, ${b}) => ${result}`);
  return result;
}
```

##### Immutability (Unchangeable)

  Never change the object or value after creating. It means that no changing elements of an array or properties of an object.

  What should I do if change required?
  Make copy of it with modification and leave the original one as it is.

##### Pure functions + Immutability
  - Immutability goes hand-in-hand with pure functions.
  - Pure functions are forced to work with data in an immutable way.

##### Function composition
 The process of combining two or more functions in order to produce a new function or perform some computation.
 Get all male major 
 ```js
 class  Person{
     constructor(name,dob, gender) {
       this.name = name;
       this.dob = dob;
       this.gender = gender;
     }
  }
  
  const calculateAge = dob => { /*calculate the age*/ };
  const isMale = (person) = person.Gender == "Male";
  const isPersonMajor = person => calculateAge(person) > 17;
  const getAllMaleAdults = (people) => {
    people.filter( person => {
      return isPersonMajor(person) && isMale(person);
    });
  }
```
##### JavaScript Array Prototype
  - forEach
  ```js
    const numbers = [1,2,3,4];
    const powOfNums = [];
    numbers.forEach( i => powOfNums.push(Math.pow(i,i) );
    console.log(powOfNums);
   ```
    
  - map
  ```js
   const numbers = [1,2,3,4];
   const powOfNums = numbers.map(i=>Math.pow(i,i));
   ```
   
  - reduce
  ```js
    const numbers = [1,2,3,4];
    const total = numbers.reduce((accumulator, currentvalue) => accumulator + currentvalue ,0);
   ```
     
 ##### Array prototypes:
 [Mozilla MDN] (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
  Useful:
  - filter
  - pop
  - push
  - some
  - sort
  - every
  - find
  
 UnderscoreJS, Lodash, Ramda JS [Contd..]
