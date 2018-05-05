# [HomePage](README.md)


Threads in Java and C# are treated in very similar ways.  I will go into them with the following

## Java

Threads can run off on their own as a part of the project.  The run concurrently with a program and in Java threads can either be extended by the Thread class or it can be implemented with the Runnable interface.

Using the runnable interface is the better of the two options as it has the option to extend other classes and there isn't as big of an overhead that the Thread class comes with.

Here is an example:

```
public class MyRunnable implements Runnable {
  public void run() {        }
}
```

## C# 

C# extends a different thread, but besides that, it works very similar to Java.  And they run seperately from the classes they are called in.