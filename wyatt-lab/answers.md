# Lab 02 - Scope Exercise
## Wyatt Pefley
## Questions:
### Question 1: 
When this code is run in Node, e.g. node index.js, what are the two stages of execution for this file called, and which order do they happen in?
  - Answer: The two stages of execution for this file would be hoisting and interpretation or execution. in that order.
### Question 2:
- Write an explanation, using as much space as you need, relating to how the first stage of execution for this file operates.

  - For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.
- Answer: During compilation  the code will be run through and keeps track of what functions and variables are declared and "hoists" them to the top to be used later.
### Question 3:
Write an explanation, using as much space as you need, relating to how the second stage of execution for this file operates.

For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.
- Answer: During execution, the code is executed and assigns values to the variables that were found during the previous stage, functions that were hoisted are also invoked during this stage as well. In the global scope, foo is assigned the value of 'bar', and within the bar() function, foo is re-assigned 'baz', and then re-assigned again as 'bam' within the scope of the baz() function. After that, the code attempts to assign 'yay' to the variable bam within the baz function, however since bam was never actually declared, this will cause an error. During this phase, or functions will be invoked as well.
## Question 4:
During the second stage of execution how many scopes have been registered by the engine?
Which segments of the code do they belong to?
Please identify any variables/refs and which scope each belongs to?

- Answer: In this code, there are three scopes. The first being the global scope, the second being baz(), and the third being bar().
- var foo = 'bar' (this is global scope)
- Baz()'s scope is from lines 8-12. Function bar()'s from lines 5-14, and the global scope contains everything outside of bar() & baz()'s scope. The lines that are in baz()'s scope are not included within bar()'s scope. The foo variable belongs to every scope because it was assigned to 'bar' in the global scope, 'baz' in the bar() scope, and 'bam' in the baz() scope. The other variable assignment, bam is in the baz() scope, however it will throw an error. The function bar() is in the global scope and function baz() within the bar() scope.
### Question 5:
When line 13 invokes the baz function, which foo will be assigned a value of bam? More specifically, bam will be assigned to the foo in ??? scope. Give a brief description in your own words to support your conclusion.
- When the baz() function is called, it first references its own scope and finds that foo is declared and has been assigned a value. If it had not found foo within it's own scope, it would have moved outward and taken the assignment from the bar() scope, moving to the global scope if it did not find it in bar().
### Question 6:
Which scope, if any, will the variable bam on line 11 be registered to when the first stage of execution occurs on this file? Provide a brief description in your own words to support your conclusion.
- Answer: No scope because this actually throws a referance error because it is not declared and therefore is not hoisted either. If there strict mode was disabled however, it would not throw an error.
### Question 7:
For each line, 16 through 19, what is the return value for each?
- Answer: bam() - Throws reference error if strict mode is enabled
- bar () - undefined
- baz() -  Throws Another reference error
- foo - 'bar'