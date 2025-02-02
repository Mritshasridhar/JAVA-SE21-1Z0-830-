JAVA-SE21-1Z0-830 STUDY MODULE
Table of Contents

About this book
What is OCP?
Why Java 21?
How to use this book
Content
Java basic concepts
OOP
Packages and modules
Handing date, time, text, numeric and boolean values
Use primitives and wrapper classes including Math API, parentheses, type promotion, and casting to evaluate arithmetic and boolean expressions
Var
Primitive types
Operator precedence
Math API
Manipulate text, including text blocks, using String and StringBuilder classes
String and StringBuilder classes
Text Blocks
Manipulate date, time, duration, period, instant and time-zone objects using Date-Time API
Date-Time API
Controlling Program Flow
Create program flow control constructs including if/else, switch statements and expressions, loops, and break and continue statements
Switch statements and expressions
Switch expressions
Pattern Matching for switch
Utilizing Java Object-Oriented Approach
Declare and instantiate Java objects including nested class objects, and explain the object life-cycle including creation, reassigning references, and garbage collection
Create classes and records, and define and use instance and static fields and methods, constructors, and instance and static initializers
Create classes and records
Records
Implement inheritance, including abstract and sealed classes
Sealed classes
Garbage collection
Understand variable scopes, use local variable type inference, apply encapsulation, and make objects immutable
Implement inheritance, including abstract and sealed classes. Override methods, including that of Object class. Implement polymorphism and differentiate object type versus reference type. Perform type casting, identify object types using instanceof operator and pattern matching
Create and use interfaces, identify functional interfaces, and utilize private, static, and default interface methods
Create and use enumerations with fields, methods and constructors
Instanceof operator and pattern matching
Instanceof operator
Pattern matching
Record Patterns
Handling Exceptions
Handle exceptions using try/catch/finally, try-with-resources, and multi-catch blocks, including custom exceptions
Working with Arrays and Collections
Create Java arrays, List, Set, Map, and Deque collections, and add, remove, update, retrieve and sort their elements
SequencedCollection, SequencedSet and SequencedMap.
Working with Streams and Lambda expressions
Use Java object and primitive Streams, including lambda expressions implementing functional interfaces, to supply, filter, map, consume, and sort data
Perform decomposition, concatenation and reduction, and grouping and partitioning on sequential and parallel streams
Packaging and deploying Java code and use the Java Platform Module System
Define modules and their dependencies, expose module content including for reflection. Define services, producers, and consumers
Compile Java code, produce modular and non-modular jars, runtime images, and implement migration using unnamed and automatic modules
Managing concurrent code execution
Virtual threads
Create worker threads using Runnable and Callable, manage the thread lifecycle, including automations provided by different Executor services and concurrent API
Develop thread-safe code, using different locking mechanisms and concurrent API
Process Java collections concurrently including the use of parallel streams
Using Java I/O API
Read and write console and file data using I/O Streams
Serialize and de-serialize Java objects
Create, traverse, read, and write Path objects and their properties using java.nio.file API
Access databases using JDBC
Create connections, create and execute basic, prepared and callable statements, process query results and control transactions using JDBC API
Control transactions using JDBC API
Implementing Localization
Implement localization using locales, resource bundles, parse and format messages, dates, times, and numbers including currency and percentage values
About this book
This book’s primary purpose is to provide a straightforward and convenient way to prepare for the new Oracle exam - 1z0-829. This book assumes that you already have experience with java because the information in some chapters is very concentrated.

What is OCP?
This is professional JAVA certification from Oracle. You can use it as proof of your knowledge to your new employer. There is a lot of controversy about whether it is necessary or not. I believe that certification is necessary. It gives you the possibility to structure your knowledge of java core.

Why Java 21?
Java 21 is LTS release. It stands for Long Time Support version. So, support for this version will continue until the end of 2029. The following Java 24 LTS release will appear in September 2026. Until it, you will have up-to-date certification.

How to use this book
Book has 11 significant chapters. Each chapter corresponds to a specific topic in the Oracle exam. Each topic describes a problem in a maximum compressed format. The topics are loosely connected to study them in any order.

Content
Java basic concepts
OOP
Let’s clarify the main computer concepts, to speak one language.

Problem: it is too hard to write programs in structured languages where an object’s behavior is separated from object logic.

Solution: object-oriented programming. The main idea is very simple. Everything in our universe we could describe as an object with condition and behavior. Each condition variable is a field, each function, that represents object behavior is a method.

In structural programming languages, data is stored within structures, and there are separate functions designed to manipulate this data; however, these functions are not inherently linked to the data they operate on. Conversely, in object-oriented programming (OOP), methods that can operate on data are directly associated with the data itself, as they are encapsulated within the object’s class definition, allowing for a more intuitive understanding of the interactions between data and methods.

Class is a template for objects. It contains a description of fields and methods. Amount of fields and methods depends on your level of abstraction.

Packages and modules
Problem: we need a simple mechanism to store and reuse our and third party classes

Solution: Java has packages.

So, we could store our classes in separate directories. It gives us a possibility to avoid name clashes when we want to use classes with the same names. We can group classes by logic. Let’s look at an example:

package dev.ivanov.math - in this package we could store classes with math functions

In the file system it just directories with such view: /dev/ivanov/math/

package dev.ivanov.math.calculator - in this package we could store classes with our calculator logic

In the file system it just directories with such view: /dev/ivanov/math/calculator

It’s very important to know that there is not any connection between packages, even if they have similar package names.

Problem: We need to import two versions of the same package, to avoid version conflicts. Or we have a library which contains some packages which we want to make completely unavailable for our customers.

Solution: Java has modules.

Unlike packages, modules are a group of packages. So we can unit some packages into modules and use them in our dependencies.

Each module has its own descriptor, that contains such information:

Name - the name of the module

Dependencies - list of other modules on which the module depends

Public packages - list of all the packages that could be accessed from outside the module

Services Offered - list of services that can be consumed by other modules

Services Consumed - allows the current module to be a service consumer

Reflection Permissions - explicitly allows other classes to use reflection to access closed package members

Handing date, time, text, numeric and boolean values
Use primitives and wrapper classes including Math API, parentheses, type promotion, and casting to evaluate arithmetic and boolean expressions
Var
Problem: Variable declarations can be too verbose.

Solution: add var keyword to declare variables.

Just look at the example:

class A{}
class SuperLongClassName extends A{}
void print(){
    SuperLongClassName superLongClassName = getSuperLongClassName();
    System.out.print(superLongClassName);
}
SuperLongClassName getSuperLongClassName(){
    return new SuperLongClassName();
}
At first, the var keyword can make the expression more compact:

var superLongClassName = getSuperLongClassName();
System.out.print(superLongClassName);
And add flexibility to refactoring. Now we can return another expression from the getSuperLongClassName() method and the code inside the print() method won’t need to be changed

void print(){
    var superLongClassName = getSuperLongClassName();
    System.out.print(superLongClassName);
}
A getSuperLongClassName(){
    return new SuperLongClassName();
}
Note! Such a declaration can only be applied within a method and must be initialized immediately:

class SuperLongClassName{
    var classVariable; // doesn't compile
    void print(var parameter){ // doesn't compile
            var localVariable; // doesn't compile
            var superLongClassName = getSuperLongClassName(); // ok
            System.out.print(superLongClassName);
        }
}
At compile time the var turns into the type we need.

Primitive types
Problem: Objects in Java are very heavy

Solution: add primitive types

Everything is an object! You have heard this phrase more than once while learning java.

But 25 years ago, computers had problems. There were not enough memory and computing resources to run large programs. For this reason, the OOP approach won, and the functional approach lost. Creating mutable objects saved memory. But it was not enough. Numbers occur in any program in large quantities. And it was costly to make them as objects with their references. That’s why there are eight types of primitive objects in the java.

Keyword	Type	Minimum value	Maximum value	Default value
boolean

8-bit value (true or false)

-

-

false

byte

8-bit value

-128

127

0

short

16-bit value

-32,768

32,767

0

int

32-bit value

-2,147,483,648

2,147,483,647

0

long

64-bit value

-2^63

2^63 - 1

0L

float

32-bit value

-

-

0.0f

double

64-bit value

-

-

0.0

char

16-bit value

0

65,535

0

The compiler always uses the int and double types if the type is not explicitly specified. This code will not work:

byte i = 10;
int is the basic type in java for integer calculations. Therefore, if you perform operations on different smaller types(byte, short, and char), the compiler will try to convert them to the int type.

If you want to perform operations on different larger types(long, float, and double), you need to explicitly specify the type.

Operator precedence
For the exam, it is essential to know the operator precedence. Just look as closely as possible at this table:

Table 1. Operator precedence
Operator	Symbols and examples
Post-unary operators

expression++, expression--

Pre-unary operators

++expression, --expression

Other unary operators

-, + ,!, ~

Type casting

(type)expression

Multiplication & division

*, /

Division modulo

%

Addition & subtraction

+, -

Shift operations

<<, >>, >>>

Relational operators

<, ⇐, >, >=

Equal & not-equal operators

==, !=

Equal & not-equal operators

==, !=

Bit operators(from high to low)

& → ^ → |

Conditional operators(from high to low)

&& → ||

Ternary operator

boolean expression ? expressionA : expressionB

Assignment operators

=, +=, -=, *=, /=, %=, <<\=, >>=, >>>=, &=, ^=

Tip
The order of the operators is important. Always add parentheses to avoid confusion.
Math API
Math API is very useful for calculations. For exam you need to know the following: Java has min() and max() methods for the int, float, long and double types. Method round():

public static long round(double num)
public static int round(float num)
System.out.println(Math.round(3.5)) // 4
System.out.println(Math.round(3.45)) // 3
For double values we have two additional methods:

public static double ceil(double num)
public static double floor(double num)
Math.ceil(3.14) // 4
Math.floor(3.14) // 3
Math.random() method return a random double value between 0 and 1. But I urge you to use the next methods:

new Random().ints();
new Random().doubles();
this is beautiful method for generating random numbers.

Math class has couple methods to safety work with big numbers:

A BigDecimal is depicted as an arbitrary-precision unscaled integer combined with a 32-bit integer scale. For unscaled values that are non-negative, the scale denotes the count of digits positioned to the right of the decimal point. In the case of negative unscaled values, the represented number is equal to the unscaled value multiplied by 10 to the power of negative scale. For instance, a BigDecimal of 3.14 possesses an unscaled value of 314 and a scale of 2, whereas a BigDecimal of -3.1415 holds an unscaled value of -31415 and a scale of 4.

Big decimal give us possiblity to calculate values more precessely:

double d1 = 0.100;
double d2 = 0.2;
System.out.println(d1 + d2); // 0.30000000000000004

import java.math.BigDecimal;

BigDecimal b1 = new BigDecimal("0.100");
BigDecimal b2 = new BigDecimal("0.2");
System.out.println(b1.add(b2)); //0.300
System.out.println(Integer.MAX_VALUE + 2);                       // Results in overflow: -2147483647
System.out.println(Math.addExact(Integer.MAX_VALUE, 2));         // Throws ArithmeticException due to overflow
System.out.println(Math.addExact(500_000, 2_000));               // 502000, within int range, no overflow

System.out.println(Math.abs(Integer.MIN_VALUE));                // -2147483648
System.out.println(Math.absExact(Integer.MIN_VALUE));           // Throws ArithmeticException due to overflow


System.out.println(Math.toIntExact(Long.MAX_VALUE));         // Throws ArithmeticException due to overflow
System.out.println(Math.floorMod(Integer.MIN_VALUE, -1));   // Throws ArithmeticException due to overflow
Manipulate text, including text blocks, using String and StringBuilder classes
String and StringBuilder classes
String and StringBuilder classes are very useful for manipulating text. String is immutable, while StringBuilder is mutable. String is a sequence of characters.

The String class is used to create and manipulate a sequence of characters. Strings are immutable, which means once a string object is created, its value cannot be changed. If you perform any modification on a string object, a new string object is created with the modified content. This immutability feature makes String safe to use in multithreaded environments but can lead to inefficiency in scenarios where frequent modifications are required because each modification results in the creation of a new string object.

Problem: String class is too slow

Solution 1: Add strings pool Java maintains a special area in the Java heap called the string pool. When a string is created and if the same value already exists in the pool, the new variable will reference the existing string instead of creating a new object. This gives: Memory Efficiency: Reduces the overall memory footprint of an application by avoiding duplicate string objects. Faster Equality Check: When comparing two string literals, if they are from the string pool, you can use == instead of equals() for comparison, which is faster because it compares object references instead of the content.

Dynamically created strings (e.g., through user input or concatenation at runtime) do not automatically benefit from the pool unless explicitly interned using the String.intern() method, which can introduce its own performance overhead.

str1.intern() == str2.intern() // is true only if str1.equals(str1) == true.
💡
Performance Trade-off: The process of interning strings itself can be costly, especially if done frequently. It’s essential to profile the application to ensure that interning provides a net benefit.
Solution 2: Concatenate strings during compilation

“String foo = 1 + "foo";
String bar = "1foo";
if(foo==bar)     // true
Solution 3: Use StringBuilder for dynamic string manipulation For scenarios involving dynamic string manipulations—such as appending, inserting, or deleting characters StringBuilder can yield significant performance improvements. StringBuilder is mutable and designed specifically for such use cases. StringBuilder can modify strings in place without creating new string objects for each modificatin and minimizes the memory overhead by not storing multiple string objects during manipulations.

Strings have some useful methods, lets check them:

We can compare strings

String str1 = "abb";
String str2 = "ad";

int comparision = str1.compareTo(str2);
A value less than 0 if the first string is lexicographically less than the second string. A value of 0 if the first and second strings are equal. A value greater than 0 if the first string is lexicographically greater than the second string.

2. Repeat our string count times

String repeat(int count)
3. replace(char oldChar, char newChar): Replaces all occurrences of a specified character with another character. replace(CharSequence target, CharSequence replacement): Replaces each substring of the string that matches the target sequence with the specified replacement sequence.

4. You can transform any string with the method transform and pass to it a Function.

String message = "Hello, World!";
String reversed = message.transform(s -> new StringBuilder(s).reverse().toString()); // !dlroW ,olleH
5. String format

int age = 30;
String name = "John";
String message = String.format("%s is %d years old.", name, age);
System.out.println(message); // Output: John is 30 years old.
"%s is %d years old.".formatted(name, age); // Output: John is 30 years old.
StringBuilder has a couple of interesting methods:

StringBuilder builder = new StringBuilder("chocolate bar");
builder.delete(9, 13)          // Removes " bar", becomes "chocolate"
.append(" cookies")     // Appends " cookies", becomes "chocolate cookies"
.insert(9, " and")      // Inserts " and", becomes "chocolate and cookies"
.reverse()              // Reverses, becomes "seikooc dna etalocohc"
.deleteCharAt(0)        // Removes 's', becomes "eikooc dna etalocohc"
.replace(0, 2, "c")     // Replaces "ei" with "c", becomes "ckooc dna etalocohc"
.append('s');           // Appends 's', aims for "ckooc dna etalocohcs"
Managing StringBuilder Capacity The methods listed below are unique to the StringBuilder class and allow for the manipulation of various aspects related to the capacity of a StringBuilder:

int capacity() // This method returns the StringBuilder's current capacity, which is the total number of characters it can hold before it needs to allocate a larger character array.

void ensureCapacity(int minCapacity) // This method guarantees that the StringBuilder has the capacity to hold at least a specified number of characters, minCapacity. If necessary, it increases the StringBuilder's capacity based on its current capacity.

void trimToSize() //This method aims to minimize the memory footprint of the StringBuilder by reducing its storage size to fit the actual number of characters it contains. This action may alter the StringBuilder's capacity.

void setLength(int newLength) //This method adjusts the length of the character sequence within the StringBuilder to match the newLength argument, which must not be negative. Depending on whether newLength is less or more than the current length, the method may truncate the sequence or extend it with null characters ('\u0000'). If newLength exceeds the current capacity, this method also increases the capacity of the StringBuilder.
Text Blocks
Problem: it is too hard to write long strings with SQL query or HTML code.

Solution: give users a convenient way to write text blocks without unnecessary string concatenation. You can simply paste snippets of code into strings.

So we can use such strings:

var source = """
    var message = "Hello, World";
    System.out.println(message + '!');
    """;
We don’t need to use escape characters for quotes! But, be careful on the exam, such code wouldn’t compile:

// ERROR
var name = """text""";

// ERROR
var name = """first
second
""";
The position of the last three quotation marks will determine the last character in the sequence if they are right after the characters:

var name = """
first
second
""";
Will be - "first\nsecond\n"

And

var name = """
first
second""";
Will be - "first\nsecond"

If we want to adjust the indentation:

var names = """
first
second""".indent(1);
System.out.println("---");
System.out.println(names);
Output:
---
 first
 second
Manipulate date, time, duration, period, instant and time-zone objects using Date-Time API
Date-Time API
Problem: Every program needs to know the current date and time.

Solution: java new Date-Time API

In the exam, there are always questions on it. The new API that has appeared in java since version 8 makes it very easy to work with time. Here are the basic things you should know about it. We have 4 types of dates:

Table 2. Local Dates
Class name	Features
LocalDate

Date without time and time zone

LocalTime

Time without date and time zone

LocalDateTime

Date and time without time zone

ZonedDateTime

Date and time with time zone

Every class has a convenient static method to get an object with the current date and time: now() We could create an objects with current date and time:

//Most popular methods
static LocalDate of(int year, int month, int day)
static LocalTime of(int hour, int minute, int second)
LocalDateTime of(int year, Month month, int dayOfMonth, int hour, int minute)
LocalDateTime of(LocalDate date, LocalTime time)
ZonedDateTime of(LocalDateTime dateTime, ZoneId zone)
//etc
Problem: It is super hard to add days to a date in previous date-time API.

Solution: In my opinion, the most convenient methods are methods of manipulating dates and times.

Just check the following methods:

var date = LocalDateTime.now().plusDays(1).plusWeeks(2).plusMonths(3).plusYears(4).minusHours(5).minusMinutes(6);
Problem: It is super hard to work with periods and time intervals.

Solution: Period and Duration classes.

Period.ofYears(1); // every year
Period.ofMonths(2); // every two months
Period.ofWeeks(3); // every three weeks
Period.ofDays(4); // every four days
Period.of(1, 2, 3); // every 1 year, 2 months, 3 weeks

var date = LocalDate.now().plus(Period.of(1, 2, 3));
Duration.ofDays(1); // 1 day
Duration.ofHours(1); // every hour
Duration.ofMinutes(2); // every two minutes
Duration.ofSeconds(3); // every three seconds
Duration.of(4, ChronoUnit.SECONDS); // every 4 seconds
Duration.ofMillis(10); // every 10 milliseconds
Duration.ofNanos(10); // every 10 nanoseconds
var dateTime = LocalDateTime.now().plus(Duration.of(1, ChronoUnit.SECONDS));
Problem: sometimes we need to work with time points, for example, when we want to know the time when the next day starts.

Solution: Instant class

Quote from the official documentation:
An instantaneous point on the time-line.
This class models a single instantaneous point on the time-line. This might be used to record event time-stamps in the application.
var time1 = Instant.now();
var time2 = ZonedDateTime.now().toInstant();
var duration = Duration.between(time1, time2);
Controlling Program Flow
Create program flow control constructs including if/else, switch statements and expressions, loops, and break and continue statements
Switch statements and expressions
Switch expressions
Problem: switch blocks effectively replace the expression if-else, but they are very verbose. It’s very likely to forget the BREAK word at the end of an expression. And it couldn’t return values.

Solution: switch expression with lambda look syntax.

Let’s see an example. We want to write a function that returns String with animal sound:

public enum Animal {
    DOG,
    CAT,
    LION,
    BIRD;

    public String getSound(Animal animal) {
        return switch (animal) {
            case CAT, LION -> "Meow";
            case DOG -> "Bark-Bark";
            case BIRD -> "Chick-Chick";
        };
    }
}
You should agree. The expression looks much more compact than the standard switch. We could add default case for unpredictable inputs:

return switch (animal) {
    case CAT -> "Meow";
    case DOG -> "Bark-Bark";
    case BIRD -> "Chick-Chick";
    default -> "Unknown animal";
};
In this case, our switch expression doesn’t cover all possible enum values, so we add a default case, like in the old-fashioned switch. If we want to add more instructions in our lambda, we need to add curvy bracers and a new reserved word yield:

return switch (animal) {
    case CAT -> "Meow";
    case DOG -> "Bark-Bark";
    case BIRD -> {
        System.out.println("It's a Bird!");
        yield "Chick-Chick";
    }
    default -> "Unknown animal";
};
Why don’t we use return? Because return will throw us out of the expression.

Pattern Matching for switch
Pattern Matching for switch supports so-called patterns in case branches, which can be supplemented with conditions using the new 'when' keyword:

Object obj = …
return switch (obj) {
case Integer i when i > 0 -> String.format("positive int %d", i);
case Integer i -> String.format("int %d", i);
case String s -> String.format("String %s", s);
default -> obj.toString();
};
It also allows for null matching, typically achieved through an explicit 'case null' branch. However, if there is no 'case null' branch, a switch statement with null passed to it will invariably throw a NullPointerException, even if a default branch exists. Notably, the 'null' and 'default' branches can be combined.

Object obj = null;
switch (obj) { // NullPointerException
    case String s -> System.out.println("String: " + s);
    default -> System.out.println("Other");
}
String str = …
switch (str) {
    case "Foo", "Bar" -> System.out.println("Foo or Bar");
    case null, default -> System.out.println("Null or other");
}
The new pattern-matching feature in Witch has several limitations:

All switches (except those correct before Java 21) must be exhaustive, meaning the branches should cover all possible cases. For example, this can be resolved by adding an 'Object o' or 'default' branch to the above example.

Object obj = …
switch (obj) { // 'switch' expression does not cover all possible input values
    case String s -> System.out.println(s.length());
    case Integer i -> System.out.println(i);
};
The order of case branches is crucial; no branch should be dominated by another branch preceding it. For instance, since 'CharSequence' is a broader type than 'String', its branch should be placed after the 'String' branch.

return switch (obj) {
    case CharSequence cs -> // more wide
        "sequence of length " + cs.length();
    case String s -> // unreachable
        "string of length " + s.length();
    default -> "other";
 };
Multiple patterns in the same branch are not supported.

return switch (obj) {
    case String s, Integer i -> "str/int";
    default -> "other";
 };
Utilizing Java Object-Oriented Approach
Declare and instantiate Java objects including nested class objects, and explain the object life-cycle including creation, reassigning references, and garbage collection
Classifying Nested Classes:

Static Member Types: These include classes, enum types, record classes, or interfaces that are declared as static. Inner Classes: This category encompasses non-static member classes, local classes, or anonymous classes. Static Local Types: This refers to interfaces, enum types, or record classes that are declared within a static context.

// Defining a top-level class
public class Main {

  // Nested static member class.
  public static class StaticMemberClass {}

  // Nested static member interface.
  public interface StaticMemberInterface {}

  // Nested static member enumeration.
  public enum StaticMemberEnum {}

  // Nested static member record.
  public record StaticMemberRecord() {}

  // Nested non-static (inner) member class.
  public class NonStaticMemberClass {}

  // Method defining local types.
  public void nonStaticMethod() {
    // Local class inside a non-static method.
    class LocalClass {}

    // Static local interface inside a non-static method.
    interface StaticLocalInterface {}

    // Static local enumeration inside a non-static method.
    enum StaticLocalEnum {}

    // Static local record inside a non-static method.
    record StaticLocalRecord() {}
  }

  // Field initialization with an anonymous class derived from StaticMemberClass.
  private StaticMemberClass nonStaticField = new StaticMemberClass() {};

  // Static field initialization with an anonymous class derived from StaticMemberInterface.
  private static StaticMemberInterface staticField = new StaticMemberInterface() {};
}
Static member types, such as classes, enums, record classes, or interfaces, can be defined at the top level or within other nested types. Essentially, a static member type functions similarly to a top-level type. Whether it’s a class, enum, record class, or interface, a static member type supports the same kinds of declarations as its top-level counterparts. When declaring a static member class, the keyword 'static' is used, except in interfaces where it’s understood to be static without explicitly stating so. For static member enums, record classes, and interfaces, they’re inherently static, thus the 'static' keyword is not required.

public class Example {

  // Defines a static member class
  public static class Manager {

    // Static member interface within Manager
    private interface Developer { }

    // Static member class implementing the SkilledDeveloper interface
    public static class FrontendDeveloper implements SkilledDeveloper {

      // Static method within FrontendDeveloper
      public static void displaySimpleName() {
        System.out.println(FrontendDeveloper.class.getSimpleName());
      }

      // Instance method within FrontendDeveloper
      public void showName() {
        System.out.println(this.getClass().getName());
      }
    } // End of FrontendDeveloper class
  } // End of Manager class

  // Static member interface extending Developer from Manager
  interface SkilledDeveloper extends Manager.Developer {

    // Public and static by default within an interface
    class FullStackDeveloper { }
  } // End of SkilledDeveloper interface

  // Non-static member class within Example
  public class MLDev {
    // Static member class within MLDev
    private static class DataScientist { }
  }
}
Let’s see how we can init our classes:

public class OuterClass {
    private int outerValue = 100;

    public class InnerClass {
        private int innerValue;

        public InnerClass(int innerValue) {
            this.innerValue = innerValue;
        }

        public void display() {
            System.out.println("Outer Value: " + outerValue);
            System.out.println("Inner Value: " + innerValue);
        }
    }
    public static class StaticNestedClass {
        private int value;

        public StaticNestedClass(int value) {
            this.value = value;
        }

        public void display(OuterClass outerClass) {
            System.out.println("Value: " + value);
            System.out.println("Outer value: " + outerClass.outerValue);
        }
    }
    public static void main(String[] args) {
        OuterClass outerObject = new OuterClass();
        OuterClass.InnerClass innerObject = outerObject.new InnerClass(11);
        innerObject.display();
        //Outer Value: 100
        //Inner Value: 11

        OuterClass.StaticNestedClass nestedObject = new OuterClass.StaticNestedClass(22);
        nestedObject.display(outerObject);
        //Value: 22
        //Outer value: 100
    }
}
Anonymous classes in Java are a type of inner class without a name and are used to instantiate objects with certain "extras" such as methods and fields that are used for immediate needs.

Create classes and records, and define and use instance and static fields and methods, constructors, and instance and static initializers
Java allows the overloading of constructors, enabling a class to have more than one constructor, each with a different parameter list.

If a class doesn’t explicitly define any constructors, Java automatically provides a default constructor with no parameters. However, if you define any constructor explicitly, Java does not provide the default constructor.

Final fields must be initialized by the time the constructor completes.

Unlike methods, constructors are not inherited.

Create classes and records
Records
Problem: DTO in java has a lot of boilerplate.

Solution: add special data classes to avoid boilerplate code like constructors, getters, etc.

Many developers like Lombok library because it makes such DTOs very compact. But this library has some problems. Users need more robust solutions on the language level.

Let’s see how it looks with records:

public record Point(int x, int y) { }
This short expression gives us a lot of exciting functionality.

We have equals() and hashcode() methods implemented. Also, we have the overloaded method toString() - it prints all variables in the record. We have default constructor Point(int x, int y). And we have getters - x() and y(). Because records were made for DTOs at first, they were made final and immutable. But you can add new constructors, static and non-static methods.

Code

    public record Point(int x, int y) {
        Point() {
            this(0, 0);
        }

        boolean isYPositive() {
            return y >= 0;
        }

        static double dist(Point first, Point second) {
            return sqrt(pow(first.x() - second.x(), 2) + pow(first.y() - second.y(), 2));
        }
    }

    public static void main(String[] args) {
        var myPoint = new Point(1, 9);
        System.out.println(myPoint);
        System.out.println(myPoint.x());
        System.out.println(myPoint.y());
        System.out.println(myPoint.isYPositive());
        System.out.println("Equals\n");
        var myPoint2 = new Point(1, 9);
        System.out.println(myPoint == myPoint2);
        System.out.println(myPoint.equals(myPoint2));
        System.out.println(myPoint.equals(myPoint2));
        System.out.println(dist(myPoint, new Point()));
    }
Will output the following:

Point[x=1, y=9]
1
9
true
Equals

false
true
true
9.055385138137417
Implement inheritance, including abstract and sealed classes
Sealed classes
Problem: Inheritance in Java is not limited.

For example, you have abstract class Animal, and your use it as a base class to build other classes like Dog and Cat. But if someone creates a new class Car and decides to inherit it from Animal, you couldn’t prevent it.

Solution: Sealed classes in Java 17.

Sealed classes enforce rules on inheritance:

public abstract sealed class Animal permits Dog, Cat {}
Now, only two classes can extend our base class. We couldn’t write such code:

public class Lion extends Animal {}
We need to add Lion class explicitly to Animal class signature, or we could get an error:

java: class is not allowed to extend sealed class: dev.ivanov.book.Animal (as it is not listed in its permits clause)
Now, let’s look at Cat and Dog classes. We should mandatorily create them to compile our code.

Because we want to restrict inheritance, we need to foresee a situation where someone wants to inherit from our Cat and Dog classes to get functionality from the parent class. And Java 17 gives us this possibility. When we create Cat or Dog, we need to make these classes final - it prevents any inheritance from this class or mark them also sealed:

public final class Dog extends Animal {}
public sealed class Cat extends Animal permits Lion {}
Only the new Lion class can extend Cat. In this way, we have protected the logic within our Cat class from erroneous inheritance.

In the case where such protection is not needed, and we want to give users unlimited inheritance options, it is worth adding the keyword non-sealed:

public non-sealed class Lion extends Cat {}
Now, class Lion may have any heirs.

It is especially worth noting that you can reduce the signature of a base class by simply putting all its descendants into the same file:

public abstract sealed class Animal {}
final class Bird extends Animal {}
Also, interfaces could be marked sealed:

public sealed interface Animal permits Bird, Cat, Dog {}
final class Bird implements Animal {}
But in this situation, we need explicitly declare all permits.

Garbage collection
Idea: Give the programmer a language tool to manage memory instead of himself.

Solution: Provide a garbage collector system.

In such languages as C, we need to store information about our entities in our memory and write a lot of boilerplate code to free the memory.

Nobody is perfect. So memory leaks are frequent guests in such programs. Java solves this problem with GC, but you must know which CG will help you better.

Your program may run on weak hardware, or your program will work with a large number of objects, or your program needs to be speedy.

You must tweak your GC to achieve the desired performance in all these situations. So let’s start.

How JVM Works With Memory

The JVM divides its memory into two areas: the heap, which stores the application data, and the non-heap, which stores the program code and other data. Let us focus our attention on the heap area. Because precisely in this location, our program creates new objects. (Note: we also can create some records in the non-heap areas. For example, if our program creates new classes on the fly)

All garbage collectors are based on one crucial observation - many programs use short-lived objects. These objects have been created, have fulfilled their function, and are no longer needed. They prevail. Some objects live much longer, perhaps even the entire lifetime of the program.

This is where the idea of dividing objects into the young and old generations comes in. We need very often to check the young generation.

So in accordance with this division, the garbage collection processes are divided into minor GC, which affects only the younger generation, and full GC, which can affect both generations.

CG is a program. And at first, it needs time and your computer resources to function. And it also affects our application.

How?

To perform garbage collection, the JVM pauses our application. So, this is called Stop-The-World (STW) pause.

All application threads are paused at this time. The application inside does not suspect this at all. For the application, time runs evenly.

Why is it so bad? Just imagine you are writing some application for exchange or an application for the plane’s autopilot. Your application could “sleep” for one second, but the context for your problem could change dramatically.

So, this pause is a significant parameter for every GC.

The following fundamental CG property - is the total time spent in garbage collection relative to the total program execution time. What does it mean, and why is this so important?

Instead of one big “stop the world” phase, we can find an algorithm with many small pauses.

Small pauses are preferable, but nothing is free. In this case, we pay for the total execution time of the program. And we also have to take this into account.

The following parameter - is the number of hardware resources. Each CG needs memory to store information about objects and the CPU to perform cleaning.

The last one - Promptness. Promptness in garbage collection refers to how quickly and efficiently a garbage collector (GC) reclaims the memory that is no longer being used by a program.

It is the art of designing an algorithm that can free up memory as fast as possible while consuming minimal resources;

Let’s take a look at the garbage collectors available to us.

You need to know the first five for the interview. The other two are much more difficult.

Serial GC

The Serial GC is a garbage collector in the Java Virtual Machine that has been in use since the early days of Java. It is helpful for programs with tiny heaps and running on less powerful machines.

The garbage collector divides the heap into regions, including the Eden region, where newly created objects are placed. As the heap fills up, objects move between the Eden and Survivor regions.

The JVM constantly monitors how objects move between Survivor regions and choose an appropriate threshold for the number of such moves, after which the objects move to the older generation (Tenured) region.

When there is not enough room in the Tenured region, full garbage collection comes into play, working with objects from both generations.

The main advantage of this garbage collector is its low overhead, and it needs super low CPU resources to perform collection.

The main disadvantage is its long pauses during garbage collection, particularly for larger volumes of data.

Parallel CG

Parallel CG is similar to the sequential builder but includes parallel processing for some tasks and the ability to adjust performance settings automatically.

The Parallel GC is a garbage collector in Java Virtual Machine that builds on the ideas behind the Serial GC but adds parallelism and intelligence. If the computer has more than one processor core, the old JVM automatically chooses Parallel GC (valid for old JSMs).

The heap is divided into the same regions as Serial GC - Eden, Survivor 0, Survivor 1, and Old Gen (Tenured). However, multiple threads are involved in garbage collection in parallel, and the collector can adjust to the required performance parameters.

Each collector thread has a memory area to clean. The Parallel GC also has settings geared towards achieving the garbage collection efficiency required, and the collector uses statistics from previous garbage collections to adjust performance parameters for future collections.

The Parallel GC provides automatic tuning to desired performance parameters and less pause time for build time, and certain memory fragmentation is a minor drawback. It is suitable for most applications, and there are no hidden overheads.

However, for more sophisticated applications, advanced garbage collector implementations are needed.

Pros: In many cases faster than serial. Has good throughput.

Cons: Consumes more resources, and pauses can be very long because we can adjust the maximum stop the world pause.

Concurrent Mark Sweep

Concurrent Mark Sweep (CMS) aims to decrease maximum latency by performing some garbage collection tasks concurrently with the application threads and is suitable for managing large amounts of data in memory.

The Concurrent Mark Sweep (CMS) builder is an alternative to Parallel GC in the Java Virtual Machine (JVM), designed for applications that require access to multiple CPU cores and are sensitive to Stop-The-World pauses.

The CMS builder performs the Mark and Sweep garbage collection steps in parallel with the main program, allowing it to run while it is still running.

It uses the same memory organization as Serial and Parallel GC but does not wait for the Tenured region to fill up before starting the old-gen collection.

Instead, it runs in the background and tries to keep the Tenured region compact.

The CMS builder starts with the initial marking phase, which briefly stops the main threads of the application and marks all objects directly accessible from the roots.

The main application threads then resume work, and CMS starts searching for all live objects accessible via the links from the marked root objects.

After marking all live objects, the collector cleans the memory from the dead objects in several parallel threads.

One of the advantages of CMS is its focus on minimizing downtime, which is critical for many applications. However, this requires sacrificing CPU resources and often total bandwidth.

Additionally, the CMS does not compact objects in the older generation, leading to fragmentation. Long pauses for potential concurrent mode failures can be an unpleasant surprise, although they are not frequent, and CMS manages to avoid them with enough memory.

Pros: Fast. Has small STW pauses.

Cons: it consumes more memory, some pauses could be long, don’t like when the app creates a lot of objects.

Garbage-First

Garbage-First (G1) is intended to replace CMS, particularly for server applications running multiprocessor servers and managing large data sets.

The G1 garbage collector organizes memory into multiple regions of equal size except for huge regions, which are created by merging regular regions to accommodate massive objects. The regions do not have to be organized in a row and may change their generation’s belonging.

Small collections are performed periodically to clean up the younger generation and move objects to Survivor regions or upgrade them to the older generation with a transfer to Tenured.

Cleanup is performed only on the part of the regions to avoid exceeding the desired time, and it chooses to clean those regions with the most garbage ( CG tries to predict such areas).

Complete collections use a marking cycle that runs parallel with the main application to list live objects. After the marking cycle, G1 switches to running mixed collections, which add older generation regions to the set of younger generation regions to be cleaned.

The number of such assemblies is chosen based on statistics about previous assemblies to stay within the required build time.

The G1 garbage collector is considered more accurate than the CMS collector in predicting pause sizes and is better at distributing garbage collections over time to prevent lengthy application stoppages, particularly with large heap sizes.

It also does not fragment memory like the CMS collector.

However, the G1 collector requires more CPU resources to work parallel with the main program, reducing application throughput.

Pros: works better than CMS. Has shorter pauses.

Cons: consumes more CPU. It Consumes more memory in case we have a lot of quite big objects(more than 500kb) because it places such objects into one region (1-32 MB)

Epsilon GC

Epsilon GC is designed for situations where no garbage collection is necessary.

The Epsilon GC does not perform garbage collection. It uses TLABs(thread-local allocation buffers) to allocate new objects - small memory buffers requested by individual threads from the heap. Humongous objects that do not fit in the buffer request memory blocks specifically for them.

When Epsilon GC exhausts resources, an OutOfMemoryError is generated, and the process terminates.

Epsilon GC’s benefits include less overhead costs and faster memory allocation for applications that create all the objects they need at startup or run short-lived applications that don’t use all the memory allocated.

Epsilon GC can also help analyze the overhead that other garbage collectors bring to your application.

Pros: Super fast.

Cons: Doesn’t collect objects :)

The following two collectors are the most advanced of their kind and also the most complex. So we consider them briefly.

ZGC

ZGC aims to maintain pauses at a sub-millisecond level, even when managing huge amounts of data.

ZGC is a garbage collector developed by Oracle for Java that is designed to provide high throughput and low latency while handling large heaps (up to 16TB).

ZGC is based on the principles of virtual memory and uses pointer coloring to track the state of objects during garbage collection.

Pros: Sub-millisecond pauses, even on large heaps, benefit applications requiring short query processing times. It works with very big heaps with good throughput. ZGC can compact the heap memory during garbage collection

Cons: High CPU usage and initial overhead because ZGC has a relatively high initial overhead, which can slow down the startup time of applications.

Shenandoah GC

Shenandoah GC is another garbage collector aiming for short pauses regardless of the heap size.

Shenandoah GC is a low-pause-time garbage collector developed by Red Hat. It is designed to minimize an application’s time to stop its execution during garbage collection.

Like ZGC, it is a concurrent collector, which means it operates while the application is still running, minimizing pauses.

Shenandoah GC uses "forwarding pointers" to move objects during garbage collection. And a technique called "load-barrier elimination" to improve performance.

Pros: pause times. Shenandoah GC can achieve short pause times, often under 10ms, even for massive heaps. Promising throughput.

Cons: high CPU usage and complexity - it has unexpected approaches to working under heavy loads. ==== Implement overloading, including var-arg methods

Understand variable scopes, use local variable type inference, apply encapsulation, and make objects immutable
Implement inheritance, including abstract and sealed classes. Override methods, including that of Object class. Implement polymorphism and differentiate object type versus reference type. Perform type casting, identify object types using instanceof operator and pattern matching
Create and use interfaces, identify functional interfaces, and utilize private, static, and default interface methods
Create and use enumerations with fields, methods and constructors
Instanceof operator and pattern matching
Instanceof operator
The instanceof operator in Java is used to check whether an object is an instance of a specific class or an instance of a subclass of that class.

Object obj = "Hello World";

if (obj instanceof String s) {
    // s is automatically cast to String here
    System.out.println(s.toUpperCase()); // No need for an explicit cast
}
if (obj instanceof CharSequence s) {
    // work with inheritance
    System.out.println(s); // will print Hello World
}
Pattern matching
Problem: using instanceof operator has excess casting Solution: add a more convenient way without an explicit cast

Before java 16, we used such constructions:

if (o instanceof Cat) {
   System.out.println(((Cat) o).getName());
}
But it looks ugly because inside the 'if' statement, we already know the type of 'o'. So, let’s rewrite it:

if (o instanceof Cat cat) {
   System.out.println((cat.getName());
}
We also allowed to instantly use our cat variable inside if statement after 'instanceof' operator:

if (o instanceof Cat cat && cat.getAge() > 5) {
   System.out.println((cat.getName());
}
Record Patterns
Record patterns enable concise record value deconstruction:

record Point(int x, int y) {}

static void print(Object obj) {
    if (obj instanceof Point(int x, int y)) {
       println(x + " " + y);
    }
}
Also achievable through a switch statement:

static void print(Object obj) {
    switch (obj) {
        case Point(int x, int y) -> println(x + " " + y);
        default -> System.out.println("Not a point");
    }
}
Their ability to nest enhances their flexibility:

record Point(int x, int y) {}
enum Color { RED, GREEN, BLUE }
record ColoredPoint(Point p, Color c) {}
record Rectangle(ColoredPoint first, ColoredPoint second) {}

static void print(Rectangle r) {
    if (r instanceof Rectangle(ColoredPoint(Point p, var c), var coloredPoint)) { // We are using var to omit info about class
        println("Current color:" + c);
    }
}
They seamlessly integrate with type-based patterns:

record Point(Object obj) {}

static void test(Point point) {
    switch (point) {
        case Point(String s) -> println("string: " + s);
        case Point(Object o) -> println("other: " + o);
    }
}
They also accommodate generic record type outputs:

Handling Exceptions
Problem: Nobody can write code without errors. To build robust programs, we need to handle these problems.

Solution: To increase program stability, Java has two types of exceptions - runtime and checked - and several methods to handle them.

In Java, a new class of exceptions called “checked exceptions” was introduced. These are exceptions for which the software developer must write code to handle.

As we know, everything in Java is an object, and exception classes are no exception. This allows you to create new exceptions based on existing ones through inheritance.

Let’s take a closer look at the exception class hierarchy. The base class for all types of exceptions is Throwable. Two classes, Error and Exception, inherit from it.

Exceptions described by the Error type are exceptions that, according to the Java specification, should not be handled by the programmer because they are related to problems at the JVM level. These exceptions occur, for example, if the JVM does not find a necessary class in the classpath during the application’s start or if the memory available to the virtual machine runs out.

Exceptions of the Exception type, unlike Error, are designed to be handled by application tools. It is worth mentioning here that the Exception base class refers to checked exceptions.

What is it?

To increase the reliability of applications, the language creators devised a solution: explicitly highlight situations that can potentially and with high probability cause an error. This approach aims to enhance the fault tolerance of applications.

What situations require explicit intervention?

For example, consider data transfer over a network. There’s a high probability that a user may not have a connection. Therefore, you must handle this situation to prevent unexpected program termination.

try/catch/finally: Used for handling exceptions with optional cleanup code in the finally block. • try-with-resources: Used for handling resources that need to be closed automatically. • Multi-catch blocks: Used for catching multiple types of exceptions in a single catch block. • Custom Exceptions: Create specific exception classes to represent different error conditions in your application.

Handle exceptions using try/catch/finally, try-with-resources, and multi-catch blocks, including custom exceptions
Working with Arrays and Collections
Create Java arrays, List, Set, Map, and Deque collections, and add, remove, update, retrieve and sort their elements
SequencedCollection, SequencedSet and SequencedMap.
SequencedCollection is the successor of Collection and is a collection with a set order of elements. Such collections are LinkedHashSet and all implementations of List, SortedSet and Deque. These collections share the property of element sequence, but before Java 21 their common parent was Collection, which is too generic an interface and does not contain many methods specific to sequences (getFirst(), getLast(), addFirst(), addLast(), reversed(), etc.).

interface SequencedCollection<E> extends Collection<E> {
    E getFirst();
    E getLast();
    void addFirst(E);
    void addLast(E);
    E removeFirst();
    E removeLast();
    SequencedCollection<E> reversed();
}
The reversed() method is noteworthy as it provides a view of the collection in the opposite order. This simplifies the process of reversing a collection significantly.

var list = new LinkedList<>(…);

// Before Java 21
for (var it = list.descendingIterator(); it.hasNext();) {
    var e = it.next();
}

// After Java 21
for (var element : list.reversed()) {
    …
}
The SequencedSet interface, designed for sequenced sets:

interface SequencedSet<E> extends Set<E>, SequencedCollection<E> {
SequencedSet<E> reversed();
}
This interface is implemented by the successors of LinkedHashSet and SortedSet.

The SequencedMap interface:

interface SequencedSet<E> extends Set<E>, SequencedCollection<E> {
SequencedSet<E> reversed();
}
SequencedMap interface:

interface SequencedMap<K,V> extends Map<K,V> {
    Entry<K, V> firstEntry();
    Entry<K, V> lastEntry();
    Entry<K, V> pollFirstEntry();
    Entry<K, V> pollLastEntry();
    V putFirst(K, V);
    V putLast(K, V);
    SequencedSet<K> sequencedKeySet();
    SequencedCollection<V> sequencedValues();
    SequencedSet<Entry<K,V>> sequencedEntrySet();
    SequencedMap<K,V> reversed();
}
Working with Streams and Lambda expressions
Use Java object and primitive Streams, including lambda expressions implementing functional interfaces, to supply, filter, map, consume, and sort data
Perform decomposition, concatenation and reduction, and grouping and partitioning on sequential and parallel streams
Packaging and deploying Java code and use the Java Platform Module System
Define modules and their dependencies, expose module content including for reflection. Define services, producers, and consumers
Compile Java code, produce modular and non-modular jars, runtime images, and implement migration using unnamed and automatic modules
Managing concurrent code execution
Virtual threads
Problem: Creating a new thread is very expensive, forcing developers to employ various strategies—such as thread pools and reactive programming—to effectively utilize existing threads.

Solution: Virtual threads.

Virtual threads are designed to be lightweight, enabling the creation of vast quantities (up to millions) of instances. This feature simplifies the development of efficient programs by allowing a straightforward "one request - one thread" or "one task - one thread" model, eliminating the need for intricate asynchronous or reactive programming techniques. Additionally, transitioning existing code to virtual threads is intended to be straightforward. Since virtual threads are instances of the current java.lang.Thread class, they maintain high compatibility with traditional threads, including support for stack traces, the interrupt() method, ThreadLocal, and more.

Virtual threads operate atop standard threads and are recognized only by the Java Virtual Machine (JVM), not by the operating system, which is why they are termed "virtual." The physical thread that a virtual thread runs on is referred to as the host thread. Unlike platform threads that depend on the operating system’s scheduler, virtual threads are managed by the ForkJoinPool scheduler. When a virtual thread engages in a blocking operation, it detaches from its host thread. This detachment allows the host thread to take on another virtual thread and proceed with execution. This mechanism, coupled with the low cost of managing virtual threads, greatly enhances their scalability. However, there are currently two notable exceptions: synchronized blocks and Java Native Interface (JNI) operations. In these cases, a virtual thread cannot detach from its host thread due to its binding, which may affect scalability. To fully leverage virtual threads, it is advisable to minimize the use of synchronized blocks and JNI operations, especially those that are executed frequently or have lengthy durations.

While virtual threads present an appealing option, it’s not always necessary to choose them over traditional threads. For instance, traditional threads are more appropriate for CPU-bound tasks. Additionally, if your requirement is for a non-daemon thread, you would need to opt for a traditional thread since virtual threads are inherently daemon threads.

To facilitate the creation and management of virtual threads, the following API has been introduced:

Thread.Builder: This serves as a thread builder. For instance, you can create a virtual thread by using the Thread.ofVirtual().name("name").unstarted(runnable) method. Thread.startVirtualThread(Runnable): This method allows for the creation and immediate start of a virtual thread. Thread.isVirtual(): This method is used to determine whether a thread is virtual. Executors.newVirtualThreadPerTaskExecutor(): This returns an executor that creates a new virtual thread for each task. Additionally, support for virtual threads has been incorporated into the JDK toolkit, enhancing tools such as the debugger, JVM TI, and Java Flight Recorder.

Example:

    try(var ex = Executors.newVirtualThreadPerTaskExecutor()){
        ex.execute(() -> System.out.println("Running " + Thread.currentThread().isVirtual()));
    }
Create worker threads using Runnable and Callable, manage the thread lifecycle, including automations provided by different Executor services and concurrent API
Develop thread-safe code, using different locking mechanisms and concurrent API
Process Java collections concurrently including the use of parallel streams
Using Java I/O API
Read and write console and file data using I/O Streams
Serialize and de-serialize Java objects
Create, traverse, read, and write Path objects and their properties using java.nio.file API
Access databases using JDBC
Create connections, create and execute basic, prepared and callable statements, process query results and control transactions using JDBC API
Control transactions using JDBC API
Implementing Localization
Implement localization using locales, resource bundles, parse and format messages, dates, times, and numbers including currency and percentage values
(c) Roman Ivanov



