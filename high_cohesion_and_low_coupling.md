**High Cohesion** and **Low Coupling** are two fundamental principles of software design aimed at creating systems that are maintainable, scalable, and easy to understand. Let's break them down:

### High Cohesion
- **Definition**: Cohesion refers to how closely related the responsibilities of a single module (class, function, or component) are. High cohesion means that a module performs a well-defined, focused task.
- **Goal**: A highly cohesive module will have a clear purpose and contain code that is directly related to that purpose. This makes the code more understandable and easier to maintain.
- **Example**: A `UserAuthentication` class should only handle authentication-related logic, such as login, logout, or password verification. It shouldn't deal with user profile management or database connections.
  
  **Benefits of High Cohesion**:
  1. Easier to maintain and update.
  2. Increased readability.
  3. Fewer side effects when making changes.
  4. More reusable components.

### Low Coupling
- **Definition**: Coupling refers to how dependent one module is on another. Low coupling means that a module has minimal dependencies on other modules.
- **Goal**: A system with low coupling reduces the impact of changes in one module on others, leading to more modular and independent components.
- **Example**: A class responsible for sending emails (`EmailService`) should not depend on the specific implementation of the `UserAuthentication` class. If the authentication logic changes, the `EmailService` should not be affected.
  
  **Benefits of Low Coupling**:
  1. Easier to change and evolve the system.
  2. Increased module reusability.
  3. Reduces risk when modifying or adding features.
  4. Easier to test modules independently.

### Combined Impact
When you design with **high cohesion** and **low coupling**, your system becomes:
- **Easier to understand** because each module has a single responsibility.
- **More flexible** because changes in one module don’t heavily affect others.
- **More maintainable** as individual parts of the system are more isolated and self-contained.

### Example Code
```python
# High Cohesion: Each class is focused on a single responsibility.

class UserAuthentication:
    def login(self, username: str, password: str) -> bool:
        # Authentication logic here
        return True

    def logout(self) -> None:
        # Logout logic here
        pass


class EmailService:
    def send_email(self, recipient: str, subject: str, body: str) -> None:
        # Email sending logic here
        pass


# Low Coupling: EmailService doesn't depend on UserAuthentication internals.
def notify_user(auth_service: UserAuthentication, email_service: EmailService, username: str):
    if auth_service.login(username, "password"):
        email_service.send_email(username, "Welcome", "Welcome to our service!")
```

Here, both classes have high cohesion, and the interaction between them has low coupling.
