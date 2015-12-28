# An Introduction to Reactive Programming

## How Does Non-Reactive Programming Work?

In programming, there are many different paradigms *(a style of programming, how a program is built)*. Ordinary programming would be **imperative**, that uses commands *(or statements)* to tell a program *how* to operate and does not care about what the program should accomplish.

    a = 10;
    b = a + 4;
    console.log(b); // 14

This is telling the computer to get the current value of `a`, add it to 4, and store that value in a variable we call `b`. What happens if we decide that `a` is no longer 10, and that it is instead 5?  

    a = 5;
    console.log(b); // 14 
    
`a` has changed from 10 to 5, so you might be expecting the value of `b` to now be 9. Why is it still 14? When dealing with any data type that is not an object, variables are passed as *values*, not as references. These data types are known as **primitive data types**. In the example above, when the computer sees `a + 4`, it looks for `a`, gets its value, and uses that to evaluate the expression.  

    a = 10;
    b = a + 4;  
  
is the same as saying 
 
    b = 10 + 4;
    
That‘s why when we change the value of `a`, the expression stored in `b` is unchanged. But what if you want `b` to change based on the current value of `a`?  

## So, How Can We Fix This?

This is where **reactive programming** comes into play. Reactive programming is a style of programming that allows data to be automatically updated based on the new values of data being referenced.  

One example you might be familiar with is in a spreadsheet program, such as Microsoft Excel or Google Documents. A cell in a spreadsheet might contain a literal value *(=10 + 4)* or a formula *(=A1 + 4)*. Now whenever the value of cell A1 changes, so does the value of the current cell. This is what we want to accomplish with our programming example. 

## Fun, Fun, Functions  

So how can we make that happen outside of a spreadsheet program?  One way we can do this is to use functions.  

    var a = 10;
    var b = a + 4;

    function updateB() {
      var sum = a + 4;
      b = sum;
    }

    updateB();
    console.log(b); // 14
    
Here we are declaring a variable `a` and assigning it an initial value of 10. We declare a variable `b` and just as in the initial example, we assign it the value of `a` plus 4. Now, we want to write a simple function that will always update the value of `b` so it reflects whatever the value of `a` is when the value of `a` is changed. I am using a named function function expression that takes the value of `a` **when the function is called**, adds it to 4, stores the value in a local variable we call `sum`, and updates the value of `b` to be that of `sum`. As you can expect, the value of `b` is still 14 after the function is called because the value of `a` has not yet changed. But what happens if we now change the value of `a` to 5?  

    a = 5;
    updateB();
    console.log(b); // 9
    
We update the value of `a` and call `updateB()`–our updater function–once again. When we call our function this time, the computer says "Hey, what‘s the current value of `a`? Oh, 5? OK. I‘ll add that to 4 and make sure `b` gets the memo."  

This is a very simple introduction to reactive programming. I hope it was even slightly helpful.

    
