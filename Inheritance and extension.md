# [HomePage](README.md)

### Both java and C# allow inheritance from only one object. Objects of a derived class can be set to a superclass reference, but not to a subclass reference

## java
```java
package finalproject;

public class Finalproject
{
    public static void main(String[] args)
    {        
        Person Sean = new Person(24,"Sean");
        Student Kyle = new Student(20,"Kyle", 11143567);
        
        Person Bob = new Student(20,"Bob",12345678);
        Bob = (Person)Bob;
    }
}
public class Person
{
    private int age;
    public String name;
    
    public Person(int age, String name){
        this.age = age;
        this.name = name;
    }
    public int getAge(){
        return this.age;
    }
    public void setAge(int age){
        this.age = age;
    }
}
public class Student extends Person
{
    public int idNumber;
    public Student(int age, String name, int idNumber){
        super(age, name);
        this.idNumber = idNumber;
    }
    @Override
    public void setAge(int age){
        super.setAge(age);
    }
}
```

## C#
```CS
using System;
namespace Testing_CSharp_CS4330
{
    class Program
    {
        static void Main(string[] args)
        {
            Person Sean = new Person(24, "Sean");
            Student Kyle = new Student(20, "Kyle", 11143567);

            Person Bob = new Student(20, "Bob", 12345678);

        }
    }
    public class Person
    {
        public Person() { }
        public Person(int Age, string Name) : this()
        {
            this.Age = Age;
            this.Name = Name;
        }
        public int Age { get; set; }
        public string Name { get; set; }
    }
    public class Student : Person
    {
        public Student() { }
        public Student(int Age, string Name, int IDNumber) : base(Age, Name)
        {
            this.IDNumber = IDNumber;
        }
        public int IDNumber { get; set; }
    }
}
```