# Interface Segregation Principle

## Before

```php
interface Animal {
    public function fly();
    public function run();
    public function eat();
}

class Dolphin implements Animal {
    public function fly() {
        return false;
    }

    public function run() {
        // Run
    }

    public function eat() {
        // Eat
    }
}
```

## After 

```php
interface Animal {
    public function run();
    public function eat();
}

interface FlyableAnimal {
    public function fly();
}

class Dolphin implements Animal {
    public function run() {
        // Run
    }

    public function eat() {
        // Eat
    }
}

class Bird implements Animal, FlyableAnimal {
    public function run() { /* ... */ }
    public function eat() { /* ... */ }
    public function fly() { /* ... */ }
}
```
