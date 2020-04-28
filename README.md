## Basic

In JS, there are primitive data types and reference data types. Primitive data types are referenced by value while the non-primitive data types point to memory addresses.

A function is a process which takes some input, called arguments, and produces some output called a return value. Functions may serve the following purposes:

- ***Mapping***: Produce some output based on given inputs. A function maps input values to output values.
- ***Procedures***: A function may be called to perform a sequence of steps. The sequence is known as a procedure, and programming in this style is known as procedural programming.
- ***I/O***: Some functions exist to communicate with other parts of the system, such as the screen, storage, system logs, or network.



## Context vs. Scope

Context and scope are not the same. 

Every function invocation has both a scope and a context associated with it.

Fundamentally, scope is function-based while context is object-based. In other words, scope pertains to the variable access of a function when it is invoked and is unique to each invocation. 

Context is always the value of the this keyword which is a reference to the object that “owns” the currently executing code.

## This Keyword

In a function definition, this refers to the "owner" of the function.

<pre><code>
var person = {
    firstName:"John",
    lastName: "Doe",
    fullName: function () {
        return this.firstName + " " + this.lastName;
    }
}

person.fullName(); // Will return "John Doe"
</code></pre>

In the example above, this is the person object that "owns" the fullName function.

In other words, this.firstName means the firstName property of this object.

<hr />

## The JavaScript call() Method

The call() method is a predefined JavaScript method.

It can be used to invoke (call) a method with an owner object as an argument (parameter).

With call(), an object can use a method belonging to another object.

person.fullName.call(person1); // Will return "John Doe"

<hr />

## Closure

1.a. A closure is a function having access to the parent scope, even after the parent function has closed.

1.b. “...an inner function always has access to the vars and parameters of its outer function, even after the outer function has returned.”
by Douglas Crockford

<pre><code>
function myNonClosure() {
    var date = new Date();
    return date.getMilliseconds();
}

function myClosure() {
    //variable stays around even after function returns
    var date = new Date();
    
    //nested function
    return function () {
        return date.getMilliseconds();
    };
}
</code></pre>

<hr />

## Pure functions

A pure function is a function which given the same input, will always return the same output. Also, it produces no side effects (e.g. saving the value to disk or logging to the console), which means that it can't alter any external state.

Pure functions have many beneficial properties, and form the foundation of functional programming.

## Functional programming

Functional programming (often abbreviated FP) is the process of building software by composing pure functions, avoiding shared state, mutable data, and side-effects. Functional programming is declarative rather than imperative, and application state flows through pure functions. Contrast with object oriented programming, where application state is usually shared and colocated with methods in objects.

Functional programming is a programming paradigm, meaning that it is a way of thinking about software construction based on some fundamental, defining principles (listed above). Other examples of programming paradigms include object oriented programming and procedural programming.

<hr />

## Types of Patterns

- Creational Design Patterns
    - Instead of you having to directly instantiate objects directly, these are the ones that create them for you. The benefit of this approach is that it gives your program a little more flexibility when deciding which objects need to be created for certain situations.

- Behavioral Design Patterns
    - These patterns are focused on the communication between objects.

- Structural Design Patterns
    - And lastly, these patterns focus on class and object composition. They can be used to compose interfaces through inheritance and define ways to compose multiple objects in order to achieve new functionality.

<hr />

## Prototype Pattern

This pattern's main focus is to help create objects that can be used as blueprints for any object that are created by constructors. It does this through what's called prototypal inheritance.

It sounds like typical class objects, but in reality it avoids using classes altogether. The prototype design pattern simply creates copies of existing functional objects as opposed to defining brand new objects.

The biggest benefit of using the pattern in JavaScript is the performance boost gained as opposed to object oriented classes. This means that when you define **functions** inside an object, they will be created by reference. In other words, all child objects will point to the same method instead of creating their own individual copies!

- Pros:
    - Leverage JavaScript’s built-in features
    - “Modularize” code into re-useable objects
    - Variables/functions taken out of global namespace
    - Functions loaded into memory once
    - Possible to “override” functions through prototyping
    - Provides extension capabilities
- Cons:
    - “this” can be tricky
    - Constructor separate from prototype definition
- Memmory:
    - When we defined the methods bash and omniSlash on the prototype (Warrior.prototype.bash), the two separate instances are actually referencing the same bash and omniSlash functions!
    - If we instead defined them inside the Warrior scope, then they are not the same, so essentially JavaScript has created another copy of the supposedly same method for each instance.
- Variation:
    - The Revealing Prototype Pattern provides a way to add visibility (public versus private) to members

<hr />

## Module Pattern

The Module Pattern is one of the important patterns in JavaScript. It is a commonly used Design Pattern which is used to wrap a set of variables and functions together in a single scope. It is used to define objects and specify the variables and the functions that can be accessed from outside the scope of the function.

- Pros:
    - “Modularize” code into re-useable objects
    - Variables/functions taken out of global namespace
    - Expose only public members while hiding private members
- Cons:
    - Functions may be duplicated across objects in memory when not using singleton
    - Not easy to extend
    - Some complain about debugging
- Memmory:
    - Each object instance creates new copies of functions in memory
- Variation:
    - With Revealing Module Pattern we can have a cleaner way to expose public members compared to Module pattern