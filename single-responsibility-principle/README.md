# Single Responsibility Principle

## Before

```php
class User {
  public information() {}
  public sendEmail() {}
  public orders() {}
}
```

## After 

```php
class User {
  public information() {}
}

class Email {
  public send(user: User) {}
}

class Order {
  public show(user: User) {}
}
```
