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
