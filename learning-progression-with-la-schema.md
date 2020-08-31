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
  * [References and Resources](#references-and-resources)


## Learning Progression 002: Bouncing Sprites

This progression continues to introduce new programming language components, revisit those already introduced in more depth, and build up your skills to create more dynamic and compelling programs. You will get used to reading the official documentation for the JavaScript and TypeScript languages frequently as you continue learning to program.  

### Step 1: Controlling the number of iterations with `for`
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`We saw that the `while` loop is very useful for repeating behavior multiple times without having to duplicate code. But what if we wanted to repeat a behavior _exactly_ some number of times? We'll need to use a `[<cept>]`_variable_. Here's how we would go about doing this:
```javascript
// Example 1.1.1

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
   1. **Storage efficiency.** If we start at 0, we can represent 2 numbers with 1 bit, 0 and 1. If we started at 1, we would need 2 bits to represent the second number, which is 2<sub>10</sub> and 11<sub>2</sub>. By induction, we can represent 2<sup>n</sup><sub>10</sub> different `[<cept>]`_unsigned binary integers_ with n-1 bits, if we started at 0. Unsigned binary integers are just the `[<cept>]`_natural numbers_ (aka whole numbers) <img src="https://render.githubusercontent.com/render/math?math=N = {0, 1, 2, 3, ...}">.   
   2. **Computational efficiency.** Comparison to zero can be done very quickly and efficiently in `[<cept>]`_combinatorial logic_. More on combinatorial logic in a later progression.  
   3. **Convention.** It pays to follow the convention, for example, to avoid the `[<cept>]`_off-by-one_ error, usually to do with [arrays](#step-3-arrays-are-the-best-use-for-loops).     
4. It is a widely adopted practice to give constants names in `ALL_CAPS`.  

`[<lernact-ans>]`**Question 1.1.1:** Enumerate the values of the `[<cept>]`_loop variable_ `i` is the block of the `for` loop executed.    
`[<lernact-ans>]`**Question 1.1.2:** What is the value of the loop variable _after_ the termination of the loop? _Hint: Skim the reference section on [block-scoping](https://makecode.microbit.org/javascript/variables) of variables._  
`[<lernact-ans>]`**Question 1.1.3:** Enumerate the different unsigned binary integers you can represent with 4 bits?  

What we saw in Example 1.1.1 is one of the most widely used `[<cept>]`_programming patterns_:
1. Set the maximum number of iterations. Call it, say `I`. That may or may not be a constant.  
2. Start the loop variable `i` at zero.  
3. Increment the loop variable until it reaches `I - 1`, which is equivalent to `i < I`.  
   
One thing that is deficient in controlling the number of iterations of a `while` loop like the example above is that there are bits and pieces of the necessary code all over the place. This is why programming languages almost universally provide the equivalent but much cleaner alternative syntax of the `for` loop. Let's see how we can use it to rewrite the code above and make it much cleaner:

```javascript
// Example 1.1.2

const MAX_ITER : number = 10

for (let i = 0; i < MAX_ITER; i ++) {    // the loop variable is handled automatically for us
    basic.showIcon(IconNames.Heart)
    basic.pause(100)
    basic.clearScreen()
    basic.pause(100)
}
```
The `++` in `i ++` is the `[<cept>]`_unary operator_ for `[<cept>]`_increment_. `i ++` is exactly equivalent to `i = i + 1`, and, in fact, this is a perfectly valid expression to use instead.  

The loop variable `i` takes a different value each time through the loop block, so it can be used:
```javascript
// Example 1.1.3

const MAX_ITER : number = 10

for (let i = 0; i < MAX_ITER; i ++) {         // the loop variable is handled automatically for us
    basic.showIcon(IconNames.Heart, 100 * i)  // using the loop variable to vary the icon interval
    basic.clearScreen()
    basic.pause(100)
}
```

The [for](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for) loop is extremely versatile. Let's take apart its `[<cept>]`_syntax_:
```
for ([initialization]; [condition]; [final-expression])
   statement
```
The `[<cept>]`_square brackets_ `[]` indicate an _optional_ element. All three `[<cept>]`_expressions_ (more on expressions [below]((#step-6-expressions)) - the `[<cept>]`_initialization_, the `[<cept>]`_condition_, and the `[<cept>]`_final expression_ - are optional. There are various cases in which you don't want all three expressions to be included. For example, the `for (;;)` loop form is exactly equivalent to a `while (true)` loop. Note that the `[<cept>]`_expression-delimiting semi-colons_ `;` are **not optional**.

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`Write a program that shows a heart icon for odd numbers and pauses for 100 ms for even numbers in a `for` loop from 0 to 10 (not inclusive). _Hint: You will need to use the loop variable of the `for` loop to check for odd and even numbers and have an `if...else` conditional statement in the block of the loop._  
2. `[<lernact-prac>]`Write a program shown executing on the micro:bit in the this [video](https://msudenver.yuja.com/Dashboard/Permalink?authCode=754064295&b=1599792&linkType=video). It may look quite differnt from the examples, but it's very similar. Some hints:
   1. Use a `for` loop, of course.  
   2. To figure out what values the loop variable should take, realize that the micro:bit LED matrix has coordinates y = [0, 4] vertically from top to bottom and x = [0, 4] from left to right. So, the `[<cept>]`_origin_ (0, 0) is in the top-left corner.  
   3. Use the `led.plot()` function, utilizing the loop variable `i`. Note that you are plotting the `[<cept>]`_diagonal_.  
   4. Use `pause()` and `clearScreen`.  
3. `[<lernact-prac>]`Write a program that shows on the micro:bit 21 numbers, one after the other, starting at zero and increasing in _magnitude_, with the _even_ numbers in the interval [0, 20] are _positive_ and the _odd_ numbers in the same interval are _negative_. _Hint: Consider using a `for` loop with the `[<cept>]`_less-than-or-equal_ operator `<=` in the condition expression._  


#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:
1. Add your program from 1.2.1 with filename `microbit-program-1-2-1.js`.  
2. Add your program from 1.2.2 with filename `microbit-program-1-2-2.js`.  
3. Add your program from 1.2.3 with filename `microbit-program-1-2-3.js`.  

In the [Lab Notebook](README.md):
1. Answer question 1.1.1.  
2. Answer question 1.1.2.  
3. Answer question 1.1.3.  
4. Link to the program from 1.2.1.  
5. Link to a demo video showing the execution of the program from 1.2.1.  
6. Link to the program from 1.2.2.  
7. Link to a demo video showing the execution of the program from 1.2.2.  
8. Link to the program from 1.2.3.  
9. Link to a demo video showing the execution of the program from 1.2.3.  


### Step 2: Breaking out of loops with `break`
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`Being so useful in running the same code muliple times, the `while` and `for` loops are ubiquitous in computer programs. This is why computer languages have keywords for them. Just as often as one needs a loop, one is likely to need a way to break out it. There's a keyword for that, too, namely `break`:
```javascript
// Example 2.1.1

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
This example might look very foreign but only the `break` is new. Let's explain the syntax:
1. The event handlers for the button-press events are called `[<cept>]`_arrow functions_. This is just a shorthand for anonymous functions without arguments. This is essentially what is known as _syntactic sugar_: alternative but fully equivalent syntax adopted to save typing time. The reference has a nice short article on [functions](https://makecode.microbit.org/javascript/functions).  
2. The event handlers are each on one line instead of an extended block, but they are still in the block-delimiting curly braces `{}`.  
3. The "blocks" of the `if` statement are missing the curly braces `{}`, but this is okay as we are only executing one line of code.  This includes the `break` statement, which is semantically self-sufficient.  

In this example, when the Boolean `stop` becomes true upon the press of button B, the conditional at the bottom of the `while` loop block will be executed and program execution will jump out of the loop and never reenter. This will effectively stop the program as there is no more code left to execute after the `while` loop. This is a very simple and a bit contrived example, but the [`break`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/break) keyword enables the writing of very complex program logic. 

`[<lernact-rd>]`Loops can be `[<cept>]`_nested_ (e.g. a `for` loop inside a `for` loop, or a `for` loop inside a `while` loop) any which way to achieve more complex but regular behavior. For example, the following code lights up the LEDs of the micro:bit one column at a time:
```javascript
// Example 2.1.2

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
// Example 2.1.3

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

`[<lernact-rd>]`Data types divide into two main groups: `[<cept>]`_primitive_ data types have `[<cept>]`_word-storage_, which means that in memory they take up a `[<cept>]`_word of memory_, usually 16 or 32 bits, while `[<cept>]`_composite_ data types have `[<cept>]`_structure-storage_, which means that they are composed of some combination of primitive-type variables. Here are examples of primitive-type variables.  
```javascript
// Example 3.1.1

let i : number = 345
let f : number = 5.602
let b : boolean = true
```

`[<lernact-rd>]`Arrays are a composite data type which is a linear sequence of elements of the **same type**, called the `[<cept>]`_base type_. The base type can be primitive or complex. Here is an example of various arrays:
```javascript
// Example 3.1.2

let iArr : number[] = [0, 1, 2]                                        // an array of integers, initialized with literal values
let fArr : number[] = [3.14, 3.142, 3.1416, 3.14159]                   // an array of floating-point numbers, also initialized with literal values
let bArr : number[] = [false, true, true, false]                       // an array of Booleans

let sArr : string[] = ["Hellow", "world", "the", "microbit", "rocks"]  // an array of strings (words of text or sequences of characters)
let twoDArr : number[][] = [[1, 3, 4], [3, 4, 5, 6, 7]]                // a 2-dimensional array, that is, an array of arrays (in this case of numbers)
let iconArr : IconNames[] = [IconNames.Heart, IconNames.Butterfly]     // an array of icons (themselves an enum type)
```
So, an array is a named variable with multiple values in a specific order. The syntax of an array variable declaration is as follows:
1. We start with the keyword `let`, followed by the variable name.  
2. We continue with the colon `:` and the base type of the array, followed by the `[<cept>]`_square brackets_ `[]`.  
3. In this example, we are initializing the arrays with values. For example, the integer array `iArr` has the values `0`, `1`, and `2`.  

An array does not have to be initialized. We can fill them later:
```javascript
// Example 3.1.3

let iArr : number[] = []                                              // an empty array of integers

iArr.push(0)                                                          // add a value at the end of the array
iArr.push(1)                                                          // add a value at the end of the array
iArr.push(2)                                                          // add a value at the end of the array
```
In memory, arrays are arranged with all the elements `[<cept>]`_contiguous_, one "on top of" the other, as in this sketch:
```
// Example 3.1.4

|-------------|
|  000000000  |           // element at index 0 has value 0 in 8-bit binary
|-------------|
|  000000001  |           // element at index 1 has value 1 in 8-bit binary
|-------------|
|  000000010  |           // element at index 2 has value 2 in 8-bit binary
|-------------|
```
This allows for array elements to be read and written based on their `[<cept>]` index. Let's see how:
```javascript
// Example 3.1.5

let fArr : number[] = []

fArr.push(3.14)
fArr.push(3.142)
fArr.push(3.1416)
fArr.push(3.14159)

let pi                 = fArr[0]        // the variable pi will have the value 3.14, taken from index 0 of the array
let piMoreAccurate     = fArr[1]        // the variable piMoreAccurate will have the value 3.142, taken from index 1 of the array
let piEvenMoreAccurate = fArr[2]        // etc.
let piVeryAccurate     = fArr[3]
```
There are many operations that can be done on arrays: add elements, remove elements, get the length, etc. The best thing to do is to check out the `Arrays` package of the Advanced section in the MakeCode menue, and, once you create an array with a name, say `myFirstArray`, type this name on a new line, and then a dot `.` to see all the available functions and properties.

`[<lernact-rd>]`Loops and arrays are often used together as the loop variable can be used as the index into the array:
```javascript
// Example 3.1.6

let favoriteIcons : IconNames[] = [IconNames.Heart, IconNames.Cow, IconNames.Diamond]

for (let i=0; i < favoriteIcons.length; i ++) {     // note the use of the length property
    basic.showIcon(favoriteIcons[i])
    basic.pause(100)
}
```
Notice how we don't need to know how many elements there are in the array to get our loop correct, because we can use the `length` property of the array type.

`[<lernact-rd>]`To iterate through a 2D array, we need 2 nested `for` loops:
```javascript
// Example 3.1.7

let twoDArr : number[][] = [[1, 3, 4], [3, 4, 5]]                 // notice that the nested arrays are all the same length

for (int x=0; x < twoDArr.length; x ++) {
    for (int y=0; y < twoDArr[0].length; y ++) {
         basic.showNumber(twoDArr[x][y])
         basic.pause(100)
    }
}
```
Let's explain this code:
1. Notice the double brackets on the array declaration `[][]`. They indicate a 2-dimensional array.  
2. The 2-dimensional array has, naturally, 2 indices. The first one (on the left) is the "outer" index, in our case, indexing the nested arrays. The second one (on the right) is the "inner" index, in our case, indexing the numbers in each nested array. That's why we have `twoDArr[x][y]`.  
3. For the second index `y`, we need to only loop through the length of the nexted arrays (assuming they are the same length, as in our case). That's why we take the length like this `twoDArr[0].length`.  

`[<lernact-rd>]`There is another way to iterate through an array, using the `forEach` function, which every array has:
```javascript
// Example 3.1.8

let favoriteIcons : IconNames[] = [IconNames.Heart, IconNames.Cow, IconNames.Diamond]

favoriteIcons.forEach(function (value: IconNames, index: number) {
    basic.showIcon(value)
    basic.pause(100)
})
```
You might recognize the function-as-an-argument paradigm that is so fundamental to JavaScript. Again, it is an anonymous function, called a `[<cept>]`_callback_ function, but notice that this time it has parameters `value` and `index`. For each element of the array, this function is called, the value of the element and its index are passed in as arguments to the callback. In our case, we only need the value, which will be an icon.  

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`Extend Example 3.1.6 to show 5 different icons and, using the loop variable `i`, show each subsequent one for a shorter period of time.  
2. `[<lernact-prac>]`Show the icons from the previous program in reverse order in two different way:
   1. By manipulating the loop variable `i` to count backwords. _Hint: What would be the corresponding unary decrement operator?_  
   2. By using the arrays's `reverse()` method.  
3. `[<lernact-prac>]`Take Example 2.1.3 and create two number arrays, `xArr` and `yArr`, where the columna and row indices are _scrambled_ (that is, not in order). Then, instead of plotting `x` and `y`, use the loop variables as indices into the two arrays.

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 3.2.1 with filename `microbit-program-3-2-1.js`.  
2. Add your program from 3.2.2.1 with filename `microbit-program-3-2-2-1.js`.  
2. Add your program from 3.2.2.2 with filename `microbit-program-3-2-2-2.js`.  
3. Add your program from 3.2.3 with filename `microbit-program-3-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 3.2.1.  
2. Link to a demo video for your program from 3.2.1.  
3. Link to your program from 3.2.2.1.  
4. Link to a demo video for your program from 3.2.2.1.  
5. Link to your program from 3.2.2.2.  
6. Link to a demo video for your program from 3.2.2.2.  
7. Link to your program from 3.2.3.  
8. Link to a demo video for your program from 3.2.3.


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
**TODO:** relational
**TODO:** arithmetic
**TODO:** overloading for strings!!!
**TODO:** binary and unary
**TODO:** precedence: when not sure, enclose in parentheses `()`

**TODO:** a look at the [documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference); operators vs functions (?)


**TODO:** Switch order with [expressions](#step-6-expressions)?  

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** string concat...   
2. `[<lernact-prac>]`**TODO:** string as array...   
3. `[<lernact-prac>]`**TODO:** `in`...   

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

`[<lernact-rd>]`**TODO:** logical operators `&&` and `||`  
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
3. `[<lernact-prac>]`**TODO:** a number of custom functions with a piece of data passed as argument and re-assigned to return value... (nested function calls)... the `Point` "class" without classes...    

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

`[<lernact-rd>]`As we saw in the last program of the previous step, it became quite tedious to pass our variable around to many functions and re-assigning the changed value to keep up. This was actually such a big problem in early computing that it brought about the introduction of one of the most powerful programming paradigms, `[<cept>]`_object-oriented programming_. Objects are `[<cept>]`_user-defined composite types_, which encapsulate data along with the `[<cept>]`_methods_ (that is, functions) that can be executed against them. Objects are defined by `[<cept>]`_classes_, which are essentially _object templates_ or _object blueprints_. With this powerful programming language construct, we don't need to pass data around to various functions, trying to keep the data updated at all times. The object-oriented paradigm turn this around: now we create objects which encapsulate this data and call their methods to manipulate the data; all the bookkeeping is taken care for us.

**TODO:** the `Point` class, fields, constuctor, methods, `this`, instantiation, object lifecycle   

**TODO:** the `game.LedSprite`   

**TODO:** So, how is this a "user-defined type"? `string`, behavior, variables!  

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** class `BrightPoint` with brightness (3-dimensional point) with small program...  
2. `[<lernact-prac>]`**TODO:** class `RandomSquare` with random side (1, 2, 3) and appearing at random places in the matrix...  
3. `[<lernact-prac>]`**TODO:** class `Slytherin`, a snake with length, moving slowly from left to right or right to left, buttons up and down by one...  

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 9.2.1 with filename `microbit-program-9-2-1.js`.  
2. Add your program from 9.2.2 with filename `microbit-program-9-2-2.js`.  
3. Add your program from 9.2.3 with filename `microbit-program-9-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 9.2.1.  
2. Link to a demo video for your program from 9.2.1.  
3. Link to your program from 9.2.2.  
4. Link to a demo video for your program from 9.2.2.  
5. Link to your program from 9.2.3.  
6. Link to a demo video for your program from 9.2.3.


### Step 10: The separate lives of objects
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`**TODO:** objects are independent entities, with their own lifecycle...   
**TODO:** A glimpse at memory storage: object data vs methods...   
**TODO:** More on `this`  

**TODO:** Argument pass by reference(?)...

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** Program that spawns many sprites, doing different things...  
2. `[<lernact-prac>]`**TODO:** Program that spawns many 3-point sprites, doing different things...  
3. `[<lernact-prac>]`**TODO:** Program showcasing the lifecycle of 3-point sprites, blinking at different frequencies...  

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 10.2.1 with filename `microbit-program-10-2-1.js`.  
2. Add your program from 10.2.2 with filename `microbit-program-10-2-2.js`.  
3. Add your program from 10.2.3 with filename `microbit-program-10-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 10.2.1.  
2. Link to a demo video for your program from 10.2.1.  
3. Link to your program from 10.2.2.  
4. Link to a demo video for your program from 10.2.2.  
5. Link to your program from 10.2.3.  
6. Link to a demo video for your program from 10.2.3.


### Step 11: Inheritance with classes
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`**TODO:** What if we generally like the capabilities of `LedSprite` objects, but we are not quite satisfied? What if we want to tweak them a little bit but don't actually want to go out of our way to rewrite the whole class? One of the foremost features of object-oriented programming is the ability to fine tune classes by extending and/or specifying the object behavior they define. Because we are actually creating a new class on top of an existing one, without changing the existing one, this programming language feature is called `[<cept>]`_inheritance_. The class we are building on top of is called the `[<cept>]`_superclass_ or `[<cept>]`_base class_, and our derived class is called a `[<cept>]`_subclass_. 

In this step, we'll build a `HaloSprite` class that is almost exactly like the base `LedSprite`, but it has an optional "halo" around it which we can toggle with a button. **TODO:** 8 adjacent positions, brightness => halo

**TODO:** using a 2-dimensional array to define the halo

**TODO:** we only want to show the halo around the sprite, not having trailing behind and leaving lit LEDs, so we need to get the current position and brightness, plot the halo, pause briefly so the halo is visible, and then unplot it because the sprite will move away from the current position at the next instant

**TODO:** getting the current coordinates and brightness

**TODO:** plotting and unplotting the halo using a `for` loop

**TODO:** modifying the existing `move()` method to add the halo

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`**TODO:** Base program...  
2. `[<lernact-prac>]`**TODO:** Program to plot and unplot a halo around a certain position, toggled by button B...  
3. `[<lernact-prac>]`**TODO:** Putting it all together in `HaloSprite`...  

#### 3. Present
[[toc](#table-of-contents)]

In the [programs](programs) directory:

1. Add your program from 11.2.1 with filename `microbit-program-11-2-1.js`.  
2. Add your program from 11.2.2 with filename `microbit-program-11-2-2.js`.  
3. Add your program from 11.2.3 with filename `microbit-program-11-2-3.js`.

In the [Lab Notebook](README.md):

1. Link to your program from 11.2.1.  
2. Link to a demo video for your program from 11.2.1.  
3. Link to your program from 11.2.2.  
4. Link to a demo video for your program from 11.2.2.  
5. Link to your program from 11.2.3.  
6. Link to a demo video for your program from 11.2.3.


### Step 12: Execution with branches
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

`[<lernact-rd>]`**TODO:** How do the lines of program code that we write actually get executed. They don't, until they are transformed into processor instructions. User code to cpu instructions: overview of the compilation process...   

**TODO:** How do the language constructs - loops, conditional statements, functions, and classes - affect the execution order of sequences of processor instructions...
**TODO:**<img src="" alt="" width="" />
Assembly-level execution:
- sequential  
- branches:  
  - `if...else`  
  - loops  
  - function calls  
  - object methods  
  
#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-disc>]`**[Optional full-stack challenge, max 10 step points]** We have shown how all of our familar programming language constructs actually execute on the processor, except one, namely handling external events like `input.onButtonPressed()`. Using sketches, code snippets, documentation references, and original narrative, show how the processor handles external events. Consider using the following resources:  
   1. [The micro:bit - a reactive system](https://makecode.microbit.org/device/reactive)
   2. **TODO:** Resource links  

#### 3. Present
[[toc](#table-of-contents)]


## References and Resources

1. [JavaScript Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript).  
2. 
