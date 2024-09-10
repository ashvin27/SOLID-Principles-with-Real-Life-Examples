# Single Responsibility Principle (SRP)
**Definition:** A class should have only one reason to change, meaning it should have only one job or responsibility.

### Example: User Management System
**Bad Example:**

```
class User {
  constructor(public name: string, public email: string) {}

  getUserInfo() {
    return `Name: ${this.name}, Email: ${this.email}`;
  }

  sendWelcomeEmail() {
    console.log(`Sending welcome email to ${this.email}`);
  }

  saveToDatabase() {
    console.log(`Saving user ${this.name} to the database`);
  }
}
```

**Explanation:**

- The **User** class is responsible for handling user data, sending emails, and interacting with the database.

- **Violation of SRP:** The class has multiple responsibilities, making it harder to maintain and test.


**Good Example:**

```
class User {
  constructor(public name: string, public email: string) {}

  getUserInfo() {
    return `Name: ${this.name}, Email: ${this.email}`;
  }
}

class UserRepository {
  save(user: User) {
    console.log(`Saving user ${user.name} to the database`);
  }
}

class EmailService {
  sendWelcomeEmail(email: string) {
    console.log(`Sending welcome email to ${email}`);
  }
}
```

**Explanation:**

- The responsibilities are split across different classes (**User**, **UserRepository**, **EmailService**), each with a single responsibility.
- **Adherence to SRP:** Each class is easier to maintain and test individually.
