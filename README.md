# Low-Level Design (LLD) Notes

---

## * Introduction
**What is LLD?**
* **LLD = Low-Level Design**
* Focuses on how the code will be implemented.
* Converts High-Level Design (HLD) into actual classes, methods, and logic.
* Acts as a bridge between design and coding.

---

## * Easy Real-Life Example

🏠 **Building a House**
* **HLD:** House blueprint (Rooms, Size, Connections)
* **LLD:** Construction details (Switch locations, Plumbing, Materials, Wiring)

👉 **HLD** = *What to build*  
👉 **LLD** = *How to build it*

---

## * Definition
LLD is the detailed design of individual components of a system.

It defines:
* Classes
* Methods
* Data Structures
* Algorithms
* Internal Logic

...before writing the actual code.

---

## * Example
**Website Login System**

LLD decides:
* `login()`
* `signup()`
* `forgotPassword()`
* Validation
* Error handling
* Database calls
* Password encryption

---

## * Key Characteristics

### 1. Granular (Code-Level)
LLD goes into implementation details. It includes:
* Classes
* Objects
* Methods
* Variables
* Data Structures

*Example:* Instead of saying *"Need User Authentication"*, LLD specifies:
* `User` class
* `LoginService`
* `validatePassword()`
* Error handling flow

### 2. Implementation Focused
LLD is the coding blueprint. It defines:
* Logic
* Workflow
* Function interactions
* Module implementation

May include: Pseudocode, Flowcharts, Sequence Diagrams.

### 3. Uses OOP Principles
LLD heavily uses OOP concepts:
* Encapsulation
* Abstraction
* Inheritance
* Polymorphism

*Benefits:* Reusable code, Modular design, Easy maintenance.

*Example:*
```text
      Notification
           |
  -------------------
  |                 |
Email              SMS
```

---

## * Stakeholders
People involved in implementation:
* Senior Developers
* Software Engineers
* Technical Leads
* Engineering Managers

---

## * HLD vs LLD

| HLD | LLD |
| :--- | :--- |
| System overview | Detailed implementation |
| Architecture | Classes & Methods |
| Modules | Functions & Logic |
| Abstract | Detailed |
| System diagrams | Class diagrams |

---

## * Importance of LLD
* **Avoids Rework:** Finds design issues early, saves development time.
* **Improves Collaboration:** Common reference for developers, easier integration.
* **Better Scalability:** Modular components, easy to extend with new features.
* **Encourages Best Practices:** Clean Code, OOP Principles, Design Patterns, maintainable code.

---
---
---
---

**TOPIC COMPLETED MOVING TO NEXT**

---
---
---
---

## * Software Design Principles
Software design principles are guidelines that help software developers create systems that are easy to understand, maintain, and extend. These principles can be applied at both the high-level and low-level design stages. Here are three cornerstone key software design principles:

### 1. DRY (Don't Repeat Yourself)
### 2. KISS (Keep It Simple, Stupid)
### 3. YAGNI (You Aren't Gonna Need It)

Let's understand each of these design principles in detail.

### 1. DRY: Don't Repeat Yourself
This principle states that every piece of knowledge must have a single, unambiguous, authoritative representation within a system. In simple terms, **avoid duplication of logic or code**. Repeating code makes the system hard to maintain and error-prone. If a change is required, you might forget to update all occurrences.

**Importance:**
* Reduces redundancy
* Easier maintenance
* Single point of change

#### Example: Area Calculation

**Bad Code (Violates DRY):**
The logic for calculating the area is repeated. If we need to change the logic, we have to do it in multiple places.
```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        int length1 = 10, width1 = 5;
        int area1 = length1 * width1;
        System.out.println("Area1: " + area1);

        int length2 = 8, width2 = 4;
        int area2 = length2 * width2;
        System.out.println("Area2: " + area2);
    }
}
```

**Good Code (Follows DRY):**
We have created a single method `calculateArea`. If we need to change the logic, we only need to do it in one place.
```java
import java.util.*;
class AreaCalculator {
    public static int calculateArea(int length, int width) {
        return length * width;
    }
}

class Main {
    public static void main(String[] args) {
        int area1 = AreaCalculator.calculateArea(10, 5);
        int area2 = AreaCalculator.calculateArea(8, 4);

        System.out.println("Area1: " + area1);
        System.out.println("Area2: " + area2);
    }
}
```

**Applying DRY in Practice:**
* Identify repetitive code and replace it with a single, reusable code segment.
* Extract common functionality into methods or utility classes.
* Leverage libraries and frameworks when available.
* Refactor duplicate logic regularly across classes or layers.

**When Not to Use the DRY Principle:**
| Scenario | Reason |
| :--- | :--- |
| **Premature Abstraction** | Don't extract common code too early. It can create unnecessary coupling between unrelated parts. |
| **Performance-Critical Code** | Repeating optimized low-level logic is sometimes faster than calling a generalized, reusable method. |
| **Sacrificing Readability** | If extracting repeated code makes the code less readable, prefer clarity over DRYness. |
| **Legacy Codebases** | Introducing DRY by extracting shared logic can accidentally change behavior if not well-tested. |

### 2. KISS: Keep It Simple, Stupid
This principle states that simplicity should be a key goal in design and unnecessary complexity should be avoided. In simple terms, **use the simplest possible solution that works**. Avoid clever, convoluted code.

**Importance:**
* Easier debugging
* Improved readability
* Better maintainability
* Faster development

#### Example: Checking for Even Numbers

**Bad Code (Too Complex / Overengineered):**
Uses extra variables and unnecessary `if-else` logic. Makes the code longer and harder to follow.
```java
import java.util.*;
public class NumberUtils {
    public static boolean isEven(int number) {
        // Using unnecessary logic to determine evenness
        boolean isEven = false;
        
        if (number % 2 == 0) {
            isEven = true;
        } else {
            isEven = false;
        }
        
        return isEven;
    }
}
```

**Good Code (Simple and Clear):**
Simple, one-liner solution that is easy to read and understand.
```java
import java.util.*;
public class NumberUtils {
    public static boolean isEven(int number) {
        return number % 2 == 0;
    }
}
```

### 3. YAGNI: You Aren't Gonna Need It
This principle states: *"Always implement things when you actually need them, never when you just foresee that you need them."* In simple terms, **don't add functionality until it's necessary**. Avoid building features that you think you might need in the future to keep the codebase clean and reduce unnecessary complexity.

**Example:**
Assume you've been asked to build a note-taking app that allows users to create and view notes. 
* **Violating YAGNI:** Thinking ahead to add categories, tagging, or Google Drive syncing immediately. This creates a lot of unnecessary complexity and wastage of time.

**Importance:**
* Reduced waste
* Simplified codebase
* Faster development

**When NOT to use YAGNI:**
| Scenario | Reason |
| :--- | :--- |
| **Requirements are well-known** | If a feature is guaranteed soon (e.g., adding image support in 2 sprints), preparing the data model now might save significant refactoring later. |
| **Performance-Critical Areas** | Preemptively building and testing real-world usage patterns can catch bottlenecks early. |

---
---
---
---

**TOPIC COMPLETED MOVING TO NEXT**

---
---
---
---

## * SOLID Principles: Single Responsibility Principle (SRP)

### Introduction
There is a set of five principles for writing clean, scalable, maintainable object-oriented code. These principles are known as **SOLID** principles. The **S** in SOLID stands for **Single Responsibility Principle**.

**Definition:**
> A class should have only one reason to change. In other words, a class should only have one job, one responsibility, and one purpose.

If a class takes on more than one responsibility, it becomes coupled. This means that if one responsibility changes, the other responsibilities may also be affected, leading to a ripple effect of changes throughout the codebase.

### Real-life Analogy
Imagine a chef who is responsible for cooking, cleaning, serving food, and ordering groceries. If the chef is busy cleaning, they can't focus on cooking, and the quality of the food may suffer.

Instead, different people should handle each task:
* **Chef:** Cooks the food.
* **Cleaner:** Cleans.
* **Waiter:** Serves the food.
* **Manager:** Orders groceries.

This way, each person can focus on their specific responsibility, leading to better results overall.

### Significance of SRP

Let us understand this with the example of a **TUF+ compiler**. 

**Violating SRP:**
Currently, a single `TUFplusCompiler` class does all of the following things:
1. Adds driver code
2. Performs syntax check
3. Runs code with already fed test cases
4. Stores the output in Database
5. Returns the necessary output to the user

Implementing all these functionalities in a single class violates the Single Responsibility Principle.

**Following SRP:**
Instead, we can break it down into smaller classes, each with a single responsibility. We can also add a `Coordinator` class to manage them.

| Class | Responsibility |
| :--- | :--- |
| `DriverCodeGenerator` | Responsible for adding driver code. |
| `SyntaxChecker` | Responsible for performing syntax checks. |
| `TestRunner` | Responsible for running code with test cases. |
| `DatabaseManager` | Responsible for storing output in the database. |
| `UserOutputHandler` | Responsible for returning output to the user. |
| `Coordinator` | Coordinates between all these classes/modules. |

By following SRP, we make the code more modular, easier to maintain, and less prone to bugs. Each class can be modified or replaced independently.

### Advantages of SRP
* **Improved Maintainability:** Changes in one part won't affect other parts.
* **Enhanced Readability:** Smaller, focused classes are easier to read and understand.
* **Better Reusability:** Single-responsibility classes can be reused in different contexts without unnecessary dependencies.
* **Facilitates Testing:** Smaller classes have fewer dependencies and are easier to test.
* **Lower Risk in Changes:** Changes are less likely to cause unintended side effects.

### Common Mistakes When Violating SRP

| Mistake | Consequence |
| :--- | :--- |
| **Mixing Database Logic with Business Logic** | Putting data access (e.g., SQL) and core business rules in the same class makes it hard to change the database layer without affecting business logic. |
| **Coupling UI Code with Business Logic** | Embedding application logic directly in the UI layer makes it tedious to change the UI without affecting the underlying logic. |

> [!NOTE]
> **Is SRP just for classes?**
> No. SRP can be applied to methods, modules, microservices, and even entire systems. The key is to ensure that each component has a single responsibility. It's a mindset you can apply from the smallest method to the largest system design.

---

## * SOLID Principles: Open/Closed Principle (OCP)

### Introduction
There is a set of five principles for writing clean, scalable, maintainable object-oriented code. These principles are known as **SOLID** principles. The **O** in SOLID stands for **Open/Closed Principle**.

**Definition:**
> As per OCP, Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.

This means that the behavior of a module can be extended without modifying its source code. The goal is to reduce the risk of breaking existing functionality when requirements change.

### Real-life Analogy
Let's understand the application of OCP in real-life with the help of power adapters. Imagine you travel from India to the UK. Your Indian charger doesn't fit into UK power sockets. Instead of buying a new charger, you use a travel adapter.
* The adapter extends your existing charger's usability (now works in UK).
* You did not modify the charger itself.

Similarly, in code, OCP encourages adding new functionality via extension, rather than altering existing, stable code.

### Real-World Example
Let's now use region-based tax calculation (e.g., India, US, UK) in an Invoicing System to explain the Open/Closed Principle. As an invoicing system grows, it must handle tax rules for different regions (the values might not be accurate):
* India: GST 18%
* US: Sales Tax 8%
* UK: VAT 12%

New regions maybe added over time.

#### Bad Design (Violating OCP)
```java
class InvoiceProcessor {
    public double calculateTotal(String region, double amount) {
        if (region.equalsIgnoreCase("India")) {
            return amount + amount * 0.18;
        } else if (region.equalsIgnoreCase("US")) {
            return amount + amount * 0.08;
        } else if (region.equalsIgnoreCase("UK")) {
            return amount + amount * 0.12;
        } else {
            return amount; // No tax for unknown region
        }
    }
}
```
The above code is considered a bad practice because:
* Adding a new region (e.g., Germany) requires modifying this method.
* You risk breaking existing logic while adding new functionality.
* Hard to test, maintain, or scale.
* Violates the Open/Closed Principle.

#### Good Design (Follows OCP)
```java
// Tax strategy Interface
interface TaxCalculator {
    double calculateTax(double amount);
}

// Implementing Region-Specific Tax Calculators
class IndiaTaxCalculator implements TaxCalculator {
    public double calculateTax(double amount) {
        return amount * 0.18; // GST
    }
}
class USTaxCalculator implements TaxCalculator {
    public double calculateTax(double amount) {
        return amount * 0.08; // Sales Tax
    }
}
class UKTaxCalculator implements TaxCalculator {
    public double calculateTax(double amount) {
        return amount * 0.12; // VAT
    }
}

// Using Dependency Injection
class Invoice {
    private double amount;
    private TaxCalculator taxCalculator;

    public Invoice(double amount, TaxCalculator taxCalculator) {
        this.amount = amount;
        this.taxCalculator = taxCalculator;
    }

    public double getTotalAmount() {
        return amount + taxCalculator.calculateTax(amount);
    }
}

// Main class
class Main {
    public static void main(String[] args) {
        double amount = 1000.0;

        Invoice indiaInvoice = new Invoice(amount, new IndiaTaxCalculator());
        System.out.println("Total (India): ₹" + indiaInvoice.getTotalAmount());

        Invoice usInvoice = new Invoice(amount, new USTaxCalculator());
        System.out.println("Total (US): $" + usInvoice.getTotalAmount());

        Invoice ukInvoice = new Invoice(amount, new UKTaxCalculator());
        System.out.println("Total (UK): £" + ukInvoice.getTotalAmount());
    }
}
```
**Explanation:**
* **Define a Tax Strategy Interface:** The `TaxCalculator` interface defines a contract for all region-specific tax classes to follow, enabling polymorphism and extension.
* **Implement Region-Specific Tax Calculators:** The `IndiaTaxCalculator`, `USTaxCalculator`, and `UKTaxCalculator` classes provide concrete implementations of the `TaxCalculator` interface for each region, encapsulating tax logic.
* **Using Dependency Injection:** The `Invoice` class is decoupled from specific tax types by receiving a `TaxCalculator` from the outside (this is called Dependency Injection).
* **Main Running Code:** In the main function, we create the appropriate tax calculator and inject it into the `Invoice` class, making the system easily extensible for new regions.

Assume that now, we want to support Germany with 15% tax. In such a case, a simple code snippet can be introduced in the file:
```java
class GermanyTaxCalculator implements TaxCalculator {
    public double calculateTax(double amount) {
        return amount * 0.15;
    }
}
```
...and just pass `new GermanyTaxCalculator()` to `Invoice`. No modification to `Invoice` or main logic is needed.

### When to Apply OCP?
The Open/Closed Principle is especially useful in the following scenarios:
* When a module is expected to change or evolve due to shifting business or technical requirements.
* When there is a need to extend functionality without modifying existing, tested code.
* When developing frameworks, plugins, or extensible systems such as billing engines, tax calculators, or UI components.
* When aiming to safeguard stable, production-ready modules from regression caused by direct changes.
* When a class is becoming a God Class - handling too many responsibilities or branching logic - which signals a need to extract behaviors into separate, extendable components.

That said, applying the principle preemptively without clear extension needs can introduce unnecessary abstraction and complexity. It is generally most effective when applied in response to observed patterns of change or a well-understood need for scalability.

### Common Misconceptions about OCP
There are a few misconceptions that revolve around OCP:

| Misconception | Reality |
| :--- | :--- |
| **“Open/Closed means code should never be changed again.”** | This interpretation overlooks the intent of OCP. The principle emphasizes avoiding changes to core logic while allowing behavior to be extended safely. |
| **“OCP leads to too many classes, so it's overkill.”** | It's true that applying OCP often results in more classes or interfaces. However, this trade-off typically improves modularity, testability, and maintainability. |
| **“OCP makes the code harder to read.”** | In systems with complex behavior or frequent changes, well-structured extensibility actually improves clarity by separating concerns and reducing conditional logic. |
| **“OCP should always be applied upfront.”** | Applying OCP preemptively can result in unnecessary abstraction. It is often more effective when used in response to emerging patterns of change. |
| **“Refactoring contradicts OCP.”** | Refactoring is frequently a step toward making code compliant with OCP by improving its structure and extensibility. |
| **“OCP makes retesting legacy code unnecessary.”** | New extensions still require thorough testing to ensure correctness and integration. |

---

## * SOLID Principles: Liskov Substitution Principle (LSP)

### Introduction
There is a set of five principles for writing clean, scalable, maintainable object-oriented code. These principles are known as **SOLID** principles. The **L** in SOLID stands for **Liskov Substitution Principle**.

**Definition:**
> If `S` is a subtype of `T`, then objects of type `T` may be replaced with objects of type `S` without altering the correctness of the program.

This means that any subclass should be substitutable for its parent class without breaking the functionality.

Think of it like this:
If you write code using a parent class (say `Shape`), and later swap in a child class (like `Circle`), the code should still work without errors or unexpected behavior. If the subclass changes behavior in a way that breaks expectations, it violates LSP.

### Real-life Analogy
Imagine you run a pet hotel, and you have a general policy: *"Any pet staying here must be able to be fed, walked, and groomed."*
You design your hotel to handle pets, and you've had dogs, cats, and rabbits as guests, and things work fine.

**Problem:**
Assume someone brings in a pet snake. Here are the issues:
* You try to walk it. Can't.
* You try to groom it. Doesn't make sense.
* You offer pet food. Snake needs live mice.

Suddenly, your normal pet hotel process breaks. Your system expected all pets to behave like dogs or cats, but this snake breaks the assumptions. This creates an LSP Violation.

**A Valid Substitution:**
If instead someone brings in a pet hamster - it still eats food, needs care, and maybe doesn't walk outside, but it still fits within the expected “pet” behavior. You just make a minor adjustment (like putting it in a wheel instead of walking it). Still fine - no big surprises.

**Understanding:**
The pet hotel needs to trust that any "pet" will behave in expected ways. If a new pet completely changes the rules, the whole system becomes fragile.
That's exactly what the Liskov Substitution Principle protects us from in software - making sure substituting one thing for another doesn't break the expected behavior.

### Example: LSP Violation
Let's illustrate this with the classic Rectangle-Square example, which is a famous LSP violation case.

```java
// Rectangle class
class Rectangle {
    int width, height;

    void setWidth(int w) { width = w; }
    void setHeight(int h) { height = h; }
    int getArea() { return width * height; }
}

// Square class extending the Rectangle class
class Square extends Rectangle {
    @Override 
    void setWidth(int w) {
        width = w;
        height = w; // makes it a square
    }

    @Override
    void setHeight(int h) {
        height = h;
        width = h; // makes it a square
    }
}

// Main class
class Main {
    public static void main(String args[]) {
        // Replacing object of Rectangle class with Square class
        Rectangle r = new Square();
        
        // Method call to print the area of the rectangle
        printArea(r);
    }
    
    private static void printArea(Rectangle r) {
        r.setWidth(5);
        r.setHeight(10);
        System.out.println(r.getArea()); // Expected: 50 but Actual: 100
    }
}
```

In the above code:
* `Square` class is a subclass of `Rectangle` class.
* The `printArea()` function takes a `Rectangle` object as an argument and prints its area.
* To demonstrate the violation of LSP, the object of `Rectangle` class is replaced with the object of `Square` class.

**Violation:**
* **Expected Output:** 50
* **Actual Output:** 100 (since both the width and height became 10)

So, the `Square` violates LSP because it changes the behavior of `setWidth` and `setHeight`, breaking the assumptions of the parent class.

### Need of LSP
Consider the example of a Notification system:
```java
// Notification class
class Notification {
    public void sendNotification() {
        System.out.println("Notification sent");
    }
}

// Main class
class Main {
    public static void main(String args[]) {
        Notification notification = new Notification();
        notification.sendNotification();
    }
}
```
Assume we wish to introduce some new type of notifications, say Email Notification or Text Notification. We can easily extend the system without breaking existing code using LSP.

```java
// Notification class
class Notification {
    public void sendNotification() {
        System.out.println("Notification sent");
    }
}

// Subclass for Email Notification
class EmailNotification extends Notification {
    @Override
    public void sendNotification() {
        System.out.println("Email Notification sent");
    }
}

// Subclass for Text Notification
class TextNotification extends Notification {
    @Override
    public void sendNotification() {
        System.out.println("Text Notification sent");
    }
}

// Main class
class Main {
    public static void main(String args[]) {
        /* Replaced the Notification class object
        with one of its subclass' objects */
        Notification notification = new EmailNotification();
        notification.sendNotification();
    }
}
```
Here, the only change needed for introducing two different types of the notification system is to create two subclasses with an overridden `sendNotification()` method. The main class can remain unchanged. This is the power of LSP.

### Why Does LSP Matter?
When LSP is violated, the code becomes:
* **Unpredictable:** Code relying on base class assumptions will break with certain subclasses.
* **Hard to Maintain:** Adding new subclasses requires rechecking all usages.
* **Bug-Prone:** Runtime errors, wrong outputs, or inconsistent behavior.
* **Less Reusable:** Substituting child objects becomes dangerous.
* **Tight Coupling:** Client code ends up getting tightly coupled to specific types, making it less maintainable.

### How to Spot LSP Violations?
To spot LSP violations, ask yourself these questions:
1. Does the subclass override methods in a way that changes meaning or assumptions?
2. Can I replace the base class with the subclass everywhere without changing expected behavior or breaking correctness?
3. Does the subclass throw unexpected exceptions or return wrong values?
4. Does the subclass weaken any preconditions or strengthen postconditions?

If the answer to any of these questions is "yes", there might be an LSP violation.

### Key Principles to Follow
* Subclasses should honor the contract (expectations) of the parent class.
* Avoid overriding methods in a way that changes behavior drastically.
* Prefer composition over inheritance when possible.
* Think in terms of interfaces and behavioral compatibility.
* Subclass should only extend, not restrict behavior.

---

## * SOLID Principles: Interface Segregation Principle (ISP)

### Introduction
There is a set of five principles for writing clean, scalable, maintainable object-oriented code. These principles are known as **SOLID** principles. The **I** in SOLID stands for **Interface Segregation Principle**.

**Definition:**
> It says: "Don't force a class to depend on methods it does not use."

### Understanding
Suppose you order an Uber. You're just a rider - you only care about booking rides, tracking the driver, and paying. You don't care about picking up passengers, verifying driver's licenses, or managing earnings - that's for drivers!

But what if the app gave you one massive interface with everything - rider features and driver features? It would be confusing, right?

That's exactly what ISP helps prevent in software.

### Uber Example: Applying ISP
Let's say you're designing Uber's app interfaces.

#### Bad Interface Design (Violates ISP):
```java
interface UberUser {
    void bookRide();
    void acceptRide();
    void trackEarnings();
    void ratePassenger();
    void rateDriver();
}
```
Using such an interface would force riders to implement methods they don't need, like `acceptRide()` and `trackEarnings()`. For instance:
```java
class Rider implements UberUser {
    public void bookRide() { /* yes */ }
    public void acceptRide() { /* not needed */ }
    public void trackEarnings() { /* not needed */ }
    public void ratePassenger() { /* not needed */ }
    public void rateDriver() { /* yes */ }
}
```
This is extremely messy. `Rider` is forced to implement stuff it never uses!

#### Good Interface Design (Follows ISP):
A better interface design would separate the concerns:
```java
interface RiderInterface {
    void bookRide();
    void rateDriver();
}

interface DriverInterface {
    void acceptRide();
    void trackEarnings();
    void ratePassenger();
}
```
Now, each class only implements what it actually needs:
```java
class Rider implements RiderInterface {
    public void bookRide() { /* yes */ }
    public void rateDriver() { /* yes */ }
}

class Driver implements DriverInterface {
    public void acceptRide() { /* yes */ }
    public void trackEarnings() { /* yes */ }
    public void ratePassenger() { /* yes */ }
}
```
Now, each class has exactly what it needs - no more, no less. Thus, following the ISP keeps the code clean and easy to maintain.

### Benefits of using ISP
There are several benefits to using the Interface Segregation Principle (ISP) in software design. Here are some of the key advantages:
* **Cleaner Codebase:** Classes are not bloated with irrelevant methods.
* **Better Flexibility:** Easier to change one part without affecting others.
* **High Maintainability:** Smaller interfaces are easier to understand and test.
* **Fewer Bugs:** Less chance of someone accidentally using or overriding a method they don't need.
* **Scalability:** As your app grows, adding new roles (like delivery partners in Uber Eats) becomes easier.

### When to apply ISP
The Interface Segregation Principle (ISP) is a valuable guideline in software design, but it should be applied judiciously. Here are some scenarios where you should consider applying ISP:
* You see a class implementing methods it doesn't use.
* An interface starts to grow too big and is being used by multiple types of classes.
* Adding a new feature requires modifying several unrelated classes.
* You're working with APIs or plugins where exposing only relevant methods improves usability.

### Conclusion
The Interface Segregation Principle is all about designing interfaces that are tailored to the needs of each client - just like Uber doesn't show driver options to passengers. This leads to modular, understandable, and future-proof code.

> [!TIP]
> **Remember:** Fat interfaces are bad. Slim, purpose-specific interfaces are good.

---

## * Pre-requisites
To better understand the DIP, it is recommended to have a basic understanding of the following terms:
* **High-Level Modules:** The parts of your code that contain the core logic - the brains of your application. They make big decisions and coordinate how different features work together.
  * *Example:* CEO (makes decisions, plans strategies).
* **Low-Level Modules:** The ones that handle the details - like talking to a database, making API calls, reading files, or providing data. They support the high-level logic by doing the grunt work.
  * *Example:* Employees (do the actual implementation, logistics, and execution).
* **Abstraction**

---

## * SOLID Principles: Dependency Inversion Principle (DIP)

### Introduction
There is a set of five principles for writing clean, scalable, maintainable object-oriented code. These principles are known as **SOLID** principles. The **D** in SOLID stands for **Dependency Inversion Principle**.

**Definition:**
> "High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions."

In simpler words, Rather than high-level classes controlling and depending on the details of lower-level ones, both should rely on interfaces or abstract classes. This makes your code flexible, testable, and easier to maintain.

### Real-life Analogy
Let's say you're hungry and you want pizza. You use a food delivery app, and not contact the chef directly.
* You (user) → Use → Food App (Abstraction)
* Food App → Deals with → Restaurant/Chef (Implementation)

**Understanding**
You don't care which chef will make the pizza or how the pizza is made or who is your delivery partner - you just want it delivered from your selected restaurant on time. Here:
* You = High-level module
* Food App Interface = Abstraction
* Restaurant = Low-level module

You're not directly dependent on any specific details, but only on the food delivery system (abstraction).

This is what exactly DIP suggests while writing code with industry standards - high-level modules should not depend on low-level modules. Instead, both should depend on abstractions.

### Example: Netflix Recommendation Engine
Let's illustrate the Dependency Inversion Principle with a simple example of a Netflix recommendation engine.

Netflix uses various recommendation strategies:
* **Recently Added:** Shows/movies recently added to the catalog
* **Trending Now:** Based on what's currently popular
* **Genre-Based:** What you've watched and liked before

Now let's see how Netflix might (badly) and should (correctly) implements this using the Dependency Inversion Principle.

#### Without DIP - Tightly Coupled Code
```java
// Class implementing the recommendations based on recently added
class RecentlyAdded {
    // Method to get the recommendations
    public void getRecommendations() {
        System.out.println("Showing recently added content...");
    }
}

// Class implementing the overall Recommendation Engine
class RecommendationEngine {
    private RecentlyAdded recommender = new RecentlyAdded();

    public void recommend() {
        recommender.getRecommendations();
    }
}
```
**Issues in the above code:**
* `RecommendationEngine` is tightly coupled to `RecentlyAdded`.
* If we want to switch to `TrendingNow` or `GenreBased` strategies, we have to modify the engine.

#### With DIP - Using Abstraction
```java
// Interface provided for classes to implement different recommendation strategies
interface RecommendationStrategy {
    void getRecommendations();
}

// Class implementing recommendations based on recently added
class RecentlyAdded implements RecommendationStrategy {
    public void getRecommendations() {
        System.out.println("Showing recently added content...");
    }
}

// Class implementing recommendations based on trending now
class TrendingNow implements RecommendationStrategy {
    public void getRecommendations() {
        System.out.println("Showing trending content...");
    }
}

// Class implementing recommendations based on Genre
class GenreBased implements RecommendationStrategy {
    public void getRecommendations() {
        System.out.println("Showing content based on your favorite genres...");
    }
}

// Class implementing the Recommendation Engine (High - level module)
class RecommendationEngine {
    private RecommendationStrategy strategy;

    public RecommendationEngine(RecommendationStrategy strategy) {
        this.strategy = strategy;
    }

    public void recommend() {
        strategy.getRecommendations();
    }
}

// Main driver code
class Main {
    public static void main(String[] args) {
        RecommendationStrategy strategy = new TrendingNow(); // could also be RecentlyAdded or GenreBased
        RecommendationEngine engine = new RecommendationEngine(strategy);
        engine.recommend();
    }
}
```
Here:
* `RecommendationEngine` doesn't care how recommendations are made - it just needs a recommendation.
* The strategies (`TrendingNow`, `RecentlyAdded`, `GenreBased`) can be switched or upgraded anytime, without changing the engine.

#### Easier Switching between Strategies at Runtime
Let's say a user switches from "Recently Added" to "Genre-Based" dynamically:
```java
// Interface provided for classes to implement different recommendation strategies
interface RecommendationStrategy {
    void getRecommendations();
}

// Class implementing recommendations based on recently added
class RecentlyAdded implements RecommendationStrategy {
    public void getRecommendations() {
        System.out.println("Showing recently added content...");
    }
}

// Class implementing recommendations based on trending now
class TrendingNow implements RecommendationStrategy {
    public void getRecommendations() {
        System.out.println("Showing trending content...");
    }
}

// Class implementing recommendations based on Genre
class GenreBased implements RecommendationStrategy {
    public void getRecommendations() {
        System.out.println("Showing content based on your favorite genres...");
    }
}

// Class implementing the Recommendation Engine (High - level module)
class RecommendationEngine {
    private RecommendationStrategy strategy;

    public RecommendationEngine(RecommendationStrategy strategy) {
        this.strategy = strategy;
    }

    public void recommend() {
        strategy.getRecommendations();
    }
}

// Main driver code
class Main {
    public static void main(String[] args) {
        RecommendationEngine engine = new RecommendationEngine(new GenreBased());
        engine.recommend();
    }
}
```
No changes required in `RecommendationEngine` class - just pass a new strategy. That's the power of Dependency Inversion Principle used in designing the Recommendation Strategy.

### Benefits of using DIP
There are various benefits to using the Dependency Inversion Principle (DIP) in software design. Here are some of the key advantages:
* **Flexibility:** Easily swap out implementations without modifying high-level code.
* **Testability:** You can mock or stub the abstractions during testing.
* **Reusability:** Code becomes reusable since it's not tightly bound to one specific implementation.
* **Maintainability:** Makes it easier to change one part of the system without affecting others.
* **Scalability:** You can scale or upgrade parts of your codebase without a massive rewrite.

---
---
---
---

**TOPIC COMPLETED MOVING TO NEXT**

---
---
---
---

## * Unified Modeling Language (UML)

### Introduction
**Formal Definition:**
> UML (Unified Modeling Language) is a standardized modeling language used to visualize, specify, construct, and document the structure and behavior of software systems.

It provides a set of graphic notation techniques to create abstract models of systems, covering both static and dynamic aspects.

### Understanding
Think of UML as a toolkit of diagrams that helps software developers and designers map out how a system works, before or alongside writing the actual code. It's like planning a journey with a map — you get a clear picture of where everything is and how it all connects.

### Real-life Analogy
Imagine you're building a house. Before laying bricks, you'd need blueprints — diagrams that show where each room goes, how pipes connect, and how electricity flows. Without these, things can get messy, expensive, and confusing.

In the same way, UML diagrams are the blueprints of software systems. They help teams design systems clearly, avoid confusion, and catch problems early — before any code is written.

### Types of UML Diagrams
UML diagrams are divided into two main categories, each serving a different purpose in modeling software systems:

#### 1. Structural Diagrams
These describe the static structure of a system — what it contains, how different parts relate to each other, and how data is organized.

They are like the architectural blueprints of the system, showing the foundation, components, and their connections. Structural diagrams focus on the elements that exist in the system (like classes, objects, and hardware), rather than what happens during execution.

#### 2. Behavioral Diagrams
These describe the dynamic behavior of a system — how it behaves over time, how users interact with it, and how parts communicate during execution.

They are like the scripts and animations in a movie — showing what happens, when it happens, and who is involved. Behavioral diagrams focus on actions, interactions, processes, and state changes.

### Different Structural Diagrams
There are seven main types of structural diagrams in UML, each serving a specific purpose in modeling the static aspects of a system:
* **Class Diagram:** Shows classes, their properties, methods, and relationships — a map of the code structure.
* **Object Diagram:** Shows a snapshot of instances of classes and their relationships at a specific point in time.
* **Component Diagram:** Depicts how software components (modules) are organized and connected.
* **Composite Structure Diagram:** Shows the internal parts of a class and how they interact to carry out behavior.
* **Deployment Diagram:** Illustrates how software is physically deployed onto hardware devices or servers.
* **Package Diagram:** Groups related elements (like classes) into packages for better organization.
* **Profile Diagram:** Used to customize UML for specific platforms or domains by extending its elements.

### Different Behavioral Diagrams
There are seven main types of behavioral diagrams in UML, each serving a specific purpose in modeling the dynamic aspects of a system:
* **Use Case Diagram:** Captures what users (actors) can do with the system — its high-level functionalities.
* **Activity Diagram:** Models workflows and business processes — similar to flowcharts.
* **Sequence Diagram:** Shows the order of messages exchanged between objects over time.
* **Communication Diagram:** Emphasizes interactions between objects and how they're connected.
* **State Machine Diagram:** Depicts how an object transitions between states based on events.
* **Interaction Overview Diagram:** Combines features of sequence and activity diagrams to model interaction flow.
* **Timing Diagram:** Focuses on object behavior with respect to time, particularly useful for real-time systems.

> [!NOTE]
> **Focusing on Low-Level Design (LLD):**
> When diving into Low-Level Design, the focus is on the internal structure and detailed interaction of software components. While all UML diagrams have their place, the **Class Diagram** is considered the most important for mastering LLD. It provides a clear view of the classes, their attributes, methods, and relationships, making it essential for understanding how to design and implement software systems effectively.

### UML Class Diagrams: Introduction
A UML Class Diagram provides a high-level overview of the system architecture. It captures the system's classes, interfaces, enumerations, their attributes and operations (methods), and the relationships among them. It is instrumental in both forward and reverse engineering processes and is widely used in modeling object-oriented systems.

Class diagrams support various design activities including domain modeling, data modeling, and the architectural representation of systems. These diagrams are often created during the early stages of the software development lifecycle and refined as the project progresses.

Looking at a class diagram, you must quickly be able to understand the system's structure and how different components interact with each other. This is particularly useful for new team members or stakeholders who need to get up to speed with the system's design regardless of understanding the underlying code.

In this section, we will explore the various components of UML Class Diagrams, including classes, attributes, methods, and relationships. We will also discuss the notations used to represent these elements and how they can be effectively utilized in software design.

### UML Class Notations

#### 1. Class representation
A class in UML is depicted as a rectangle divided into three compartments:
* **Top compartment:** Contains the class name (bold and centered).
* **Middle compartment:** Lists the attributes.
* **Bottom compartment:** Lists the operations (methods).

![Class Representation](IMAGES/uml/class.png)

Each attribute or method is listed with its visibility marker, name, and type (for attributes) or return type (for methods). Parameters for methods are also specified in the parentheses.

#### 2. Visibility Markers
Visibility markers define access levels for attributes and operations:
* **Public (+):** Accessible from any other class.
* **Private (-):** Accessible only within the class itself.
* **Protected (#):** Accessible within the class and its subclasses.
* **Package (~):** Accessible within the same package.

These markers help enforce encapsulation, a core principle in object-oriented design.

#### 3. Attributes and Method System
Attributes and methods follow this syntax in class diagrams:

**3.1 Attributes**
`visibility name: Type [multiplicity] = DefaultValue`

Let's break this down:
* `visibility`: The visibility marker (e.g., +, -, #, ~).
* `name`: The name of the attribute.
* `Type`: The data type of the attribute (e.g., int, String).
* `multiplicity`: An optional field indicating how many instances of the attribute can exist (e.g., 0..1, 1..*, etc.).
* `DefaultValue`: An optional default value for the attribute.

For example, if you wish to represent the following statement: 
`public int age = 21;`

using a class diagram, then the conversion will look like this: 
`+ age: int = 21`

![UML Representation of Attribute](IMAGES/uml/attribute.png)

**3.2 Methods (Operations):**
`visibility name(parameterName1: Type1,...): ReturnType`

Let's break this down:
* `visibility`: The visibility marker (e.g., +, -, #, ~).
* `name`: The name of the method.
* `parameterName`: The name of the parameter.
* `Type`: The data type of the parameter.
* `ReturnType`: The return type of the method.

For example, if you wish to represent the method inside the class:
```java
class Person {
    private boolean isAdult(int age) { 
        return age >= 18; 
    }
}
```

using a class diagram, then the conversion will look like this:
`- isAdult(age:int): boolean`

![UML Representation of Method](IMAGES/uml/method.png)

Optional elements like multiplicity, default values, and stereotypes (e.g., `<<constructor>>`, `<<static>>`) can also be included to enrich the diagram.

#### 4. Interface
An interface defines a contract that other classes must follow. It contains only abstract methods (no implementation). UML class diagram for interfaces contains the following compartments:
* **Name compartment:** Contains the stereotype `<<interface>>` and the name of the interface.
* **Operation compartment:** Contains method signatures (i.e., abstract operations to be implemented).

For example, consider the following interface that can be represented as the diagram given below:
```java
// Interface for classes that can calculate pay
public interface Payable {
    
    // Method to calculate pay
    double calculatePay();
}
```

![UML Representation of Interface](IMAGES/uml/interface.png)

> [!NOTE]
> Note that by default, interfaces don't have a compartment for attributes like regular classes. However, there is an exception, i.e., If the interface declares constants, you may include an attribute compartment to show them.

#### 5. Abstract Class
An abstract class is a class that cannot be instantiated and may contain both implemented and unimplemented (abstract) methods. It is represented in UML class diagrams with the `<<abstract>>` stereotype above the class name and the class name being italic.
```java
// Abstract class representing an Animal
public abstract class Animal {

    // Abstract method to make sound
    public abstract void makeSound();
}
```
The diagram representation of the above code will look like this:

![UML Representation of Abstract Class](IMAGES/uml/abstract.png)

#### 6. Enumeration (Enum)
An enumeration is a data type consisting of a fixed set of named values, often called literals. It is represented in UML class diagrams with the `<<enumeration>>` stereotype above the name in one compartment and list of literals in another compartment.

![UML Representation of Enumeration](IMAGES/uml/enum.png)

### Perspectives of Class Diagrams

#### 1. Conceptual Perspective
Its purpose is to provide a high-level view of the system, focusing on the main concepts and their relationships. It is often used in the early stages of system design to establish a common understanding among stakeholders (Business Analysts, Domain Experts).
* **Diagram Style:**
  * Classes represent real-world concepts, like Customer, Order, Invoice.
  * No attributes or operations are shown unless absolutely necessary.
  * Relationships depict business-level associations, not implementation details.

#### 2. Specification Perspective
Its purpose is to define the structure and behavior of the system's classes, focusing on responsibilities, roles, and collaborations without specifying code-level details. This view highlights what operations a class should support, enabling interface and design-level planning. It is meant for System Architects and Software Designers.
* **Diagram Style:**
  * Includes abstract classes, interfaces, and key public methods.
  * Shows associations and inheritance relationships between classes and interfaces.
  * Focuses on contract-based design (e.g., what a class promises to do).

#### 3. Implementation Perspective
Its purpose is to present a concrete, code-level view of the system. This perspective includes complete class definitions, access modifiers, attributes with types and default values, and full method signatures. It is mainly used by developers and software engineers during the implementation phase.
* **Diagram Style:**
  * Shows all attributes (public, private, etc.) and methods.
  * Includes visibility markers (`+` public, `-` private, `#` protected).
  * May show data types, default values, and even constructors.
  * All relationships — including association, aggregation, composition, inheritance, and dependency — are explicitly visualized.

### Relationship Between Classes

#### 1. Association (USE-A)
Association represents a general relationship between two classes where one class uses or interacts with another. It can be: one-to-one, one-to-many or many-to-many.
* **Example:** A teacher can teach multiple students, and a student can be taught by multiple teachers (many-to-many association).
* **UML Notation:** A solid line between the two classes.

#### 2. Aggregation (HAS-A)
Aggregation is a "whole-part" relationship where a class is made up of one or more classes, but those parts can exist independently.
* **Example:** A Department has multiple Professors. If the department is removed, the professors still exist.
* **UML Notation:** A hollow diamond at the container (whole) class.

#### 3. Composition (Strong HAS-A)
Composition is a stronger form of aggregation where the part cannot exist without the whole. It is a "whole-part" relationship where the part is dependent on the whole.
* **Example:** A House has Rooms. If the House is destroyed, so are the Rooms.
* **UML Notation:** A filled diamond at the whole side.

#### 4. Inheritance
Inheritance defines an IS-A relationship where a subclass inherits properties and behavior from a superclass. The subclass can extend or override the superclass's attributes and methods.
* **Example:** A Dog is an Animal.
* **UML Notation:** A solid line with a hollow triangle pointing to the parent class.

#### 5. Realization (Implementation)
Realization is the relationship between a class and an interface. The class agrees to implement the behavior declared by the interface.
* **Example:** A Circle class implements the Shape interface.
* **UML Notation:** A dashed line with a hollow triangle pointing to the interface.

#### 6. Dependency
Dependency indicates that a class uses another class temporarily. Changes to the used class may affect the dependent class.
* **Example:** `OrderService` depends on `PaymentService` to process payments.
* **UML Notation:** A dashed line with an open arrow pointing to the class being used.

### Summary Table
| Relationship | UML Notation | Example |
| :--- | :--- | :--- |
| Association | Solid line | `Student ——— Teacher` |
| Aggregation | Solid line with hollow diamond | `Department ◇——— Professor` |
| Composition | Solid line with filled diamond | `House ◆——— Room` |
| Inheritance | Solid line with hollow triangle | `Dog ———▷ Animal` |
| Realization | Dashed line with hollow triangle | `Circle - - - ▷ Shape Interface` |
| Dependency | Dashed line with open arrow | `Order - - - → Payment Services` |

![Summary Table](IMAGES/uml/summary.png)

---
---
---
---
---
---
---
---
---
---
---
---
---
---
---

**TOPIC COMPLETED MOVING TO NEXT**

---
---
---
---
---
---
---
---
---
---
---
---
---
---
---

## * Design Patterns

### Introduction
Design patterns are a foundational concept in software engineering, especially when building scalable and maintainable systems. In this article, we explore what design patterns are, why they matter, how they originated, and how they are categorized. This introduction sets the stage for deeper dives into individual patterns in upcoming discussions.

### What Are Design Patterns?
Design patterns are standard, time-tested solutions to common software design problems. They are not code templates but abstract descriptions or blueprints that help developers solve issues in code architecture and system design.

To put it simply: Design patterns help you avoid reinventing the wheel when facing recurring design challenges.

#### Real-World Analogy
Think of design patterns like recipes in cooking. If you want to bake a cake, you don't experiment from scratch each time - you follow a proven recipe. Similarly, design patterns are tried-and-tested “recipes” for solving common coding problems efficiently and consistently.

### The Origin of Design Patterns
The idea of design patterns was formalized by the Gang of Four (GoF) - Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides - in their seminal 1994 book "Design Patterns: Elements of Reusable Object-Oriented Software."

They cataloged 23 design patterns that were repeatedly seen in object-oriented software development and grouped them into three major categories.

### The Three Categories of Design Patterns

#### 1. Creational Patterns
These focus on object creation mechanisms, trying to create objects in a manner suitable to the situation. They abstract the instantiation process, making the system independent of how its objects are created.

**Real-World Analogy:**
Imagine ordering a drink at a vending machine. You press a button (say “Orange Juice”), and the machine internally figures out how to prepare it - whether to pour from a bottle, mix a concentrate, or use a fresh dispenser. You don't care how it's made - you just get your drink.

This is similar to the Factory Pattern, where the creation logic is hidden from the user and abstracted for flexibility.

**Examples include:**
* Singleton Pattern
* Factory Method
* Abstract Factory Pattern
* Builder Pattern
* Prototype Pattern

#### 2. Structural Patterns
These deal with object composition - how classes and objects can be combined to form larger structures while keeping the system flexible and efficient. It helps systems to work together that otherwise could not because of incompatible interfaces.

**Real-World Analogy:**
Suppose you have a modern smartphone (your system) that uses a USB-C charger, but your old power adapter only supports micro-USB. Instead of replacing either device, you use an adapter that connects the two.

That adapter is like a structural pattern (specifically, the Adapter Pattern) - it allows incompatible components to work together seamlessly without changing their internals.

**Examples include:**
* Adapter Pattern
* Bridge Pattern
* Composite Pattern
* Decorator Pattern
* Facade Pattern
* Flyweight Pattern
* Proxy Pattern

#### 3. Behavioral Patterns
These are concerned with object interaction and responsibility - how they communicate and assign responsibilities while ensuring loose coupling.

**Real-World Analogy:**
Think of a restaurant. The waiter takes your order and passes it to the kitchen. You don't talk directly to the chef - the waiter acts as a mediator between you and the kitchen.

This reflects the Mediator Pattern, which defines an object that controls communication between other objects, preventing tight interdependencies.

**Examples include:**
* Observer Pattern
* Strategy Pattern
* Interpreter Pattern
* Command Pattern
* Chain of Responsibility
* Mediator Pattern
* State Pattern
* Template Method
* Visitor Pattern
* Iterator Pattern
* Memento Pattern

> [!NOTE]
> This is just a brief overview of design patterns. Each pattern has its own unique characteristics, advantages, and use cases. In the following topics, we will delve deeper into each category and explore specific patterns in detail.

### Creational Design Patterns

#### 1. Singleton Pattern
The Singleton Pattern ensures that a class has only one instance and provides a global point of access to that instance.

**In simpler terms:**
Imagine you're building an application where you only want one shared object throughout the lifecycle of the program. This is where Singleton comes into play - it restricts object creation and guarantees that all parts of your application use the same object.

**The Problem It Solves**
In a typical application, creating multiple objects of a class might not be problematic. However, in certain scenarios - like logging, configuration handling, or managing a database connection - you want just one instance to avoid redundancy, excessive memory use, or inconsistent behavior.

**Real-World Analogy: The Operating System's Print Spooler**
Imagine you're in an office with multiple employees, and everyone sends documents to a single shared printer. Now, if each computer tried to talk directly to the printer on its own terms, the printer would get overwhelmed - prints might get jumbled, overlap, or crash the device.

Instead, there's a Print Spooler - a background service that manages all print jobs. No matter who initiates the print, they all go through one centralized spooler instance that queues and handles the tasks in order.

**Why Is It a Creational Pattern?**
The Singleton Pattern falls under the creational design patterns. This is because it deals with how objects are created. Unlike simple instantiation (`new`), Singleton controls the object creation process by returning an existing instance rather than creating a new one.

**Identifying the Need for a Singleton**
Imagine you're developing a logging service. You need a class that writes logs to a file. If every part of your application creates a new logger instance, the result might be:
* Overwritten logs
* Multiple file handles
* Synchronization issues

Instead, if there's only one logger instance (a Singleton), all parts of the program write to the same log file in a controlled manner.

#### Working of Singleton Pattern
The Singleton Pattern typically involves the following steps:
1. **Private constructor:** Prevents instantiation from outside the class.
2. **Static variable:** Holds the single instance of the class.
3. **Public static method:** Provides a global access point to get the instance.

This ensures that no matter how many times you call the method to get an instance, it will always return the same object.

#### Approaches to Implement Singleton Pattern:
In the real world, while designing the product, there are two primary ways to implement the Singleton pattern:
1. Eager Loading
2. Lazy Loading

Each with its own trade-offs in terms of performance, memory usage, and thread safety.

##### 1. Eager Loading (Early Initialization)
In Eager Loading, the Singleton instance is created as soon as the class is loaded, regardless of whether it's ever used. Let's understand this with a real-life analogy.

**Real-World Analogy: Fire Extinguisher in a Building**
A fire extinguisher is always present, even if a fire never occurs. Similarly, eager loading creates the Singleton instance upfront, just in case it's needed.

**Example Code:**
```java
// Class implementing Eager Loading
class EagerSingleton {
    private static final EagerSingleton instance = new EagerSingleton();

    // private constructor
    private EagerSingleton() {
        // Declaring it private prevents creation of its object using the new keyword
    }

    // Method to get the instance of class
    public static EagerSingleton getInstance() {
        return instance; // Always returns the same instance 
    }
}
```

**Understanding**
* The object is created immediately when the class is loaded.
* It's always available and inherently thread-safe.

**Pros**
* Very simple to implement.
* Thread-safe without any extra handling.

**Cons**
* Wastes memory if the instance is never used.
* Not suitable for heavy objects.

##### 2. Lazy Loading (On-Demand Initialization)
In Lazy Loading, the Singleton instance is created only when it's needed - the first time the `getInstance()` method is called.

**Real-World Analogy: Coffee Machine**
Imagine a coffee machine that only brews coffee when you press the button. It doesn't waste energy or resources until you actually want a cup. Similarly, lazy loading creates the Singleton instance only when it's requested.

**Example Code:**
```java
// Class implementing Lazy Loading
class LazySingleton {
    // Object declaration
    private static LazySingleton instance;

    // private constructor
    private LazySingleton() {
        // Declaring it private prevents creation of its object using the new keyword
    }

    // Method to get the instance of class
    public static LazySingleton getInstance() {
        // If the object is not created 
        if (instance == null) {
            // A new object is created
            instance = new LazySingleton();
        }

        // Otherwise the already created object is returned
        return instance;
    }
}
```

**Understanding**
* The instance starts as null.
* It is only created when `getInstance()` is first called.
* Future calls return the already created instance.

**Pros**
* Saves memory if the instance is never used.
* Object creation is deferred until required.

**Cons**
* Lazy Loading is **Not** thread-safe by default. Thus, it requires synchronization in multi-threaded environments.

#### Thread Safety: A Critical Concern in Singleton Pattern
In a single-threaded environment, implementing a Singleton is straightforward. However, things get complicated in multi-threaded applications, which are very common in modern software (especially web servers, mobile apps, etc.).

**The Problem**
Let's say two threads simultaneously call `getInstance()` for the first time in a lazy-loaded Singleton. If the instance hasn't been created yet, both threads might pass the `null` check and end up creating two different instances - completely breaking the Singleton guarantee.

This kind of bug is:
* **Hard to detect**, as it may not occur every time.
* **Severe**, because it defeats the whole purpose of the pattern.
* **Costly**, especially if the Singleton manages critical resources like logging, configuration, or DB connections.

#### Different Ways to Achieve Thread Safety
There are several ways to make the Singleton pattern thread-safe. Here are a few common approaches:

##### 1. Synchronized Method
This is the simplest way to ensure thread safety. By synchronizing the method that creates the instance, we can prevent multiple threads from creating separate instances at the same time. However, this approach can lead to performance issues due to the overhead of synchronization.

Consider the following code snippet for better understanding:
```java
public class Singleton {
    // Object declaration
    private static Singleton instance;

    // Private constructor
    private Singleton() {}

    // Synchronized keyword used
    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

**What synchronized keyword does?**
The `synchronized` keyword ensures that only one thread at a time can execute the `getInstance()` method. This prevents multiple threads from entering the method simultaneously and creating multiple instances.

**Pros**
* Simple and easy to implement.
* Thread-safe without needing complex logic.

**Cons**
* Performance overhead: Every call to `getInstance()` is synchronized, even after the instance is created.
* May slow down the application in high-concurrency scenarios.

##### 2. Double-Checked Locking
This is a more efficient way to achieve thread safety. The idea is to check if the instance is `null` before acquiring the lock. If it is, then we synchronize the block and check again. This reduces the overhead of synchronization after the instance has been created.

Consider the following code snippet for better understanding:
```java
public class Singleton {
    // Volatile object declaration
    private static volatile Singleton instance;

    // Private constructor
    private Singleton() {}

    // Thread-safe method using double-checked locking
    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}
```

**Understanding**
* The outer `if` check avoids synchronization once the instance is created.
* The inner `if` inside `synchronized` ensures that only one thread creates the instance.
* `volatile` keyword ensures changes made by one thread are visible to others. Without `volatile`, one thread might create the Singleton instance, but other threads may not see the updated value due to caching. `volatile` ensures that the instance is always read from the main memory, so all threads see the most up-to-date version.

**Pros**
* Efficient: Synchronization only happens once, when the instance is created.
* Safe and fast in concurrent environments.

**Cons**
* Slightly more complex than the synchronized method.
* Requires Java 1.5 or above due to reliance on `volatile`.

##### 3. Bill Pugh Singleton (Best Practice for Lazy Loading)
This is a highly efficient way to implement the Singleton pattern. It uses a static inner helper class to hold the Singleton instance. The instance is created only when the inner class is loaded, which happens only when `getInstance()` is called for the first time.

Consider the following code snippet for better understanding:
```java
public class Singleton {
    // Private constructor
    private Singleton() {}

    // Static inner class to hold the Singleton instance
    private static class Holder {
        private static final Singleton INSTANCE = new Singleton();
    }

    // Public method to return the Singleton instance
    public static Singleton getInstance() {
        return Holder.INSTANCE;
    }
}
```

**Explanation**
* The Singleton instance is not created until `getInstance()` is called.
* The static inner class (`Holder`) is not loaded until referenced, thanks to Java's class loading mechanism.
* It ensures thread safety, lazy loading, and high performance without synchronization overhead.

**Pros**
* Best of both worlds: Lazy + Thread-safe.
* No need for `synchronized` or `volatile`.
* Clean and efficient.

**Cons**
* It is slightly less intuitive for beginners due to the use of a nested static class.

##### 4. Eager Loading
As discussed earlier, eager loading does not face thread safety issues. This approach avoids thread issues altogether by creating the instance upfront - at the cost of potential memory waste. Thus, it is not a preferred method in most cases but is still a valid option.

#### Pros of Singleton Pattern
* **Cleaner Implementation:** Singleton offers a straightforward and tidy way to manage a single instance of a class, especially when designed with thread safety and simplicity in mind.
* **Guarantees One Instance:** This pattern enforces that only one instance of the class can exist, making it ideal for shared resources.
* **Provides a Way to Maintain a Global Resource:** It allows centralized access to a global resource or service, which can be useful in managing application-wide configurations or state.
* **Supports Lazy Loading:** Many Singleton implementations allow the instance to be created only when it is first accessed, optimizing memory usage and startup performance.

#### Cons of Singleton Pattern
* **Used with Parameters and Confused with Factory:** When a Singleton class requires parameters for instantiation, it may blur lines with the Factory pattern, leading to design confusion.
* **Hard to Write Unit Tests:** Since the Singleton holds a global state, it becomes difficult to isolate and mock for unit testing, thus potentially hindering testability.
* **Classes Using It Are Highly Coupled to It:** Components that depend on the Singleton become tightly coupled to its implementation, which reduces flexibility and makes code harder to maintain or refactor.
* **Special Cases to Avoid Race Conditions:** In multi-threaded environments, care must be taken to avoid race conditions during the instance creation phase, complicating implementation.
* **Violates the Single Responsibility Principle (SRP):** A Singleton often handles both instance control and its core functionality, thereby violating the SRP, a key principle of clean software design.

#### Conclusion
#### Conclusion
The Singleton pattern can be a powerful tool when used appropriately, particularly for managing global states and shared resources. However, developers should be mindful of its drawbacks, especially regarding testing and maintainability. Consider alternatives or enhanced implementations (like dependency injection) where appropriate to maintain clean and scalable codebases.

---
---
---
---
---

#### 2. Factory Pattern
The Factory Pattern is a creational design pattern that provides an interface for creating objects but allows subclasses to alter the type of objects that will be created.

**In simpler terms:**
Rather than calling a constructor directly to create an object, we use a factory method to create that object based on some input or condition.

**When Should You Use It?**
We can use the Factory Pattern when:
* The client code needs to work with multiple types of objects.
* The decision of which class to instantiate must be made at runtime.
* The instantiation process is complex or needs to be controlled.

**Real-World Analogy: Ordering Pizza**
Imagine you walk into a pizza shop and say, “I'd like a pizza.” The shop doesn't ask you to go into the kitchen and make it yourself. Instead, it asks, “Which type? Margherita? Pepperoni? Veggie?” Based on your choice, the kitchen (factory) creates the specific pizza for you and hands it over.

You (the client), don't care how it's made or what specific class of ingredients is used. You just want your pizza. The factory (kitchen) handles the creation logic behind the scenes.

This is exactly what the Factory Pattern does in code: it creates an object based on some input without exposing the instantiation logic to the client.

#### Basic Structure of Factory Pattern
The Factory Pattern typically consists of the following components:
* **Product:** It is an interface or abstract class that defines the methods the product must implement.
* **Concrete Products:** The concrete classes that implement the Product interface.
* **Factory:** A class with a method that returns different concrete products based on input.

Consider the following example code snippet:
```java
// Interface 
interface Shape {
    void draw();
}

// Class implementing the Shape Interface
class Circle implements Shape {
    @Override
    public void draw() {
        System.out.println("Drawing Circle");
    }
}

// Class implementing the Shape Interface
class Square implements Shape {
    @Override
    public void draw() {
        System.out.println("Drawing Square");
    }
}

// Factory Class
class ShapeFactory {
    /* Method that takes the type of shape as input 
    and returns the corresponding object */
    public Shape getShape(String shapeType) {
        if (shapeType.equalsIgnoreCase("CIRCLE")) {
            return new Circle();
        } else if (shapeType.equalsIgnoreCase("SQUARE")) {
            return new Square();
        }
        return null;
    }
}

// Driver code
class Main {
    public static void main(String[] args) {
        // Object of ShapeFactory is initialized
        ShapeFactory shapeFactory = new ShapeFactory();

        // Get a Circle object and call its draw method
        Shape shape1 = shapeFactory.getShape("CIRCLE");
        shape1.draw();

        // Get a Square object and call its draw method
        Shape shape2 = shapeFactory.getShape("SQUARE");
        shape2.draw();
    }
}
```

Here, `ShapeFactory` is the factory that returns different objects (`Circle`, `Square`) based on input.

#### Real-life Product Example - Logistics Services
Let's say you are building a logistics application that needs to handle different types of transport services: By Road, By Air, etc.

##### Bad Practice: Not Following Factory Pattern
Consider the following code snippet where object creation logic is tightly coupled with business logic:
```java
// Logistics Interface
interface Logistics {
    void send();
}

// Class implementing the Logistics Interface
class Road implements Logistics {
    @Override
    public void send() {
        System.out.println("Sending by road logic");
    }
}

// Class implementing the Logistics Interface
class Air implements Logistics {
    @Override
    public void send() {
        System.out.println("Sending by air logic");
    }
}

// Class implementing Logistics Service
class LogisticsService {
    public void send(String mode) {
        if (mode.equals("Air")) {
            Logistics logistics = new Air();
            logistics.send();
        } else if (mode.equals("Road")) {
            Logistics logistics = new Road();
            logistics.send();
        }
    }
}

// Driver code
class Main {
    public static void main(String[] args) {
        LogisticsService service = new LogisticsService();
        service.send("Air");
        service.send("Road");
    }
}
```

**Understanding the Issue:**
In the `LogisticsService` class:
* The object of `Air` or `Road` is directly instantiated based on string comparison.
* The object creation logic is embedded inside the business logic (`send` method).
* This violates the Open/Closed Principle — if you want to add a new mode (e.g., Ship), you have to modify the `send` method.

**Problems:**
* **Tight Coupling:** `LogisticsService` depends directly on `Air` and `Road` classes.
* **Hard to Extend:** Adding a new mode (e.g., Drone, Ship) requires modifying existing code.
* **No Separation of Concerns:** Object creation and business logic are mixed.
* **Code Duplication:** Repeated instantiation and `send()` logic.
* **Testing & Maintenance Nightmare:** Hard to test independently or mock logistics.

##### Good Practice: Following Factory Pattern
Let's now apply the Factory Pattern to clean this up and make it scalable.
```java
// Logistic Interface
interface Logistics {
    void send();
}

// Class implementing the Logistics Interface
class Road implements Logistics {
    @Override
    public void send() {
        System.out.println("Sending by road logic");
    }
}

// Class implementing the Logistics Interface
class Air implements Logistics {
    @Override
    public void send() {
        System.out.println("Sending by air logic");
    }
}

// Factory Class taking care of Logistics
class LogisticsFactory {
    public static Logistics getLogistics(String mode) {
        if (mode.equalsIgnoreCase("Air")) {
            return new Air();
        } else if (mode.equalsIgnoreCase("Road")) {
            return new Road();
        }
        throw new IllegalArgumentException("Unknown logistics mode: " + mode);
    }
}

// Class implementing the Logistics Services
class LogisticsService {
    public void send(String mode) {
        /* Using the Logistics Factory to get the 
        desired object based on the mode */
        Logistics logistics = LogisticsFactory.getLogistics(mode);
        logistics.send();
    }
}

// Driver Code
class Main {
    public static void main(String[] args) {
        LogisticsService service = new LogisticsService();
        service.send("Air");
        service.send("Road");
    }
}
```

**Understanding the Improvement:**
In this refactored code:
* The object creation logic is moved to the `LogisticsFactory`.
* The `LogisticsService` class now only focuses on business logic.
* Adding a new mode (e.g., Ship) only requires modifying the factory, not the service.

**Benefits:**
* **Loose Coupling:** The service is decoupled from specific logistics classes.
* **Open/Closed Principle:** New modes can be added without modifying existing code.
* **Separation of Concerns:** Object creation and business logic are separated.
* **No Code Duplication:** Instantiation logic is centralized in the factory.
* **Easier Testing & Maintenance:** Each component can be tested independently.

#### Pros of Factory Pattern
* **Promotes Loose Coupling:**
  * The client code is decoupled from the actual instantiation of classes.
  * You work with interfaces rather than concrete classes.
* **Enhances Extensibility (OCP - Open/Closed Principle):**
  * You can introduce new classes (e.g., new types of logistics like Ship) without modifying existing client code.
  * The system becomes easier to scale and extend.
* **Centralizes Object Creation (SRP - Single Responsibility Principle):**
  * The responsibility of object creation is moved to a dedicated factory class.
  * Business logic stays clean and focused only on "what to do" with the object.
* **Increases Flexibility:**
  * The decision of "which object to create" can be deferred to runtime based on input, config, or logic.
  * Makes your system adaptable to dynamic requirements.
* **Improves Code Reusability:**
  * Common instantiation logic can be reused from a single factory.
  * Avoids code duplication when creating similar objects in different parts of the system.

#### Cons of Factory Pattern
* **Increased Complexity:** Introduces additional layers (factory classes/interfaces) which might be overkill for very small programs.
* **More Code Overhead:** Requires writing extra code like factory classes and interfaces, which might look unnecessary in simpler use-cases.

#### Class Diagram
![Factory Pattern Class Diagram](IMAGES/factory_class_diagram.png)

---
---
---
---
---

#### 3. Builder Pattern
The Builder Pattern is a creational design pattern that separates the construction of a complex object from its representation. This allows you to create different types and representations of an object using the same construction process.

**Formal Definition:**
"Builder pattern builds a complex object step by step. It separates the construction of a complex object from its representation, so that the same construction process can create different representations."

**In simpler terms:**
Imagine you're ordering a custom burger. You choose the bun, patty, toppings, sauces, and whether you want it grilled or toasted. The chef follows your instructions step by step to build your custom burger. This is what the Builder Pattern does - it lets you construct complex objects by specifying their parts one at a time, giving you flexibility and control over the object creation process.

**Real-life Analogy (Custom Pizza Order)**
Think of ordering a pizza online. You select the crust type, size, toppings, cheese, and sauce - all step by step. The pizza shop then builds your pizza according to your selections. Different customers can use the same process to get entirely different pizzas. This is the essence of the Builder Pattern: a structured, step-wise approach to creating customized complex objects.

#### Understanding the Problem
Imagine you're building a `BurgerMeal` in your application. A burger must have some mandatory components like: Bun and Patty. And it can also include optional components like: Sides, Toppings, and Cheese.

Now let’s try to implement this using a traditional constructor approach:
```java
import java.util.*;

// Represents a customizable Burger Meal
class BurgerMeal {
    // Mandatory components
    private String bun;
    private String patty;

    // Optional components
    private String sides;
    private List<String> toppings;
    private boolean cheese;

    // Constructor trying to handle all combinations
    public BurgerMeal(String bun, String patty, String sides, List<String> toppings, boolean cheese) {
        this.bun = bun;
        this.patty = patty;
        this.sides = sides;
        this.toppings = toppings;
        this.cheese = cheese;
    }
}

class Main {
    public static void main(String[] args) {
        // Constructing the object with only required details
        BurgerMeal burgerMeal = new BurgerMeal("wheat", "veg", null, null, false);
    }
}
```

**Issues in Code:**
This constructor approach works, but it creates multiple problems:
* **Hard to Read and Maintain:** The user has to remember the order of parameters and their types. It becomes difficult to read when more optional parameters are added.
* **Unnecessary null values:** Even if the user doesn’t want toppings or sides, they still have to pass `null` explicitly. This clutters the object creation code.
* **Risk of NullPointerException:** If we forget to null-check before accessing optional values inside the class, it may lead to runtime exceptions.
* **Too Many Constructor Overloads:** To handle various combinations (e.g., with cheese, without sides, only toppings, etc.), you’d need to create multiple overloaded constructors - which is not scalable.
* **Tight Coupling Between Parameters and Construction:** There is no flexibility to set values step by step. The entire object must be built in one go, which doesn't match the natural way of ordering or customizing a burger.

##### Telescoping Constructor Anti-Pattern
To manage optional parameters, many developers try to solve this by writing multiple overloaded constructors - each with one more optional parameter than the last. For example:
```java
class BurgerMeal {
    public BurgerMeal(String bun, String patty) { ... }
    public BurgerMeal(String bun, String patty, boolean cheese) { ... }
    public BurgerMeal(String bun, String patty, boolean cheese, String side) { ... }
    public BurgerMeal(String bun, String patty, boolean cheese, String side, String drink) { ... }
}
```

This is called the **Telescoping Constructor Anti-Pattern**.

But this creates a cascade of constructors that become:
* Hard to read and write
* Error-prone due to confusing parameter order
* Difficult to maintain when more fields are added
* Inflexible, as users must use parameters in a specific order

It occurs most commonly in Java, which lacks support for optional or default parameters (unlike C++ or Python). Because of this limitation, developers are forced to create multiple constructor overloads to handle different combinations of parameters.

Clearly, this approach doesn't scale well. And this is exactly the kind of problem that the Builder Pattern is designed to solve. It gives the user full control over which parts to build while keeping the construction code clean, readable, and safe.

#### The Solution
To solve the problems we saw earlier with constructors, we use the Builder Pattern. It separates object construction from its representation, allowing us to build step-by-step while keeping the object immutable and readable.

**Code**
```java
import java.util.*;

// Represents a customizable Burger Meal
class BurgerMeal {
    // Required components
    private final String bunType;
    private final String patty;

    // Optional components
    private final boolean hasCheese;
    private final List<String> toppings;
    private final String side;
    private final String drink;

    // Private constructor to force use of Builder
    private BurgerMeal(BurgerBuilder builder) {
        this.bunType = builder.bunType;
        this.patty = builder.patty;
        this.hasCheese = builder.hasCheese;
        this.toppings = builder.toppings;
        this.side = builder.side;
        this.drink = builder.drink;
    }

    // Static nested Builder class
    public static class BurgerBuilder {
        // Required
        private final String bunType;
        private final String patty;

        // Optional
        private boolean hasCheese;
        private List<String> toppings;
        private String side;
        private String drink;

        // Builder constructor with required fields
        public BurgerBuilder(String bunType, String patty) {
            this.bunType = bunType;
            this.patty = patty;
        }

        // Method to set cheese
        public BurgerBuilder withCheese(boolean hasCheese) {
            this.hasCheese = hasCheese;
            return this;
        }

        // Method to set toppings
        public BurgerBuilder withToppings(List<String> toppings) {
            this.toppings = toppings;
            return this;
        }

        // Method to set side
        public BurgerBuilder withSide(String side) {
            this.side = side;
            return this;
        }

        // Method to set drink
        public BurgerBuilder withDrink(String drink) {
            this.drink = drink;
            return this;
        }

        // Final build method
        public BurgerMeal build() {
            return new BurgerMeal(this);
        }
    }
}

class Main {
    public static void main(String[] args) {
        // Creating burger with only required fields
        BurgerMeal plainBurger = new BurgerMeal.BurgerBuilder("wheat", "veg")
                                    .build();

        // Burger with cheese only
        BurgerMeal burgerWithCheese = new BurgerMeal.BurgerBuilder("wheat", "veg")
                                        .withCheese(true)
                                        .build();

        // Fully loaded burger
        List<String> toppings = Arrays.asList("lettuce", "onion", "jalapeno");
        BurgerMeal loadedBurger = new BurgerMeal.BurgerBuilder("multigrain", "chicken")
                                        .withCheese(true)
                                        .withToppings(toppings)
                                        .withSide("fries")
                                        .withDrink("coke")
                                        .build();
    }
}
```

**Understanding the Code**
* **Private Constructor:** The constructor of `BurgerMeal` is made private so that object creation is restricted to the Builder only.
* **Nested Static BurgerBuilder Class:** This builder class holds the same fields as `BurgerMeal`. It ensures immutability and keeps construction controlled.
* **Fluent API Style:** Each method (like `withCheese`, `withSide`) returns the builder itself, enabling method chaining in a fluent and readable manner.
* **Selective Configuration:** Only required fields (`bunType`, `patty`) are passed to the builder's constructor. Everything else is optional and set via `withXYZ()` methods.
* **Final Step: build():** Once all desired fields are set, calling `.build()` finalizes the object construction and returns the `BurgerMeal` instance.

##### Why This is Better
| Aspect | Constructor Approach | Builder Pattern |
| :--- | :--- | :--- |
| **Object readability** | Poor (nulls, long argument list) | Excellent (fluent and expressive) |
| **Flexibility** | Low (all-or-nothing setup) | High (configure only what’s needed) |
| **Maintainability** | Hard to scale with more fields | Easy to extend with more options |
| **Safety** | High chance of errors with nulls | Controlled and safe instantiation |

#### When to Use and When to Avoid the Builder Pattern

**When to Use?**
You should consider using the Builder Pattern in the following scenarios:
* An object has multiple fields, especially when many of them are optional. Managing such objects using constructors becomes messy and error-prone.
* Immutability is preferred - Builder lets you construct an object step by step and then make it immutable once built.
* You want readable, maintainable object creation, especially when dealing with domain models or configuration objects. The fluent interface style improves clarity and flexibility.

**When to Avoid?**
The Builder Pattern can be overkill in simpler use cases. Avoid it when:
* Your class has only 1-2 fields: Using a constructor or setter methods is simpler and more concise.
* You don’t need object customization or immutability: If the object is small, mutable, or built only in one place, a builder adds unnecessary complexity.

#### Pros and Cons of Builder Pattern
Understanding both the advantages and limitations of the Builder Pattern helps in deciding when to use it effectively.

**Pros**
* **Avoids constructor telescoping:** You no longer need to write multiple overloaded constructors for different configurations.
* **Ensures immutability:** The final object can be made immutable once built, which improves safety and thread-safety.
* **Clean, readable object creation:** The fluent API makes object construction expressive and easy to follow.
* **Great for complex configurations:** If your object has many optional parameters or conditional setup, the builder pattern keeps it organized.

**Cons**
* **Slightly tough to set up:** Initial setup requires writing a separate builder class, which adds to boilerplate.
* **Overkill for small classes:** If a class only has one or two fields, using a builder adds unnecessary complexity.
* **Separate builder class needed:** You need to maintain a second class or static inner class just to construct the main object, increasing maintenance.

#### Real World Products Using Builder Pattern
Understanding where the Builder Pattern is used in real products helps solidify its relevance. Let's look at two real-world examples:

##### 1. Lombok's @Builder Annotation (Java)
Lombok is a Java library that reduces boilerplate code using annotations. One of its popular features is the `@Builder` annotation, which automatically generates a builder class behind the scenes.

Instead of writing the builder logic manually, you just annotate your class:
```java
@Builder
public class User {
    private String name;
    private int age;
    private String address;
}
```

Now, you can build objects using a fluent API:
```java
User user = User.builder()
            .name("John")
            .age(30)
            .address("NYC")
            .build();
```

##### 2. Amazon Cart Configuration
Think about Amazon's shopping cart system. When you add an item to your cart, you're not just storing an item ID. You're building a complex object with fields like:
* Quantity
* Size or color (for apparel)
* Delivery option
* Gift wrap
* Save for later status
* Discounted price or offer tag

Each user may customize these options differently. Internally, such cart items are likely created using a Builder Pattern to allow step-by-step configuration while ensuring data consistency and immutability.

---
---
---
---
---

#### 4. Abstract Factory Pattern
The Abstract Factory Pattern is a creational design pattern that provides an interface for creating families of related or dependent objects without specifying their concrete classes.

**In simpler terms:**
You use it when you have multiple factories, each responsible for producing objects that are meant to work together.

**When Should You Use It?**
Use of the Abstract Factory Pattern is appropriate in the following scenarios:
* When multiple related objects must be created as part of a cohesive set (e.g., a payment gateway and its corresponding invoice generator).
* When the type of objects to be instantiated depends on a specific context, such as country, theme, or platform.
* When client code should remain independent of concrete product classes.
* When consistency across a family of related products must be maintained (e.g., a US payment gateway paired with a US-style invoice).

#### Real-life Example
Imagine we're building a Checkout Service for our platform TUF Plus:

##### Bad Design: Hardcoded Object Creation in CheckoutService
This version of the CheckoutService tightly couples business logic with object creation. It works for a simple scenario but quickly becomes problematic as the application scales or needs to support multiple payment gateways and invoice formats.

```java
// Interface representing any payment gateway
interface PaymentGateway {
    void processPayment(double amount);
}

// Concrete implementation: Razorpay
class RazorpayGateway implements PaymentGateway {
    public void processPayment(double amount) {
        System.out.println("Processing INR payment via Razorpay: " + amount);
    }
}

// Concrete implementation: PayU
class PayUGateway implements PaymentGateway {
    public void processPayment(double amount) {
        System.out.println("Processing INR payment via PayU: " + amount);
    }
}

// Interface representing invoice generation
interface Invoice {
    void generateInvoice();
}

// Concrete invoice implementation for India
class GSTInvoice implements Invoice {
    public void generateInvoice() {
        System.out.println("Generating GST Invoice for India.");
    }
}

// CheckoutService that directly handles object creation (bad practice)
class CheckoutService {
    private String gatewayType;

    // Constructor accepts a string to determine which gateway to use
    public CheckoutService(String gatewayType) {
        this.gatewayType = gatewayType;
    }

    // Checkout process hardcodes logic for gateway and invoice creation
    public void checkOut(double amount) {
        PaymentGateway paymentGateway;

        // Hardcoded decision logic
        if (gatewayType.equals("razorpay")) {
            paymentGateway = new RazorpayGateway();
        } else {
            paymentGateway = new PayUGateway();
        }

        // Process payment using selected gateway
        paymentGateway.processPayment(amount);

        // Always uses GSTInvoice, even though more types may exist later
        Invoice invoice = new GSTInvoice();
        invoice.generateInvoice();
    }
}

// Main method
class Main {
    public static void main(String[] args) {
        // Example: Using Razorpay
        CheckoutService razorpayService = new CheckoutService("razorpay");
        razorpayService.checkOut(1500.00);
    }
}
```

**Issues with this design:**
* **Tight Coupling:** The `CheckoutService` directly creates instances of `RazorpayGateway`, `PayUGateway`, and `GSTInvoice`, making it dependent on specific implementations.
* **Violation of the Open/Closed Principle:** Any addition of new payment gateways or invoice types will require modifying the `CheckoutService` class.
* **Lack of Extensibility:** Hardcoding limits the ability to support other countries or multiple combinations of payment methods and invoice formats.

Now, let's refactor this code using the Abstract Factory Pattern to improve its design and flexibility.

##### Improved Design: Abstract Factory Pattern for CheckoutService
This version follows the Abstract Factory Pattern to cleanly separate the creation of `PaymentGateway` and `Invoice` objects from the business logic of `CheckoutService`.

```java
// ========== Interfaces ==========
interface PaymentGateway {
    void processPayment(double amount);
}

interface Invoice {
    void generateInvoice();
}

// ========== India Implementations ==========
class RazorpayGateway implements PaymentGateway {
    public void processPayment(double amount) {
        System.out.println("Processing INR payment via Razorpay: " + amount);
    }
}

class PayUGateway implements PaymentGateway {
    public void processPayment(double amount) {
        System.out.println("Processing INR payment via PayU: " + amount);
    }
}

class GSTInvoice implements Invoice {
    public void generateInvoice() {
        System.out.println("Generating GST Invoice for India.");
    }
}

// ========== US Implementations ==========
class PayPalGateway implements PaymentGateway {
    public void processPayment(double amount) {
        System.out.println("Processing USD payment via PayPal: " + amount);
    }
}

class StripeGateway implements PaymentGateway {
    public void processPayment(double amount) {
        System.out.println("Processing USD payment via Stripe: " + amount);
    }
}

class USInvoice implements Invoice {
    public void generateInvoice() {
        System.out.println("Generating Invoice as per US norms.");
    }
}

// ========== Abstract Factory ==========
interface RegionFactory {
    PaymentGateway createPaymentGateway(String gatewayType);
    Invoice createInvoice();
}

// ========== Concrete Factories ==========
class IndiaFactory implements RegionFactory {
    public PaymentGateway createPaymentGateway(String gatewayType) {
        if (gatewayType.equalsIgnoreCase("razorpay")) {
            return new RazorpayGateway();
        } else if (gatewayType.equalsIgnoreCase("payu")) {
            return new PayUGateway();
        }
        throw new IllegalArgumentException("Unsupported gateway for India: " + gatewayType);
    }

    public Invoice createInvoice() {
        return new GSTInvoice();
    }
}

class USFactory implements RegionFactory {
    public PaymentGateway createPaymentGateway(String gatewayType) {
        if (gatewayType.equalsIgnoreCase("paypal")) {
            return new PayPalGateway();
        } else if (gatewayType.equalsIgnoreCase("stripe")) {
            return new StripeGateway();
        }
        throw new IllegalArgumentException("Unsupported gateway for US: " + gatewayType);
    }

    public Invoice createInvoice() {
        return new USInvoice();
    }
}

// ========== Checkout Service ==========
class CheckoutService {
    private PaymentGateway paymentGateway;
    private Invoice invoice;
    private String gatewayType;

    public CheckoutService(RegionFactory factory, String gatewayType) {
        this.gatewayType = gatewayType;
        this.paymentGateway = factory.createPaymentGateway(gatewayType);
        this.invoice = factory.createInvoice();
    }

    public void completeOrder(double amount) {
        paymentGateway.processPayment(amount);
        invoice.generateInvoice();
    }
}

// ========== Main Method ==========
class Main {
    public static void main(String[] args) {
        // Using Razorpay in India
        CheckoutService indiaCheckout = new CheckoutService(new IndiaFactory(), "razorpay");
        indiaCheckout.completeOrder(1999.0);

        System.out.println("---");

        // Using PayPal in US
        CheckoutService usCheckout = new CheckoutService(new USFactory(), "paypal");
        usCheckout.completeOrder(49.99);
    }
}
```

**How This Code Fixes the Original Issues**
* **Object creation logic was mixed with business logic:** Now moved to separate factory classes like `IndiaFactory` and `USFactory`.
* **Concrete classes like Razorpay and PayU were hardcoded in the service:** Replaced with abstractions (`PaymentGateway`, `Invoice`) and created via interfaces.
* **Adding a new gateway or invoice type required modifying CheckoutService:** Now, new gateways or invoices can be added by updating/adding a new factory - no changes required in the service class.
* **The code was difficult to maintain and scale across regions:** Now easy to maintain and scale by plugging in region-specific factories (e.g., `USFactory`, `IndiaFactory`, etc.).

**Key Benefits of this design**
* **Scalable:** Add new countries or payment systems by simply creating new factories.
* **Clean and Maintainable:** `CheckoutService` doesn’t care what kind of gateway or invoice it's using.
* **Easy to Test:** Each factory can be tested independently with its own unit tests.
* **Follows SOLID Principles:** Especially the Open/Closed Principle and Dependency Inversion Principle.

#### Pros and Cons

**Pros of the Abstract Factory Pattern**
* **Encapsulates Object Creation:** Centralizes and abstracts the instantiation logic for related objects, making client code cleaner and more focused on behavior.
* **Promotes Consistency Across Products:** Ensures that related objects (e.g., UI components or payment modules) are used together correctly and consistently.
* **Enhances Scalability:** Adding new product families or regions can be done by introducing new factory classes, without modifying existing logic.
* **Supports Open/Closed Principle:** Code is open for extension (new factories/products) but closed for modification, improving long-term maintainability.
* **Improves Code Maintainability:** Reduces tight coupling between components and specific implementations, making it easier to modify, test, and debug individual parts.
* **Provides a Layer of Abstraction:** Abstracts away platform-specific or environment-specific details from the client, enhancing code portability.

**Cons of the Abstract Factory Pattern**
* **Increased Complexity:** Adds additional layers (interfaces, factories, families of products) which might be overkill for small or simple projects.
* **Difficult to Extend Product Families:** Adding a new product to an existing family requires updating all factory implementations.
* **More Boilerplate Code:** Requires writing multiple classes and interfaces even for basic use cases.
* **Reduced Flexibility in Runtime Decisions:** Factories are often chosen at compile-time, making dynamic switching at runtime more complex.

#### Class Diagram
The class diagram below illustrates the structure of the Abstract Factory Pattern, showing how the various components interact with each other.

![Abstract Factory Class Diagram](IMAGES/abstract_factory_class_diagram.png)

---
---
---
---
---

#### 5. Prototype Pattern
The Prototype Pattern is a creational design pattern used to clone existing objects instead of constructing them from scratch. It enables efficient object creation, especially when the initialization process is complex or costly.

**Formal Definition:**
"Prototype pattern creates duplicate objects while keeping performance in mind. It provides a mechanism to copy the original object to a new one without making the code dependent on their classes."

**In simpler terms:**
Imagine you already have a perfectly set-up object - like a well-written email template or a configured game character. Instead of building a new one every time (which can be repetitive and expensive), you just copy the existing one and make small adjustments. This is what the Prototype Pattern does. It allows you to create new objects by copying existing ones, saving time and resources.

**Real-life Analogy (Photocopy Machine)**
Think of preparing ten offer letters. Instead of typing the same letter ten times, you write it once, photocopy it, and change just the name on each copy. This is how the Prototype Pattern works: start with a base object and produce modified copies with minimal changes.

#### Understanding
Let's understand better through a common challenge in software systems.

Consider an email notification system where each email instance requires extensive setup - loading templates, configurations, user settings, and formatting. Creating every email from scratch introduces redundancy and inefficiency.

Now imagine having a pre-configured prototype email, and simply cloning it for each user while modifying a few fields (like the name or content). That would save time, reduce errors, and simplify the logic.

#### Suitable Use Cases
Apply the Prototype Pattern in these situations:
* Object creation is resource-intensive or complex.
* You require many similar objects with slight variations.
* You want to avoid writing repetitive initialization logic.
* You need runtime object creation without tight class coupling.

#### Real-life Example
Imagine we're building an Email Template System at TUF:

##### Bad Code: Incomplete Use of Design Principles
```java
import java.util.*;

interface EmailTemplate {
    void setContent(String content);
    void send(String to);
}

// A concrete email class, hardcoded
class WelcomeEmail implements EmailTemplate {
    private String subject;
    private String content;

    public WelcomeEmail() {
        this.subject = "Welcome to TUF+";
        this.content = "Hi there! Thanks for joining us.";
    }

    @Override
    public void setContent(String content) {
        this.content = content;
    }

    @Override
    public void send(String to) {
        System.out.println("Sending to " + to + ": [" + subject + "] " + content);
    }
}

class Main {
    public static void main(String[] args) {
        // Create a welcome email
        WelcomeEmail email1 = new WelcomeEmail();
        email1.send("user1@example.com");

        // Suppose we want a similar email with slightly different content
        WelcomeEmail email2 = new WelcomeEmail();
        email2.setContent("Hi there! Welcome to TUF Premium.");
        email2.send("user2@example.com");

        // Yet another variation
        WelcomeEmail email3 = new WelcomeEmail();
        email3.setContent("Thanks for signing up. Let's get started!");
        email3.send("user3@example.com");
    }
}
```

**Issues in the Bad design**
* **Tight Coupling to Concrete Class:** The code uses the `WelcomeEmail` class directly.
* **No abstraction for cloning:** Client code is tightly bound to object creation logic (`new WelcomeEmail()` everywhere).
* **Repetitive Instantiation:** For every variation, a new instance is created using the constructor - even though most data remains the same. This leads to unnecessary duplication of code and logic.
* **Violates DRY Principle:** Repeated calls to `new WelcomeEmail()` and then `setContent()` for slight modifications break the Don't Repeat Yourself principle.
* **No Cloning or Copy Mechanism:** There is no concept of cloning or reusing a pre-defined template and just modifying small parts.

##### Good Code (Prototype Pattern Applied)
```java
import java.util.*;

// Defining the Prototype Interface
interface EmailTemplate extends Cloneable {
    EmailTemplate clone(); // Recommended to perform deep copy
    void setContent(String content);
    void send(String to);
}

// Concrete Class implementing clone logic
class WelcomeEmail implements EmailTemplate {
    private String subject;
    private String content;

    public WelcomeEmail() {
        this.subject = "Welcome to TUF+";
        this.content = "Hi there! Thanks for joining us.";
    }

    @Override
    public WelcomeEmail clone() {
        try {
            return (WelcomeEmail) super.clone();
        } catch (CloneNotSupportedException e) {
            throw new RuntimeException("Clone failed", e);
        }
    }

    @Override
    public void setContent(String content) {
        this.content = content;
    }

    @Override
    public void send(String to) {
        System.out.println("Sending to " + to + ": [" + subject + "] " + content);
    }
}

// Template Registry to store and provide clones
class EmailTemplateRegistry {
    private static final Map<String, EmailTemplate> templates = new HashMap<>();

    static {
        templates.put("welcome", new WelcomeEmail());
        // templates.put("discount", new DiscountEmail());
        // templates.put("feature-update", new FeatureUpdateEmail());
    }

    public static EmailTemplate getTemplate(String type) {
        return templates.get(type).clone(); // clone to avoid modifying original
    }
}

// Driver code
class Main {
    public static void main(String[] args) {
        EmailTemplate welcomeEmail1 = EmailTemplateRegistry.getTemplate("welcome");
        welcomeEmail1.setContent("Hi Alice, welcome to TUF Premium!");
        welcomeEmail1.send("alice@example.com");

        EmailTemplate welcomeEmail2 = EmailTemplateRegistry.getTemplate("welcome");
        welcomeEmail2.setContent("Hi Bob, thanks for joining!");
        welcomeEmail2.send("bob@example.com");

        // Reuse the base WelcomeEmail structure, just changing dynamic content
    }
}
```

**Benefits of Good Design**
* **Implements clone():** Allows object copying instead of recreation.
* **Introduces Registry:** Central location (`EmailTemplateRegistry`) holds template prototypes.
* **Decouples creation from usage:** Client code doesn't depend on how `WelcomeEmail` is constructed.
* **Improves performance:** Avoids complex re-initialization logic by cloning pre-configured templates.

#### Deep Cloning VS Shallow Cloning
There are two types of cloning in Java: **Shallow Cloning** and **Deep Cloning**.

In the context of the Prototype Pattern, **Deep Cloning is often preferred**. This means that when you clone an object, not only the object itself is copied, but also all the objects it references. This ensures that changes to the cloned object do not affect the original object or any of its referenced objects.

Deep cloning is considered safer as well than shallow cloning because it avoids unintended side effects and ensures each clone is truly independent - especially important when templates contain complex internal structures (like nested configuration objects, lists, etc.).

#### Pros of Prototype Pattern
* **Faster object creation:** No need to reinitialize objects from scratch.
* **Reduces subclassing:** No need to create multiple subclasses for variations.
* **Runtime object configuration:** Easy to modify a clone on the fly.
* **Ideal for UI/UX cloning:** Useful when duplicating component trees or screen states.

#### Cons of Prototype Pattern
* **Deep cloning can be hard:** Implementing a true deep copy takes extra effort.
* **Trouble with circular references:** Cloning objects that refer to each other can lead to complex issues.
* **Potential for bugs:** If cloning isn't handled carefully, it may introduce unexpected behavior.

#### Class Diagram
The class diagram below illustrates the structure of the Prototype Pattern, showing how the various components interact with each other. Only the specification perspective is shown here, as the implementation perspective is not relevant for this pattern.

![Prototype Pattern Class Diagram](IMAGES/prototype_class_diagram.png)

---
---
---
---
---

### Structural Design Patterns

#### Introduction
Structural design patterns are concerned with the composition of classes and objects. They focus on how to assemble classes and objects into larger structures while keeping these structures flexible and efficient. Adapter Pattern is one of the most important structural design patterns. Let's understand in depth.

#### 1. Adapter Pattern
The Adapter Pattern allows incompatible interfaces to work together by acting as a translator or wrapper around an existing class. It converts the interface of a class into another interface that a client expects.

It acts as a bridge between the Target interface (expected by the client) and the Adaptee (an existing class with a different interface). This structural wrapping enables integration and compatibility across diverse systems.

**Real-Life Analogy**
Imagine traveling from India to Europe. Your mobile charger doesn't fit into European sockets. Instead of buying a new charger, you use a plug adapter. The adapter allows your charger (with its Indian plug) to fit the European socket, enabling charging without modifying either the socket or the charger.

**Problem It Solves**
* Interface incompatibility between classes.
* Reusability of existing classes without modifying their source code.
* Enables systems to communicate that otherwise couldn't due to differing method signatures.

Similarly, the Adapter Pattern allows objects with incompatible interfaces to collaborate by introducing an adapter.

#### Real-Life Coding Example
Let's consider a scenario where we are implementing the Payment Gateway System. And we have two different payment methods: PayU and Razorpay. While the PayU gateway already conforms to this interface, Razorpay follows a different structure as shown in the code below.

##### Using Incompatible Interface (Without Adapter)
```java
import java.util.*;

// Target Interface: 
// Standard interface expected by the CheckoutService
interface PaymentGateway {
    void pay(String orderId, double amount);
}

// Concrete implementation of PaymentGateway for PayU
class PayUGateway implements PaymentGateway {
    @Override
    public void pay(String orderId, double amount) {
        System.out.println("Paid Rs. " + amount + " using PayU for order: " + orderId);
    }
}

// Adaptee: 
// An existing class with an incompatible interface
class RazorpayAPI {
    public void makePayment(String invoiceId, double amountInRupees) {
        System.out.println("Paid Rs. " + amountInRupees + " using Razorpay for invoice: " + invoiceId);
    }
}

// Client Class:
// Uses PaymentGateway interface to process payments
class CheckoutService {
    private PaymentGateway paymentGateway;

    // Constructor injection for dependency inversion
    public CheckoutService(PaymentGateway paymentGateway) {
        this.paymentGateway = paymentGateway;
    }

    // Business logic to perform checkout
    public void checkout(String orderId, double amount) {
        paymentGateway.pay(orderId, amount);
    }
}

class Main {
    public static void main(String[] args) {
        // Using PayU payment gateway to process payment
        CheckoutService checkoutService = 
            new CheckoutService(new PayUGateway());
            
        checkoutService.checkout("12", 1780);
    }
}
```

**Understanding the Issues**
* `CheckoutService` expects any payment provider to implement the `PaymentGateway` interface.
* `PayUGateway` fits this requirement and works correctly.
* `RazorpayAPI`, however, uses a different method (`makePayment`) and does not implement `PaymentGateway`.
* Due to this mismatch, `RazorpayAPI` cannot be used directly with `CheckoutService`.

This is a case of interface incompatibility, where similar functionalities can't work together because of structural differences. To solve this without modifying existing code, we use the Adapter Pattern to make `RazorpayAPI` compatible with the expected interface.

##### Using Adapter Pattern
```java
import java.util.*;

// Target Interface: 
// Standard interface expected by the CheckoutService
interface PaymentGateway {
    void pay(String orderId, double amount);
}

// Concrete implementation of PaymentGateway for PayU
class PayUGateway implements PaymentGateway {
    @Override
    public void pay(String orderId, double amount) {
        System.out.println("Paid Rs." + amount + " using PayU for order: " + orderId);
    }
}

// Adaptee: 
// An existing class with an incompatible interface
class RazorpayAPI {
    public void makePayment(String invoiceId, double amountInRupees) {
        System.out.println("Paid Rs." + amountInRupees + " using Razorpay for invoice: " + invoiceId);
    }
}

// Adapter Class:
// Allows RazorpayAPI to be used where PaymentGateway is expected
class RazorpayAdapter implements PaymentGateway {
    private RazorpayAPI razorpayAPI;
    
    public RazorpayAdapter() {
        this.razorpayAPI = new RazorpayAPI();
    }
    
    // Translates the pay() call to RazorpayAPI's makePayment() method
    @Override
    public void pay(String orderId, double amount) {
        razorpayAPI.makePayment(orderId, amount); 
    }
}

// Client Class:
// Uses PaymentGateway interface to process payments
class CheckoutService {
    private PaymentGateway paymentGateway;

    // Constructor injection for dependency inversion
    public CheckoutService(PaymentGateway paymentGateway) {
        this.paymentGateway = paymentGateway;
    }

    // Business logic to perform checkout
    public void checkout(String orderId, double amount) {
        paymentGateway.pay(orderId, amount);
    }
}

class Main {
    public static void main(String[] args) {
        // Using razorpay payment gateway adapter to process payment
        CheckoutService checkoutService = 
            new CheckoutService(new RazorpayAdapter());
            
        checkoutService.checkout("12", 1780);
    }
}
```

Here, we created an adapter class `RazorpayAdapter` that implements the `PaymentGateway` interface. The adapter internally uses the `RazorpayAPI` class and translates the method calls from the expected interface to the actual implementation.

This allows us to use `RazorpayAPI` seamlessly with the `CheckoutService` without modifying either class.

#### When to Use Adapter Pattern
The Adapter Pattern is ideal in scenarios where you're trying to integrate components that were not originally designed to work together. It proves especially useful when:
* You need to use an existing class, but its interface does not match the one your system expects.
* You want to reuse legacy code without modifying its internal structure.
* You're integrating third-party APIs or external services into your application.

In such cases, the Adapter Pattern serves as a bridge, allowing seamless compatibility without altering existing codebases.

#### Advantages and Disadvantages
Like any design pattern, the Adapter Pattern comes with its own set of pros and cons:

**Pros:**
* **Code Reusability:** Encourages the reuse of existing classes without changing their implementation.
* **Code Extensibility:** Makes systems more flexible and adaptable to change.
* **Minimal Changes to Client Code:** Enables integration without requiring modifications to existing client logic.
* **Simplifies Third-party Integration:** Makes it easier to incorporate external services and APIs.

**Cons:**
* **Adds an Extra Layer of Abstraction:** Can introduce unnecessary complexity if not used judiciously.
* **Overuse Can Obscure System Design:** Excessive use of adapters might make the architecture harder to understand and maintain.

#### Real Product Use Cases
The Adapter Pattern is not just a theoretical concept - it plays a crucial role in real-world software products and systems. Many enterprise-level applications rely on this pattern to integrate with third-party tools, legacy systems, and platform-specific APIs. Below are some common and impactful use cases:

##### 1. Payment Gateways
**Scenario:** Different payment providers (e.g., PayPal, Stripe, Razorpay, PayU) expose their own APIs with varying method names, parameters, and response formats.

**Adapter Use:** By implementing a common `PaymentGateway` interface and creating adapters for each provider, businesses can switch or support multiple gateways without rewriting business logic. This decouples the checkout flow from provider-specific implementations.

##### 2. Logging Frameworks
**Scenario:** Enterprise applications often need to support different logging libraries like Log4j, SLF4J, or custom logging solutions.

**Adapter Use:** An adapter can unify the logging interface so developers can write `log.debug(...)`, regardless of whether the underlying implementation is Log4j or `java.util.logging`. This makes it easier to switch or support multiple logging backends with minimal changes.

##### 3. Cloud Providers and SDKs
**Scenario:** Cloud platforms like AWS, Azure, and Google Cloud offer similar functionalities (storage, compute, database) but expose them through different SDKs and APIs.

**Adapter Use:** Using an adapter layer, developers can abstract cloud operations behind a common interface, enabling them to change providers (e.g., from AWS S3 to Google Cloud Storage) without impacting the rest of the application. This is particularly useful for hybrid-cloud or multi-cloud strategies.

#### Class Diagram
The class diagram below illustrates the Adapter Pattern. The `PaymentGateway` interface is the target interface, while `RazorpayAPI` is the adaptee. The `RazorpayAdapter` acts as a bridge, allowing the client to interact with the adaptee through the target interface.

![Adapter Pattern Class Diagram](IMAGES/adapter_class_diagram.png)

---
---
---
---
---

#### 2. Decorator Pattern
The Decorator Pattern is a structural design pattern that allows behavior to be added to individual objects, dynamically at runtime, without affecting the behavior of other objects from the same class.

It wraps an object inside another object that adds new behaviors or responsibilities at runtime, keeping the original object's interface intact.

**Real-Life Analogy**
Think of a coffee shop:
* You order a simple coffee.
* Then, you can add milk, add sugar, add whipped cream, etc.
* You don't need a whole new drink class for every combination.

Each addition wraps the original and adds something more.

**Problem It Solves**
It solves the problem of class explosion that occurs when you try to use inheritance to add combinations of behavior. For Example, imagine you have:
* A Pizza
* A CheesePizza
* A CheeseAndOlivePizza
* A CheeseAndOliveStuffedPizza

Every combination would need a new subclass as shown in the code below.

```java
import java.util.*;

// Each combination of pizza requires a new class
class PlainPizza {}
class CheesePizza extends PlainPizza {}
class OlivePizza extends PlainPizza {}
class StuffedPizza extends PlainPizza {}
class CheeseStuffedPizza extends CheesePizza {}
class CheeseOlivePizza extends CheesePizza {}
class CheeseOliveStuffedPizza extends CheeseOlivePizza {}

public class Main {
    public static void main(String[] args) {
        // Base pizza
        PlainPizza plainPizza = new PlainPizza();

        // Pizzas with individual toppings
        CheesePizza cheesePizza = new CheesePizza();
        OlivePizza olivePizza = new OlivePizza();
        StuffedPizza stuffedPizza = new StuffedPizza();

        // Combinations of toppings require separate classes
        CheeseStuffedPizza cheeseStuffedPizza = new CheeseStuffedPizza();
        CheeseOlivePizza cheeseOlivePizza = new CheeseOlivePizza();

        // Further combinations increase complexity exponentially
        CheeseOliveStuffedPizza cheeseOliveStuffedPizza = new CheeseOliveStuffedPizza();

    }
}
```

This quickly becomes unmanageable. Here, the Decorator Pattern comes into play. It lets you compose behaviors using wrappers instead of subclassing.

#### Solution to Pizza Problem
The Decorator Pattern solves the above discussed Pizza problem. It allows us to add responsibilities (like toppings) to objects dynamically without modifying their structure.

Instead of relying on a rigid class hierarchy, we compose objects using wrappers. This promotes flexibility, scalability, and cleaner code architecture.

##### Using Decorator Pattern
```java
import java.util.*;

// =========== Component Interface ============
interface Pizza {
    String getDescription();
    double getCost();
}

// ============= Concrete Components: Base pizza ==============
class PlainPizza implements Pizza {
    @Override
    public String getDescription() {
        return "Plain Pizza";
    }

    @Override
    public double getCost() {
        return 150.00;
    }
}

class MargheritaPizza implements Pizza {
    @Override
    public String getDescription() {
        return "Margherita Pizza";
    }

    @Override
    public double getCost() {
        return 200.00;
    }
}

// ======================== Abstract Decorator ===========================
// ====== Implements Pizza and holds a reference to a Pizza object =======
abstract class PizzaDecorator implements Pizza {
    protected Pizza pizza;

    public PizzaDecorator(Pizza pizza) {
        this.pizza = pizza;
    }
}

// ============ Concrete Decorator: Adds Extra Cheese ================
class ExtraCheese extends PizzaDecorator {
    public ExtraCheese(Pizza pizza) {
        super(pizza);
    }

    @Override
    public String getDescription() {
        return pizza.getDescription() + ", Extra Cheese";
    }

    @Override
    public double getCost() {
        return pizza.getCost() + 40.0;
    }
}

// ============ Concrete Decorator: Adds Olives ================
class Olives extends PizzaDecorator {
    public Olives(Pizza pizza) {
        super(pizza);
    }

    @Override
    public String getDescription() {
        return pizza.getDescription() + ", Olives";
    }

    @Override
    public double getCost() {
        return pizza.getCost() + 30.0;
    }
}

// =========== Concrete Decorator: Adds Stuffed Crust Cheese ==============
class StuffedCrust extends PizzaDecorator {
    public StuffedCrust(Pizza pizza) {
        super(pizza);
    }

    @Override
    public String getDescription() {
        return pizza.getDescription() + ", Stuffed Crust";
    }

    @Override
    public double getCost() {
        return pizza.getCost() + 50.0;
    }
}

// Driver code
public class Main {
    public static void main(String[] args) {
        // Start with a basic Margherita Pizza
        Pizza myPizza = new MargheritaPizza();

        // Add Extra Cheese
        myPizza = new ExtraCheese(myPizza);

        // Add Olives
        myPizza = new Olives(myPizza);

        // Add Stuffed Crust
        myPizza = new StuffedCrust(myPizza);

        // Final Description and Cost
        System.out.println("Pizza Description: " + myPizza.getDescription());
        System.out.println("Total Cost: ₹" + myPizza.getCost());
    }
}
```

**Understanding the Code**
The above code:
* Defines a `Pizza` interface that all pizzas (base and decorated) must implement.
* Implements two concrete `PlainPizza` and `MargheritaPizza` as the base pizzas.
* Defines an abstract `PizzaDecorator` which wraps a `Pizza` object and forwards method calls to it.
* Implements concrete decorators like `ExtraCheese`, `Olives`, and `StuffedCrust` which extend the functionality of the pizza object.

In the main method:
* A plain Margherita pizza is created.
* It is then wrapped successively with different decorators: `ExtraCheese`, `Olives`, and `StuffedCrust`.
* Each decorator adds to the pizza's description and cost.
* Finally, the composed pizza's description and total cost are printed.

**How Decorator Pattern Solves the Issue**
* **Avoids Class Explosion:** You no longer need a separate class for each combination of toppings. Just create new decorators as needed.
* **Flexible & Scalable:** Toppings can be added, removed, or reordered at runtime, offering high customization.
* **Follows Open/Closed Principle:** The base `Pizza` classes are open for extension (via decorators) but closed for modification.
* **Cleaner Code Architecture:** Composition is used instead of inheritance, resulting in loosely coupled components.
* **Promotes Reusability:** Each topping is a self-contained decorator and can be reused across different pizza compositions.

#### Key Takeaways
* **Abstract Classes and Constructors:** Abstract classes can have constructors, and these constructors are executed when a subclass is instantiated. This is important for initializing common properties or behavior shared across all subclasses.
* **Decorator as Layers:** Each decorator acts like a layer, similar to wrapping a gift box. Every decorator adds behavior on top of the previous one, allowing for flexible and dynamic composition of functionality.
* **Call Stack Analogy:** The Decorator Pattern functions like a call stack, where behavior is accumulated step by step as each decorator wraps the component. This stacked behavior is then unwrapped during method calls, preserving the order and layering.
* **Loose Coupling Between Classes:** The use of interfaces and composition in the Decorator Pattern ensures loose coupling between components. This makes the system more flexible, testable, and easier to extend without affecting existing code.

#### When Should You Use the Decorator Pattern?
The Decorator Pattern is particularly useful in scenarios where flexibility, modularity, and extensibility are key. Consider using it when:
* **You need to add responsibilities to objects dynamically:** Instead of hardcoding behaviors into a class, decorators allow you to attach additional functionality at runtime, offering great flexibility.
* **You want to avoid an explosion of subclasses:** For every possible combination of features, creating separate subclasses leads to unmanageable and bloated class hierarchies. Decorators eliminate this by composing behaviors.
* **You want to follow the Open/Closed Principle (OCP):** The pattern supports the OCP by allowing classes to be open for extension but closed for modification. You enhance behavior without altering existing code.
* **You want reusable and composable behaviors:** Decorators can be reused across different components and can be composed in various combinations to achieve desired functionality.
* **You need layered, step-by-step enhancements:** Decorators can be applied one after another, layering features gradually in a controlled and traceable way—much like wrapping layers around an object.

#### Advantages
A few advantages of using the Decorator Pattern are:
* **Adheres to the Open/Closed Principle (OCP):** Enhancements can be made without modifying existing code, supporting scalability and maintainability.
* **Runtime Flexibility to Compose Features:** Behaviors can be added or removed dynamically, allowing for highly customizable solutions.
* **Avoids Subclass Explosion:** Instead of creating multiple subclasses for every feature combination, decorators provide a cleaner, more modular approach.
* **Promotes Single Responsibility for Each Add-on:** Each decorator focuses on a specific functionality, leading to better code organization and readability.

#### Disadvantages
A few trade-offs while using the Decorator Pattern are:
* **Can Result in Many Small Classes:** Each feature typically requires its own decorator class, which can clutter the codebase.
* **Stack Trace Debugging is Difficult:** Debugging layered decorators can be challenging, as stack traces may become complex and harder to trace.
* **Overhead of Multiple Wrapping Classes:** Composing many decorators can introduce runtime overhead and make the class structure harder to follow.
* **Developers Must Understand Decorator Flow:** Proper implementation requires developers to grasp the decorator chaining logic, which may introduce a learning curve.

#### Real-World Use Cases
The Decorator Pattern is widely used in real-life software products to enable dynamic behavior composition without bloating the class hierarchy. Below are practical examples where it plays a critical role:

##### 1. Food Delivery Applications (e.g., Swiggy, Zomato)
**Context:** Customers can customize food items with add-ons like extra cheese, sauces, toppings, or side dishes.

**Role of Decorator Pattern:**
* Each add-on modifies the base food item's description and price dynamically.
* Instead of creating subclasses for every combination (e.g., `PizzaWithCheeseAndOlives`), decorators like `CheeseDecorator`, `OliveDecorator`, etc., can be stacked over a base `Pizza`.
* This allows the system to stay open for extension (new add-ons) but closed for modification.

##### 2. Google Docs or Word Processors
**Context:** Users can apply text formatting like bold, italic, or underline independently or in combination.

**Role of Decorator Pattern:**
* Each text style is implemented as a decorator that wraps the plain text object.
* Allows flexible layering of styles, e.g., `UnderlineDecorator(BoldDecorator(ItalicDecorator(Text)))`.
* Avoids subclassing for all combinations like `BoldItalicUnderlineText`, keeping the design clean and extensible.

#### Class Diagram
The class diagram for the Decorator Pattern illustrates the relationship between the component interface, concrete components, and decorators. It shows how decorators extend the functionality of components without modifying their structure.

![Decorator Pattern Class Diagram](IMAGES/decorator.png)

---
---
---
---
---

#### 3. Facade Pattern
The Facade Pattern is a structural design pattern that provides a simplified, unified interface to a complex subsystem or group of classes.

It acts as a single entry point for clients to interact with the system, hiding the underlying complexity and making the system easier to use.

**Real-Life Analogy**
Think of Manual vs. Automatic Car:
* **Complex Subsystem (Manual Car):** Driving a manual car requires intricate knowledge of multiple components (clutch, gear shifter, accelerator) and their precise coordination to shift gears and drive. It's complex and requires the driver to manage many interactions.
* **Facade (Automatic Car):** An automatic car acts as a facade. It provides a simplified interface (e.g., "Drive," "Reverse," "Park") to the complex underlying mechanics of gear shifting. The driver (client) no longer needs to manually coordinate the clutch and gears; the automatic transmission handles these complexities internally, making driving much easier.

In short, the manual car exposes the complexity, while the automatic car (the facade) simplifies it for the user.

**Problem It Solves**
It solves the problem of dealing with complex subsystems by hiding the complexities behind a single, unified interface. For example, imagine a movie ticket booking system with:
* PaymentService
* SeatReservationService
* NotificationService
* LoyaltyPointsService
* TicketService

Instead of making the client interact with all of these directly, the Facade Pattern provides a single class like `MovieBookingFacade`, which internally coordinates all the services.

#### Real-Life Coding Example
Imagine you're developing a movie ticket booking application, like BookMyShow. Let's first take a look at a poorly structured approach to implementing the booking functionality.

##### The Bad Way (Without Using Facade pattern)
```java
// Service class responsible for handling payments
class PaymentService {
    public void makePayment(String accountId, double amount) {
        System.out.println("Payment of ₹" + amount + " successful for account " + accountId);
    }
}

// Service class responsible for reserving seats
class SeatReservationService {
    public void reserveSeat(String movieId, String seatNumber) {
        System.out.println("Seat " + seatNumber + " reserved for movie " + movieId);
    }
}

// Service class responsible for sending notifications
class NotificationService {
    public void sendBookingConfirmation(String userEmail) {
        System.out.println("Booking confirmation sent to " + userEmail);
    }
}

// Service class for managing loyalty/reward points
class LoyaltyPointsService {
    public void addPoints(String accountId, int points) {
        System.out.println(points + " loyalty points added to account " + accountId);
    }
}

// Service class for generating movie tickets
class TicketService {
    public void generateTicket(String movieId, String seatNumber) {
        System.out.println("Ticket generated for movie " + movieId + ", Seat: " + seatNumber);
    }
}

// Client Code
class Main {
    public static void main(String[] args) {
        // Booking a movie ticket manually (without a facade)

        // Step 1: Make payment
        PaymentService paymentService = new PaymentService();
        paymentService.makePayment("user123", 500);

        // Step 2: Reserve seat
        SeatReservationService seatReservationService = new SeatReservationService();
        seatReservationService.reserveSeat("movie456", "A10");

        // Step 3: Send booking confirmation via email
        NotificationService notificationService = new NotificationService();
        notificationService.sendBookingConfirmation("user@example.com");

        // Step 4: Add loyalty points to user's account
        LoyaltyPointsService loyaltyPointsService = new LoyaltyPointsService();
        loyaltyPointsService.addPoints("user123", 50);

        // Step 5: Generate the ticket
        TicketService ticketService = new TicketService();
        ticketService.generateTicket("movie456", "A10");
    }
}
```

While this code works, it's tightly coupled. The `Main` class (or client code) is manually calling each subsystem service in the correct order and with the correct parameters.

This leads to:
* High complexity for the client
* Duplicate code if you have to do this in multiple places
* Violation of the Single Responsibility Principle (the Main class knows too much)

This sets the stage for the Facade Pattern, which will encapsulate all these steps in one high-level method like `bookTicket()` and make the client code clean and readable.

##### Using Facade Pattern
```java
// Service class responsible for handling payments
class PaymentService {
    public void makePayment(String accountId, double amount) {
        System.out.println("Payment of ₹" + amount + " successful for account " + accountId);
    }
}

// Service class responsible for reserving seats
class SeatReservationService {
    public void reserveSeat(String movieId, String seatNumber) {
        System.out.println("Seat " + seatNumber + " reserved for movie " + movieId);
    }
}

// Service class responsible for sending notifications
class NotificationService {
    public void sendBookingConfirmation(String userEmail) {
        System.out.println("Booking confirmation sent to " + userEmail);
    }
}

// Service class for managing loyalty/reward points
class LoyaltyPointsService {
    public void addPoints(String accountId, int points) {
        System.out.println(points + " loyalty points added to account " + accountId);
    }
}

// Service class for generating movie tickets
class TicketService {
    public void generateTicket(String movieId, String seatNumber) {
        System.out.println("Ticket generated for movie " + movieId + ", Seat: " + seatNumber);
    }
}


// ========== The MovieBookingFacade class  ==============
class MovieBookingFacade {
    private PaymentService paymentService;
    private SeatReservationService seatReservationService;
    private NotificationService notificationService;
    private LoyaltyPointsService loyaltyPointsService;
    private TicketService ticketService;

    // Constructor to initialize all the subsystem services.
    public MovieBookingFacade() {
        this.paymentService = new PaymentService();
        this.seatReservationService = new SeatReservationService();
        this.notificationService = new NotificationService();
        this.loyaltyPointsService = new LoyaltyPointsService();
        this.ticketService = new TicketService();
    }

    // Method providing a simplified interface for booking a movie ticket
    public void bookMovieTicket(String accountId, String movieId, String seatNumber, String userEmail, double amount) {
        paymentService.makePayment(accountId, amount);
        seatReservationService.reserveSeat(movieId, seatNumber);
        ticketService.generateTicket(movieId, seatNumber);
        loyaltyPointsService.addPoints(accountId, 50);
        notificationService.sendBookingConfirmation(userEmail);

        // Indicate successful completion of the entire booking process.
        System.out.println("Movie ticket booking completed successfully!");
    }
}

// Client Code
class Main {
    public static void main(String[] args) {
        // Booking a movie ticket manually (using facade)
        MovieBookingFacade movieBookingFacade = new MovieBookingFacade();
        movieBookingFacade.bookMovieTicket("user123", "movie456", "A10", "user@example.com", 500);
    }
}
```

**How Facade Pattern Solves the Issue**
By introducing `MovieBookingFacade`, we:
* Provide a simple, unified interface (`bookMovieTicket()`).
* Hide the complexity of internal service calls from the client.
* Reduce coupling, so changes in internal services don't affect the client.
* Centralize the workflow logic, making it easier to update and reuse.

#### When to use Facade Pattern?
You should use use Facade pattern when:
* **Subsystems are complex:** This means there are too many classes and too many dependencies within the system you are trying to simplify.
* **You want to provide a simpler API for the outer world:** The Facade acts as a simplified entry point, hiding the complexity from clients.
* **You want to reduce coupling between subsystems and client code:** By interacting with the facade, the client code becomes less dependent on the individual components of the subsystem.
* **You want to layer your architecture cleanly:** The Facade helps in organizing the system into distinct layers, making it more modular and understandable.

#### Advantages
A few advantages of using the Facade Pattern are:
* **Lightweight coupling:** It reduces the dependencies between the client and the subsystem.
* **Flexibility:** It allows the subsystem to evolve without impacting the client code.
* **Simplifies client design:** Clients interact with a single, simplified interface instead of multiple complex objects.
* **Promotes layered architecture:** It helps organize the system into distinct layers, improving maintainability and scalability.
* **Better testability:** Individual subsystem components can be tested independently, and the facade itself can be tested for its orchestration logic.

#### Disadvantages
A few disadvantages of using the Facade Pattern are:
* **Fragile coupling:** If the facade itself changes frequently, it can still lead to ripple effects on client code.
* **Hidden complexity:** While it simplifies the client's view, the underlying complexity of the subsystem still exists, just hidden. This can make debugging or understanding the full flow more challenging for developers working on the subsystem.
* **Runtime errors:** Errors originating from the complex subsystem might be harder to diagnose when only interacting through the facade.
* **Difficult to trace:** Debugging can be more challenging as the facade adds another layer of indirection.
* **Violation of SRP (Single Responsibility Principle):** A facade might take on too many responsibilities if it orchestrates a very large and diverse set of operations, potentially becoming a "god object."

#### Class Diagram
![Facade Pattern Class Diagram](IMAGES/facade.png)

---
---
---
---
---

#### 4. Composite Pattern
The Composite Pattern is a structural design pattern that allows you to compose objects into tree structures to represent part-whole hierarchies. It lets clients treat individual objects and compositions of objects uniformly.

**Problem It Solves**
The Composite Pattern solves the problem of treating individual objects and groups of objects in the same way. The main problem arises when:
* You want to work with a hierarchy of objects.
* You want the client code to be agnostic to whether it's dealing with a single object or a collection of them.

#### Understanding the Problem
Consider you are building the checkout service of an e-commerce application and you take the following approach as shown in the code below.

##### Code (Without Composite Pattern)
```java
import java.util.*;

// Represents a single product
class Product {
    private String name;
    private double price;
    
    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public double getPrice() {
        return price;
    }

    public void display(String indent) {
        System.out.println(indent + "Product: " + name + " - ₹" + price);
    }
}

// Represents a bundle of products
class ProductBundle {
    private String bundleName;
    private List<Product> products = new ArrayList<>();
    
    public ProductBundle(String bundleName) {
        this.bundleName = bundleName;
    }

    public void addProduct(Product product) {
        products.add(product);
    }

    public double getPrice() {
        double total = 0;
        for (Product product : products) {
            total += product.getPrice();
        }
        return total;
    }

    public void display(String indent) {
        System.out.println(indent + "Bundle: " + bundleName);
        for (Product product : products) {
            product.display(indent + "  ");
        }
    }
}

// Main logic
class Main {
    public static void main(String[] args) {
        // Individual Items
        Product book = new Product("Book", 500);
        Product headphones = new Product("Headphones", 1500);
        Product charger = new Product("Charger", 800);
        Product pen = new Product("Pen", 20);
        Product notebook = new Product("Notebook", 60);
        
        // Bundle: Iphone Combo
        ProductBundle iphoneCombo = new ProductBundle("iPhone Combo Pack");
        iphoneCombo.addProduct(headphones);
        iphoneCombo.addProduct(charger);
    
        // Bundle: School Kit
        ProductBundle schoolKit = new ProductBundle("School Kit");
        schoolKit.addProduct(pen);
        schoolKit.addProduct(notebook);
        
        // Add to cart logic
        List<Object> cart = new ArrayList<>();
        cart.add(book);
        cart.add(iphoneCombo);
        cart.add(schoolKit);
        
        // Display Cart    
        double total = 0;
        System.out.println("Cart Details:\n");

        for (Object item : cart) {
            if (item instanceof Product) {
                ((Product) item).display("  ");
                total += ((Product) item).getPrice();
            } else if (item instanceof ProductBundle) {
                ((ProductBundle) item).display("  ");
                total += ((ProductBundle) item).getPrice();
            }
        }

        System.out.println("\nTotal Price: ₹" + total);
    }
}
```

**Working of Code**
* `Product` class represents a simple item with name and price.
* `ProductBundle` class represents a group of products bundled together.
* Both classes have methods to display and return their prices.
* In `main()`, individual products and bundles are created and added to the cart.
* The cart is a `List<Object>` that holds both products and bundles.
* During checkout, the code checks each item's type using `instanceof`.
* Based on the type, it casts the object and calls its respective methods.
* Finally, it displays all items and calculates the total price.

**Problem in above code**
In the above example, the code lacks the structure to treat individual and group items uniformly, i.e., In the current implementation, individual products (`Product`) and product bundles (`ProductBundle`) are completely separate types with no shared interface or superclass. This means we cannot write code that treats both uniformly and the logic always has to check which type we're working with.

Other than these, there are some other problems as well:
* `instanceof` is used repeatedly, breaking polymorphism.
* Cart uses `List<Object>`, which is unsafe and violates abstraction.
* `ProductBundle` cannot contain another `ProductBundle` (no recursive structure).
* Display and price logic are duplicated instead of unified.

#### Refactored Code Using Composite Pattern
Let's refactor the code using the Composite Pattern. The idea is to create a common interface `CartItem` for both `Product` and `ProductBundle`, allowing us to treat them uniformly.

```java
import java.util.*;

// Interface for items that can be added to the cart
interface CartItem {
    double getPrice();
    void display(String indent);
}

// Product class implementing CartItem
class Product implements CartItem {
    private String name;
    private double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    @Override
    public double getPrice() {
        return price;
    }

    @Override
    public void display(String indent) {
        System.out.println(indent + "Product: " + name + " - ₹" + price);
    }
}

// ProductBundle class implementing CartItem
class ProductBundle implements CartItem {
    private String bundleName;
    private List<CartItem> items = new ArrayList<>();

    public ProductBundle(String bundleName) {
        this.bundleName = bundleName;
    }

    public void addItem(CartItem item) {
        items.add(item);
    }

    @Override
    public double getPrice() {
        double total = 0;
        for (CartItem item : items) {
            total += item.getPrice();
        }
        return total;
    }

    @Override
    public void display(String indent) {
        System.out.println(indent + "Bundle: " + bundleName);
        for (CartItem item : items) {
            item.display(indent + "  ");
        }
    }
}

// Main class
class Main {
    public static void main(String[] args) {
        // Individual Products
        CartItem book = new Product("Atomic Habits", 499);
        CartItem phone = new Product("iPhone 15", 79999);
        CartItem earbuds = new Product("AirPods", 15999);
        CartItem charger = new Product("20W Charger", 1999);

        // Combo Deal
        ProductBundle iphoneCombo = new ProductBundle("iPhone Essentials Combo");
        iphoneCombo.addItem(phone);
        iphoneCombo.addItem(earbuds);
        iphoneCombo.addItem(charger);

        // Back to School Kit
        ProductBundle schoolKit = new ProductBundle("Back to School Kit");
        schoolKit.addItem(new Product("Notebook Pack", 249));
        schoolKit.addItem(new Product("Pen Set", 99));
        schoolKit.addItem(new Product("Highlighter", 149));

        // Add everything to cart
        List<CartItem> cart = new ArrayList<>();
        cart.add(book);
        cart.add(iphoneCombo);
        cart.add(schoolKit);

        // Display cart
        System.out.println("Your Amazon Cart:");
        double total = 0;
        for (CartItem item : cart) {
            item.display("  ");
            total += item.getPrice();
        }

        System.out.println("\nTotal: ₹" + total);
    }
}
```

**Working of Refactored Code**
* `CartItem` interface defines the common methods for both products and bundles.
* `Product` and `ProductBundle` classes implement the `CartItem` interface.
* The cart now holds a list of `CartItem`, allowing us to treat both products and bundles uniformly.
* The display and price calculation logic is simplified, as we no longer need to check types.

#### Understanding Leaf and Composite in the Composite Pattern
In the Composite Design Pattern, we categorize components into two main roles:

* **Leaf (Individual Object):** A Leaf is a simple, atomic object in the structure. It does not contain any child components. In our example:
  * `Product` is a Leaf.
  * It represents individual purchasable items like books, phones, pens, etc.
  * Implements `CartItem` and provides its own `getPrice()` and `display()` logic.
* **Composite (Container of Components):** A Composite is a complex object that can hold multiple `CartItem` objects, including both Leaf and other Composite objects. In our example:
  * `ProductBundle` is a Composite.
  * It can contain Products (leaves) and even other ProductBundles (nested composites).
  * Implements `CartItem` and delegates actions (`getPrice()` and `display()`) to its children.

**How it Solves the Issues**
* **Uniform Treatment via Shared Interface (`CartItem`):** Now, both `Product` and `ProductBundle` implement `CartItem`, so the cart can contain any of them without special handling. This eliminates the need for type checking (`instanceof`).
* **Enables Polymorphism:** All operations like `getPrice()` and `display()` are defined in the `CartItem` interface, so they can be called uniformly on both products and bundles. This simplifies logic and improves code extensibility.
* **Recursive Composition Made Easy:** Bundles can now include other bundles or products seamlessly. This supports deeply nested combos or kits which is a common real-world scenario.
* **No Code Duplication:** The cart-handling logic like computing total and displaying items is written once and works for any `CartItem`. This promotes cleaner, DRY (Don't Repeat Yourself) code.

#### When to Use Composite Pattern
The Composite Pattern is particularly useful when:
* **You have a hierarchical structure:** Use the composite pattern when your objects form a tree-like structure (e.g., folders inside folders, or products inside bundles).
* **You want to treat individual and groups in the same way:** When operations on single items and collections of items should be uniform (e.g., calculating total price, displaying structure).
* **You want to avoid client-side logic to differentiate leaf and composite:** Let polymorphism handle the differences between simple and composite objects, keeping client code clean and maintainable.

#### Advantages and Disadvantages
**Pros:**
* **Uniformity:** Treats individual and composite objects in the same way.
* **Extensible:** Easy to add new item types or structures.
* **Cleaner client code:** Reduces complexity for the user of the structure.
* **Supports OCP (Open/Closed Principle):** Add new components without modifying existing code.

**Cons:**
* **Violates SRP on scale:** Components manage both hierarchy and business logic.
* **Overkill for flat and simple structures:** Adds unnecessary complexity.
* **Can hide important distinctions:** In regulated or sensitive systems, uniform treatment might blur critical differences between types.

#### Class Diagram
The class diagram below illustrates the structure of the Composite Pattern.

![Composite Pattern Class Diagram](IMAGES/composite.png)

---
---
---
---
---

#### 5. Proxy Pattern
The Proxy Pattern is a structural design pattern that provides a surrogate or placeholder for another object to control access to it.

A proxy acts as an intermediary that implements the same interface as the original object, allowing it to intercept and manage requests to the real object.

**Real-Life Analogy**
Think of a personal assistant:
* A busy CEO may not respond to everyone directly.
* Instead, their assistant takes calls, filters emails, manages the calendar, and only involves the CEO when necessary.
* The assistant controls access to the CEO while still providing essential services to others.

Here, the assistant is the proxy that controls and optimizes access to the real resource (the CEO).

**Problem It Solves**
It solves the problem of uncontrolled or expensive access to an object. For example, consider a scenario where:
* You have a heavy object like a video player that consumes a lot of resources on initialization.
* You want to delay its creation until it's actually needed (lazy loading).
* Or maybe the object resides on a remote server and you want to add a layer to manage the network communication.

The Proxy Pattern allows you to control access, defer initialization, add logging, caching, or security without modifying the original object.

#### Real-Life Coding Example
Imagine you're building a feature like a video streaming app (think YouTube or Netflix) where users can download videos. Now, consider this: multiple users might try to download the same video multiple times - or even the same user may repeat the request. In such scenarios, if we go ahead and download the video from the internet every single time, it leads to unnecessary network calls, longer wait times, and wasted bandwidth.

Let’s consider a scenario where we want to download a video multiple times, perhaps from different places in the code or by different users. A poor design would look like this:

##### Bad Design: Without Proxy
```java
// ========== RealVideoDownloader Class ==========
class RealVideoDownloader {
    public String downloadVideo(String videoUrl) {
        // caching logic missing
        // filtering logic missing
        // access logic missing
        System.out.println("Downloading video from URL: " + videoUrl);
        String content = "Video content from " + videoUrl;
        System.out.println("Downloaded Content: " + content);
        return content;
    }
}

// ================ Main Class ===================
class Main {
    public static void main(String[] args) {
        System.out.println("User 1 tries to download the video.");
        RealVideoDownloader downloader1 = new RealVideoDownloader();
        downloader1.downloadVideo("https://video.com/proxy-pattern");

        System.out.println();

        System.out.println("User 2 tries to download the same video again.");
        RealVideoDownloader downloader2 = new RealVideoDownloader();
        downloader2.downloadVideo("https://video.com/proxy-pattern");
    }
}
```

**Understanding the Issues**
* There's no caching, so the same video is downloaded again and again even if it’s already available.
* There's no access control or content filtering - any video URL is downloaded without restrictions.
* The client directly depends on the `RealVideoDownloader`, meaning there’s no way to intercept, log, or modify the download behavior without changing core logic.
* It results in multiple object creations and redundant resource usage.

The previous implementation made direct use of the `RealVideoDownloader` class for every download request, even if the same video was requested multiple times. This meant the system would re-download and reprocess the same video repeatedly, leading to unnecessary network usage and redundant computation.

To solve this, we use the Proxy Design Pattern - a structural pattern that provides a placeholder or surrogate for another object to control access to it.

##### Good Design: Using Proxy Pattern
```java
import java.util.*;

interface VideoDownloader {
    String downloadVideo(String videoURL);
}

// ========== RealVideoDownloader Class ==========
class RealVideoDownloader implements VideoDownloader {

    @Override
    public String downloadVideo(String videoUrl) {
        System.out.println("Downloading video from URL: " + videoUrl);
        return "Video content from " + videoUrl;
    }
}

// =============== Proxy With Cache ====================
class CachedVideoDownloader implements VideoDownloader {

    private RealVideoDownloader realDownloader;
    private Map<String, String> cache;

    public CachedVideoDownloader() {
        this.realDownloader = new RealVideoDownloader();
        this.cache = new HashMap<>();
    }

    @Override
    public String downloadVideo(String videoUrl) {
        if (cache.containsKey(videoUrl)) {
            System.out.println("Returning cached video for: " + videoUrl);
            return cache.get(videoUrl);
        }

        System.out.println("Cache miss. Downloading...");
        String video = realDownloader.downloadVideo(videoUrl);
        cache.put(videoUrl, video);
        return video;
    }
}


// ================ Main Class ===================
class Main {
    public static void main(String[] args) {
        VideoDownloader cacheVideoDownloader = new CachedVideoDownloader();
        System.out.println("User 1 tries to download the video.");
        cacheVideoDownloader.downloadVideo("https://video.com/proxy-pattern");

        System.out.println();

        System.out.println("User 2 tries to download the same video again.");
        cacheVideoDownloader.downloadVideo("https://video.com/proxy-pattern");
    }
}
```

**How Proxy Pattern Solves the Issue**
In this example, the proxy (`CachedVideoDownloader` Class) was used that implements a caching logic that checks if a video has already been downloaded. If so, it simply returns the cached result, saving time and resources.

This way, the real object is accessed only when absolutely necessary, while repeated requests are served efficiently through the proxy - resulting in faster response times and optimized performance.

#### When to Use Proxy Pattern?
The proxy pattern can be used when:
* When object creation is expensive, and you want to delay or control its instantiation.
* When you need to control access to sensitive operations or enforce permission checks.
* When interacting with remote objects that are costly or slow to fetch.
* When lazy loading is needed to optimize system performance and resource usage.

#### Types of Proxy
At a high level, proxies can be categorized into several types based on the specific purpose they serve:
* **Virtual Proxy**
  * **Purpose:** Controls access to a resource that is expensive to create.
  * **Use Case:** Commonly used for lazy initialization - where the real object is created only when absolutely necessary.
  * **Example:** A video downloader app that only fetches and loads the video data when the user hits “Play”.
* **Protection Proxy**
  * **Purpose:** Controls access to an object based on user permissions or roles.
  * **Use Case:** Useful in systems with multi-level access control, such as admin vs. regular users.
  * **Example:** In a document editor, only editors can modify content while viewers can only read.
* **Remote Proxy**
  * **Purpose:** Controls access to an object located on a remote server or in a different address space.
  * **Use Case:** Enables local code to access remote services as if they were local.
  * **Example:** A Java RMI object or API wrapper that abstracts out network communication.
* **Smart Proxy**
  * **Purpose:** Adds additional behavior when accessing the real object.
  * **Use Case:** Often used for logging, access counting, or reference counting.
  * **Example:** Automatically logging every time a file is accessed or updated.

#### Advantages
A few advantages of using the Proxy Pattern are:
* **Performance Optimization:** By introducing features like caching or lazy initialization, proxies can significantly reduce resource consumption and improve application performance.
* **Access Control:** Proxies act as a gatekeeper, controlling access to sensitive or expensive resources, and ensuring that only authorized users can access them.
* **Lazy Initialization:** Proxies delay the creation of costly resources until they are actually needed, optimizing resource usage and startup times.
* **Added Functionality:** Without modifying the original object, proxies can add additional behavior such as logging, security checks, or usage tracking.

#### Disadvantages
A few disadvantages of using the Proxy Pattern are:
* **Increased Complexity:** Introducing a proxy layer adds more components to the system, which can make the overall design harder to understand and maintain.
* **Potential Delays:** The proxy may introduce delays in accessing the actual object, especially when additional logic like permission checks or data fetching is involved.
* **Maintenance Overhead:** With extra layers and duplicated interfaces, maintaining proxies alongside real objects can increase the development and debugging effort.

#### Class Diagram
![Proxy Pattern Class Diagram](IMAGES/proxy.png)

---
---
---
---
---

#### 6. Bridge Pattern
The Bridge Pattern is a structural design pattern that is used to decouple an abstraction from its implementation so that the two can vary independently.

**Problem It Solves**
When you have multiple dimensions of variability, such as different types of features (abstractions) and multiple implementations of those features, you might end up with a combinatorial explosion of subclasses if you try to use inheritance to handle all combinations. Thus bridge pattern:
* Avoids tight coupling between abstraction and implementation.
* Eliminates code duplication that would occur if every combination of abstraction and implementation had its own class.
* Promotes composition over inheritance, allowing more flexible code evolution.

**Real-Life Analogy**
Think of a TV remote and a TV:
* The remote is the abstraction (interface the user interacts with).
* The TV is the implementation (actual functionality).

You can have different types of remotes (basic, advanced) and different brands of TVs (Samsung, Sony). Bridge Pattern allows any remote to work with any TV without creating a separate class for each combination.

#### Real-Life Coding Example
Assume we are building a video player that aims to model different video players (like Web, Mobile, Smart TV) each with different quality types (HD, Ultra HD, 4K).

##### Using Tight Coupling Causing Class Explosion
```java
import java.util.*;

// ======= Interface for video quality =======
interface PlayQuality {
    void play(String title);
}

// Each class here represents a combination of platform and quality
class WebHDPlayer implements PlayQuality {
    public void play(String title) {
        // Web player plays in HD
        System.out.println("Web Player: Playing " + title + " in HD");
    }
}

class MobileHDPlayer implements PlayQuality {
    public void play(String title) {
        // Mobile player plays in HD
        System.out.println("Mobile Player: Playing " + title + " in HD");
    }
}

class SmartTVUltraHDPlayer implements PlayQuality {
    public void play(String title) {
        // Smart TV plays in Ultra HD
        System.out.println("Smart TV: Playing " + title + " in ultra HD");
    }
}

class Web4KPlayer implements PlayQuality {
    public void play(String title) {
        // Web player plays in 4K
        System.out.println("Web Player: Playing " + title + " in 4K");
    }
}

// ============ Main class ================
class Main {
    public static void main(String[] args) {
        PlayQuality player = new WebHDPlayer();
        player.play("Interstellar");
    }
}
```

**Understanding the Issue**
In the given design, platform types (like Web, Mobile, Smart TV) are tightly coupled with video quality types (like HD, Ultra HD, 4K). This results in a rigid system where every combination requires a separate class - for example, `WebHDPlayer`, `MobileHDPlayer`, `SmartTVUltraHDPlayer`, and so on.

As new platforms or quality types are introduced, the number of classes grows rapidly. Adding just one new platform or one new quality level leads to multiple new classes. If you have 5 platforms and 5 quality types, you end up with 25 distinct classes - most of which share very similar code.

Such tightly coupled designs are hard to test, extend, and manage over time. This is where the Bridge Pattern proves valuable - by decoupling the abstraction (platform) from its implementation (quality), it allows both to evolve independently, eliminating unnecessary class combinations.

##### Using Bridge Pattern
```java
import java.util.*;

// ======== Implementor Interface =========
interface VideoQuality {
    void load(String title);
}

// ============ Concrete Implementors ==============
class SDQuality implements VideoQuality {
    public void load(String title) {
        System.out.println("Streaming " + title + " in SD Quality");
    }
}

class HDQuality implements VideoQuality {
    public void load(String title) {
        System.out.println("Streaming " + title + " in HD Quality");
    }
}

class UltraHDQuality implements VideoQuality {
    public void load(String title) {
        System.out.println("Streaming " + title + " in 4K Ultra HD Quality");
    }
}

// ========== Abstraction ==========
abstract class VideoPlayer {
    protected VideoQuality quality;

    public VideoPlayer(VideoQuality quality) {
        this.quality = quality;
    }

    public abstract void play(String title);
}

// =========== Refined Abstractions ==============
class WebPlayer extends VideoPlayer {
    public WebPlayer(VideoQuality quality) {
        super(quality);
    }

    public void play(String title) {
        System.out.println("Web Platform:");
        quality.load(title);
    }
}

class MobilePlayer extends VideoPlayer {
    public MobilePlayer(VideoQuality quality) {
        super(quality);
    }

    public void play(String title) {
        System.out.println("Mobile Platform:");
        quality.load(title);
    }
}

// Client Code
class Main {
    public static void main(String[] args) {
        // Playing on Web with HD Quality
        VideoPlayer player1 = new WebPlayer(new HDQuality());
        player1.play("Interstellar");

        // Playing on Mobile with Ultra HD Quality
        VideoPlayer player2 = new MobilePlayer(new UltraHDQuality());
        player2.play("Inception");
    }
}
```

**How Bridge Pattern Solves the Issue:**
* **Separation of Concerns:** `VideoPlayer` (abstraction) focuses on the platform-specific behavior, while `VideoQuality` (implementor) handles quality-specific streaming logic.
* **Flexible Combinations:** You can mix and match any platform with any quality at runtime without creating new classes.
* **Easier to Extend:** Adding a new platform or a new quality only requires one new class, not multiple combinations:
  * Add `SmartTVPlayer` → works with all existing qualities.
  * Add `FullHDQuality` → works with all existing players.
* **Cleaner Code Structure:** Each class has a single responsibility. This promotes maintainability, scalability, and adheres to the Open/Closed Principle.

#### When to use Bridge Pattern?
Bridge Pattern is particularly useful when:
* You have multiple dimensions of variation
* You want to decouple abstraction from implementation
* You anticipate frequent changes or additions
* You want to follow SOLID principles
* You want runtime flexibility

#### Advantages
A few advantages of using the Bridge Pattern are:
* **Decouples abstraction and implementation:** Changes in one side (abstraction or implementation) do not affect the other.
* **Avoids class explosion:** You don't need to create a separate class for every combination of abstraction and implementation.
* **Supports the Open/Closed Principle (OCP):** You can extend functionalities without modifying existing code.
* **Ideal for cross-platform development:** Useful when developing for multiple platforms that share similar features.
* **Improves maintainability and testing:** Easier to manage and test each part independently.

#### Disadvantages
A few disadvantages of using the Bridge Pattern are:
* **Increased complexity:** Might be overkill if your application is simple or has limited variations.
* **Can be confused with other patterns:** Especially with patterns like Strategy or Adapter, due to structural similarities.
* **Coordination needed between teams:** If abstraction and implementation are developed separately, good communication is essential.

#### Class Diagram
![Bridge Pattern Class Diagram](IMAGES/bridge.png)

---
---
---
---
---

#### 7. Flyweight Pattern
The Flyweight Pattern is a structural design pattern used to minimize memory usage by sharing as much data as possible with similar objects.

It separates the intrinsic (shared) state from the extrinsic (unique) state, so that shared parts of objects are stored only once and reused wherever needed.

**Real-Life Analogy**
Think of trees in a video game. In an open-world video game, you might see thousands of trees:
* All oak trees have the same texture, shape, and behavior (shared/intrinsic).
* But their location, size, or health status may differ (extrinsic).

Rather than loading the same tree model thousands of times, the game engine uses a single shared tree model and passes different parameters when rendering.

**Problem It Solves**
It solves the problem of high memory usage when a large number of similar objects are created. For example, imagine a system rendering:
* Thousands of tree objects in a forest
* Each with the same shape and texture but a different location

Instead of creating thousands of identical objects, the Flyweight Pattern lets you share the common parts (shape, texture) and store the unique parts (location) externally, dramatically reducing memory consumption.

**Core Concepts**
* **Intrinsic State:** The immutable, shared data stored inside the flyweight. It is independent of context.
* **Extrinsic State:** The context-specific data passed from the client and not stored in the flyweight.

#### Real-Life Coding Example
Imagine you're building a feature like Google Maps where you need to visually represent trees across the globe. Now, even though millions of trees are shown, most of them belong to only a few common types like “Oak”, “Pine”, or “Birch”. However, if we were to create a separate object for each individual tree — storing the same data repeatedly for tree type, color, and texture — it would lead to massive memory consumption.

Let’s consider a scenario where we want to create 1 million trees, all with the same name, color, and texture. A poor design would look like this:

##### Bad Design: Without Flyweight
```java
import java.util.*;

// ================ Tree Class =================
class Tree {
    // Attributes that keep on changing 
    private int x;
    private int y;
    
    // Attributes that remain constant
    private String name;
    private String color;
    private String texture;
    
    public Tree(int x, int y, String name, String color, String texture) {
        this.x = x;
        this.y = y;
        this.name = name;
        this.color = color;
        this.texture = texture;
    }
    
    public void draw() {
        System.out.println("Drawing tree at (" + x + ", " + y + ") with type " + name);
    }
}

// ================ Forest Class =================
class Forest {

    private List<Tree> trees = new ArrayList<>();

    public void plantTree(int x, int y, String name, String color, String texture) {
        Tree tree = new Tree(x, y, name, color, texture);
        trees.add(tree);
    }

    public void draw() {
        for (Tree tree : trees) {
            tree.draw();
        }
    }
}

// =============== Client Code ==================
class Main {
    public static void main(String[] args) {
        Forest forest = new Forest();
        
        // Planting 1 million trees
        for(int i = 0; i < 1000000; i++) {
            forest.plantTree(i, i, "Oak", "Green", "Rough");
        }
        
        System.out.println("Planted 1 million trees.");
    }
}
```

**Understanding the Issues**
Although the above codes works absolutely fine but there are a few problems associated with it:
* **Redundant memory usage:** Same tree data duplicated a million times.
* **Inefficient:** Slower rendering, higher GC overhead.

The previous implementation created a new `Tree` object for each of the 1 million trees, even when most of them had identical properties like name, color, and texture. This led to unnecessary duplication of memory for the shared attributes.

To solve this, we use the Flyweight Design Pattern — a structural pattern focused on minimizing memory usage by sharing as much data as possible between similar objects.

##### Good Design: Using Flyweight Pattern
```java
import java.util.*;

// ============= TreeType Class ================
class TreeType {
    // Properties that are common among all trees of this type
    private String name;
    private String color;
    private String texture;

    public TreeType(String name, String color, String texture) {
        this.name = name;
        this.color = color;
        this.texture = texture;
    }

    public void draw(int x, int y) {
        System.out.println("Drawing " + name + " tree at (" + x + ", " + y + ")");
    }
}


// ================ Tree Class =================
class Tree {
    // Attributes that keep on changing 
    private int x;
    private int y;
    
    // Attributes that remain constant
    private TreeType treeType;
    
    public Tree(int x, int y, TreeType treeType) {
        this.x = x;
        this.y = y;
        this.treeType = treeType;
    }
    
    public void draw() {
        treeType.draw(x, y);
    }
}


// ============ TreeFactory Class ==============
class TreeFactory {

    static Map<String, TreeType> treeTypeMap = new HashMap<>();

    public static TreeType getTreeType(String name, String color, String texture) {
        String key = name + " - " + color + " - " + texture;

        if (!treeTypeMap.containsKey(key)) {
            treeTypeMap.put(key, new TreeType(name, color, texture));
        }
        return treeTypeMap.get(key);
    }
}


// ================ Forest Class =================
class Forest {
    private List<Tree> trees = new ArrayList<>();

    public void plantTree(int x, int y, String name, String color, String texture) {
        Tree tree = new Tree(x, y, TreeFactory.getTreeType(name, color, texture));
        trees.add(tree);
    }

    public void draw() {
        for (Tree tree : trees) {
            tree.draw();
        }
    }
}


// =============== Client Code ==================
class Main {
    public static void main(String[] args) {
        Forest forest = new Forest();
        
        // Planting 1 million trees
        for(int i = 0; i < 1000000; i++) {
            forest.plantTree(i, i, "Oak", "Green", "Rough");
        }
        
        System.out.println("Planted 1 million trees.");
    }
}
```

**How Flyweight Pattern Solves the Issue**
Let’s break it down:
* **TreeType Class:** This acts as the flyweight object. It stores data common to all trees of a given type—like name, color, and texture. Instead of duplicating this data, we create only one instance per unique combination.
* **Tree Class:** This now only stores:
  * Intrinsic data: `x`, `y` (unique to each tree)
  * Reference to shared data: A `TreeType` instance
* **TreeFactory Class:** This is the central factory that ensures `TreeType` instances are reused:
  * **Memory Efficiency:** Even with 1 million trees, if they all share the same `TreeType` ("Oak", "Green", "Rough"), only one `TreeType` object is created and shared across all trees, reducing memory usage dramatically.

#### When to Use Flyweight Pattern?
The flyweight pattern can be used when:
* When you need to create a large number of similar objects.
* When memory and performance optimization is crucial.
* When the object's intrinsic properties could be shared independently of its extrinsic properties.

#### Advantages
A few advantages of using the Flyweight Pattern are:
* Greatly reduces memory usage when there are a lot of similar objects.
* Improves performance in resource-constrained environments.
* Enables faster object creation.

#### Disadvantages
A few disadvantages of using the Flyweight Pattern are:
* Adds complexity (especially around factory and object management).
* Harder to debug due to shared state.
* Can lead to tight coupling between flyweight and client code if not designed carefully.

#### Real-World Applications of Flyweight Pattern
The Flyweight pattern is widely used in large-scale applications where rendering or managing many similar objects efficiently is essential. Here are some real-world examples:

##### 1. Google Maps
When displaying millions of trees or similar visual landmarks, Google Maps avoids creating separate objects for each tree. Instead, it shares the same data (like tree type, color, texture) across all trees and only varies extrinsic properties like position — a classic use of the Flyweight pattern.

##### 2. Uber App
Uber renders many nearby cars on the map, but most of them are visually identical (same icon, color, etc.). Instead of creating a new object for each car from scratch, Uber reuses a common flyweight object and just changes the coordinates — reducing memory and improving performance.

##### 3. Web Browsers (Chrome, Firefox, etc.)
When rendering complex webpages with thousands of similar DOM elements (like repeated icons, buttons, text styles), modern browsers internally use the Flyweight pattern to optimize memory. For instance:
* A webpage might have hundreds of `<div>` or `<button>` elements styled identically.
* Instead of allocating separate memory for each element’s styling and behavior, browsers reuse the same shared style object (like CSS rules or rendering data) across all similar components.
* This allows browsers to load and display large webpages faster and with less RAM usage.

#### Class Diagram
![Flyweight Pattern Class Diagram](IMAGES/flyweight.png)

---
---
---
---
---

### Behavioral Design Patterns

