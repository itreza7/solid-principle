# Solid principles

## Single Responsibility Principle

Convert

```php
class User {
  public information() {}
  public sendEmail() {}
  public orders() {}
}
```

to 

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
