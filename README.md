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

### Conditional Statements
Conditional statements in PHP allow you to execute different blocks of code based on whether a condition is true or false. They are essential for decision-making in programming.

#### 1. `if` Statement
- Executes a block of code if a condition is true.
- Syntax:
  ```php
  if (condition) {
      // Code to execute if condition is true
  }
  ```

**Example:**
```php
<?php
$age = 20;
if ($age >= 18) {
    echo "You are an adult.";
}
// Output: You are an adult.
?>
```

---

#### 2. `if...else` Statement
- Adds an alternative block of code to execute if the condition is false.
- Syntax:
  ```php
  if (condition) {
      // Code if condition is true
  } else {
      // Code if condition is false
  }
  ```

**Example:**
```php
<?php
$age = 15;
if ($age >= 18) {
    echo "You can vote.";
} else {
    echo "You cannot vote yet.";
}
// Output: You cannot vote yet.
?>
```

---

#### 3. `if...elseif...else` Statement
- Tests multiple conditions in sequence, executing the first true condition’s block or the `else` block if none are true.
- Syntax:
  ```php
  if (condition1) {
      // Code if condition1 is true
  } elseif (condition2) {
      // Code if condition2 is true
  } else {
      // Code if no conditions are true
  }
  ```

**Example:**
```php
<?php
$score = 85;
if ($score >= 90) {
    echo "Grade: A+";
} elseif ($score >= 80) {
    echo "Grade: A";
} elseif ($score >= 70) {
    echo "Grade: A-";
} else {
    echo "Grade: F";
}
// Output: Grade: A
?>
```

---

#### 4. `switch` Statement
- Evaluates an expression and executes code based on matching cases. It’s an alternative to multiple `if...elseif` statements.
- Syntax:
  ```php
  switch (expression) {
      case value1:
          // Code if expression equals value1
          break;
      case value2:
          // Code if expression equals value2
          break;
      default:
          // Code if no cases match
  }
  ```
- `break` prevents fall-through to the next case.
- `default` is optional and runs if no case matches.

**Example:**
```php
<?php
$day = "Monday";
switch ($day) {
    case "Monday":
        echo "Start of the week.";
        break;
    case "Friday":
        echo "End of the work week.";
        break;
    default:
        echo "Some other day.";
}
// Output: Start of the week.
?>
```
---

### PHP Looping
Loops in PHP allow you to repeat a block of code multiple times based on a condition or a set number of iterations. They are crucial for tasks like iterating over arrays or performing repetitive actions.

#### 1. `for` Loop
- Repeats a block of code a specific number of times.
- Syntax:
  ```php
  for (initialization; condition; increment/decrement) {
      // Code to repeat
  }
  ```
- `initialization`: Sets the starting value (runs once at the start).
- `condition`: Checked before each iteration; loop continues if true.
- `increment/decrement`: Updates the counter after each iteration.

**Example:**
```php
<?php
for ($i = 1; $i <= 5; $i++) {
    echo "Number: $i <br>";
}
?>
```

---

#### 2. `while` Loop
- Repeats a block of code as long as a condition is true.
- Syntax:
  ```php
  while (condition) {
      // Code to repeat
  }
  ```

**Example:**
```php
<?php
$count = 0;
while ($count < 3) {
    echo "Count: $count <br>";
    $count++;
}
?>
```

---

#### 3. `do...while` Loop
- Similar to `while`, but the code runs at least once before checking the condition.
- Syntax:
  ```php
  do {
      // Code to repeat
  } while (condition);
  ```

**Example:**
```php
<?php
$x = 5;
do {
    echo "Value: $x <br>";
    $x++;
} while ($x < 5);
// Output: Value: 5 (runs once even though condition is false)
?>
```

---

#### 4. `foreach` Loop
- Designed for iterating over arrays or objects.
- Syntax (for arrays):
  ```php
  foreach ($array as $value) {
      // Code to repeat for each element
  }
  ```
  Or with keys:
  ```php
  foreach ($array as $key => $value) {
      // Code using key and value
  }
  ```

**Example:**
```php
<?php
$colors = ["Red", "Green", "Blue"];
foreach ($colors as $color) {
    echo "Color: $color <br>";
}
?>
```

---

#### Loop Control
- **`break`**: Exits the loop entirely.
- **`continue`**: Skips the current iteration and moves to the next.

**Example with `break`:**
```php
<?php
for ($i = 0; $i < 10; $i++) {
    if ($i == 4) {
        break; // Stops loop when $i is 4
    }
    echo "$i <br>";
}
// Output: 0, 1, 2, 3
?>
```

**Example with `continue`:**
```php
<?php
for ($i = 0; $i < 5; $i++) {
    if ($i == 2) {
        continue; // Skips 2
    }
    echo "$i <br>";
}
// Output: 0, 1, 3, 4
?>
```

---

### PHP Functions
Functions in PHP are reusable blocks of code that perform a specific task. They can take input (parameters), process it, and optionally return a value. PHP also supports variable-length argument lists for flexibility.

#### 1. Defining a Function
- Use the `function` keyword followed by the function name and parentheses `()`.
- Syntax:
  ```php
  function functionName($parameter1, $parameter2) {
      // Code to execute
      return $value; // Optional
  }
  ```

**Example:**
```php
<?php
function sayHello() {
    echo "Hello, World!";
}
sayHello(); // Output: Hello, World!
?>
```

---

#### 2. Functions with Parameters
- Parameters allow data to be passed into a function.

**Example:**
```php
<?php
function greet($name) {
    echo "Hello, $name!";
}
greet("Alice"); // Output: Hello, Alice!
?>
```

---

#### 3. Default Parameter Values
- Parameters can have default values, making them optional.

**Example:**
```php
<?php
function welcome($name = "Guest") {
    echo "Welcome, $name!";
}
welcome();       // Output: Welcome, Guest!
welcome("John"); // Output: Welcome, John!
?>
```

---

#### 4. Return Values
- Use `return` to send a value back to the caller.

**Example:**
```php
<?php
function multiply($x, $y) {
    return $x * $y;
}
$result = multiply(4, 5);
echo $result; // Output: 20
?>
```

---

#### 5. Type Declarations (Optional)
- Optional type hints for parameters and return values.

**Example:**
```php
<?php
function divide(float $a, float $b): float {
    return $a / $b;
}
echo divide(10.5, 2.0); // Output: 5.25
?>
```

---

#### 6. Variable-Length Argument Lists
- The `...` operator collects all arguments into an array.

**Syntax:**
```php
function functionName(...$args) {
    // $args is an array of all passed arguments
}
```

**Example:**
```php
<?php
function sum(...$numbers) {
    $total = 0;
    foreach ($numbers as $num) {
        $total += $num;
    }
    return $total;
}
echo sum(1, 2, 3);       // Output: 6
echo sum(4, 5, 6, 7);    // Output: 22
echo sum();              // Output: 0 (no arguments)
?>
```

**With Type Hinting:**
```php
<?php
function concatenate(string ...$words) {
    return implode(" ", $words);
}
echo concatenate("Hello", "World"); // Output: Hello World
echo concatenate("PHP", "is", "fun"); // Output: PHP is fun
?>
```

**Mixing Fixed and Variable Arguments:**
- Fixed parameters must come before the variadic parameter.
```php
<?php
function describe($prefix, ...$items) {
    echo "$prefix: " . implode(", ", $items);
}
describe("Fruits", "apple", "banana", "orange");
// Output: Fruits: apple, banana, orange
?>
```

**Using an Array as Arguments:**
- You can pass an array to a variadic function using the `...` operator to "unpack" it.
```php
<?php
$numbers = [1, 2, 3, 4];
echo sum(...$numbers); // Output: 10
?>
```

---

#### 7. Variable Scope
- Variables inside a function are local by default; use `global` to access external variables.

**Example:**
```php
<?php
$num = 10;
function increment() {
    global $num;
    $num++;
}
increment();
echo $num; // Output: 11
?>
```

---

#### 8. Anonymous Functions (Closures)
- Nameless functions, often used as callbacks.

**Example:**
```php
<?php
$square = function($x) {
    return $x * $x;
};
echo $square(3); // Output: 9
?>
```

---

#### 9. Pass by Reference
- Use `&` to modify the original variable.

**Example:**
```php
<?php
function addFive(&$number) {
    $number += 5;
}
$value = 10;
addFive($value);
echo $value; // Output: 15
?>
```
