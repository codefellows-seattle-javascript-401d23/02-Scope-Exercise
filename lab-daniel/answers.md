#### Questions:
1. When this code is run in Node, e.g. `node index.js`, what are the two stages of execution for this file called, and which order do they happen in?

Answer: LHS and RHS, first LHS, then RHS.

2. Write an explanation, using as much space as you need, relating to how the first stage of execution for this file operates.
    - For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.

Answer: The first step compiles (LHS) by assigning variables and function declarations to memory. It begins in the global scope and assigns foo and bar() to memory, when it hits the bar() function it assigns 'foo' and 'baz()' to the scope of bar. When it hits 'baz()' it assigns the 'foo' identifier and 'bam' to 'baz()'. After that it recognizes that 'foo' and 'bam' have already been saved to memory.

3. Write an explanation, using as much space as you need, relating to how the second stage of execution for this file operates.
    - For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.
Answer: The second step is the actual execution phase (RHS) which assigns values to the LHS logged variables and functions. The first RHS operation detects 'foo' and assigns the string of 'bar' to it, it then skips down to where the first function is invoked at 'bar()' and executes it by changing the 'foo' variable to 'baz' thus shadowing the global 'foo' variable. Then it executes baz() and returns 'foo' for assignment. While still in the baz function it checks if 'bam' has been logged to memory and traverses up the scopes until it hits global where it logs 'bam' to memory. The final step of this phase checks where baz is invoked and throws a reference error because there is no identifier 'baz'.

4. During the second stage of execution how many scopes have been registered by the engine?
    - Which segments of the code do they belong to?
    - Please identify any variables/refs and which scope each belongs to?

Answer: There are 3 scopes:
- the global scope contains the 'foo' variable and 'bar()' function.
- the bar() scope contains the 'foo' variable and 'baz()' function.
- the baz() scope contains the 'foo' variable.

5. When line 13 invokes the `baz` function, which `foo` will be assigned a value of `bam`? More specifically, `bam` will be assigned to the `foo` in ??? scope. Give a brief description in your own words to support your conclusion.

Answer: 'bam' will get assigned to the foo in the 'baz()' function scope as 'foo' was only an identifier in the 'baz()' function. Before the 'baz()' function assigns 'bam' to 'foo', 'foo' would be undefined in this scope. So after the file has ran its course the 'foo' in the global scope would be 'bar', the 'foo' in the 'bar()' scope would be 'baz', and the 'foo' in the 'baz()' scope will be 'bam' after assignment (line 10).

6. Which scope, if any, will the variable `bam` on line 11 be registered to when the first stage of execution occurs on this file? Provide a brief description in your own words to support your conclusion.
Answer: 'bam' will be registered to the global scope due to hoisting as the compiler traverses up the scopes looking for its declaration. As for my support, this file will incur a ReferenceError at this line which means a LHS error during compilation.

7. For each line, 16 through 19, what is the return value for each?
Answer: The return value for each line is:
- bar() = undefined
- foo; = 'bar'
- bam; = ReferenceError
-baz() = ReferenceError
