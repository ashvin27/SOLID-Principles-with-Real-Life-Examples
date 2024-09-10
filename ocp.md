# Open/Closed Principle (OCP)
**Definition:** Software entities should be open for extension but closed for modification.

### Example: Notification System
**Bad Example:**

```
class Notification {
  sendNotification(type: string, message: string) {
    if (type === 'email') {
      this.sendEmail(message);
    } else if (type === 'sms') {
      this.sendSms(message);
    } else if (type === 'push') {
      this.sendPush(message);
    }
  }

  private sendEmail(message: string) {
    console.log(`Sending email: ${message}`);
  }

  private sendSms(message: string) {
    console.log(`Sending SMS: ${message}`);
  }

  private sendPush(message: string) {
    console.log(`Sending push notification: ${message}`);
  }
}

```

**Explanation:**

- Adding a new notification type requires modifying the **sendNotification** method, which violates OCP.


**Good Example:**

```
interface Notification {
  send(message: string): void;
}

class EmailNotification implements Notification {
  send(message: string): void {
    console.log(`Sending email: ${message}`);
  }
}

class SmsNotification implements Notification {
  send(message: string): void {
    console.log(`Sending SMS: ${message}`);
  }
}

class PushNotification implements Notification {
  send(message: string): void {
    console.log(`Sending push notification: ${message}`);
  }
}

class NotificationService {
  constructor(private notification: Notification) {}

  notify(message: string) {
    this.notification.send(message);
  }
}

```

**Explanation:**

- New notification types can be added by creating new classes that implement the **Notification** interface.
- **Adherence to OCP:** Existing code remains unchanged, promoting easy extension.
