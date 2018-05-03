# [HomePage](README.md)
## Types

### Variables in both C# and java must be declared with a data type since they are both strongly-typed languages.

## java
#### Java supports value types and reference types. Value types include primitive data types such as boolean, char, byte, short, int, long, float, and double. All other types in java are reference types. All other types in java are reference types which inherit from the base class of java. A few of these reference types include string, arrays, hashmaps, enumerations and structs. Structs and enumerations in java are actually classes. In order to create a new data type, a new class must be created that inherits from object or another existing class.

### An example of value types and a reference to a string object
```java
public class Finalproject
{
    public static void main(String[] args)
    {
        //primitive data types
        boolean bool = true;
        byte yum = 127;
        char character = 'c';
        short int16 = 32767;
        int int32 = 2^31-1;
        long uint64 = 2^63-1;
        float float32 = -32;
        double float64 = -64;
        
        //Reference to string object
        String hello = "Hello!";
    }
}
```
### Creating a new data type requires creating a new class
```java
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
---
## C#
#### C# supports both value types and reference types. Value types in C# include bool, char, sbyte, byte, short, int, long, ushort, uint, ulong, float, double, decimal, struct and enum. Reference types in C# include class, string, array, and delegates. All types in C# are aliases for Classes and structs in the .NET framework. All value types are inherited from .NET structs while reference types are inherited from .NET Classes. Unlike java, C# has the ability to create new data types by defining data structures and enumerations. Classes can also be created to store data.
```CS
using System;
namespace Testing_CSharp_CS4330
{
    class Program
    {
        public struct Person
        {
            int Age;
            string Name;
            public Person(int age, string name)
            {
                Age = age;
                Name = name;
            }
        }
        enum Colors
        {
            Red,Blue,Green
        }
        static void Main(string[] args)
        {
            bool isTrue = true;
            char letter = 'a';
            sbyte one = 0b0000_1000;
            byte three = 0b0000_0011;
            short int16 = 32767;
            int int32 = 2147483647;
            long int64 = 9223372036854775807;
            ushort uint16 = 65535;
            uint uint32 = 4294967295;
            ulong uint64 = 18446744073709551615;
            float single32 = 3.402823f;
            double double64 = 1.797;
            decimal dec = 7.9m;

            //Create Person object from Person class in Testing_CSharp_CS4330 namespace
            Testing_CSharp_CS4330.Person Sean = new Testing_CSharp_CS4330.Person(24, "Winegar");

            //Create Person structure from Person struct within Testing_CSharp_CS4330.Program namespace
            Person Sean2 = new Person(24, "Sean");

            //Take value from Color enumeration and cast it to color string
            string color = Colors.Blue.ToString();
        }
    }
    public class Person
    {
        int Years;
        string LastName;
        public Person(int age, string name)
        {
            Years = age;
            LastName = name;
        }
    }
}
```
### Classes can exist within a class in C#, and they can also contain the same name as another class or structure if they are in a different scope.