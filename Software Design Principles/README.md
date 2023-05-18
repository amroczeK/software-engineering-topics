# Software Design Princicples

Software design principles are fundamental guidelines or best practices that software developers should adhere to, to create maintainable, scalable, and robust software. Here are some of the most popular software design principles:

  

1. **Single Responsibility Principle (SRP)**: This principle, which is part of the SOLID principles, suggests that a class should have only one reason to change. In other words, a class should have only one job or responsibility.

  

2. **Open-Closed Principle (OCP)**: Another one of the SOLID principles, the OCP states that software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification. The idea is to allow adding new functionality without changing the existing code.

  

3. **Liskov Substitution Principle (LSP)**: The third SOLID principle, LSP, states that if a program is using a base class, it should be able to use any of its subclasses without the program knowing it. Essentially, subclasses should be substitutable for their base classes without causing any issues.

  

4. **Interface Segregation Principle (ISP)**: ISP, another SOLID principle, suggests that clients should not be forced to depend on interfaces they do not use. This means having multiple, specific interfaces is better than one general-purpose interface.

  

5. **Dependency Inversion Principle (DIP)**: The last of the SOLID principles, DIP suggests that high-level modules should not depend on low-level modules. Both should depend on abstractions. Also, abstractions should not depend upon details. Details should depend upon abstractions. This principle allows for decoupling.

  

6. **DRY (Don't Repeat Yourself)**: This principle suggests that every piece of knowledge or logic should have a single, unambiguous representation within a system. When the DRY principle is applied successfully, a modification of any single element of a system does not require a change in other logically unrelated elements.

  

7. **KISS (Keep It Simple, Stupid)**: This principle states that most systems work best if they are kept simple rather than made complicated. Simplicity should be a key goal in design, and unnecessary complexity should be avoided.

  

8. **YAGNI (You Ain't Gonna Need It)**: This Extreme Programming principle suggests not to add functionality until deemed necessary. It's aimed at reducing unnecessary code that may increase complexity and could potentially introduce bugs.

  

9. **Separation of Concerns (SoC)**: This principle is about breaking a program into distinct sections, such that each section addresses a separate concern. It improves the modularity of the program and makes it more maintainable.

  

10. **Composition Over Inheritance**: This principle suggests it's better to compose complex objects by putting simple objects together rather than inheriting from a base class. It promotes flexibility and reduces problems associated with tight coupling. These principles provide a valuable framework for designing software, improving code readability, and making the software easier to maintain and extend over time. The principles are interrelated, and many times, following one will also involve others. However, they're guidelines, not hard rules, and should be applied using good judgment.

11. **Clean Architecture**: Is a software design that emphasizes the separation of software into distinct layers, each with its own responsibility. The core idea is that dependencies between these layers should point inward towards higher-level policies (business logic), and that the software should be independent of frameworks, UI, and databases, making it more flexible, easily testable, and maintainable. It embodies principles such as the Dependency Rule, stating that dependencies should only point inwards from outer layers (like the UI and database) towards inner layers, which hold business logic and business entities.

  

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
-----
## Domain-Driven Design

Domain-Driven Design (DDD) is an approach to software development that centers the design and the development process around the domain—the subject area the software is intended to address. The main goal of DDD is to create a software model that provides solutions for specific business domains.

  

DDD contains a rich set of technical practices and strategic design principles, but at its heart are three core concepts:

1. **Ubiquitous Language**: This is a common language used by all team members—both technical and non-technical—to describe the domain and the software models. The idea is to eliminate or minimize misunderstanding between team members. The ubiquitous language is used everywhere—in discussions, in diagrams, in code.
2. **Bounded Contexts**: These are logical boundaries within which a model applies. In complex systems, no single model can effectively cover all areas. By defining bounded contexts, we can create a number of smaller, more manageable models, each applying within its own context.
3. **Strategic Design**: This concept concerns how different bounded contexts interact and how they fit into the larger system. It includes considerations about shared kernels (common models shared between contexts), customer-supplier relationships (where one context supplies data to another), and anti-corruption layers (which translate between different contexts to prevent one model from corrupting another).

  

**Let's consider an example:**

Suppose you're building a software system for a library. The domain includes concepts such as "Book", "Member", "Loan", etc.

  

The **Ubiquitous Language** here would use these terms. For example, a "Loan" might refer to the event of a "Member" borrowing a "Book". Everyone on the team, from the software developers to the library staff, would use these terms in discussions and design.

  

The system might have several **Bounded Contexts**. For example, one context might deal with membership management (signing up new members, renewing memberships, etc.), another with inventory management (adding new books, removing damaged books, etc.), and another with loan management (loaning books, returning books, tracking overdue loans, etc.). Each context has its own model that is valid within that context. For example, the "Member" in the membership management context might include data about the member's contact information and membership status, while the "Member" in the loan management context might include data about the member's current and past loans.

  

The **Strategic Design** might dictate that the membership management context is the authoritative source of member data. The loan management context might need some of this data, but to prevent corruption of its model, it might use an anti-corruption layer to translate from the membership context's model to its own. The loan management context might also be a customer of the inventory management context, using data from it to keep track of which books are currently available for loan.

  

DDD is especially valuable in complex domains, where a deep understanding of the domain is crucial to the success of the software. It's less suitable for simple CRUD (Create, Read, Update, Delete) applications or domains where the business rules are simple and unlikely to change.

  

### Pros and Cons

**Pros:**

*   Improved Communication: The ubiquitous language improves communication within the team and with stakeholders.
*   Handles Complexity: It provides techniques to manage complexity in business logic.
*   Focus on Core Business: It puts the focus on the core business, making it easier to align the software with business needs.

**Cons:**

*   Overkill for Simple Domains: DDD can be overkill for simple applications with little domain complexity.
*   Learning Curve: It can be hard to learn and correctly implement, especially strategic patterns.
*   Requires Domain Expertise: It requires close collaboration with domain experts.

-----  

## CLEAN Architecture

It is a software design philosophy that emphasizes the separation of concerns, making the system easier to understand, develop, test, and maintain.

  

In Clean Architecture, the software is divided into layers with specific roles, each layer being independent of the specific details of the other layers. Here are the main layers:

  

1. **Entities**: These are the business objects of the application, representing the business rules that are independent of any specific database or UI implementation.

  

2. **Use Cases**: This layer contains specific business rules for the application. It encapsulates and implements all of the use cases of a system.

  

3. **Interface Adapters**: This layer includes classes that convert data from the format most convenient for use cases and entities, to the format convenient for things like the web, database, UI, etc.

  

4. **Frameworks and Drivers**: This is the outermost layer, typically composed of frameworks and tools such as the database and the web framework.

  

The main rule that makes this architecture "clean" is the Dependency Rule. The Dependency Rule states that dependencies should point only inward. That means:

*   The outer layers depend on the inner layers (the application's core). The inner layers do not depend on anything external.
*   High-level modules (closer to the center) do not depend on low-level modules (closer to the edge). Both depend on abstractions.

  

This results in a decoupled and modular system, where business logic can evolve independently of infrastructure and interface details, and vice versa. This architecture also makes it easier to test the business logic without requiring a database or UI.

In summary, the Clean Architecture aims to make the system:

*   Independent of Frameworks
*   Testable
*   Independent of the UI
*   Independent of the Database
*   Independent of any external agency