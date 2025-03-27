# Introduction To PHP

PHP, which stands for Hypertext Preprocessor, is a popular open-source, server-side scripting language designed primarily for web development. It is embedded within HTML code and executed on the server, generating dynamic web content that is then sent to the client's browser. PHP is widely used due to its simplicity, flexibility, and robust ecosystem.

**Key Features of PHP**
- **Server-Side:** Runs on the server (e.g., Apache, Nginx), not the client’s browser.
-   **Embedded in HTML:** PHP code is written inside ```<?php ... ?> ``` tags within HTML files.
- **Dynamic Content:** Enables websites to display content based on user input, database data, or other conditions.
- **Cross-Platform:** Works on various operating systems like Windows, Linux, and macOS.
- **Database Integration:** Strong support for databases like MySQL, PostgreSQL, and SQLite.
- **Open-Source:** Free to use, with a large community contributing to its development.

---

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
---

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
---

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

### Looping
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

---

### PHP Array Functions
PHP arrays can be indexed (numeric keys), associative (string keys), or multidimensional. These functions help you create, modify, and query arrays efficiently.

#### 1. Creating and Adding Elements
- **`array()` or `[]`**: Create an array.
  ```php
  <?php
  $fruits = array("apple", "banana"); // Old syntax
  $colors = ["red", "blue"];          // Modern syntax
  ?>
  ```

- **`array_push()`**: Add one or more elements to the end of an array.
  ```php
  <?php
  $numbers = [1, 2];
  array_push($numbers, 3, 4);
  print_r($numbers); // Output: Array ( [0] => 1 [1] => 2 [2] => 3 [3] => 4 )
  ?>
  ```

- **`array_unshift()`**: Add elements to the beginning of an array.
  ```php
  <?php
  $letters = ["b", "c"];
  array_unshift($letters, "a");
  print_r($letters); // Output: Array ( [0] => a [1] => b [2] => c )
  ?>
  ```

---

#### 2. Removing Elements
- **`array_pop()`**: Remove and return the last element.
  ```php
  <?php
  $stack = [1, 2, 3];
  $last = array_pop($stack);
  echo $last;        // Output: 3
  print_r($stack);   // Output: Array ( [0] => 1 [1] => 2 )
  ?>
  ```

- **`array_shift()`**: Remove and return the first element.
  ```php
  <?php
  $queue = [1, 2, 3];
  $first = array_shift($queue);
  echo $first;       // Output: 1
  print_r($queue);   // Output: Array ( [0] => 2 [1] => 3 )
  ?>
  ```

- **`unset()`**: Remove an element by key (does not reindex numeric keys).
  ```php
  <?php
  $data = ["a" => 1, "b" => 2, "c" => 3];
  unset($data["b"]);
  print_r($data); // Output: Array ( [a] => 1 [c] => 3 )
  ?>
  ```

---

#### 3. Searching and Checking
- **`in_array()`**: Check if a value exists in an array.
  ```php
  <?php
  $fruits = ["apple", "banana"];
  if (in_array("apple", $fruits)) {
      echo "Found!"; // Output: Found!
  }
  ?>
  ```

- **`array_search()`**: Return the key of a value (or `false` if not found).
  ```php
  <?php
  $colors = ["a" => "red", "b" => "blue"];
  $key = array_search("blue", $colors);
  echo $key; // Output: b
  ?>
  ```

- **`array_key_exists()`**: Check if a key exists in an array.
  ```php
  <?php
  $person = ["name" => "Alice", "age" => 25];
  if (array_key_exists("name", $person)) {
      echo "Key exists!"; // Output: Key exists!
  }
  ?>
  ```

---

#### 4. Sorting
- **`sort()`**: Sort array in ascending order (reindexes numeric keys).
  ```php
  <?php
  $numbers = [3, 1, 4];
  sort($numbers);
  print_r($numbers); // Output: Array ( [0] => 1 [1] => 3 [2] => 4 )
  ?>
  ```

- **`rsort()`**: Sort array in descending order.
  ```php
  <?php
  $numbers = [3, 1, 4];
  rsort($numbers);
  print_r($numbers); // Output: Array ( [0] => 4 [1] => 3 [2] => 1 )
  ?>
  ```

- **`asort()`**: Sort associative array by value, preserving keys.
  ```php
  <?php
  $ages = ["Alice" => 25, "Bob" => 20];
  asort($ages);
  print_r($ages); // Output: Array ( [Bob] => 20 [Alice] => 25 )
  ?>
  ```

- **`ksort()`**: Sort associative array by key.
  ```php
  <?php
  $data = ["z" => 1, "a" => 2];
  ksort($data);
  print_r($data); // Output: Array ( [a] => 2 [z] => 1 )
  ?>
  ```

---

#### 5. Merging and Combining
- **`array_merge()`**: Merge two or more arrays.
  ```php
  <?php
  $arr1 = [1, 2];
  $arr2 = [3, 4];
  $merged = array_merge($arr1, $arr2);
  print_r($merged); // Output: Array ( [0] => 1 [1] => 2 [2] => 3 [3] => 4 )
  ?>
  ```

- **`array_combine()`**: Create an array using one array for keys and another for values.
  ```php
  <?php
  $keys = ["name", "age"];
  $values = ["Alice", 25];
  $combined = array_combine($keys, $values);
  print_r($combined); // Output: Array ( [name] => Alice [age] => 25 )
  ?>
  ```

---

#### 6. Filtering and Mapping
- **`array_filter()`**: Filter array elements using a callback function.
  ```php
  <?php
  $numbers = [1, 2, 3, 4];
  $even = array_filter($numbers, function($n) {
      return $n % 2 == 0;
  });
  print_r($even); // Output: Array ( [1] => 2 [3] => 4 )
  ?>
  ```

- **`array_map()`**: Apply a callback to each element and return a new array.
  ```php
  <?php
  $numbers = [1, 2, 3];
  $squared = array_map(function($n) {
      return $n * $n;
  }, $numbers);
  print_r($squared); // Output: Array ( [0] => 1 [1] => 4 [2] => 9 )
  ?>
  ```

---

#### 7. Counting and Sizing
- **`count()` or `sizeof()`**: Return the number of elements in an array.
  ```php
  <?php
  $items = [1, 2, 3];
  echo count($items); // Output: 3
  ?>
  ```

- **`array_keys()`**: Return all keys of an array.
  ```php
  <?php
  $data = ["name" => "Bob", "age" => 30];
  $keys = array_keys($data);
  print_r($keys); // Output: Array ( [0] => name [1] => age )
  ?>
  ```

- **`array_values()`**: Return all values of an array (reindexed).
  ```php
  <?php
  $data = ["name" => "Bob", "age" => 30];
  $values = array_values($data);
  print_r($values); // Output: Array ( [0] => Bob [1] => 30 )
  ?>
  ```

---

#### 8. Multidimensional Arrays
- Functions like `array_column()` extract values from a specific key in a multidimensional array.
  ```php
  <?php
  $users = [
      ["id" => 1, "name" => "Alice"],
      ["id" => 2, "name" => "Bob"]
  ];
  $names = array_column($users, "name");
  print_r($names); // Output: Array ( [0] => Alice [1] => Bob )
  ?>
  ```
---

### PHP Array Destructuring
Array destructuring in PHP (introduced in PHP 7.4 with improved syntax) lets you assign array elements to variables directly. It’s a shorthand for extracting values without manually indexing the array.

#### 1. Basic Destructuring
- Use square brackets `[]` or `list()` to unpack array elements into variables.
- Syntax:
  ```php
  [$var1, $var2] = $array; // Modern syntax (PHP 7.4+)
  // OR
  list($var1, $var2) = $array; // Older syntax
  ```

**Example:**
```php
<?php
$coords = [10, 20];
[$x, $y] = $coords;
echo "X: $x, Y: $y"; // Output: X: 10, Y: 20
?>
```

---

#### 2. Skipping Elements
- Use commas to skip elements you don’t want to assign.
- Syntax: `[$var1, , $var3] = $array;`

**Example:**
```php
<?php
$data = [1, 2, 3, 4];
[$a, , $c] = $data;
echo "A: $a, C: $c"; // Output: A: 1, C: 3
?>
```

---

#### 3. Destructuring Associative Arrays
- Use the `=>` operator to target specific keys (PHP 7.4+).
- Syntax: `["key1" => $var1, "key2" => $var2] = $array;`

**Example:**
```php
<?php
$person = ["name" => "Alice", "age" => 25];
["name" => $name, "age" => $age] = $person;
echo "Name: $name, Age: $age"; // Output: Name: Alice, Age: 25
?>
```

---

#### 4. Nested Destructuring
- Destructure multidimensional arrays by nesting the syntax.

**Example:**
```php
<?php
$nested = [1, [2, 3]];
[$a, [$b, $c]] = $nested;
echo "A: $a, B: $b, C: $c"; // Output: A: 1, B: 2, C: 3
?>
```

---

#### 5. Using with Functions
- Destructure return values from functions that return arrays.

**Example:**
```php
<?php
function getInfo() {
    return ["John", 30];
}
[$name, $age] = getInfo();
echo "Name: $name, Age: $age"; // Output: Name: John, Age: 30
?>
```

---

#### 6. Swapping Variables
- Destructuring can swap values without a temporary variable.

**Example:**
```php
<?php
$a = 5;
$b = 10;
[$a, $b] = [$b, $a];
echo "A: $a, B: $b"; // Output: A: 10, B: 5
?>
```

---

#### 7. Variable-Length Destructuring (with `...`)
- Use the splat operator `...` to collect remaining elements into an array (similar to variable-length arguments).

**Example:**
```php
<?php
$numbers = [1, 2, 3, 4, 5];
[$first, $second, ...$rest] = $numbers;
echo "First: $first, Second: $second, Rest: ";
print_r($rest); 
// Output: First: 1, Second: 2, Rest: Array ( [0] => 3 [1] => 4 [2] => 5 )
?>
```
---


### PHP String Functions

PHP provides a rich set of functions to create, modify, search, and format strings. Strings in PHP are sequences of characters enclosed in single (`'`) or double (`"`) quotes.

#### 1. Basic String Operations
- **`strlen()`**: Returns the length of a string.
  ```php
  <?php
  $text = "Hello";
  echo strlen($text); // Output: 5
  ?>
  ```

- **`strtolower()`**: Converts a string to lowercase.
  ```php
  <?php
  $text = "HELLO World";
  echo strtolower($text); // Output: hello world
  ?>
  ```

- **`strtoupper()`**: Converts a string to uppercase.
  ```php
  <?php
  $text = "hello world";
  echo strtoupper($text); // Output: HELLO WORLD
  ?>
  ```

- **`ucfirst()`**: Capitalizes the first character of a string.
  ```php
  <?php
  $text = "hello";
  echo ucfirst($text); // Output: Hello
  ?>
  ```

- **`ucwords()`**: Capitalizes the first character of each word.
  ```php
  <?php
  $text = "hello world";
  echo ucwords($text); // Output: Hello World
  ?>
  ```

---

#### 2. Substring Operations
- **`substr()`**: Extracts a portion of a string.
  - Syntax: `substr($string, $start, $length)` (length is optional).
  ```php
  <?php
  $text = "Hello World";
  echo substr($text, 0, 5); // Output: Hello
  echo substr($text, 6);    // Output: World (from index 6 to end)
  ?>
  ```

- **`strstr()` or `strchr()`**: Finds the first occurrence of a substring and returns the rest of the string.
  ```php
  <?php
  $email = "user@example.com";
  echo strstr($email, "@"); // Output: @example.com
  ?>
  ```

- **`strrchr()`**: Finds the last occurrence of a character and returns the rest of the string.
  ```php
  <?php
  $path = "/home/user/file.txt";
  echo strrchr($path, "/"); // Output: /file.txt
  ?>
  ```

---

#### 3. Searching and Replacing
- **`strpos()`**: Finds the position of the first occurrence of a substring (returns `false` if not found).
  ```php
  <?php
  $text = "Hello World";
  $pos = strpos($text, "World");
  echo $pos; // Output: 6
  if (strpos($text, "PHP") === false) {
      echo "Not found"; // Output: Not found
  }
  ?>
  ```

- **`strrpos()`**: Finds the position of the last occurrence of a substring.
  ```php
  <?php
  $text = "Hello Hello World";
  echo strrpos($text, "Hello"); // Output: 6
  ?>
  ```

- **`str_replace()`**: Replaces all occurrences of a substring with another string.
  ```php
  <?php
  $text = "Hello World";
  echo str_replace("World", "PHP", $text); // Output: Hello PHP
  ?>
  ```

- **`substr_replace()`**: Replaces a portion of a string with another string.
  ```php
  <?php
  $text = "Hello World";
  echo substr_replace($text, "PHP", 6, 5); // Output: Hello PHP
  ?>
  ```

---

#### 4. Trimming
- **`trim()`**: Removes whitespace (or specified characters) from both ends.
  ```php
  <?php
  $text = "  Hello  ";
  echo trim($text); // Output: Hello
  ?>
  ```

- **`ltrim()`**: Removes whitespace (or specified characters) from the left.
  ```php
  <?php
  $text = "  Hello";
  echo ltrim($text); // Output: Hello
  ?>
  ```

- **`rtrim()`**: Removes whitespace (or specified characters) from the right.
  ```php
  <?php
  $text = "Hello  ";
  echo rtrim($text); // Output: Hello
  ?>
  ```

---

#### 5. Splitting and Joining
- **`explode()`**: Splits a string into an array based on a delimiter.
  ```php
  <?php
  $text = "apple,banana,orange";
  $fruits = explode(",", $text);
  print_r($fruits); // Output: Array ( [0] => apple [1] => banana [2] => orange )
  ?>
  ```

- **`implode()` or `join()`**: Joins array elements into a string with a delimiter.
  ```php
  <?php
  $fruits = ["apple", "banana", "orange"];
  echo implode(", ", $fruits); // Output: apple, banana, orange
  ?>
  ```

---

#### 6. Formatting
- **`sprintf()`**: Formats a string with placeholders.
  ```php
  <?php
  $name = "Alice";
  $age = 25;
  echo sprintf("Name: %s, Age: %d", $name, $age); // Output: Name: Alice, Age: 25
  ?>
  ```

- **`number_format()`**: Formats a number with thousands separators and decimal precision.
  ```php
  <?php
  $price = 1234.567;
  echo number_format($price, 2); // Output: 1,234.57
  ?>
  ```

---

#### 7. Comparison
- **`strcmp()`**: Compares two strings (case-sensitive).
  - Returns 0 if equal, negative if first is less, positive if first is greater.
  ```php
  <?php
  echo strcmp("apple", "apple"); // Output: 0
  echo strcmp("apple", "banana"); // Output: -1
  ?>
  ```

- **`strcasecmp()`**: Compares two strings (case-insensitive).
  ```php
  <?php
  echo strcasecmp("Apple", "apple"); // Output: 0
  ?>
  ```

---

#### 8. Miscellaneous
- **`str_repeat()`**: Repeats a string a specified number of times.
  ```php
  <?php
  echo str_repeat("Ha", 3); // Output: HaHaHa
  ?>
  ```

- **`str_pad()`**: Pads a string to a certain length with another string.
  ```php
  <?php
  echo str_pad("Hello", 10, "-"); // Output: Hello-----
  ?>
  ```

- **`wordwrap()`**: Wraps a string to a given number of characters.
  ```php
  <?php
  $text = "This is a long string";
  echo wordwrap($text, 7, "<br>"); 
  // Output: 
  // This is
  // a long
  // string
  ?>
  ```
---

#### Multibyte Example
```php
<?php
$utf8 = "こんにちは"; // Japanese "Hello"
echo mb_strlen($utf8); // Output: 5 (counts characters, not bytes)
?>
```


---

### PHP File Handling
PHP provides built-in functions to work with files: reading, writing, creating, deleting, and more. File operations are essential for tasks like logging, configuration management, or data storage.

#### 1. Opening and Closing Files
- **`fopen()`**: Opens a file or URL and returns a file pointer resource.
  - Modes: `"r"` (read), `"w"` (write, overwrites), `"a"` (append), `"r+"` (read/write), etc.
  ```php
  <?php
  $file = fopen("example.txt", "r");
  // Work with file
  fclose($file); // Always close the file
  ?>
  ```

- **`fclose()`**: Closes an open file pointer.
  ```php
  <?php
  $file = fopen("example.txt", "r");
  fclose($file); // Closes the file
  ?>
  ```

---

#### 2. Reading Files
- **`fread()`**: Reads a specified number of bytes from a file.
  ```php
  <?php
  $file = fopen("example.txt", "r");
  $content = fread($file, filesize("example.txt"));
  echo $content;
  fclose($file);
  ?>
  ```

- **`file_get_contents()`**: Reads the entire file into a string (simpler alternative).
  ```php
  <?php
  $content = file_get_contents("example.txt");
  echo $content;
  ?>
  ```

- **`fgets()`**: Reads a single line from a file.
  ```php
  <?php
  $file = fopen("example.txt", "r");
  while (!feof($file)) {
      echo fgets($file) . "<br>";
  }
  fclose($file);
  ?>
  ```

- **`file()`**: Reads a file into an array, each element being a line.
  ```php
  <?php
  $lines = file("example.txt", FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES);
  print_r($lines);
  ?>
  ```

---

#### 3. Writing to Files
- **`fwrite()` or `fputs()`**: Writes a string to a file.
  ```php
  <?php
  $file = fopen("example.txt", "w");
  fwrite($file, "Hello, World!");
  fclose($file);
  ?>
  ```

- **`file_put_contents()`**: Writes a string to a file (simpler alternative).
  - Overwrites by default; use `FILE_APPEND` to append.
  ```php
  <?php
  file_put_contents("example.txt", "Hello, PHP!");
  // Append
  file_put_contents("example.txt", " More text.", FILE_APPEND);
  ?>
  ```

---

#### 4. Checking File Existence and Properties
- **`file_exists()`**: Checks if a file or directory exists.
  ```php
  <?php
  if (file_exists("example.txt")) {
      echo "File exists!";
  }
  ?>
  ```

- **`filesize()`**: Returns the size of a file in bytes.
  ```php
  <?php
  echo filesize("example.txt"); // Output: Size in bytes
  ?>
  ```

- **`is_readable()` / `is_writable()`**: Checks if a file can be read or written.
  ```php
  <?php
  if (is_readable("example.txt")) {
      echo "File is readable!";
  }
  ?>
  ```

---

#### 5. Deleting and Renaming Files
- **`unlink()`**: Deletes a file.
  ```php
  <?php
  if (file_exists("example.txt")) {
      unlink("example.txt");
      echo "File deleted!";
  }
  ?>
  ```

- **`rename()`**: Renames or moves a file.
  ```php
  <?php
  rename("oldname.txt", "newname.txt");
  ?>
  ```

---

#### 6. Working with Directories
- **`mkdir()`**: Creates a directory.
  ```php
  <?php
  mkdir("new_folder");
  ?>
  ```

- **`rmdir()`**: Removes an empty directory.
  ```php
  <?php
  rmdir("new_folder");
  ?>
  ```

- **`scandir()`**: Lists files and directories in a directory.
  ```php
  <?php
  $files = scandir("."); // Current directory
  print_r($files);
  ?>
  ```

---

#### 7. File Pointer Control
- **`feof()`**: Checks if the end of the file has been reached.
  ```php
  <?php
  $file = fopen("example.txt", "r");
  while (!feof($file)) {
      echo fgets($file);
  }
  fclose($file);
  ?>
  ```

- **`rewind()`**: Moves the file pointer back to the beginning.
  ```php
  <?php
  $file = fopen("example.txt", "r");
  echo fgets($file); // Reads first line
  rewind($file);
  echo fgets($file); // Reads first line again
  fclose($file);
  ?>
  ```

---

#### Example: Complete File Operation
```php
<?php
// Write to a file
file_put_contents("log.txt", "Log entry 1\n");

// Append to the file
file_put_contents("log.txt", "Log entry 2\n", FILE_APPEND);

// Read and display file
if (file_exists("log.txt")) {
    $content = file_get_contents("log.txt");
    echo nl2br($content); // Converts newlines to <br>
    // Output:
    // Log entry 1
    // Log entry 2
}

// Delete the file
unlink("log.txt");
?>
```

---

### PHP File Uploads
PHP allows you to handle file uploads from HTML forms using the `$_FILES` superglobal array. This process involves creating a form, processing the uploaded file on the server, and managing it (e.g., saving, validating).

#### 1. HTML Form Setup
- Use an HTML form with `enctype="multipart/form-data"` and a file input field.
- The `method` must be `"POST"`.

**Example:**
```html
<!DOCTYPE html>
<html>
<body>
    <form action="upload.php" method="post" enctype="multipart/form-data">
        <label for="file">Choose a file:</label>
        <input type="file" name="uploaded_file" id="file">
        <input type="submit" value="Upload">
    </form>
</body>
</html>
```

---

#### 2. Handling the Upload in PHP
- PHP stores uploaded file details in the `$_FILES` superglobal array.
- Keys in `$_FILES` for a file input named `uploaded_file`:
  - `$_FILES["uploaded_file"]["name"]`: Original file name.
  - `$_FILES["uploaded_file"]["type"]`: MIME type (e.g., `image/png`).
  - `$_FILES["uploaded_file"]["size"]`: Size in bytes.
  - `$_FILES["uploaded_file"]["tmp_name"]`: Temporary file path on the server.
  - `$_FILES["uploaded_file"]["error"]`: Error code (0 = success).

**Basic Example (`upload.php`):**
```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    if (isset($_FILES["uploaded_file"]) && $_FILES["uploaded_file"]["error"] == UPLOAD_ERR_OK) {
        $fileTmpPath = $_FILES["uploaded_file"]["tmp_name"];
        $fileName = $_FILES["uploaded_file"]["name"];
        $fileSize = $_FILES["uploaded_file"]["size"];
        $fileType = $_FILES["uploaded_file"]["type"];

        // Destination path
        $uploadDir = "uploads/";
        $destPath = $uploadDir . basename($fileName);

        // Move the file from temporary location to destination
        if (move_uploaded_file($fileTmpPath, $destPath)) {
            echo "File uploaded successfully: $fileName";
        } else {
            echo "Error moving file.";
        }
    } else {
        echo "Upload failed. Error code: " . $_FILES["uploaded_file"]["error"];
    }
}
?>
```

---

#### 3. Key Functions
- **`move_uploaded_file()`**: Moves the uploaded file from its temporary location to a permanent one.
  - Syntax: `move_uploaded_file($tmp_name, $destination)`
  - Returns `true` on success, `false` on failure.

- **`is_uploaded_file()`**: Checks if a file was uploaded via HTTP POST (security check).
  ```php
  <?php
  if (is_uploaded_file($_FILES["uploaded_file"]["tmp_name"])) {
      echo "This is a valid uploaded file.";
  }
  ?>
  ```

- **`pathinfo()`**: Extracts file information (e.g., extension).
  ```php
  <?php
  $fileName = "image.jpg";
  $info = pathinfo($fileName);
  echo $info["extension"]; // Output: jpg
  ?>
  ```

---

#### 4. Validation and Security
- **Check File Size**:
  ```php
  <?php
  $maxSize = 2 * 1024 * 1024; // 2MB in bytes
  if ($_FILES["uploaded_file"]["size"] > $maxSize) {
      die("File too large. Max size is 2MB.");
  }
  ?>
  ```

- **Restrict File Types**:
  ```php
  <?php
  $allowedTypes = ["image/jpeg", "image/png", "application/pdf"];
  if (!in_array($_FILES["uploaded_file"]["type"], $allowedTypes)) {
      die("Invalid file type. Only JPG, PNG, and PDF allowed.");
  }
  ```

- **Sanitize File Names**:
  - Avoid security risks (e.g., overwriting files or path traversal).
  ```php
  <?php
  $fileName = basename($_FILES["uploaded_file"]["name"]); // Removes path info
  $fileName = preg_replace("/[^A-Za-z0-9._-]/", "", $fileName); // Keep only safe characters
  ?>
  ```

- **Unique File Names**:
  - Prevent overwriting existing files.
  ```php
  <?php
  $fileName = uniqid() . "_" . basename($_FILES["uploaded_file"]["name"]);
  $destPath = "uploads/" . $fileName;
  ?>
  ```

---

#### 5. Error Handling
- `$_FILES["uploaded_file"]["error"]` returns an error code:
  - `UPLOAD_ERR_OK` (0): Success.
  - `UPLOAD_ERR_INI_SIZE` (1): File exceeds `upload_max_filesize` in `php.ini`.
  - `UPLOAD_ERR_FORM_SIZE` (2): File exceeds `MAX_FILE_SIZE` in the form.
  - `UPLOAD_ERR_PARTIAL` (3): File only partially uploaded.
  - `UPLOAD_ERR_NO_FILE` (4): No file uploaded.

**Example:**
```php
<?php
$error = $_FILES["uploaded_file"]["error"];
if ($error !== UPLOAD_ERR_OK) {
    switch ($error) {
        case UPLOAD_ERR_INI_SIZE:
            echo "File too large (server limit).";
            break;
        case UPLOAD_ERR_NO_FILE:
            echo "No file uploaded.";
            break;
        default:
            echo "Upload error: $error";
    }
}
?>
```

---

#### 6. Complete Example with Validation
```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    if (isset($_FILES["uploaded_file"]) && $_FILES["uploaded_file"]["error"] == UPLOAD_ERR_OK) {
        $fileTmpPath = $_FILES["uploaded_file"]["tmp_name"];
        $fileName = basename($_FILES["uploaded_file"]["name"]);
        $fileSize = $_FILES["uploaded_file"]["size"];
        $fileType = $_FILES["uploaded_file"]["type"];

        // Validation
        $maxSize = 2 * 1024 * 1024; // 2MB
        $allowedTypes = ["image/jpeg", "image/png"];
        if ($fileSize > $maxSize) {
            die("File too large. Max 2MB.");
        }
        if (!in_array($fileType, $allowedTypes)) {
            die("Only JPG and PNG allowed.");
        }

        // Unique file name
        $uploadDir = "uploads/";
        if (!file_exists($uploadDir)) {
            mkdir($uploadDir, 0777, true); // Create directory if it doesn't exist
        }
        $destPath = $uploadDir . uniqid() . "_" . $fileName;

        // Move file
        if (move_uploaded_file($fileTmpPath, $destPath)) {
            echo "File uploaded successfully: $destPath";
        } else {
            echo "Error uploading file.";
        }
    } else {
        echo "No file uploaded or upload error.";
    }
}
?>
```

---

#### 7. Configuration in `php.ini`
- **`upload_max_filesize`**: Max size of an uploaded file (e.g., `2M`).
- **`post_max_size`**: Max size of POST data (e.g., `8M`).
- **`max_file_uploads`**: Max number of files that can be uploaded at once (e.g., `20`).
- **`file_uploads`**: Must be `On` to enable file uploads.

Check with:
```php
<?php
phpinfo();
?>
```