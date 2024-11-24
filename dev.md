# Initialization: 

<link rel="stylesheet" href="/home/nathan/dev/dino.css">

```java
public class main{
    public static void main(String []args){
        System.out.println("Hello World");
    }
```
==Replace== main with whatever the file is, eg, someshit.java `public class someshit`, (__NOTE: It Is Case Sensitive__)

---

# 1) Tf Does `static` even do?  {#static}

- It states that "__this belongs to the class rather than any instance of the class.__"  
- It is __shared across all instance of classes.__

__Shared Instance:__ {#shared-instance}
```java
class example {
    static int counter = 0;

    example(){
        counter ++;
    }
}

public class main {
    public static void main(String []args){
        example obj1 = new example();
        example obj2 = new example();
        System.out.println(obj2.counter); // Prints 2
    }
}
```

__Allows a method to be called without an object:__ {#objlmc}
```java
class example { // Becomes default class example, if no access modifier is mentioned, default is implicit
    static int counter = 0;

    example(){
        counter ++;
    }
    static int add(int a, int b){
        return a+b;
    }
}

public class main {
    public static void main(String []args){
        System.out.println(example.add(1,2)); // Prints 3
    }
}
```
---

# 2. Function imports from Other File?
> For A Directory Structure   
├── another   
│   ├── other.class  
│   └── other.java  
├── main.class  
└── main.java  

```java
// main.java
import another.other;
public class main {
    public static void main(String[] args){
        System.out.println(other.add(1,2)); // Prints 3
;
    }
}

```

```java
// another/other.java
package another;
public class other {
    public static int add(int a, int b){
        return a+b;
    }
}
```
---

# 3. toString() 
> It is a method that the compiler automatically generates, that is used to display the structure of a class.
by default, it outputs the `classname@_itsHash_`
```java
// Signature:
public String toString(){
    return "..."
}
```
```java
class someclass {
    String name;
    int age;

    someclass(){
        this.name = "someone" ;
        this.age = 69; // lol.
    }
    
}
public class main {
    public static void main(String[] args){
        someclass someobj = new someclass();
        System.out.println(someobj); // prints someclass@2a139a55 , (implicitly calls .toString())
        System.out.println(someobj.toString()); // prints someclass@2a139a55 
    }
}
```
> Printing an object implicitly calls the .toString() method. Think of it as the stringer interface in golang.
This behaviour can be overridden, which is where it shines. 

``` java
class someclass {
    String name;
    int age;

    someclass(){
        this.name = "someone" ;
        this.age = 69; // lol.
    }

    @Override
    public String toString() {
        // return "Name: " + name + ", Age: " + age;
        return "Type shit";
    }
    
}
public class main {
    public static void main(String[] args){
        someclass someobj = new someclass();
        System.out.println(someobj); // Outputs: Type shit
        System.out.println(someobj.toString()); // Outputs: Type shit 
    }
}
```
---

# 4. Ternary Operators 


> Yes, turns out java with its weird long ass syntax atleast supports this. Its the same old.

```java
public class main {
    public static void main(String[] args){
        int age = 18;
        String result = (age >= 18) ? "Adult" : "Minor";
        System.out.println(result); 
    }
}
```
---


# 5. Taking User Input

So to take user input we need the `Scanner` thingy.

```c
import java.util.Scanner;
public class main{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("enter 2 numbers: ");
        int a = scanner.nextInt();
        int b = scanner.nextInt();
        System.out.println(a+b);
        scanner.close();
    }
}
```

Other things we can use:
| Method                 | Description                                         | Example Usage                  |
|------------------------|-----------------------------------------------------|--------------------------------|
| `nextInt()`            | Reads the next token as an integer.                 | `int a = scanner.nextInt();`  |
| `nextDouble()`         | Reads the next token as a double.                   | `double d = scanner.nextDouble();` |
| `nextLine()`           | Reads the entire line of input as a `String`.       | `String line = scanner.nextLine();` |
| `next()`               | Reads the next token as a `String` (up to a space). | `String word = scanner.next();` |
| `nextBoolean()`        | Reads the next token as a boolean.                  | `boolean b = scanner.nextBoolean();` |
| `nextLong()`           | Reads the next token as a long integer.             | `long l = scanner.nextLong();` |
| `nextFloat()`          | Reads the next token as a float.                    | `float f = scanner.nextFloat();` |
| `hasNext()`            | Checks if there is another token in the input.      | `if (scanner.hasNext()) { ... }` |
| `hasNextInt()`         | Checks if the next token can be interpreted as an int. | `if (scanner.hasNextInt()) { ... }` |
| `hasNextDouble()`      | Checks if the next token can be interpreted as a double. | `if (scanner.hasNextDouble()) { ... }` |
| `close()`              | Closes the scanner (releases resources).            | `scanner.close();`            |

