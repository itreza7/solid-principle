# Dependency Inversion Principle

## Before

```php
class MySql {
    public function insert() {}
    public function update() {}
    public function delete() {}
}

class Log {
    private $database;

    public function __construct() {
        $this->database = new MySql;
    }
}
```

## After 

```php
interface Database {
    public function insert();
    public function update();
    public function delete();
}

class MySql implements Database {
    public function insert() {}
    public function update() {}
    public function delete() {}
}

class FileSystem implements Database {
    public function insert() {}
    public function update() {}
    public function delete() {}
}

class MongoDB implements Database {
    public function insert() {}
    public function update() {}
    public function delete() {}
}

class Log {
    private Database $db;

    public function setDatabase(Database $db) {
        $this->db = $db;
    }

    public function update() {
        $this->db->update();
    }
}

$logger = new Log();

$logger->setDatabase(new MongoDB);

$logger->setDatabase(new FileSystem);

$logger->setDatabase(new MySql);

$logger->update();
```
