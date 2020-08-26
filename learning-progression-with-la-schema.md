# CPE 1040 - Fall 2020

This is learning progression 002 for the Fall 2020 installment of the course CPE 1040: Introduction to Computer Engineering at MSU Denver.

Table of Contents
=================

* [CPE 1040 \- Fall 2020](#cpe-1040---fall-2020)
  * [Learning Progression 002: Bouncing Sprites](#learning-progression-002-bouncing-sprites)
    * [Step 1: Controlling the number of iterations with for](#step-1-controlling-the-number-of-iterations-with-for)
      * [1\. Study](#1-study)
      * [2\. Apply](#2-apply)
      * [3\. Present](#3-present)
    * [Step 2: Breaking out of loops with break](#step-2-breaking-out-of-loops-with-break)
      * [1\. Study](#1-study-1)
      * [2\. Apply](#2-apply-1)
      * [3\. Present](#3-present-1)
    * [Step 3: Arrays are the best use for loops](#step-3-arrays-are-the-best-use-for-loops)
      * [1\. Study](#1-study-2)
      * [2\. Apply](#2-apply-2)
      * [3\. Present](#3-present-2)
    * [Step 4: Beyond if\.\.\.else](#step-4-beyond-ifelse)
      * [1\. Study](#1-study-3)
      * [2\. Apply](#2-apply-3)
      * [3\. Present](#3-present-3)
    * [Step 5: Operators](#step-5-operators)
      * [1\. Study](#1-study-4)
      * [2\. Apply](#2-apply-4)
      * [3\. Present](#3-present-4)
    * [Step 6: Expressions](#step-6-expressions)
      * [1\. Study](#1-study-5)
      * [2\. Apply](#2-apply-5)
      * [3\. Present](#3-present-5)
    * [Step 7: Composite conditions](#step-7-composite-conditions)
      * [1\. Study](#1-study-6)
      * [2\. Apply](#2-apply-6)
      * [3\. Present](#3-present-6)
    * [Step 8: Functions and variable scope](#step-8-functions-and-variable-scope)
      * [1\. Study](#1-study-7)
      * [2\. Apply](#2-apply-7)
      * [3\. Present](#3-present-7)
    * [Step 9: Encapsulating data and functions into classes](#step-9-encapsulating-data-and-functions-into-classes)
      * [1\. Study](#1-study-8)
      * [2\. Apply](#2-apply-8)
      * [3\. Present](#3-present-8)
    * [Step 10: The separate lives of objects](#step-10-the-separate-lives-of-objects)
      * [1\. Study](#1-study-9)
      * [2\. Apply](#2-apply-9)
      * [3\. Present](#3-present-9)
    * [Step 11: Inheritance with classes](#step-11-inheritance-with-classes)
      * [1\. Study](#1-study-10)
      * [2\. Apply](#2-apply-10)
      * [3\. Present](#3-present-10)
    * [Step 12: Execution with branches](#step-12-execution-with-branches)
      * [1\. Study](#1-study-11)
      * [2\. Apply](#2-apply-11)
      * [3\. Present](#3-present-11)


## Learning Progression 002: Bouncing Sprites

This progression continues to introduce new programming language components, revisit those already introduced in more depth, and build up your skills to create more dynamic and compelling programs. You will get used to reading the official documentation for the JavaScript and TypeScript languages frequently as you continue learning to program.  

### Step 1: Controlling the number of iterations with `for`
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`We saw that the `while` loop is very useful for repeating behavior multiple times without having to duplicate code. But what if we wanted to repeat a behavior _exactly_ some number of times? We'll need to use a `[<cept>]`_variable_. Here's how we would go about doing this:
```javascript
const MAX_ITER : number = 10  // the number of iterations
let i : number = 0            // a variable to keep track of how many iterations we have done so far

while (i < MAX_ITER) {
    basic.showIcon(IconNames.Heart)
    basic.pause(100)
    basic.clearScreen()
    basic.pause(100)
    
    i = i + 1                // increment the loop variable
}
```
Several things to notice here:
1. We need to delimit the number of iterations, in this case 10, which is a `[<cept>]`_constant_.  
2. We need to keep track of how many iterations we have done so far, which is a variable, incremented each time we complete a pass through the code block.  
3. In computing, we almost always start `[<cept>]`_counting up_ from 0 and _counting down_ to 0. There are good reasons for that:  
   1. 1 bit vs 2 bits  
   2. compare to zero very efficient
4. It is a widely adopted practice to give constants names in `ALL_CAPS`.  

`[<lernact-ans>]`**Question 1.1.1:** values of i...  

pattern _zero-start-and-less-than-target-count_
   
One thing that is deficient in controlling the number of iterations of a `while` loop like the example above is that there are bits and pieces of the necessary code all over the place. This is why programming languages almost universally provide the equivalent but much cleaner alternative syntax of the `for` loop. Let's see how we can use it to rewrite the code above and make it much cleaner:

```javascript
const MAX_ITER : number = 10

for (let i = 0; i < MAX_ITER; i ++) {    // the loop variable is handled automatically for us
    basic.showIcon(IconNames.Heart)
    basic.pause(100)
    basic.clearScreen()
    basic.pause(100)
}
```

Using the loop variable in the block...


[for](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for) loops: Controlling the number of iterations  

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 2: Breaking out of loops with `break`
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

[break](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/break): Breaking out of loops    

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 3: Arrays are the best use for loops
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

[arrays](https://makecode.microbit.org/javascript/types): Best use of loops    

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 4: Beyond `if...else`
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

[if...else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else) redux: 
   - `else if` cascades  
   - [switch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch)  

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 5: Operators
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 6: Expressions
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 7: Composite conditions
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 8: Functions and variable scope
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

   - variable scope  
   - [return](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/return)  

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 9: Encapsulating data and functions into classes
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

classes: encapsulation of data and functions    

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 10: The separate lives of objects
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 11: Inheritance with classes
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 12: Execution with branches
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

  
