![cf](https://i.imgur.com/7v5ASc8.png) 02: Tools and Context
======

## Feature Tasks
#### Scope and Context
Given the code linked [HERE](https://gist.github.com/sjschmidt44/556d31146a2b1ff3be84820e5fc06959), answer the set of questions below. Please copy the questions to your lab directory in a file called `answers.md`.



#### Questions:
1. When this code is run in Node, e.g. `node index.js`, what are the two stages of execution for this file called, and which order do they happen in?

The interpretor for JavaScript, and in this case Node, has 2 stages it goes through when interpretting a JS file. This first is an overview of the entire file, it collects information based on declaration. If data has been declared it is stored as a reference for the second stage.
During the first stage Node will find global and local variable and function names, noting the context in which they are declared (i.e. let, var, const, function, object).
During the second stage Node will start executing the code from top to bottom.

2. Write an explanation, using as much space as you need, relating to how the first stage of execution for this file operates.
    - For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.

During the first stage Node will take note "foo" is a var, "bar" is a function and "baz" is a function. It also notes that "bam" is not declared.

3. Write an explanation, using as much space as you need, relating to how the second stage of execution for this file operates.
    - For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.

During the second stage Node will execute the code from top to bottom. It is here where the code will break if it has any errors. For this file "bam" is not declared so the interpretor throws a Reference Error in the output.

4. During the second stage of execution how many scopes have been registered by the engine?
    - Which segments of the code do they belong to?
    - Please identify any variables/refs and which scope each belongs to?

Three scopes have been identified. Global scope, Local scope for "bar" function and Local scope for "baz" function.

5. When line 13 invokes the `baz` function, which `foo` will be assigned a value of `bam`? More specifically, `bam` will be assigned to the `foo` in ??? scope. Give a brief description in your own words to support your conclusion.

When the "baz" function is called inside of the "bar" function, no parameter is passed and "foo" is assigned a new value of 'bam', where previously it was declared as a var and assigned the value of 'bar'. This assignment of 'bam' to "foo" is affecting the assignment of the global variable "foo".

6. Which scope, if any, will the variable `bam` on line 11 be registered to when the first stage of execution occurs on this file? Provide a brief description in your own words to support your conclusion.

"bam" has not been declared and therefore throws a Reference Error. Because declarations are observed during the first stage this code never goes to execution. This also means it has no scope because it has not been declared.

7. For each line, 16 through 19, what is the return value for each?

This file does not have any return statements, so nothing would ever be returned. This code is also blocked by "bam" not being declared and given scope. IF this file was to be looked at from a pseudo code p.o.v. the following COULD be ASSUMED:
line 16: undefined, because there is no return
line 17: 'bam',  because it is called after bar(), which reassigned "foo" to 'bam' from previously 'bar'.
line 18: 'yay', because "bam" is used only once and that is simply to have 'yay' assigned to it.
line 19: undefined, because it have no return statement
