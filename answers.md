#### Questions and Answers:
1. When this code is run in Node, e.g. `node index.js`, what are the two stages of execution for this file called, and which order do they happen in?
    * First: compilation
    * Second: execution
2. Write an explanation, using as much space as you need, relating to how the first stage of execution for this file operates. For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.
    * Tokenizing/Lexing: Break up each line into chunks that are meaningful to the JS engine. Line 3 might be broken into `var`,`foo`,`=`, `'bar'`,`;`. Each of those chunks is a 'token', which will be used in the next step, parsing.
    * Parsing: turn the tokens into a tree that reflects how all the tokens relate to each other, representing the entire program.
    * Code-Generation: turn the parsed tree into machine language to be executed by the computer.
3. Write an explanation, using as much space as you need, relating to how the second stage of execution for this file operates. For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.
    * Look up each variable to determine either 
      * its current value (which is called a Right-hand Side or RHS lookup), or
      * its memory location (which is called a Left-hand Side or LHS lookup).
   
     RHS lookups are preparing to use the value of the variable. LHS lookups are preparing to assign value to that variable. The answers to these lookups depend heavily on scope, as they may be completely different in different contexts.
4. During the second stage of execution how many scopes have been registered by the engine? Which segments of the code do they belong to? Please identify any variables/refs and which scope each belongs to?
    * Three scopes: 
      * global scope: var `foo`, function `bar`
      * function `bar` scope: var `foo`, function `baz`
      * function `baz`scope: parameter `foo`

5. When line 13 invokes the `baz` function, which `foo` will be assigned a value of `bam`? More specifically, `bam` will be assigned to the `foo` in ??? scope. Give a brief description in your own words to support your conclusion.
    * `bam` will be assigned to the `foo` in the `baz` scope, because when the engine does a lookup on `foo` in line 10, it first looks in local scope (which is the function `baz`) to see if `foo` exists there. It will find that, yes, `foo` has been declared as a parameter of the `baz` function, so it will not continue on to look in the global scope, it will just use the local `foo`.

6. Which scope, if any, will the variable `bam` on line 11 be registered to when the first stage of execution occurs on this file? Provide a brief description in your own words to support your conclusion.
    * `bam` will not be assigned a scope because `bam` has not been declared and 'use strict' mode has been specified. It will return a ReferenceError when the program is run. If we remove 'use strict' mode, then declaration of `bam` is assumed, and it will be registered to the scope of `baz()`, which is inside the scope of `bar()`.

7. For each line, 16 through 19, what is the return value for each?
    * 16: ReferenceError: bam is not defined. The `bar` function can't execute because `bam` is not defined. If we remove the `bam` declaration, then `bar` will execute, though it still returns nothing.
    * 17: If you removed the other lines that produce errors so this line could execute, this line would still not return anything because it's just a variable name. It would have the value `bar`, but it wouldn't do anything with it.
    * 18: ReferenceError: bam is not defined. This error will be produced even if we remove 'use strict' mode. Even if declaration of `bam` is assumed, it's still declared inside the scope of `baz`, inside `bar`, so it doesn't exist at line 18 which is in the global scope.
    * 19: ReferenceError: baz is not defined. Although it is defined inside the scope of function `bar`, line 19 is in the global scope so there is no `baz` here.
