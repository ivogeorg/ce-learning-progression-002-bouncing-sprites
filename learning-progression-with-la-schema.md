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

`[<lernact-rd>]`**TODO:** Data types: primitive vs composite
```javascript
// Example 3.1

// TOOD primitive data types
```

`[<lernact-rd>]`**TODO:** Arrays are a composite data type which is a linear sequence of elements of the same type, called the `[<cept>]`_base type_. Example...
```javascript
// Example 3.2

// TOOD simple declaration and use of an array
```
**TODO:** Things to notice

**TODO:** Sketch of memory storage for primitive types and arrays...
**TODO:**<img src="" alt="" width="" />
**TODO:** What are arrays good for and why are loops and [arrays](https://makecode.microbit.org/javascript/types): Best use of loops    
 used together so often...
```javascript
// Example 3.3

// TOOD looping through an array
```

`[<lernact-rd>]`**TODO:** A glimpse of multidimensional arrays...


#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** Simple extension of example 3.3  
2. `[<lernact-prac>]`**TODO:** Loop "backwards" with a hint on `for` starting at the "end" and decreasing with `i --`.  
3. `[<lernact-prac>]`**TODO:** Multidimensional array for lighting up rows and columns in various orders...   

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 3.2.1 with filename `microbit-program-2-2-1.js`.  
2. Add your program from 3.2.2 with filename `microbit-program-2-2-2.js`.  
3. Add your program from 3.2.3 with filename `microbit-program-2-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 3.2.1.  
2. Link to a demo video for your program from 3.2.1.  
3. Link to your program from 3.2.2.  
4. Link to a demo video for your program from 3.2.2.  
5. Link to your program from 3.2.3.  
6. Link to a demo video for your program from 3.2.3.


### Step 4: Beyond `if...else`
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`Branching upon conditions is one of the most powerful features of programming languages. The basic `if...else` statement that we encountered earlier allows a `[<cept>]`_two-way branch_ in the execution of a program's code. Here we will introduce some further abilities of the statement. The first one, which we already saw in a previous section, is the `[<cept>]`_conditional one-way branch_:
```javascript
// Example 4.1

// TODO: if without else
```
This is essentially an `if` statement without an `else` `[<cept>]`_clause_: if the condition is false, no branching happens.

The second variety gives us the option of having more than 2 branches at the same point, by extending extending the `else` clause with its own `if` statements:
```javascript
// Example 4.2

// TODO: if...else cascade
```
This is called an `if...else` cascade. The most important thing to notice is that, as we descend down the cascade, we test for _increasingly narrow_ cases, and we should write the conditions accordingly. Let's illustrate with an example:
```javascript
// Example 4.3

// TODO: test for even and then test for 40
```
Obviously, if the number is not even, it cannot be 40. Graphically, an `if...else` cascade can be illustrated as a `[<cept>]`_decision tree_. 
**TODO:** <img src="" alt="" width="" />
In general, the cases one level down the cascade should belong to the branch that was taken in the level above them.

Looking at the syntax of the [if...else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else) statement in the JavaScript documentation, we see a generalization of all the cases we have seen:
```
// Example 4.4

// TODO: if...else syntax
```

`[<lernact-rd>]`We have seen that `if...else` cascades, for all their power, can be quite error-prone and hard to read (and, so, fix if erroneous). There is another statement that can be used instead, namely the `switch` statement. Here's the cascade from Example 4.2, written as a `switch` statement:
```javascript
// Example 4.5

// TODO: switch
```
Notice two important points:
1. Each `case` should have a `break` unless we intentionally want to _fall through_ and do the same thing for more than one case.  
2. The `default` clause is a `[<cept>]`_catch-all_, just like the final `else` in an `if...else` cascade.   

Once again, let's take a look at syntax for the `switch` statement in the documentation:
```
// Example 4.6

// TODO: switch syntax
```
Notice how all but the first `case` clauses as well as the `default` clause are all _optional_.

**TODO:** Finally, `switch` statements are best for numerical equalities and `if...else` cascades are best for `[<cept>]`_intervals_ and `[<cept>]`_inequalities_...  

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** `enum` type names are represented as numbers under the hood. Cycle through the icons and show only "even" icons...
2. `[<lernact-prac>]`**TODO:** cycle through the icons and show them for a time proportional to the decade of their index, rounded up to the nearest decade...  
3. `[<lernact-prac>]`**TODO:** cycle through the icons and, using a `switch` statement show them as many times as the smallest odd divisor of their index (3 times if divisible by 3, 5 if div by 5, 2 if even, and once otherwise) and 2 if even...   

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 4.2.1 with filename `microbit-program-4-2-1.js`.  
2. Add your program from 4.2.2 with filename `microbit-program-4-2-2.js`.  
3. Add your program from 4.2.3 with filename `microbit-program-4-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 4.2.1.  
2. Link to a demo video for your program from 4.2.1.  
3. Link to your program from 4.2.2.  
4. Link to a demo video for your program from 4.2.2.  
5. Link to your program from 4.2.3.  
6. Link to a demo video for your program from 4.2.3.


### Step 5: Operators
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`**TODO:** what are operators
**TODO:** assignment vs equality
**TODO:** comparison
**TODO:** arithmetic
**TODO:** overloading for strings!!!
**TODO:** binary and unary
**TODO:** precedence

**TODO:** a look at the documentation, operators vs functions


**TODO:** Switch order with [expressions](#step-6-expressions)?  

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** string concat...   
2. `[<lernact-prac>]`**TODO:** string as array...   
3. `[<lernact-prac>]`**TODO:** ???   

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 5.2.1 with filename `microbit-program-5-2-1.js`.  
2. Add your program from 5.2.2 with filename `microbit-program-5-2-2.js`.  
3. Add your program from 5.2.3 with filename `microbit-program-5-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 5.2.1.  
2. Link to a demo video for your program from 5.2.1.  
3. Link to your program from 5.2.2.  
4. Link to a demo video for your program from 5.2.2.  
5. Link to your program from 5.2.3.  
6. Link to a demo video for your program from 5.2.3.


### Step 6: Expressions
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`**TODO:** what are expressions
**TODO:** operators & expressions
**TODO:** expressions vs statements

**TODO:** Switch order with [operators](#step-5-operators)?  
[JavaScript exrepssions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference#Expressions_and_operators)   
[JavaScript reference: expressions & operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators)   

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** conditionals - equality  
2. `[<lernact-prac>]`**TODO:** conditionals - comparisons  
3. `[<lernact-prac>]`**TODO:** expressions in rvalues of assignments  
4. `[<lernact-prac>]`**TODO:** expressions in arguments of functions    

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 6.2.1 with filename `microbit-program-6-2-1.js`.  
2. Add your program from 6.2.2 with filename `microbit-program-6-2-2.js`.  
3. Add your program from 6.2.3 with filename `microbit-program-6-2-3.js`.
4. Add your program from 6.2.4 with filename `microbit-program-6-2-4.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 6.2.1.  
2. Link to a demo video for your program from 6.2.1.  
3. Link to your program from 6.2.2.  
4. Link to a demo video for your program from 6.2.2.  
5. Link to your program from 6.2.3.  
6. Link to a demo video for your program from 6.2.3.
7. Link to your program from 6.2.4.  
8. Link to a demo video for your program from 6.2.4.


### Step 7: Composite conditions
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`**TODO:** logical operator
**TODO:** Boolean algebra
**TODO:** composite conditions

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** using `led.plot()`, blink a 3x3 square in the middle of the 5x5 LED matrix...
2. `[<lernact-prac>]`**TODO:** using `led.plot()`, blink a 3x3 square along the top-left botton-right diagonal...
3. `[<lernact-prac>]`**TODO:** using `led.plot()`, blink a 3x3 square clockwise and counterclockwise in the corners of the 5x5 LED matrix, using...

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 7.2.1 with filename `microbit-program-7-2-1.js`.  
2. Add your program from 7.2.2 with filename `microbit-program-7-2-2.js`.  
3. Add your program from 7.2.3 with filename `microbit-program-7-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 7.2.1.  
2. Link to a demo video for your program from 7.2.1.  
3. Link to your program from 7.2.2.  
4. Link to a demo video for your program from 7.2.2.  
5. Link to your program from 7.2.3.  
6. Link to a demo video for your program from 7.2.3.


### Step 8: Functions and variable scope
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`Blocks, that is lines of code enclosed in curly braces `{}`, not only encapsulate code, but also define `[<cept>]`_variable scope_. The scope of a variable is the region of code where it is defined and accessible. Variables defined in a block are defined and visible to all the code inside the block, including any _nested_ blocks, but **not** outside the block where they are defined. This is called `[<cept>]`_block scoping_ and is an important capability that allows well-organized and modular programs. Let's revisit the various block scopes that we have encountered so far:
```javascript
// Example 8.1

// TODO: standalone block
```
This is just a standalone block that does not change the way the lines of code inside are executed, but still performs its scoping function. This kind of block is rarely encountered as it is effectively equivalent to the `[<cept>]`_global scope_, the highest "block" in the nesting hierarchy. Variables declared at this level are called, naturally, `[<cept>]`_global variables_. We have used them a number of times so far.

Loops and conditional statements come with blocks whenever there are more than one line of code to encapsulate:
```javascript
// Example 8.2

// TODO: loop conditional nesting hierarchy
```
Loops and conditional statements are very frequently nested within one another, creating a complex block scoping hierarchy. A good rule of thumb is to declare variables as close as possible to the code that will use them. This allows the programmer to focus on a narrow part of the hierarchy (containing block and contained block) around the variable and get the scoping correct. **TODO:** In the example above...

**TODO:** Functions
```javascript
// Example 8.3

// TODO: function example
```
**TODO:** Thorough review, including scoping, parameters, arguments and locals, calls and [return](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/return)... Data flow throught the scope hierarchy...

`[<lernact-rd>]`**TODO:** Argument pass by value and reference (see Classes)

`[<lernact-rd>]`**TODO:** Nested function declarations...  (**TODO:** Declaration vs definition in JS?) Returning functions...

`[<lernact-rd>]`**TODO:** A glimpse at `[<cept>]`_stack frames_...

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** trailing case for comma-delimited _strings_: declaring the loop variable before the loop, so it can be used after the loop     
2. `[<lernact-prac>]`**TODO:** declaring the loop variable before the loop, so it can be used as a diagnostic about how the loop terminated (terminal expression or `break`)...    
3. `[<lernact-prac>]`**TODO:** a number of custom functions with a piece of data passed as argument and re-assigned to return value...    

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 8.2.1 with filename `microbit-program-8-2-1.js`.  
2. Add your program from 8.2.2 with filename `microbit-program-8-2-2.js`.  
3. Add your program from 8.2.3 with filename `microbit-program-8-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 8.2.1.  
2. Link to a demo video for your program from 8.2.1.  
3. Link to your program from 8.2.2.  
4. Link to a demo video for your program from 8.2.2.  
5. Link to your program from 8.2.3.  
6. Link to a demo video for your program from 8.2.3.


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

`[<lernact-rd>]`**TODO:** User code to cpu instructions: overview of the compilation process...   

**TODO:** How do the language constructs - loops, conditional statements, functions, and classes - actually execute...
**TODO:**<img src="" alt="" width="" />
Assembly-level execution:
- sequential  
- branches:  
  - `if...else`  
  - loops  
  - function calls  
  - object methods  
  
`[<lernact-ans>]`**TODO:** questions on 

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-disc>]`**[Optional challenge]** 

#### 3. Present
[[toc](#table-of-contents)]

  
