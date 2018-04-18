
1. When this code is run in Node, e.g. node index.js, what are the two stages of execution for this file called, and which order do they happen in?

  the code is executed in two stages-- first the compiler goes through looking for any variables to hoist
  then the engine goes through looking for code to execute.

2. Write an explanation, using as much space as you need, relating to how the first stage of execution for this file operates.

- For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.

I don't understand in what order the hoisting occurs.





3. Write an explanation, using as much space as you need, relating to how the second stage of execution for this file operates.

- For example, identify the high level steps in a line by line overview and then define what each of those steps are accomplishing.

But the engine goes to the first line of executable code at bar();
it looks for bar, the compiler returns bar as a function at line 5.
so the engine goes inside the function and looks for more functions to execute, it hits
line 13, baz(); ok, what's baz? the compiler says, its a function at line 8. 
so the engine goes to line 8 and sees ok, we have a function now what's foo? the compiler looks for foo being defined at 13, null.  the engine is like cool, and goes into the function (what do I do here)-- it see's foo, hey compiler do you have foo? compiler is like yeah, its null! <-- here's where I get confused
is foo reassiagned to bam at this point? then bam is reasssigned yay? or is all broken because no argument was passed in?

regardless, we're done and the engine runs bar(); returning either 'yay' or referenceError it does return a reference error... i just don't totally get why.

cool now the code goes is there anything more for me to do, it looks up foo, is foo then bam? cause bar ran?
then it looks up bam-- which I guess is a referenceError 
then it would look up baz()-- baz is a function with all the issues mentioned above?

4. During the second stage of execution how many scopes have been registered by the engine?
Which segments of the code do they belong to?
Please identify any variables/refs and which scope each belongs to?

there is the global scope containing 'foo' holding 'bar' and 'bar' holding a function.
then there is the scope of 'bar' which contains foo holding 'baz', baz holding a function.
then there is the scope of baz contains foo holding bam, and bam holding yay.

 
5. When line 13 invokes the baz function, which foo will be assigned a value of bam? More specifically, bam will be assigned to the foo in ??? scope. Give a brief description in your own words to support your conclusion.
when baz() is invoked on 13, foo is assigned the value in the ()'s in this case, nothing, foo=null. so the scope of baz as it's invoked, not as its defined?

6. Which scope, if any, will the variable bam on line 11 be registered to when the first stage of execution occurs on this file? Provide a brief description in your own words to support your conclusion.

bam will be registered to the global scope? I don't understand the first compiling stage! will it be defined within the scope of the function definition of baz?

7. For each line, 16 through 19, what is the return value for each?

16-returns reference error, because nothing is passed to baz when it's invoked inside bar!
17- I would say... I'm not sure, has it mutated now because bar ran, so it's null?
18- bam is undefined because it is only assigned within the scope of baz(), but not returned by it.
19-baz() is undefined because it is only assigned within the scope of baz(), but not returned by it.  