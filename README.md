# Introduction To PHP

PHP, which stands for Hypertext Preprocessor, is a popular open-source, server-side scripting language designed primarily for web development. It is embedded within HTML code and executed on the server, generating dynamic web content that is then sent to the client's browser. PHP is widely used due to its simplicity, flexibility, and robust ecosystem.

**Key Features of PHP**
- **Server-Side:** Runs on the server (e.g., Apache, Nginx), not the client’s browser.
-   **Embedded in HTML:** PHP code is written inside ```<?php ... ?> ``` tags within HTML files.
- **Dynamic Content:** Enables websites to display content based on user input, database data, or other conditions.
- **Cross-Platform:** Works on various operating systems like Windows, Linux, and macOS.
- **Database Integration:** Strong support for databases like MySQL, PostgreSQL, and SQLite.
- **Open-Source:** Free to use, with a large community contributing to its development.

### Installation

- **Ubuntu**
```
sudo apt update
sudo apt upgrade
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.4-common php8.4-cli php8.4-fpm php8.4-{curl,bz2,mbstring,intl}
```
```
php -v
```

### Basic Syntax

Here's a concise overview of PHP basic syntax, covering variables, data types, and operators:

#### Variables
- Variables in PHP start with a `$` sign followed by the variable name.
- Variable names are case-sensitive and must start with a letter or underscore, followed by letters, numbers, or underscores.
- No need to declare variable types explicitly (PHP is loosely typed).

**Examples:**
```php
$name = "John";          // String
$age = 25;              // Integer
$price = 19.99;         // Float
$isStudent = true;      // Boolean
```
#### Comment

Comments in PHP are used to add explanations or notes within the code. They are ignored by the PHP interpreter and do not affect the program's execution. Comments are essential for making code readable and maintainable.

#### Types of Comments
1. **Single-Line Comments**
   - Use `//` or `#` to comment out the rest of the line.
   - Ideal for short explanations or notes.

   **Examples:**
   ```php
   <?php
   $x = 10; // This is a single-line comment using //
   $y = 20; # This is a single-line comment using #
   echo $x + $y; // Outputs 30
   ?>
   ```

2. **Multi-Line Comments**
   - Use `/*` to start and `*/` to end a comment block.
   - Useful for longer explanations or commenting out multiple lines of code.

   **Examples:**
   ```php
   <?php
   /* 
      This is a multi-line comment.
      It can span several lines.
      Below, we calculate the sum of two numbers.
   */
   $a = 5;
   $b = 3;
   echo $a + $b; // Outputs 8
   ?>
   ```

**Example with Mixed Comments**
```php
<?php
// Define user details
$name = "John"; // User's first name
$age = 25;      // User's age in years

/* 
   Check if the user is eligible to vote.
   In this country, voting age is 18.
   The result is stored in $canVote.
*/
$canVote = $age >= 18;

echo "Name: " . $name . "<br>"; // Display the name
echo "Can vote? " . ($canVote ? "Yes" : "No"); // Ternary operator for eligibility
?>
```


#### Data Types
1. **Scalar Types:**
   - **String**: Text enclosed in single (`'`) or double (`"`) quotes. Also can be written in HereDoc and NowDoc.
     ```php
     $greeting = "Hello, World!";

     $heredoc = <<<TEXT
                Line 1
                Line 2
                $greeting
                TEXT;

     $nowdoc = <<<'TEXT'
                Veriables name get plain text.
            TEXT;
     ```
   - **Integer**: Whole numbers (no decimals).
     ```php
     $count = 42;
     ```
   - **Float**: Decimal numbers.
     ```php
     $temperature = 36.6;
     ```
   - **Boolean**: `true` or `false`.
     ```php
     $isActive = false;
     ```

2. **Compound Types:**
   - **Array**: Ordered collection of values.
     ```php
     $fruits = ["apple", "banana", "orange"];
     // Or older syntax
     $numbers = array(1, 2, 3);
     echo $fruits[0];

     $multi = [[10,11,12],[11,12,13]];

     echo $multi[0][1];
     ```
   - **Object**: Instances of classes (more advanced, not covered here).
   - **Iterables**
   - **Callable**

3. **Special Types:**
   - **NULL**: Represents no value.
     ```php
     $empty = null;
     ```
    - **Resource**

#### Operators
1. **Arithmetic Operators:**
   - `+` (Addition): `$a + $b`
   - `-` (Subtraction): `$a - $b`
   - `*` (Multiplication): `$a * $b`
   - `/` (Division): `$a / $b`
   - `%` (Modulus): `$a % $b` (remainder)
   - `**` (Exponentiation): `$a ** $b` (e.g., 2 ** 3 = 8)

   **Example:**
   ```php
   $x = 10;
   $y = 3;
   echo $x + $y; // Outputs 13
   echo $x % $y; // Outputs 1
   ```

2. **Assignment Operators:**
   - `=` : Assigns a value.
   - `+=`, `-=`, `*=`, `/=`, `%=` : Combined operations.
     ```php
     $x = 5;
     $x += 3; // $x is now 8
     ```

3. **Comparison Operators:**
   - `==` : Equal (value only).
   - `===` : Identical (value and type).
   - `!=` or `<>` : Not equal.
   - `!==` : Not identical.
   - `<`, `>`, `<=`, `>=` : Less than, greater than, etc.

   **Example:**
   ```php
   $a = 5;
   $b = "5";
   var_dump($a == $b);  // true (same value)
   var_dump($a === $b); // false (different types)
   ```

4. **Logical Operators:**
   - `&&` or `and` : Both conditions true.
   - `||` or `or` : At least one condition true.
   - `!` : Not (inverts true/false).
     ```php
     $x = true;
     $y = false;
     echo $x && $y; // false
     echo $x || $y; // true
     echo !$x;      // false
     ```

5. **String Operator:**
   - `.`/`.=` : Concatenation.
     ```php
     $first = "Hello";
     $last = "World";
     echo $first . " " . $last; // Outputs "Hello World"
     ```
6. **Increment/Decrement Operator:**: 
    - `++`: Increment Operator.
    - `--`: Decrement Operator.
    ```php
     $i=1;
     $i++; //incrementing i by 1
     echo $i; //2

     $i--; //decrementing i by 1
     echo $i; //1
     ```
7. **Error Controll Operator:** `@`
8. **Bitwise Operator:**
    - `&`: Bitwise And
    - `|`: Bitwise OR
    - `~`: Bitwise NOT
    - `^`: Bitwise XOR
    - `<<`: Bitwise Left Shift
    - `>>`: Bitwise Right Shift

#### Basic Example Combining Everything:
```php
<?php
$name = "Alice";           // String variable
$age = 20;                // Integer variable
$height = 1.65;           // Float variable
$isStudent = true;        // Boolean variable

// Using operators
$nextAge = $age + 1;      // Arithmetic
$greeting = "Hi, " . $name; // Concatenation
$canVote = $age >= 18;    // Comparison

echo $greeting . "<br>";  // Output: Hi, Alice
?>
```
