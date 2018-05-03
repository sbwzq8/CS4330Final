# [HomePage](README.md)

### Comparing value and reference types between these 2 languages are very different.

## java
#### In java, comparing primitive data types can be done with the == operator, while comparing objects needs to be done with the equals() method of object. When comparing user defined objects, the equals() method of object needs to be overriden

### Lets compare primitives first
```java
package finalproject;

public class Finalproject
{
    public static void main(String[] args)
    {
        int int1 = 5;
        int int2 = 5;
        System.out.println(int1 == int2);
        //returns true - primitive types are equal in value since their references are the same
        
        Integer wrapperInt1 = new Integer(5);
        Integer wrapperInt2 = new Integer(5);
        System.out.println(wrapperInt1 == wrapperInt2);
        //returns false - references are not the same
        System.out.println(wrapperInt1.equals(wrapperInt2));
        //returns true - objects are unwrapped and their primitive data types are checked
        System.out.println(wrapperInt1.equals(int1));
        //returns true - wrapperInt1 is unwrapped and the primitive inside is compared to int1
    }
}
```
### Now let's try to compare a user defined object
```java
package finalproject;

public class Finalproject
{
    public static void main(String[] args)
    {
        Person person1 = new Person(24, "Sean");
        Person person2 = new Person(24, "Sean");
        System.out.println(person1 == person2);
        //returns false - references are not the same
        System.out.println(person1.equals(person2));
        //returns false - need to override object.equals()
    }
}
public class Person
{
    public int age;
    public String name;
    
    public Person(int age, String name){
        this.age = age;
        this.name = name;
    }
}
```
### We need to override equals() and create a new method body in Person. Might as well override hashCode() as well.
```java
package finalproject;

import java.util.Objects;

public class Finalproject
{
    public static void main(String[] args)
    {
        Person person1 = new Person(24, "Sean");
        Person person2 = new Person(24, "Sean");
        System.out.println(person1 == person2);
        //returns false - references are not the same
        System.out.println(person1.equals(person2));
        //returns true
    }
}

public class Person
{
    public int age;
    public String name;
    
    public Person(int age, String name){
        this.age = age;
        this.name = name;
    }
    
    @Override
    public boolean equals(Object obj){
        if(obj == null || !(obj instanceof Person)){
            return false;
        }
        Person person = (Person)obj;
        return(age == person.age) && (name.equals(person.name));
    }

    @Override
    public int hashCode()
    {
        int hash = 7;
        hash = 67 * hash + this.age;
        hash = 67 * hash + Objects.hashCode(this.name);
        return hash;
    }
}
```
### So in order to compare user defined objects, the equals() method of Object must be overriden

## C#
#### In C#, comparisons can be made using the == operator, as well as the Equals() and ReferenceEquals() methods of object(). However it gets tricky. Unlike java, the == operator CAN be used to compare the contents of 2 string objects. It can also be used to compare primitive data types also called predefined values such as int and double. However, when == is used on any object other than string or predefined values, it will only compare the reference. Equals and ReferenceEquals should not be used on predefined data types.

### Lets start with comparing string objects and predefined value types
```CS
using System;
namespace Testing_CSharp_CS4330
{
    class Program
    {
        static void Main(string[] args)
        {
            //try creating 2 strings separately
            string string1 = "Hello";
            string string2 = "He";
            string2 += "llo";
            Console.WriteLine(string1 == string2);
            //returns True - string values are equal
            Console.WriteLine(string1.Equals(string2));
            //returns True - string values are equal
            Console.WriteLine(object.ReferenceEquals(string1,string2));
            //returns false - not referencing same object

            //try by assigning values during declaration
            int number3 = 5;
            int number4 = 5;
            Console.WriteLine(number3 == number4);
            //returns true - int values are equal
            Console.WriteLine(number3.Equals(number4));
            //returns true - int values are equal
            Console.WriteLine(object.ReferenceEquals(number3, number4));
            //returns false - int references are not equal. Assigning int created two separate objects without needing a new keyword

            //create objects and assign values after declaration
            int number1 = new int();
            int number2 = new int();
            number1 = 5;
            number2 = 5;
            Console.WriteLine(number1 == number2);
            //returns true - int values are equal. references are definitely not
            Console.WriteLine(number1.Equals(number2));
            //returns true - int values are equal. references are definitely not
            Console.WriteLine(object.ReferenceEquals(number1, number2));
            //returns false - int references are not equal
        }
    }
}
```
#### So in C#, the == operator CAN be used to test values of strings.
### Let's try to compare Objects now
```CS
using System;
namespace Testing_CSharp_CS4330
{
    class Program
    {
        static void Main(string[] args)
        {
            //now try with a Person Object
            Person person1 = new Person(24, "Sean");
            Person person2 = new Person(24, "Sean");
            Console.WriteLine(person1 == person2);
            //returns false - Uh oh, cant use == to compare values of objects
            Console.WriteLine(person1.Equals(person2));
            //returns false - oh no, cant use Equals() either
            Console.WriteLine(object.ReferenceEquals(person1, person2));
            //returns false - well we knew those weren't equal references
        }
    }
    public class Person : IEquatable<Person>
    {
        public int Age;
        public string Name;

        public Person(int age, string name)
        {
            this.Age = age;
            this.Name = name;
        }
    }
}
```

### So we can't use Equals() as is, but we have 2 options, we can implement IEquatable or we can override Object.Equals()
#### Let's try overriding first
```CS
using System;
namespace Testing_CSharp_CS4330
{
    class Program
    {
        static void Main(string[] args)
        {   
            Person person1 = new Person(24, "Sean");
            Person person2 = new Person(24, "Sean");
            Console.WriteLine(person1 == person2);
            //returns true - sweet that works
            Console.WriteLine(person1.Equals(person2));
            //returns true - awesome
            Console.WriteLine(object.ReferenceEquals(person1, person2));
            //returns false - we already know that
        }
    }
    public class Person
    {
        public int Age;
        public string Name;

        public Person(int age, string name)
        {
            this.Age = age;
            this.Name = name;
        }

        //override object.Equals()
        public override bool Equals(object obj)
        {
           if (obj == null || GetType() != obj.GetType())
               return false;
           Person person = (Person)obj;
           return (Age == person.Age) && (Name == person.Name);
        }

        //Might as well override == as well
        public static bool operator ==(Person lho, Object rho)
        {
           if (rho == null || lho.GetType() != rho.GetType())
               return false;
           Person person = (Person)rho;
           return (lho.Age == person.Age) && (lho.Name == person.Name);
        }

        //have to override != if you override ==
        public static bool operator !=(Person lho, Object rho)
        {
           if (rho == null || lho.GetType() != rho.GetType())
               return true;
           Person person = (Person)rho;
           return !((lho.Age == person.Age) && (lho.Name == person.Name));
        }
    }
}
```
#### Lets try implementing IEquatable now

```CS
using System;
namespace Testing_CSharp_CS4330
{
    class Program
    {
        static void Main(string[] args)
        {
            Person person1 = new Person(24, "Sean");
            Person person2 = new Person(24, "Sean");
            Console.WriteLine(person1 == person2);
            //returns true - overriding ==
            Console.WriteLine(person1.Equals(person2));
            //returns true - implementing iequatable
            Console.WriteLine(object.ReferenceEquals(person1, person2));
            //returns false - we know they arent equal
            Console.WriteLine(person1.Equals(5));

        }
    }
    //Using IEquatable interface, takes care of type checking and typecasting behind the scenes
    public class Person : IEquatable<Person>
    {
        public int Age;
        public string Name;

        public Person(int age, string name)
        {
            this.Age = age;
            this.Name = name;
        }

        public bool Equals(Person person)
        {
            return (Age == person.Age) && (Name == person.Name);
        }

        //Still need to implement these if we want it to work
        public static bool operator ==(Person lho, Object rho)
        {
           if (rho == null || lho.GetType() != rho.GetType())
               return false;
           Person person = (Person)rho;
           return (lho.Age == person.Age) && (lho.Name == person.Name);
        }

        public static bool operator !=(Person lho, Object rho)
        {
           if (rho == null || lho.GetType() != rho.GetType())
               return true;
           Person person = (Person)rho;
           return !((lho.Age == person.Age) && (lho.Name == person.Name));
        }
    }
}
```
### So in C#, if you want to compare two objects of the same type for equality, you need to have an Equals() method in the class body