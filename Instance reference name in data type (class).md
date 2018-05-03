# [HomePage](README.md)

### Both C# and java use the "this" keyword to reference members within a class. This differentiates variables in constructor and method definitions from the fields within the classes.

## java
### In java, the this keyboard differentiates current object fields methods and properties from method and constructor parameters. The super keyword is also used to reference fields methods and constructors in an inherited class's base class.
```java
package finalproject;

public class Finalproject
{
    public static void main(String[] args)
    {
        Person Sean = new Person(24, "Sean");
        Student Kyle = new Student(18, "Kyle", 11143567);
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
public class Student extends Person
{
    public int idNumber;
    public Student(int age, String name, int idNumber){
        super(age, name);
        this.idNumber = idNumber;
    }
}
```

## C#
### In C#, the this keyword can be used to reference fields and methods within the current class, but can also be used to reference another constructor within the class. The base keyword can also be used to reference a constructor in a class the current class inherits from

```CS
using System;
namespace Testing_CSharp_CS4330
{
    class Program
    {
        static void Main(string[] args)
        {
            Person Sean = new Person(24, "Sean");
            Student Kyle = new Student(18, "Kyle", 11143567);
        }
    }
    public class Person
    {
        string _name;
        public Person() { }
        //call current object no parameter constructor before calling paramaterized constructor
        public Person(int Age, string Name) : this()
        {
            //differentiate current object Age constructor parameter Age with this.Age
            this.Age = Age;
            this.Name = Name;
        }
        public int Age { get; set; }
        public string Name { get { return _name; } set { _name = value; } }
    }
    public class Student : Person
    {
        public int IdNumber { get; set; }
        //call base class constructor before calling current class constructor
        public Student(int Age, string Name, int IdNumber) : base(Age, Name)
        {
            base.Age = 21;
            this.IdNumber = IdNumber;
        }
    }
}
```
