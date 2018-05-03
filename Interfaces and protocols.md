# [HomePage](README.md)


### Both java and C# use the concept of interfaces which add structure to classes through implicitly abstract functions. Interfaces methods must be abstract and contain no implementation, but do not have to have the abstract keyword. Common practice in java is to not have fields in interfaces, while c# cannot have fields in interfaces

## java
#### In java, interface methods and fields must be declared public. Java also has functional interfaces and marker interfaces. Marker interfaces tell the compiler that it needs to treat the interface differently from other interfaces.
```java
package finalproject;

public class Finalproject
{
    public static void main(String[] args)
    {        
        Person Sean = new Person(24, "Sean");
        Sean.getAge();
        Sean.setAge(24);
        
        Sean.name = "Sean";
        String name = Sean.name;
        //Calling interface method from Person implementing American
        Sean.isLazy();
        //Using annonymous inner class that implements Runnable interface to create a thread
        new Thread(new Runnable()
        {
            @Override
            public void run()
            {
                System.out.println("New thread created");
            }
        }).start();
    }
}
//implementing American interface in Person class
public class Person implements American
{
    private boolean lazy = true;
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

    @Override
    public boolean isLazy()
    {
        return lazy;
    }
}
//interface
public interface American
{
    public boolean isLazy();
}
```
### Example of implementing marker interface
```java
import java.io.Serializable;

public class Student extends Person implements Serializable
{
    public int idNumber;
    public Student(int age, String name, int idNumber){
        super(age, name);
        this.idNumber = idNumber;
    }
}
```
---
## C#
#### C# interfaces are more or less the same as java. There are also marker interfaces in C# which are implemented at run time. Interface methods must not declare an access type
```CS
using System;
namespace Testing_CSharp_CS4330
{
    class Program
    {
        static void Main(string[] args)
        {
            Person Sean = new Person(24, "Sean");
            Console.WriteLine(Sean.isLazy());
        }
    }
    public class Person : American
    {
        string _name;
        public Person() { }
        bool lazy;
        public Person(int Age, string Name) : this()
        {
            this.Age = Age;
            this.Name = Name;
        }
        public int Age { get; set; }
        public string Name { get; set; }

        public bool isLazy()
        {
            return this.lazy;
        }
    }
    public interface American
    {
        bool isLazy();
    }
}
```