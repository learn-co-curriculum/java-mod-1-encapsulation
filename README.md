# Encapsulation

## Learning Goals

- Review the definition of encapsulation
- Learn how it is used in Java

## What is Encapsulation?

As we saw in the last lesson, encapsulation is one of the four pillars of
object-oriented programming. **Encapsulation** is a programming mechanism that
wraps up data and its code acting on the data in a single unit and keeps it safe
from outside interference. We can think about our classes and the instance
variables that were encapsulated inside them using the `private` access
modifier. We can think of this as **data-hiding**.

## Encapsulation Example

Believe it or not, we actually already know all the tools to hide our data from
other classes! We learned about access modifiers, accessor methods, and mutator
methods all in the last module. As we said time and time again:

> It is best practice for us to make our variables `private` and their values
> accessible through `public` methods (accessor and mutator methods).

But this just isn't a common practice - it is actually a rule of thumb when it
comes to encapsulation! Let's go back to our `Student` class from the last
module:

```java
public class Student {
    private String firstName;
    private String lastName;
    private String major;

    public Student(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.major = "Undeclared";
    }
    
    public Student(String firstName, String lastName, String major) {
       this(firstName, lastName);
       this.major = major;
    }

    public String getFirstName() {
       return firstName;
    }
    
    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }
    
    public String getLastName() {
        return lastName;
    }
    
    public void setLastName(String lastName) {
        this.lastName = lastName;
    }
    
    public String getMajor() {
        return major;
    }
    
    public void setMajor(String major) {
        this.major = major;
    }
}
```

In our `Student` class, we are hiding the `firstName`, `lastName`, and `major`
data points from other classes by restricting their access to `private`. Only
methods within the `Student` class can truly modify their values. If other
classes need access to these variables, then they have to go through the
getters and setters defined and have `public` access. This allows the object to
be in charge of its own state.

## What Happens If We Don't Use Encapsulation?

If we were to make one of the variables `public` in a class, then it would open
up doors for other classes to change the object's state! To better explain, let
us look at an example that doesn't use encapsulation and has its variables set
to `public`:

```java
public class Dog {
    public String bark;
    
    public Dog() {
        this.bark = "Woof!";
    }
    
    public static void main(String[] args) {
        Dog snoopy = new Dog();
        snoopy.bark = "Meow!";
    }
}
```

The above code is valid but do we see what happened? Our `Dog` instance is now
meowing instead of barking! The variable is no longer encapsulated within the
`Dog` class and can now be modified through careless intent. This is why
encapsulation is so important - it keeps the data hidden and safe.
