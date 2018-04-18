Question 1:
When this code is run in Node, e.g. node index.js, what are the two stages of execution for this file called, and which order do they happen in?

Answer 1:
The two stages are called compile and execution, in that order. 

Question 2:
Write an explanation, using as much space as you need, relating to how the first stage of execution for this file operates. For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.

Answer 2:
The first stage can be broken down into two actions. This stage uses a compiler which does all of the parsing and code-generation. The compiler first looks through the code and finds variables. If the variable already exists for that particular scope collection, it ignores the declaration and moves on. If they were not previously defined in the current scope, it declares a variable. Next, it assigns the value to the variable in scope, which the engine will use later to execute. 

Question 3:
Write an explanation, using as much space as you need, relating to how the second stage of execution for this file operates. For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.

Answer 3:
The second stage involves an engine. When the engine runs, it will first look at scope to see if the variable is accessible in the current scope collection. If it is, the engine will use the variable and the value the compiler assigned in stage one. If it is not, the engine will move out and keep looking for it.  

Question 4:
During the second stage of execution how many scopes have been registered by the engine? Which segments of the code do they belong to? Please identify any variables/refs and which scope each belongs to?

Answer 4:
Three scopes have been registered. var foo = 'bar', function bar(), and function baz(foo). var foo = 'bar' (global), var foo = 'baz' (function bar()), foo = 'bam' (function baz(foo)), bam = 'yay' (function baz(foo)).

Question 5:
When line 13 invokes the baz function, which foo will be assigned a value of bam? More specifically, bam will be assigned to the foo in ??? scope. Give a brief description in your own words to support your conclusion.

Answer 5:
Just the one that is being defined at that scope, bam will be assigned to the foo in the function baz(foo) scope. The baz function is the inner most bubble, therefore, bam is only be passed to the foo that is defined at that level when that function is invoked. 

Question 6:
Which scope, if any, will the variable bam on line 11 be registered to when the first stage of execution occurs on this file? Provide a brief description in your own words to support your conclusion.

Answer 6:
It will not be registered at all. Because we are using strict, since bam is never defined, it will not declare it, and therefore, will not be executed and will return a reference error. 

Question 7:
For each line, 16 through 19, what is the return value for each?

Answer 7:
line 16 - ReferenceError: bam is not defined
line 17 - 'bar'
line 18 - ReferenceError: bam is not defined
line 19 - ReferenceError: bam is not defined