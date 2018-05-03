# [HomePage](README.md)

### Properties between C# and java are both stored in backing variables rather than computed properties.

## java
### In java, you must write your own getters and setters unless you access the public properties.
```java
package finalproject;

public class Finalproject
{
    public static void main(String[] args)
    {        
        Person Sean = new Person(24, "Sean");
        //Use getters and setters to access private backing variables
        Sean.getAge();
        Sean.setAge(24);
        //Access public backing variables directly
        Sean.name = "Sean";
        String name = Sean.name;
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
```
---
## C#
### In C#, ou can explicitly assign a backing variable or let the compiler do it for you. You can also write your own getters and setters. C# also uses a value concept, where the setter is called with the value to the right hand side of an = operator.
```CS
using System;
namespace Testing_CSharp_CS4330
{
    class Program
    {
        static void Main(string[] args)
        {
            Person Sean = new Person(24, "Sean");
            Sean.SetName("Not Sean");
        }
    }
    public class Person
    {
        //backing variable _name. _ followed by a lower case is common formatting for private variables
        string _name;
        public Person() { }
        public Person(int Age, string Name) : this()
        {
            this.Age = Age;
            this.Name = Name;
        }
        //this will handle the Age backing variable and lets the compiler handle the reading and writing
        public int Age { get; set; }
        //this is an explicit declaration for getting and setting values of the backing variables. value is the right hand operand of an = operator when Age = int is called
        public string Name { get { return _name; } set { _name = value; } }
        //You can also write your own getters and setters but...why?
        public void SetName(string Name)
        {
            this.Name = Name;
        }
        public string GetName()
        {
            return this.Name;
        }
    }
}
```