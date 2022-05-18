# Liskov Substitution Principle

## Basis

```php
class A { ... }

x = new A();

// ...

y = new A();

// ...

z = new A();

class B extends A { ... }

x = new B();

// ...

y = new B();

// ...

z = new B();

```


## Wrong 

```php
class Note {

    public constructor($id) {
        // ...
    }

    public save($text): void {
        // save process
    }
}

$note = new Note(429);
$note->save("Let's do this!");

class ReadonlyNote extends Note {
    public save($text): void {
        throw new Error("Can't update readonly notes");
    }
}

$note = new ReadonlyNote(429);
$note->save("Let's do this!");

```

## Better Way

```php
class Note {
    public __constructor($id) {
        // ...
    }
}

class WritableNote extends Note {
    public save($text): void {
        // save process
    }
}
```
