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
   1. **TODO** 1 bit vs 2 bits, always 1 bit more to represent the same number of numbers! 
   2. **TODO** compare to zero very efficient
   3. **TODO** convention to avoid the _off-by-one_ error  
4. It is a widely adopted practice to give constants names in `ALL_CAPS`.  

`[<lernact-ans>]`**Question 1.1.1:** Enumerate the values of the `[<cept>]`_loop variable_ `i` is the block of the `for` loop executed.    
`[<lernact-ans>]`**Question 1.1.2:** What is the value of the loop variable _after_ the termination of the loop? _Hint: Skim the reference section on [block-scoping](https://makecode.microbit.org/javascript/variables) of variables._  

**TODO** pattern _zero-start-and-less-than-target-count_
   
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
**TODO** Explain `i ++`...
**TODO** Using the loop variable in the block...

The [for](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for) loop is extremely versatile. Let's take apart its `[<cept>]`_syntax_:
```
for ([initialization]; [condition]; [final-expression])
   statement
```
The `[<cept>]`_square brackets_ `[]` indicate an _optional_ element. All three `[<cept>]`_expressions_ (more on expressions [below]((#step-6-expressions)) - the `[<cept>]`_initialization_, the `[<cept>]`_condition_, and the `[<cept>]`_final expression_ - are optional. There are various cases in which you don't want all three expressions to be included. For example, the `for (;;)` loop form is exactly equivalent to a `while (true)` loop. Note that the `[<cept>]`_expression-delimiting semi-colons_ `;` are **not optional**.

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`Write a program that shows a heart icon for odd numbers and pauses for 100 ms for even numbers in a `for` loop from 0 to 10 (not inclusive). _Hint: You will need to use the loop variable of the `for` loop to check for odd and even numbers and have an `if...else` conditional statement in the block of the loop._  
2. `[<lernact-prac>]`**TODO** The following program:
```javascript
basic.forever(function () {
    for (let i=0; i<=4; i++) {
        led.plot(i, i)	
        basic.pause(50)
        basic.clearScreen()
    }
})
```
with [video](https://msudenver.yuja.com/Dashboard/Permalink?authCode=754064295&b=1599792&linkType=video).  
3. `[<lernact-prac>]`Write a program that shows on the micro:bit 21 numbers, one after the other, starting at zero and increasing in _magnitude_, with the _even_ numbers in the interval [0, 20] are _positive_ and the _odd_ numbers in the same interval are _negative_. _Hint: Consider using a `for` loop with the `[<cept>]`_less-than-or-equal_ operator `<=` in the condition expression._  


#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:
1. Add your program from 1.2.1 with filename `microbit-program-1-2-1.js`.  
2. Add your program from 1.2.2 with filename `microbit-program-1-2-2.js`.  
3. Add your program from 1.2.3 with filename `microbit-program-1-2-3.js`.  

In the [Lab Notebook](README.md):
1. Link to the program from 1.2.1.  
2. Link to a demo video showing the execution of the program from 1.2.1.  
3. Link to the program from 1.2.2.  
4. Link to a demo video showing the execution of the program from 1.2.2.  
5. Link to the program from 1.2.3.  
6. Link to a demo video showing the execution of the program from 1.2.3.  


### Step 2: Breaking out of loops with `break`
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`Being so useful in running the same code muliple times, the `while` and `for` loops are ubiquitous in computer programs. This is why computer languages have keywords for them. Just as often as one needs a loop, one is likely to need a way to break out it. There's a keyword for that, too, namely `break`:
```javascript
// Example 2.1
let stop : boolean = false
let isHeart : boolean = true

input.onButtonPressed(Button.A, () => { isHeart = !isHeart })   // "Arrow" functions are best for short code passed as argument to a function.
input.onButtonPressed(Button.B, () => { stop = true })

while (true) {
    if (isHeart)                                                 // If only one line, no block braces are required.
        basic.showIcon(IconNames.Heart)
    else
        basic.showIcon(IconNames.Butterfly)
    basic.pause(100)
    basic.clearScreen()
    basic.pause(100)
    
    if (stop)
        break
}
```
**TODO:** Explain all the new syntax.

In this example, when the Boolean `stop` becomes true upon the press of button B, the conditional at the bottom of the `while` loop block will be executed and program execution will jump out of the loop and never reenter. This will effectively stop the program as there is no more code left to execute after the `while` loop. This is a very simple and a bit contrived example, but the [`break`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/break) keyword enables the writing of very complex program logic. 

`[<lernact-rd>]`Loops can be `[<cept>]`_nested_ (e.g. a `for` loop inside a `for` loop, or a `for` loop inside a `while` loop) any which way to achieve more complex but regular behavior. For example, the following code lights up the LEDs of the micro:bit one column at a time:
```javascript
// Example 2.2
let on : boolean = true

basic.forever(function () {
    for (let x = 0; x < 5; x ++) {
        for (let y = 0; y < 5; y ++) {
            if (on) 
                led.plot(x, y)
            else
                led.unplot(x, y)
            basic.pause(50)
        }
    }
    on = !on
})
```
It is important to note that a `break` only exits the _innermost_ loop, and any outer loops will continue to execute, as shown in this example:
```javascript
// Example 2.3
let on : boolean = true
let halfWay : boolean = false

input.onButtonPressed(Button.A, () => { halfWay = !halfWay })

basic.forever(function () {
    for (let x = 0; x < 5; x ++) {
        for (let y = 0; y < 5; y ++) {
            if (halfWay)
                if (y > 2)
                    break
            if (on) 
                led.plot(x, y)
            else
                led.unplot(x, y)
            basic.pause(50)
        }
    }
    on = !on
})
```
Notice how, when you toggle button A, the LED lighting pattern goes all the way or stops halfway. The latter case is due to the `break` statement, which cause the inner loop to exit before running through all the values of the loop variable `y`.

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`Write a program like Example 2.2 above, which instead fills the pattern one _row_ at a time.  
2. `[<lernact-prac>]`Write a program like Example 2.3 above, which instead fills in the other remaining "half" when `halfWay` is toggled true.  
3. `[<lernact-prac>]`Write a program like Example 2.3 above, which instead breaks on the value of the outer-loop variable `x`.  
4. `[<lernact-ans>]`Explain the behavior you observe in your program from 2.2.3.


#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 2.2.1 with filename `microbit-program-2-2-1.js`.  
2. Add your program from 2.2.2 with filename `microbit-program-2-2-2.js`.  
3. Add your program from 2.2.3 with filename `microbit-program-2-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 2.2.1.  
2. Link to a demo video for your program from 2.2.1.  
3. Link to your program from 2.2.2.  
4. Link to a demo video for your program from 2.2.2.  
5. Link to your program from 2.2.3.  
6. Link to a demo video for your program from 2.2.3.
7. Write your explanation for 2.2.4.  


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
   - syntax: `else` is optional, very often the condition for `break`    
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

**TODO:** Switch order with [expressions](#step-6-expressions)?  

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 6: Expressions
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

**TODO:** Switch order with [operators](#step-5-operators)?  
[JavaScript exrepssions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference#Expressions_and_operators)   
[JavaScript reference: expressions & operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators)   

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

**TODO:** `this`

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

Assembly-level execution:
- sequential  
- branches:  
  - `if...else`  
  - loops  
  - function calls  
  - object methods  

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

  
