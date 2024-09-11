# Dependency Inversion Principle (DIP)
**Definition:** High-level modules should not depend on low-level modules. Both should depend on abstractions.

### Example: Order Processing System
**Bad Example:**

```
class MySQLDatabase {
  connect() {
    console.log('Connecting to MySQL database');
  }

  query(sql: string) {
    console.log(`Executing query: ${sql}`);
  }
}

class OrderService {
  private db: MySQLDatabase;

  constructor() {
    this.db = new MySQLDatabase();
  }

  getOrder(orderId: number) {
    this.db.connect();
    this.db.query(`SELECT * FROM orders WHERE id = ${orderId}`);
  }
}
```

**Explanation:**

- The `OrderService` class is tightly coupled to the `MySQLDatabase` class, making it hard to switch databases.


**Good Example:**

```
interface Database {
  connect(): void;
  query(sql: string): void;
}

class MySQLDatabase implements Database {
  connect() {
    console.log('Connecting to MySQL database');
  }

  query(sql: string) {
    console.log(`Executing query: ${sql}`);
  }
}

class PostgreSQLDatabase implements Database {
  connect() {
    console.log('Connecting to PostgreSQL database');
  }

  query(sql: string) {
    console.log(`Executing query: ${sql}`);
  }
}

class OrderService {
  constructor(private db: Database) {}

  getOrder(orderId: number) {
    this.db.connect();
    this.db.query(`SELECT * FROM orders WHERE id = ${orderId}`);
  }
}

// Usage
const mySQLDatabase = new MySQLDatabase();
const orderService = new OrderService(mySQLDatabase);
orderService.getOrder(123);
```

**Explanation:**

- The `OrderService` class depends on the `Database` interface, allowing for easy substitution of different database implementations.
- **Adherence to DIP:** High-level modules (`OrderService`) depend on abstractions (`Database`), not on concrete implementations.

