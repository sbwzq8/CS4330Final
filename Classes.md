# [HomePage](README.md)

### Classes in java and C# are very similar to one another in declaration, but there are many differences as well, including packaging and properties.

# Defining Classes

## java
#### In defining classes in java, they must be in a class code block with fields and methods defined within the scope of the class. Proper formatting in java includes Pascal case Class names and Constructors with camel case fields and methods. Constructors must have the same name as the class. Classes are contained in packages in java which must conform with the directory structure.
```Java
package javaexample;

public class ThisIsAJavaClass{
    //       ^--Pascal case class
    public String javaString = "This is a string in java";
    //            ^--camel case field
    public String emptyJavaString;

    public ThisIsAJavaClass(String initializeString){
    //     ^^^^^^^^^^^^^^^^--Constructor must have same name as class
        this.emptyJavaString = initializeString;
    }

    public void printThisJavaString(String javaString){
    //          ^--camel case method
        System.out.println(javaString);
    }
}
```
---
## C#
#### In defining classes in C#, they must be in a code block with the properties/fields and methods defined within the scope of the class. Proper formatting in C# includes Pascal case Class names, constructors, properties/fields and methods. Constructors must have the same name as the class. Classes are contained in namespaces in C# which do not have to conform with the directory structure.
```CS
namespace CSharp_example
{
    public class ThisIsACSharpClass
    {
            //   ^--Pascal case Class
            public string CSharpString = "This is a C# String";
            //            ^--Pascal case Properties
            private String _EmptyDotNetString;

            public ThisIsACSharpClass(string initializeString)
            //     ^^^^^^^^^^^^^^^^^^--Constructor must have same name as Class
            {
                this.EmptyDotNetString = initializeString;
            }

            public void PrintThisCSharpString(string CSharpString)
            //          ^--Pascal Case method
            {
                Console.WriteLine(CSharpString);
            }
    }
}
```
---
# Creating new instances of Classes using constructors
#### In both languages, when instantiating an object from a class, the "new" keyword must be used to construct a class.

## java
```Java
package javaexample;

public class MainClass{
    public static void main(){
        ThisIsAJavaClass newClass = new ThisIsAJavaClass("Hello World!");
    }
}
```

## C#
```CS
namespace CSharp_example{
    class Program
    {
        static void Main(string[] args)
        {
            ThisIsACSharpClass newClass = new ThisIsACSharpClass("Hello world!");
        }
    }
}
```
---
# Destructing/de-initializing

# java
#### In java, objects are destructed through the garbage collector. You don't have to do anything at all, once the object is no longer referenced, the garbage collector will hit it with the most dangerous number in computing: 9.

```java
package javaexample;

public class MainClass{
    public static void main(){
        ThisIsAJavaClass newClass = new ThisIsAJavaClass("Hello World!");

        newClass = null;
    }
}
```

# C#
#### In C#, objects are desctructed with a finalizer. Finalizers, like constructors have the same name as the class, but begin with a "~" and take in no arguments. They are called when the object no longer has a reference to it. Finalizers were used in C++, but the .Net framework uses garbage collectors so it is uncommon to use them. Basically, you dont need to implement finalizers, but you can if you want to, but why would you because .NET will do it for you.
```CS
namespace CSharp_example
{
    class Program
    {
        static void Main(string[] args)
        {
            ThisIsACSharpClass newClass = new ThisIsACSharpClass("Hello world!");

            newClass = null;

        }
    }
    class ThisIsACSharpClass
    {
        public string SomeInitializedValue;

        ~ThisIsACSharpClass(){}
        //waste of energy to type this out
    }
}
```
