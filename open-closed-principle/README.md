# Open/Closed Principle

## Before

We have this class

```php
class Hello {
    public function say($lang) {
        if ($lang == 'pr') {
            return 'درود';
        }
        elseif ($lang == 'en') {
            return 'Hi';
        }
    }
}

$hello = new Hello();
echo $hello->say('pr');

```
We want change to

```php
class Hello {
    public function say($lang) {
        if ($lang == 'pr') {
            return 'درود';
        }
        elseif ($lang == 'en') {
            return 'Hi';
        }
        elseif ($lang == 'fr') {
            return 'Bonjour';
        }
        elseif ($lang == 'de') {
            return 'Hallo';
        }
    }
}

$hello = new Hello();
echo $hello->say('de');

```




## After 

```php
interface LanguageInterface {
  public function sayHello(): string;
}

class Persian implements LanguageInterface {
   public function sayHello(): string {
    return 'درود';
  }
}

class French implements LanguageInterface {
   public function sayHello(): string {
    return 'Bonjour';
  }
}

class Hello {
   public function say($lang: LanguageInterface): string {
    return $lang.sayHello();
  }
}

$hello = new Hello();
echo $hello->say(new Persian());
```
