# Interface Segregation Principle (ISP)
**Definition:** A client should not be forced to implement interfaces they do not use. This means that a class should not be required to implement methods it doesn't need.

### Example: Document Management System
**Bad Example:**

```
interface Document {
  print(): void;
  save(): void;
  share(): void;
}

class TextDocument implements Document {
  print(): void {
    console.log('Printing document');
  }

  save(): void {
    console.log('Saving document');
  }

  share(): void {
    throw new Error('Sharing not supported');
  }
}

```

**Explanation:**

- The `TextDocument` class is forced to implement the `share` method even though it doesn't support sharing.


**Good Example:**

```
interface Printable {
  print(): void;
}

interface Savable {
  save(): void;
}

interface Shareable {
  share(): void;
}

class TextDocument implements Printable, Savable {
  print(): void {
    console.log('Printing document');
  }

  save(): void {
    console.log('Saving document');
  }
}

class ImageDocument implements Printable, Shareable {
  print(): void {
    console.log('Printing image');
  }

  share(): void {
    console.log('Sharing image');
  }
}
```

**Explanation:**

- The responsibilities are split into separate interfaces (`Printable`, `Savable`, `Shareable`), and classes only implement the interfaces they need.
- **Adherence to ISP:** Classes are not burdened with unnecessary methods, promoting better design and usability.

