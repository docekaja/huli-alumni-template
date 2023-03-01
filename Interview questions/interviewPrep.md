# YouTube interview videos:

## 1) What is the difference between GET and POST when making an AJAX (Asynchronous JavaScript and XML) request?

- two different types of HTTP request
- use GET when retrieving data
- use POST when sending data to create resourse

## 2) What does JSON stands for?

- JavScript object notation
- basically a text-based data format that is easy to transfer information across the web

## 3) What is the difference between == and === ?

- The == operator checks equality only, whereas === checks equality, and data type, i.e., a value must be of the same type.

## 4) What is the difference between null and undefined?

- null: intentional absence of value
- undefined: variable not declared or defined

## 5) What is the difference between var, let and const?

- var was the original way to declare variables in JavaScript. It is function-scoped, which means that variables declared with var are accessible within the function they were declared in or, if they are not declared within a function, they become global variables.
- let and const are both block-scoped, which means that variables declared with let and const are only accessible within the block they were declared in.
- let can be reassigned a new value, but the variable cannot be redeclared in the same scope.
- const, on the other hand, cannot be reassigned a new value and the variable cannot be redeclared in the same scope.

## 6) Explain higher order functions.

- In JavaScript, a higher-order function is a function that either takes one or more functions as arguments or returns a function as its result. This means that higher-order functions can abstract over actions, behaviors, or computations, allowing us to write more generic and reusable code.

        function repeat(func, num) {
          for (let i = 0; i < num; i++) {
            func();
          }
        }

        function greet() {
          console.log('Hello!');
        }

        repeat(greet, 3);

- In this example, repeat is a higher-order function that takes a function func and a number num as its arguments. repeat then calls func num times in a loop. Greet is a simple function that logs 'Hello!' to the console. Finally, repeat(greet, 3) is calling the repeat function with greet as the func argument and 3 as the num argument. This will log 'Hello!' to the console three times.
- Higher-order functions are useful in JavaScript because they allow us to write more generic and reusable code by abstracting over actions, behaviors, or computations. We can pass functions as arguments to higher-order functions or return functions from them to create more flexible and powerful code.

## 7) What are arrow functions? Describe differences between arrow functions and regular JS functions.

- Arrow functions are a shorthand way of writing functions in JavaScript.

        const multiply = (x, y) => x * y;
        console.log(multiply(2, 3)); // output: 6

- Syntax: Arrow functions have a more concise syntax than regular JS functions, which can make them easier to read and write.
- this binding: Arrow functions do not have their own this binding. Instead, the this value inside an arrow function is lexically bound to the this value of the enclosing execution context. This means that arrow functions are generally not suitable for methods that need to access their own this value.
- arguments object: Arrow functions do not have their own arguments object. Instead, they inherit the arguments object from their enclosing function.
- new keyword: Arrow functions cannot be used as constructors with the new keyword, since they do not have their own this binding.
- function keyword: Arrow functions do not use the function keyword to define a function, which can be confusing to developers who are used to the traditional function syntax.

        function Person(name, age) {
          this.name = name;
          this.age = age;
        }

        const john = new Person('John', 30);
        console.log(john.name); // output: John

- Arrow functions are a shorthand way of writing functions in JavaScript that have some differences compared to regular JS functions, such as the way they handle this and arguments. Arrow functions can be useful for writing concise and easy-to-read code, but they may not be suitable for all situations.

## 8) What is JavaScript event loop and call stack?

- The call stack is a data structure that JavaScript uses to keep track of function calls in a program. Whenever a function is called, a new frame is added to the top of the call stack, which contains information about the function, such as its arguments and local variables. When the function returns, its frame is removed from the top of the call stack.

        function func1() {
          console.log('func1');
        }

        function func2() {
          func1();
          console.log('func2');
        }

        function func3() {
          func2();
          console.log('func3');
        }

        func3();

- In this example, the func3 function is called first, which then calls func2, which in turn calls func1. Each time a function is called, a new frame is added to the top of the call stack. When a function returns, its frame is removed from the top of the call stack. The output of this program will be: func1, func2, func3

## 9) What are JavaScript promises and name a usecase.

- Promises have three states: pending, fulfilled, and rejected. When a promise is created, it is in the pending state. Once the asynchronous operation is completed successfully, the promise is fulfilled and moves to the fulfilled state. If the asynchronous operation fails, the promise is rejected and moves to the rejected state.
- A use case for promises is when making HTTP requests. For example, when you want to fetch data from a server using an HTTP request, you can use the fetch API to make the request and return a promise. You can then use the then method to handle the response and the catch method to handle any errors that occur. This makes it easy to write asynchronous code that is easy to read and maintain.

## What is hoisting

- Hoisting is a JavaScript mechanism that allows variable and function declarations to be moved to the top of their respective scopes before code execution. This means that you can use a variable or a function before it has been declared in your code. However, it is important to note that only the declarations are hoisted, not the initializations. This means that even though you can use a variable or a function before it has been declared, its value will be undefined until it has been initialized.

        console.log(myVariable); // undefined
        var myVariable = 10;

        function myFunction() {
          console.log('Hello, world!');
        }

        myFunction(); // 'Hello, world!'

- In this example, the myVariable variable and the myFunction function are declared after they are used, but they are still accessible. This is because their declarations are hoisted to the top of the scope. However, the value of myVariable is undefined until it is initialized to 10 on the second line of the code.

        function myFunction() {
          console.log(myVariable); // undefined
          var myVariable = 20;
          console.log(myVariable); // 20
        }

        myFunction();

- While hoisting is a well-known behavior in JavaScript, it does not apply equally to all types of variables and functions. In particular, let and const variables and function expressions behave differently from var variables and function declarations with regard to hoisting.
- let and const variables are not hoisted in the same way as var variables. While the declaration is hoisted to the top of their block, they are not initialized until the line where they are declared is executed. This means that you cannot use a let or const variable before it is declared.

        console.log(myVariable); // ReferenceError: myVariable is not defined
        let myVariable = 10;

- Function expressions also behave differently from function declarations with regard to hoisting. While function declarations are hoisted to the top of their scope and can be used before they are declared, function expressions are not hoisted in the same way.

        myFunction(); // TypeError: myFunction is not a function
        const myFunction = function() {
          console.log('Hello, world!');
        };
