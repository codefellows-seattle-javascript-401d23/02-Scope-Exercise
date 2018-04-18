<!-- Questions:
When this code is run in Node, e.g. node index.js, what are the two stages of execution for this file called, and which order do they happen in? -->

The file stages are compilation and interpretation. Compilation happens first, then interpretation happens.

<!-- Write an explanation, using as much space as you need, relating to how the first stage of execution for this file operates. -->

In compilation, every variable and function that is initialized has some space allocated for it, in advance of the values it will receive. For example, var foo is set aside as a unique memory location, as well as functions bar, baz, and var bam. 

<!-- For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing. -->

Each line that initializes a function or variable is performing this first step. 

<!-- Write an explanation, using as much space as you need, relating to how the second stage of execution for this file operates. -->

The second stage is compilation. Now the variables prepared in step 1 can be assigned values and otherwise manipulated within the program space. For example, var foo is assigned the string 'bar', function 'bar' is defined as containing a certain amount of latent information. Finally the functions and variables are called, to output their values.

<!-- For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing. -->

In line three, string 'bar' is assigned to key foo. In line five, a function under name bar is filled with other information, including a variable reassignment and a new function declaration, baz, which takes var foo as an argument. Lines 10 and 11 are variable assignments; line 11 is a declaration and assignment condensed into one line. 
Line 13 is a function call which activates baz. 
Finally, bar, foo, bam, and baz are all called.

<!-- During the second stage of execution how many scopes have been registered by the engine? -->

Three scopes-- the global, or window scope, and two scopes within functions, bar and baz.

<!-- Which segments of the code do they belong to? -->

The first includes all the code. the scope for bar includes the variable reassignment of foo to 'baz', as well as function 'baz', its sub-scope, and its function call. 
The scope for function baz includes two variable (re)assignments.

<!-- Please identify any variables/refs and which scope each belongs to? -->

foo - global
bar - global
baz - in scope of bar
foo (line 11) - still global, though reassigned locally
bam - local to baz

<!-- When line 13 invokes the baz function, which foo will be assigned a value of bam? More specifically, bam will be assigned to the foo in ??? scope. Give a brief description in your own words to support your conclusion. -->

Bam will be assigned to the global foo, because there is only one foo. Despite this variable being modified in a local context, it still exists in only one place in memory and therefore will be modified as the program runs live. 

<!-- Which scope, if any, will the variable bam on line 11 be registered to when the first stage of execution occurs on this file? Provide a brief description in your own words to support your conclusion. -->

Bam will be registered within the scope of function baz. Functions provide a local scope and since bam is declared and initialized within baz, it operates in that scope.

<!-- For each line, 16 through 19, what is the return value for each? -->

line 16 doesn't return anything, it only modifies and instantiates values.
line 17 returns 'bam', the latest assignment to foo.
line 18 returns a reference error, because bam does not exist in the global scope.
line 19 also returns a reference error, because baz is only defined in the scope of function bar.