# [HomePage](README.md)

### java and C# both have the ability to reflect and introspect on the objects and find out what methods and fields they contain.

## java
### In java, you can inspect the class and find all fields it contatins. This code block shows how to step through all fields in an object and fill them with values passed into a constructor in a form of an array of Strings.
```java
public Node(String[] values){
        try{
            int i = 0;
            for(Field f: this.getClass().getDeclaredFields()){
                f.set(this, values[i]);
                i++;
            }
        }catch(IllegalAccessException | IllegalArgumentException | SecurityException e){
            System.out.println("Error constructing object");
        }
    }
```
### Java can also check to see if an object is an instance of a class using instanceof keyword.
```java
public class Finalproject{
    public static void main(String[] args)
    {        
        Person Sean = new Person(24,"Sean");
        if(Sean instanceof Person){
            //this statement will evaluate true
        }
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

### this block of code shows how C# would inspect an object and return the properties and methods in a list.
```CS
var accessor = TypeAccessor.Create(ac.GetType());
var values = accessor.GetMembers()
        .Select(member => accessor[ac, member.Name]).ToList();
```

### C# can check to see if an object is an instance of a class using the is keyword.
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
            if(Sean is Person)
            {
                //this will evaluate true
            }

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
}
```

