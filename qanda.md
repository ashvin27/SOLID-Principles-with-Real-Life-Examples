**Q1: What is the Single Responsibility Principle, and can you provide an example?**\
**A1:** The Single Responsibility Principle states that a class should have only one reason to change, meaning it should have one responsibility.\
**Example:** A class Invoice should not handle both invoicing and printing. Instead, create two classes: Invoice for managing invoice data and InvoicePrinter for printing the invoice.

---

**Q2: How would you apply the Open/Closed Principle in a system where you need to add new features?**\
**A2:** You would design your classes in such a way that adding new features involves extending the classes rather than modifying the existing code.
**Example:** If you have a `Shape` class with a method to calculate the area, you can create subclasses like `Circle`, `Square`, etc., each implementing the area calculation without modifying the `Shape` class.

---

**Q3: Explain the Liskov Substitution Principle with an example.**\
**A3:** The Liskov Substitution Principle means that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.\
**Example:** If you have a class `Bird` with a method `fly()`, then a subclass `Penguin` (which cannot fly) should not inherit `fly()`. Instead, you should refactor the design so that `fly()` is not part of the `Bird` class or is part of an interface that `Penguin` doesn’t implement.

---

**Q4: What are High Cohesion and Low Coupling? Why are they important in software design?**\
**A4:** High Cohesion means that a module's responsibilities are closely related. Low Coupling means that modules are minimally dependent on each other. *Importance:* High Cohesion makes a module easier to maintain and understand, while Low Coupling makes it easier to change one module without affecting others, leading to more flexible and robust software.

---

**Q5: Can you describe a scenario where violating the Dependency Inversion Principle caused issues in a project?**\
**A5:** In a project where the high-level module (e.g., a business logic layer) directly depends on a low-level module (e.g., a database layer), any change in the database technology would require significant changes in the business logic, causing tight coupling and making the system less flexible. By introducing abstractions (interfaces) that both high-level and low-level modules depend on, you can easily swap out the low-level modules without affecting the high-level modules.

---

**Q6: What is the Interface Segregation Principle, and why is it important?**\
**A6:** The Interface Segregation Principle (ISP) states that no client should be forced to depend on methods it does not use. This means that interfaces should be small and specific to the needs of clients rather than large and general.\
*Example:* If you have an interface `IMachine` with methods `print()`, `scan()`, and `fax()`, and a `Printer` class only implements `print()`, then the `Printer` class should not be forced to implement the `scan()` and `fax()` methods. Instead, you can break down `IMachine` into smaller, more specific interfaces like `IPrinter`, `IScanner`, and `IFax`.

---

**Q7: What is the Dependency Inversion Principle? Can you give a real-world example?**\
**A7:** The Dependency Inversion Principle (DIP) states that high-level modules should not depend on low-level modules. Both should depend on abstractions (e.g., interfaces or abstract classes). Abstractions should not depend on details, and details should depend on abstractions.
*Real-world example:* In a payment system, a `PaymentProcessor` class should not directly depend on a specific `PayPal` class. Instead, it should depend on an interface like `IPaymentGateway`, and the `PayPal` class should implement this interface. This way, if you later need to switch to another payment provider like `Stripe`, you only need to implement the interface, and the `PaymentProcessor` remains unchanged.

---

**Q8: How does achieving low coupling help in system scalability and maintainability?**\
**A8:** Low coupling means that modules in a system have minimal dependencies on each other. This improves scalability because you can make changes to or scale individual modules without affecting others. It also enhances maintainability by reducing the ripple effect of changes, allowing developers to work on different parts of the system simultaneously without worrying about unintended side effects.

---

**Q9: What are some signs that your system has low cohesion, and how would you address them?**\
**A9:** Signs of low cohesion include:
- Classes or modules doing too many unrelated things.
- Difficulty in understanding or maintaining the code because of scattered responsibilities.
- Frequent changes to a class/module for multiple unrelated reasons.

*Addressing low cohesion:* Refactor the code by splitting the module or class into smaller, more focused entities. Group related responsibilities together in their own classes or modules, ensuring each class or module has one clear responsibility.

---

**Q10: How can the Liskov Substitution Principle improve code quality?**\
**A10:** The Liskov Substitution Principle (LSP) ensures that a subclass can be used in place of its superclass without introducing errors. This leads to better code quality because it encourages designing flexible and reliable hierarchies. Violating LSP can lead to unexpected behavior when using polymorphism. Adhering to LSP promotes a more robust and maintainable inheritance structure by ensuring that derived classes fulfill the contracts set by their base classes.

---

**Q11: Explain a scenario where Open/Closed Principle helps in adding new features.**\
**A11:** Suppose you're building a notification system that initially sends email notifications. Later, you need to add support for SMS notifications. If the system is designed with the Open/Closed Principle in mind, you can extend it by creating a new `SMSNotification` class that implements a common `INotification` interface, without modifying the existing `EmailNotification` class or the code that depends on it.

---

**Q12: Can you describe a situation where a violation of the Single Responsibility Principle caused issues in your project?**\
**A12:** In a project, there was a `User` class that not only managed user data but also handled authentication, email notifications, and logging. This led to bloated, hard-to-maintain code. Any change in the authentication logic required changes to the `User` class, which affected unrelated functionalities like logging. Refactoring the code by separating responsibilities into `UserManager`, `AuthService`, `EmailService`, and `Logger` classes improved maintainability and flexibility.

---

**Q13: How do SOLID principles contribute to a system’s maintainability?**\
**A13:** SOLID principles contribute to system's maintainability by:
- Encouraging modular design, making it easier to isolate changes.
- Reducing dependencies between components, which minimizes the impact of changes.
- Promoting the use of interfaces and abstractions, leading to flexible code that can evolve without requiring major rewrites.
- Preventing code from becoming monolithic and tightly coupled, thus enabling easier debugging and testing.

---

**Q14: What is an example of achieving high cohesion in a software module?**\
**A14:** A class `OrderService` that handles all logic related to orders—creating, canceling, and updating orders—shows high cohesion because all methods in the class are closely related to the `Order` domain. If the class also handled user authentication, billing, or shipping, it would have low cohesion. By keeping it focused on orders, the class becomes more understandable and easier to maintain.

---

**Q15: How does Interface Segregation Principle prevent unnecessary dependencies in a system?**\
**A15:** The Interface Segregation Principle prevents unnecessary dependencies by ensuring that clients only depend on the methods they use. This reduces the risk of changes in a large interface affecting clients that do not use all of its methods. Smaller, more focused interfaces minimize the impact of changes, making the system more stable and easier to maintain.
*Example:* Instead of having a single `Vehicle` interface with `drive()`, `fly()`, and `sail()`, create separate interfaces like `Car`, `Plane`, and `Boat` to prevent unnecessary method implementations.
