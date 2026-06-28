# Low-Level Design (LLD) Notes

## 1. Introduction
**What is LLD?**
* **LLD = Low-Level Design**
* Focuses on how the code will be implemented.
* Converts High-Level Design (HLD) into actual classes, methods, and logic.
* Acts as a bridge between design and coding.

## 2. Easy Real-Life Example

🏠 **Building a House**
* **HLD:** House blueprint (Rooms, Size, Connections)
* **LLD:** Construction details (Switch locations, Plumbing, Materials, Wiring)

👉 **HLD** = *What to build*  
👉 **LLD** = *How to build it*

## 3. Definition
LLD is the detailed design of individual components of a system.

It defines:
* Classes
* Methods
* Data Structures
* Algorithms
* Internal Logic

...before writing the actual code.

## 4. Example
**Website Login System**

LLD decides:
* `login()`
* `signup()`
* `forgotPassword()`
* Validation
* Error handling
* Database calls
* Password encryption

## 5. Key Characteristics

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

## 6. Stakeholders
People involved in implementation:
* Senior Developers
* Software Engineers
* Technical Leads
* Engineering Managers

## 7. HLD vs LLD

| HLD | LLD |
| :--- | :--- |
| System overview | Detailed implementation |
| Architecture | Classes & Methods |
| Modules | Functions & Logic |
| Abstract | Detailed |
| System diagrams | Class diagrams |

## 8. Importance of LLD
* **Avoids Rework:** Finds design issues early, saves development time.
* **Improves Collaboration:** Common reference for developers, easier integration.
* **Better Scalability:** Modular components, easy to extend with new features.
* **Encourages Best Practices:** Clean Code, OOP Principles, Design Patterns, maintainable code.

## 9. Software Design Principles
Software design principles are guidelines that help software developers create systems that are easy to understand, maintain, and extend. These principles can be applied at both the high-level and low-level design stages. Here are three cornerstone key software design principles:

1. **DRY** (Don't Repeat Yourself)
2. **KISS** (Keep It Simple, Stupid)
3. **YAGNI** (You Aren't Gonna Need It)

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
