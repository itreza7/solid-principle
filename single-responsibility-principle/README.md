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
class Order {
  public show(user: User) {}
}
