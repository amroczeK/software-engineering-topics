# Software Design Princicples

Software design principles are fundamental guidelines or best practices that software developers should adhere to, to create maintainable, scalable, and robust software. Here are some of the most popular software design principles:

  

1. **Single Responsibility Principle (SRP)**:

This principle, which is part of the SOLID principles, suggests that a class should have only one reason to change. In other words, a class should have only one job or responsibility.

  

2. **Open-Closed Principle (OCP)**:

Another one of the SOLID principles, the OCP states that software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification. The idea is to allow adding new functionality without changing the existing code.

  

3. **Liskov Substitution Principle (LSP)**:

The third SOLID principle, LSP, states that if a program is using a base class, it should be able to use any of its subclasses without the program knowing it. Essentially, subclasses should be substitutable for their base classes without causing any issues.

  

4. **Interface Segregation Principle (ISP)**:

ISP, another SOLID principle, suggests that clients should not be forced to depend on interfaces they do not use. This means having multiple, specific interfaces is better than one general-purpose interface.

  

5. **Dependency Inversion Principle (DIP)**:

The last of the SOLID principles, DIP suggests that high-level modules should not depend on low-level modules. Both should depend on abstractions. Also, abstractions should not depend upon details. Details should depend upon abstractions. This principle allows for decoupling.

  

6. **DRY (Don't Repeat Yourself)**:

This principle suggests that every piece of knowledge or logic should have a single, unambiguous representation within a system. When the DRY principle is applied successfully, a modification of any single element of a system does not require a change in other logically unrelated elements.

  

7. **KISS (Keep It Simple, Stupid)**:

This principle states that most systems work best if they are kept simple rather than made complicated. Simplicity should be a key goal in design, and unnecessary complexity should be avoided.

  

8. **YAGNI (You Ain't Gonna Need It)**:

This Extreme Programming principle suggests not to add functionality until deemed necessary. It's aimed at reducing unnecessary code that may increase complexity and could potentially introduce bugs.

  

9. **Separation of Concerns (SoC)**:

This principle is about breaking a program into distinct sections, such that each section addresses a separate concern. It improves the modularity of the program and makes it more maintainable.

  

10. **Composition Over Inheritance**:

This principle suggests it's better to compose complex objects by putting simple objects together rather than inheriting from a base class. It promotes flexibility and reduces problems associated with tight coupling.

  

These principles provide a valuable framework for designing software, improving code readability, and making the software easier to maintain and extend over time. The principles are interrelated, and many times, following one will also involve others. However, they're guidelines, not hard rules, and should be applied using good judgment.

  

## Implementations in C#

In the good practice examples, we are following the SOLID principles, which makes our code more understandable, flexible, and maintainable.

  

1. **Single Responsibility Principle (SRP):** A class should only have one reason to change.

**Bad practice:**

```plain
public class User
{
    public void Create(User user)
    {
        // code to save user
    }

    public void GenerateReport(User user)
    {
        // code to generate report
    }
}
```

**Good practice:**

```plain
public class User
{
    public void Create(User user)
    {
        // code to save user
    }
}

public class Report
{
    public void GenerateReport(User user)
    {
        // code to generate report
    }
}
```

  

1. **Open-Closed Principle (OCP):** Software entities should be open for extension but closed for modification.

**Bad practice:**

```plain
public class GraphicEditor
{
    public void DrawShape(Shape s)
    {
        if (s.m_type == 1)
        {
            DrawRectangle(s);
        }
        else if (s.m_type == 2)
        {
            DrawCircle(s);
        }
    }
}
```

**Good practice:**

```plain
public abstract class Shape
{
    public abstract void Draw();
}

public class Circle : Shape
{
    public override void Draw()
    {
        // Draw the Circle
    }
}

public class Rectangle : Shape
{
    public override void Draw()
    {
        // Draw the Rectangle
    }
}

public class GraphicEditor
{
    public void DrawShape(Shape s)
    {
        s.Draw();
    }
}
```

  

1. **Liskov Substitution Principle (LSP):** Subtypes must be substitutable for their base types.

**Bad practice:**

```plain
public class Bird
{
    public virtual void Fly()
    {
        // Code for bird to fly
    }
}

public class Ostrich : Bird
{
    public override void Fly()
    {
        throw new Exception("I can't fly");
    }
}
```

**Good practice:**

```plain
public class Bird
{
}

public class FlyingBird : Bird
{
    public virtual void Fly()
    {
        // Code for bird to fly
    }
}

public class Ostrich : Bird
{
}

public class Sparrow : FlyingBird
{
    public override void Fly()
    {
        // Code for sparrow to fly
    }
}
```

  

1. **Interface Segregation Principle (ISP):** Clients should not be forced to depend on interfaces they do not use.

**Bad practice:**

```plain
public interface IWorker
{
    void Work();
    void Eat();
}

public class Worker : IWorker
{
    public void Work()
    {
        // ....working
    }

    public void Eat()
    {
        // ...... eating during lunch break
    }
}
```

**Good practice:**

```plain
public interface IWork
{
    void Work();
}

public interface IEat
{
    void Eat();
}

public class Worker : IWork, IEat
{
    public void Work()
    {
        // ....working
    }

    public void Eat()
    {
        // ...... eating during lunch break
    }
}
```

  

1. **Dependency Inversion Principle (DIP):** High-level modules should not depend on low-level modules. Both should depend on abstractions.

**Bad practice:**

```plain
public class Email
{
    public void SendEmail()
    {
        // Code to send email
    }
}

public class Notification
{
    private Email _email;
    public Notification()
    {
        _email = new Email();
    }

    public void PromotionalNotification()
    {
       _email.SendEmail(); 
    }   
}
```

**Good practice:**

```plain
public interface IMessage
{
    void SendMessage();
}

public class Email : IMessage
{
    public void SendMessage()
    {
        // Code to send an email
    }
}

public class Notification
{
    private IMessage _message;
    public Notification(IMessage message)
    {
        _message = message;
    }

    public void PromotionalNotification()
    {
        _message.SendMessage();
    }
}
```