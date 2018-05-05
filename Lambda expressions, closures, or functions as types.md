# [HomePage](README.md)

Lambda's take on a more meaningful role in C# than in Java.

## Java

Lambda's were added to Java in 8.0, and the move was a good one.  For interfaces one of the best ways to use them was with functional interfaces with one method. Lamdas look at an implmeentation of functional interfaces.

Here is an example of a funcitonal interface:

```
interface SomeInterface {
    int doSomething(int o);
}
```

And using it in code as a lambda expression:

```MyInterface interface -> //code to be excecuted in the method```

It is a lot easier to use functional interfaces as well as make it cleaner and easier to read code.

## C# 

Lamda works as the following, the variable on the left of => is a parameter and the right side is the return.  The
following is an example.

```y => y*y;```

Lambda expressions are used to do different things in C#, and it's mainly twofold.

1. Delegates: Here is an example

  ```del myDelegate = y => y*y;```

Lambda functions are used in a similar way to anonymous delegates.  On top of Java they can be converted to expression trees.  These Lammda expressions can pass values to the function without adding parameters to the function call. 

2. Expression Trees: A binary tree like structures where each node is an expression.  This is extremely helpful as they are able to dynamically modify code, execute LINQ and so much other things.

The following is an example to utilize Expression Trees:

```Expression<Function<double, bool>> lamExp = number => number >15;```
    
The compiler only recognizes one line lambda expressions and doesn't recognize multiple line lambda's.
