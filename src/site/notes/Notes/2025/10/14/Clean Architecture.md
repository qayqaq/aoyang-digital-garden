---
{"dg-publish":true,"permalink":"/notes/2025/10/14/clean-architecture/"}
---

- **The Dependency Rule**: The foundational principle is that source code dependencies must always point inwards, from outer layers to inner layers. The core business logic knows nothing about outer details like databases or UIs.
- **Independence**: The architecture is designed to be independent of frameworks, UI, databases, and any external agency. This makes the system portable and long-lasting.
- **Testability**: Business rules (Entities and Use Cases) can be tested in isolation without external dependencies, leading to fast, reliable, and comprehensive tests.
- **Concentric Layers**: The architecture is visualized as four concentric circles: Entities (core domain), Use Cases (application logic), Interface Adapters (controllers, gateways), and Frameworks & Drivers (UI, DB).

#SoftwareArchitecture #SystemDesign #CleanArchitecture #RobertCMartin #SOLID

[[Clean Architecture.canvas\|Clean Architecture.canvas]]

# Clean Architecture

## 1. Introduction: A Blueprint for Stable Systems

**Clean Architecture** is a software design philosophy, popularized by Robert C. Martin ("Uncle Bob"), that prioritizes the **separation of concerns** by organizing a system into concentric layers. Its primary goal is to create systems that are independent of frameworks, user interfaces, and databases, making them highly testable, maintainable, and adaptable to change over time.

This architectural style is not a new invention but rather a consolidation of ideas from earlier patterns like Hexagonal Architecture (Ports and Adapters) and Onion Architecture. The central tenet of all these approaches is the same: to place the core business logic and application rules at the center of the design, protected from the volatile and detailed implementations of the outer layers.

## 2. The Core Principle: The Dependency Rule

The entire structure of Clean Architecture is governed by one overriding principle:

> **The Dependency Rule**: Source code dependencies can only point **inwards**. Nothing in an inner circle can know anything at all about something in an outer circle. Specifically, the name of something declared in an outer circle must not be mentioned by the code in an inner circle.

This rule is the cornerstone of the architecture. It means that the core business logic ([[Notes/2025/10/14/Domain Layer\|Domain Layer]]) and application-specific rules are completely independent of the UI, database, or any third-party frameworks. These external elements are treated as "details" that can be plugged into the core application.

![Image of Clean Architecture](https://blog.cleancoder.com/uncle-bob/images/2012-08-13-the-clean-architecture/CleanArchitecture.jpg)

## 3. The Layers of Clean Architecture

Clean Architecture is typically depicted as a set of four concentric circles, each representing a different area of the software.

### 3.1 Entities (Innermost Circle)
This layer represents the core of the application. It contains the enterprise-wide business rules and domain objects.

-   **Content**: Comprises the core domain models (Entities, Value Objects, Aggregates) that are fundamental to the business.
-   **Characteristics**: This layer is the most stable and least likely to change. It has no dependencies on any other layer in the application and should be a pure representation of the business domain. A change in an outer layer (e.g., switching from a web app to a console app) should have zero impact on the Entities.

### 3.2 Use Cases (Application Business Rules)
This layer contains the application-specific business rules. It orchestrates the flow of data to and from the Entities to achieve the goals of a particular user interaction.

-   **Content**: Implements and encapsulates all of the use cases of the system. For example, `CreateUser`, `PlaceOrder`, or `CalculateInvoiceTotal`.
-   **Characteristics**: It depends on the Entities layer but has no knowledge of the layers outside of it. It defines the operations the application can perform and enforces the application's policies.

### 3.3 Interface Adapters
This layer acts as a set of converters. Its purpose is to transform data from a format convenient for the inner layers (Entities and Use Cases) to a format convenient for the outer layers (Frameworks and Drivers), and vice versa.

-   **Content**: This layer typically includes:
    -   **Controllers/Presenters**: Handle the flow of control and data to and from the UI.
    -   **Gateways/Repositories**: Provide an abstraction over the data persistence mechanism.
    -   **API Adapters**: Interface with external systems.
-   **Characteristics**: This layer mediates between the pure business logic and the external world of frameworks and tools.

### 3.4 Frameworks & Drivers (Outermost Circle)
This is the outermost layer, where all the implementation details reside. It is the most volatile part of the system.

-   **Content**: This layer is composed of frameworks and tools such as:
    -   The User Interface (e.g., a Web Framework like ASP.NET, React, or Angular)
    -   The Database (e.g., PostgreSQL, MongoDB, and the ORM)
    -   Third-party libraries and external services.
-   **Characteristics**: The code in this layer is a "plugin" to the inner circles. Its role is to wire everything together and serve as the entry/exit point for the application.

## 4. Crossing Boundaries: The Dependency Inversion Principle

A critical question is: if dependencies only point inwards, how does a Use Case in an inner layer talk to a database in an outer layer? The answer lies in the **Dependency Inversion Principle (DIP)**, one of the SOLID principles.

Instead of the inner layer depending directly on the outer layer, both layers depend on an abstraction (like an interface) that is owned by the inner layer.

**Example Flow:**
1.  A **Use Case** (inner layer) needs to save a `User` entity. It cannot directly call a `SqlUserRepository` (outer layer).
2.  Instead, the **Use Case layer defines an interface**, such as `IUserRepository`, which dictates the contract for user persistence (e.g., `void Save(User user);`).
3.  The **Use Case** depends on this interface, not on a concrete implementation.
4.  In the **Frameworks & Drivers layer** (outer layer), a concrete class like `SqlUserRepository` is created that **implements** the `IUserRepository` interface.
5.  At runtime, a mechanism like Dependency Injection provides the Use Case with an instance of `SqlUserRepository`.

The dependency is thus "inverted." The outer layer's implementation now depends on the inner layer's interface, adhering to the Dependency Rule.

## 5. Benefits of Clean Architecture

Adopting this architecture yields significant long-term benefits:

-   **Framework Independence**: The core logic is not tied to any specific web or ORM framework. This makes it easier to update or replace frameworks without rewriting the business rules.
-   **Testability**: The Entities and Use Cases can be tested as plain objects, without needing to run a database, web server, or UI. This results in extremely fast and reliable unit tests.
-   **UI Independence**: The same business logic can be driven by multiple UIs (e.g., a web app, a console app, a mobile app) with minimal changes to the core system.
-   **Database Independence**: The persistence mechanism can be swapped out (e.g., from a SQL database to a NoSQL database) by simply creating a new implementation of the repository interface. The business rules remain unaffected.
-   **High Maintainability**: The strict separation of concerns makes the codebase easier to navigate, understand, and modify, reducing the risk of introducing bugs.

## 6. Challenges and Considerations

-   **Initial Complexity**: For very simple applications (e.g., basic CRUD services), Clean Architecture can feel like over-engineering due to the amount of boilerplate code required for interfaces, data mappers, and dependency injection setup.
-   **Learning Curve**: It requires a solid understanding of software design principles, particularly SOLID, to implement correctly. Teams unfamiliar with these concepts may struggle to apply the pattern effectively.
-   **Performance**: The additional layers of abstraction and data mapping can introduce a minor performance overhead. However, in most business applications, this is negligible compared to network and I/O latency.

## 7. Conclusion

Clean Architecture is a powerful and strategic approach to software design that prioritizes the longevity, maintainability, and testability of a system. By placing the core business logic at the center and treating external technologies as replaceable plugins, it creates a resilient and adaptable codebase. While it may require more discipline and upfront effort, the investment pays significant dividends in complex, long-lived projects where the ability to evolve is paramount.
