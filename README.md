# JavaScript Functional Programming

## What is functional programming?
Okay, good question [google helps here](https://www.google.com/search?source=hp&ei=hsNQW6qzIsjsvgSes5J4&q=functional+programming&oq=funtional+pr&gs_l=psy-ab.3.0.0i10k1l10.1469.7858.0.8810.13.12.0.0.0.0.157.1447.0j11.11.0....0...1c.1.64.psy-ab..2.11.1437.0..0j0i131k1.0.d_jUGHXOjKU) 
### Why do I need to consider it?
Wow, super. You are my customer :)
#### How it can help me?
Interesting, welcome to functional programming :D

It is pattern followed in programming. Seriously :) ???

Yes, it is and it has became quite famous now. 

Do you hate mutation?

Do you think only only about requirement?

Do you like mutating the state?

# Stop it. Hey, what mutuation?

Okay, You are welcome to functional programming?

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
 Class  Person{
    string Name;
    string DoB;
    string Gender;
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
