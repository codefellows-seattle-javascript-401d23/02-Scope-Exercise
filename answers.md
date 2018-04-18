1. When this code is run in Node, e.g. node index.js, what are the two stages of execution for this file called, and which order do they happen in?

Answer: The first stage is compilation/hoisting and the second stage is interpretation/execution.

2. Write an explanation, using as much space as you need, relating to how the first stage of execution for this file operates.

  - For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.

Answer: During the compilation/hoisting phase in the global scope, it runs through and sees the delaration of a variable `foo` and a function `bar`. These are hoisted to the top and not assigned values at this point. 

3. Write an explanation, using as much space as you need, relating to how the second stage of execution for this file operates.

- For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.

Answer: Now when the code executes it runs through and assigns the value of 'bar' to `foo` and then invokes the function `bar()`, at which point it looks inside it and compiles/executes the code inside.

4. During the second stage of execution how many scopes have been registered by the engine?
Answer: I see 3 scopes. 

- Which segments of the code do they belong to?

Answer: Global scope, inside the function `bar()` and then inside the function `baz()`.

- Please identify any variables/refs and which scope each belongs to?

Global: `foo`, `bar()`
bar(): `baz()`
baz(): `bam` (never declared)

5. When line 13 invokes the baz function, which foo will be assigned a value of bam? More specifically, bam will be assigned to the foo in ??? scope. Give a brief description in your own words to support your conclusion.

Answer: When `baz()` is invoked without an argument there is no parameter so `foo` inside `baz` is undefined...so nothing is assigned the value of 'bam'.

6. Which scope, if any, will the variable bam on line 11 be registered to when the first stage of execution occurs on this file? Provide a brief description in your own words to support your conclusion.

Answer: It will not be registered on the first stage of execution because it is not declared. Since it's never declared it's never hoisted inside the function where it appears.

7. For each line, 16 through 19, what is the return value for each?

Answer: 

`bar()` doesn't return anything because the code breaks before it runs completely. If the code doesn't break it would return undefined because it does not return anything.

`foo` has the value of 'bar' on line 17 (if the code is changed to not break).

`bam` has no return value - it throws a reference error (never declared).

`baz` returns undefined because it does not return anything (it also breaks before it completes)