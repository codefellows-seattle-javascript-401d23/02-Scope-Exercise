#Scope and Context

Given the code linked HERE, answer the set of questions below. Please copy the questions to your lab directory in a file called answers.md.
Questions:

##1. When this code is run in Node, e.g. node index.js, what are the two stages of execution for this file called, and which order do they happen in?
- The two stages are compiler phase and execution phase with the compiling happening first. Compiling being the declaration of the variables and hoisting not including assignments of variables or functions this is execution phase.  

##2. Write an explanation, using as much space as you need, relating to how the first stage of execution for this file operates.
For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.
- The compiler stage for the linked file includes the following: @line 3 var foo is declared as a global variable. @ line 5 function bar() is globally declared. @ line 6 var foo is functionally declared for a second time block scope. @line 8 function baz is declared with parameter foo. This completes the compiling stage of execution for this file. 

##3. Write an explanation, using as much space as you need, relating to how the second stage of execution for this file operates.
For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.
- The execution stage of the linked file includes the following steps: @ line 3 global variable of foo is assigned the string bar. @ line 16 global function of bar is assigned the function, and now we execute it. Now to line 6 foo variable is returned for assignment (shadowing the global scoped variable.) On to line 13 in the scope of bar we have baz function call, back to line 10 where variable foo scope of baz and is assigned the value. Now onto line 11 for variable bam, going up the scopes since this variable does not have any reference in the current scope all the way up to global scope. 

##4. During the second stage of execution how many scopes have been registered by the engine?
Which segments of the code do they belong to?
Please identify any variables/refs and which scope each belongs to?
- There are 3 different levels of scope, global which had declaration of foo @ 3 and the function of bar @ 5. The second is the functional scope of the function bar, this contains the second declaration of foo @6 and the function baz @8. 

##5. When line 13 invokes the baz function, which foo will be assigned a value of bam? More specifically, bam will be assigned to the foo in ??? scope. Give a brief description in your own words to support your conclusion. 
- This will assign the baz scoped variable to bam, even though the variable scoped to bar is set to baz and passed into the function, because the assignment is inside of the function once the parameter is already used. 

##6. Which scope, if any, will the variable bam on line 11 be registered to when the first stage of execution occurs on this file? Provide a brief description in your own words to support your conclusion.
- In the first stage of execution this will not be accessed since there is no left hand side declaration. During the second stage this will be hoisted to the global scope because it is a reference variable. 

##7. For each line, 16 through 19, what is the return value for each?
- Line 16 returns nothing just calls the function of bar and subsequently baz.
- Line 17 returns 'bar' since global scoped reference to foo variable.
- Line 18 returns 'yay' since this got bubbled up to global scope. 
- Line 19 returns a reference error since there is no identifier of baz in the global scope. 
