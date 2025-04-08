# PDO with MySQL


## 1. Introduction to PDO
PDO (PHP Data Objects) is a lightweight, consistent interface for accessing databases in PHP. It provides a data-access abstraction layer, allowing you to write database-agnostic code that can work with multiple database systems (e.g., MySQL, PostgreSQL, SQLite) with minimal changes.

With MySQL, PDO offers a secure and efficient way to interact with the database, supporting features like prepared statements, transactions, and error handling.

---

## 2. Why Use PDO with MySQL?
- **Database Agnostic**: Write code that can easily switch between databases.
- **Security**: Supports prepared statements to prevent SQL injection.
- **Flexibility**: Offers multiple ways to fetch data (e.g., associative arrays, objects).
- **Error Handling**: Robust exception-based error handling.
- **Consistency**: Uniform API for different database operations.

---

## 3. Prerequisites
To use PDO with MySQL, ensure the following:
- **PHP**: Version 7.4 or higher (PHP 8.x recommended).
- **MySQL**: MySQL 5.7 or higher (or MariaDB equivalent).
- **PDO Extension**: The PDO MySQL driver (`pdo_mysql`) must be enabled in PHP.
- **MySQL Database**: A running MySQL server with a database and user credentials.

---

## 4. Setting Up PDO with MySQL

### Installing MySQL and PHP PDO Extension
1. **Install MySQL**:
   - On Ubuntu: `sudo apt-get install mysql-server`
   - On Windows: Download and install MySQL Community Server from the official website.
   - Verify installation: `mysql -u root -p`

2. **Enable PDO MySQL Extension**:
   - Ensure the PDO MySQL driver is installed. Check with:
     ```php
     php -i | grep pdo_mysql
     ```
   - If not enabled, enable it in `php.ini`:
     ```ini
     extension=pdo_mysql
     ```
   - Restart your web server (e.g., Apache or Nginx).

3. **Verify PDO Installation**:
   ```php
   <?php
   if (extension_loaded('pdo_mysql')) {
       echo "PDO MySQL extension is enabled.";
   } else {
       echo "PDO MySQL extension is not enabled.";
   }
   ?>
   ```

### Configuring MySQL Database
1. Create a database:
   ```sql
   CREATE DATABASE my_database;
   ```
2. Create a user and grant privileges:
   ```sql
   CREATE USER 'my_user'@'localhost' IDENTIFIED BY 'my_password';
   GRANT ALL PRIVILEGES ON my_database.* TO 'my_user'@'localhost';
   FLUSH PRIVILEGES;
   ```
3. Test the connection using the MySQL client:
   ```bash
   mysql -u my_user -p my_database
   ```

---

## 5. Connecting to MySQL Using PDO

### Basic Connection
To connect to MySQL using PDO, create a `PDO` instance with the appropriate DSN (Data Source Name).

```php
<?php
$dsn = "mysql:host=localhost;dbname=my_database;charset=utf8mb4";
$username = "my_user";
$password = "my_password";

try {
    $pdo = new PDO($dsn, $username, $password);
    echo "Connected successfully!";
} catch (PDOException $e) {
    echo "Connection failed: " . $e->getMessage();
}
?>
```

- **DSN Format**: `mysql:host=<hostname>;dbname=<database_name>;charset=<charset>`
- **Charset**: Use `utf8mb4` for full Unicode support.

### Handling Connection Errors
Wrap the connection in a `try-catch` block to handle exceptions gracefully.

```php
try {
    $pdo = new PDO("mysql:host=localhost;dbname=my_database", "my_user", "my_password");
} catch (PDOException $e) {
    die("Error: Could not connect to the database. " . $e->getMessage());
}
```

### Connection Options
You can pass an array of options to the PDO constructor to customize the connection behavior.

```php
$options = [
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION, // Enable exceptions
    PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC, // Default fetch mode
    PDO::ATTR_EMULATE_PREPARES => false, // Use native prepared statements
];

try {
    $pdo = new PDO($dsn, $username, $password, $options);
} catch (PDOException $e) {
    echo "Connection failed: " . $e->getMessage();
}
```

---

## 6. Executing Queries with PDO

### Types of Queries
- **Non-SELECT Queries**: Use `exec()` for `INSERT`, `UPDATE`, `DELETE`.
- **SELECT Queries**: Use `query()` or prepared statements for retrieving data.
- **Prepared Statements**: Use for parameterized queries to prevent SQL injection.

### Using `exec()` for Non-SELECT Queries
The `exec()` method executes a query and returns the number of affected rows.

```php
try {
    $affectedRows = $pdo->exec("INSERT INTO users (name, email) VALUES ('John Doe', 'john@example.com')");
    echo "Inserted $affectedRows row(s).";
} catch (PDOException $e) {
    echo "Error: " . $e->getMessage();
}
```

**Note**: Avoid `exec()` for user input to prevent SQL injection. Use prepared statements instead.

### Using `query()` for SELECT Queries
The `query()` method executes a query and returns a `PDOStatement` object.

```php
try {
    $result = $pdo->query("SELECT * FROM users");
    while ($row = $result->fetch(PDO::FETCH_ASSOC)) {
        echo "Name: {$row['name']}, Email: {$row['email']}<br>";
    }
} catch (PDOException $e) {
    echo "Error: " . $e->getMessage();
}
```

### Using Prepared Statements
Prepared statements are the recommended way to execute queries with user input.

```php
try {
    $stmt = $pdo->prepare("SELECT * FROM users WHERE email = ?");
    $stmt->execute(['john@example.com']);
    $user = $stmt->fetch(PDO::FETCH_ASSOC);
    print_r($user);
} catch (PDOException $e) {
    echo "Error: " . $e->getMessage();
}
```

---

## 7. Fetching Data

### Fetch Modes
PDO supports multiple fetch modes:
- `PDO::FETCH_ASSOC`: Returns an associative array.
- `PDO::FETCH_NUM`: Returns a numeric array.
- `PDO::FETCH_BOTH`: Returns both associative and numeric arrays.
- `PDO::FETCH_OBJ`: Returns an object.
- `PDO::FETCH_CLASS`: Maps results to a class.

Set the default fetch mode in the PDO constructor or specify it per query.

### Fetching Single Row
Use `fetch()` to retrieve a single row.

```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE id = ?");
$stmt->execute([1]);
$user = $stmt->fetch(PDO::FETCH_ASSOC);
if ($user) {
    echo "Name: {$user['name']}";
} else {
    echo "No user found.";
}
```

### Fetching Multiple Rows
Use `fetchAll()` to retrieve all rows.

```php
$stmt = $pdo->query("SELECT * FROM users");
$users = $stmt->fetchAll(PDO::FETCH_ASSOC);
foreach ($users as $user) {
    echo "Name: {$user['name']}, Email: {$user['email']}<br>";
}
```

---

## 8. Prepared Statements and Parameter Binding

Prepared statements improve security by separating SQL logic from user input.

### Named Placeholders
Use named placeholders (`:name`) for readable queries.

```php
$stmt = $pdo->prepare("INSERT INTO users (name, email) VALUES (:name, :email)");
$stmt->execute([
    ':name' => 'Jane Doe',
    ':email' => 'jane@example.com'
]);
echo "User inserted successfully.";
```

### Positional Placeholders
Use question marks (`?`) for positional parameters.

```php
$stmt = $pdo->prepare("INSERT INTO users (name, email) VALUES (?, ?)");
$stmt->execute(['Jane Doe', 'jane@example.com']);
echo "User inserted successfully.";
```

### Binding Values
You can explicitly bind values using `bindValue()` or `bindParam()`.

```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE id = :id");
$stmt->bindValue(':id', 1, PDO::PARAM_INT);
$stmt->execute();
$user = $stmt->fetch(PDO::FETCH_ASSOC);
print_r($user);
```

- `bindValue()`: Binds a value directly.
- `bindParam()`: Binds a variable (useful for loops or dynamic values).

---

## 9. Error Handling

### Setting Error Modes
PDO supports three error modes:
- `PDO::ERRMODE_SILENT`: No errors or exceptions (default).
- `PDO::ERRMODE_WARNING`: Trigger PHP warnings.
- `PDO::ERRMODE_EXCEPTION`: Throw exceptions (recommended).

Set the error mode in the PDO constructor:

```php
$pdo = new PDO($dsn, $username, $password, [
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION
]);
```

### Catching Exceptions
Always wrap PDO operations in `try-catch` blocks.

```php
try {
    $stmt = $pdo->prepare("SELECT * FROM nonexistent_table");
    $stmt->execute();
} catch (PDOException $e) {
    echo "Database error: " . $e->getMessage();
}
```

---

## 10. Transactions
PDO supports transactions for atomic operations.

```php
try {
    $pdo->beginTransaction();
    
    $stmt1 = $pdo->prepare("INSERT INTO users (name, email) VALUES (?, ?)");
    $stmt1->execute(['Alice', 'alice@example.com']);
    
    $stmt2 = $pdo->prepare("UPDATE accounts SET balance = balance - ? WHERE user_id = ?");
    $stmt2->execute([100, 1]);
    
    $pdo->commit();
    echo "Transaction successful.";
} catch (PDOException $e) {
    $pdo->rollBack();
    echo "Transaction failed: " . $e->getMessage();
}
```

- `beginTransaction()`: Starts a transaction.
- `commit()`: Commits the transaction.
- `rollBack()`: Rolls back the transaction on error.

---

## 11. Best Practices
- **Use Prepared Statements**: Always use prepared statements for user input.
- **Enable Exceptions**: Set `PDO::ERRMODE_EXCEPTION` for better error handling.
- **Close Connections**: Set `$pdo = null` when done to free resources.
- **Use UTF-8**: Specify `charset=utf8mb4` in the DSN.
- **Avoid Emulated Prepares**: Set `PDO::ATTR_EMULATE_PREPARES` to `false`.
- **Secure Credentials**: Store database credentials in a configuration file outside the web root.
- **Log Errors**: Log database errors to a file for debugging (avoid exposing to users).

---

## 12. Example Application
Below is a complete example of a simple CRUD application using PDO with MySQL.

### Database Schema
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE
);
```

### PHP Code
```php
<?php
$dsn = "mysql:host=localhost;dbname=my_database;charset=utf8mb4";
$username = "my_user";
$password = "my_password";
$options = [
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
    PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,
    PDO::ATTR_EMULATE_PREPARES => false,
];

try {
    $pdo = new PDO($dsn, $username, $password, $options);
} catch (PDOException $e) {
    die("Connection failed: " . $e->getMessage());
}

// Create
function createUser($pdo, $name, $email) {
    $stmt = $pdo->prepare("INSERT INTO users (name, email) VALUES (:name, :email)");
    $stmt->execute(['name' => $name, 'email' => $email]);
    return $pdo->lastInsertId();
}

// Read
function getUser($pdo, $id) {
    $stmt = $pdo->prepare("SELECT * FROM users WHERE id = ?");
    $stmt->execute([$id]);
    return $stmt->fetch();
}

// Update
function updateUser($pdo, $id, $name, $email) {
    $stmt = $pdo->prepare("UPDATE users SET name = :name, email = :email WHERE id = :id");
    $stmt->execute(['name' => $name, 'email' => $email, 'id' => $id]);
    return $stmt->rowCount();
}

// Delete
function deleteUser($pdo, $id) {
    $stmt = $pdo->prepare("DELETE FROM users WHERE id = ?");
    $stmt->execute([$id]);
    return $stmt->rowCount();
}

// Example Usage
try {
    // Create
    $userId = createUser($pdo, "John Doe", "john@example.com");
    echo "Created user with ID: $userId<br>";
    
    // Read
    $user = getUser($pdo, $userId);
    echo "User: {$user['name']}, {$user['email']}<br>";
    
    // Update
    updateUser($pdo, $userId, "John Smith", "john.smith@example.com");
    echo "User updated.<br>";
    
    // Delete
    deleteUser($pdo, $userId);
    echo "User deleted.<br>";
} catch (PDOException $e) {
    echo "Error: " . $e->getMessage();
}

// Close connection
$pdo = null;
?>
```

---

## 13. Common Issues and Troubleshooting
- **"SQLSTATE[HY000] [2002] No such file or directory"**:
  - Ensure MySQL is running and the host is correct (`localhost` vs. `127.0.0.1`).
- **"Access denied for user"**:
  - Verify username, password, and database privileges.
- **"Unknown database"**:
  - Ensure the database exists and the DSN is correct.
- **Prepared statement errors**:
  - Check for typos in SQL or incorrect parameter counts.
- **Character encoding issues**:
  - Use `charset=utf8mb4` in the DSN and ensure the database uses UTF-8.
