# Kotlin: A Beginner’s Complete Guide

## **What is Kotlin?**
Kotlin is a modern, statically-typed programming language developed by JetBrains. It is fully interoperable with Java and runs on the JVM (Java Virtual Machine). It is widely used for Android development, backend development, and more.

---

## **1. Basic Syntax**

### Variables
```kotlin
// Immutable (val) and mutable (var)
val name: String = "John" // Read-only
var age: Int = 25         // Mutable

// Type inference
val city = "New York"
var score = 100
```

### Functions
```kotlin
// Basic function
fun greet(): String {
    return "Hello, World!"
}

// Single-expression function
fun square(x: Int) = x * x

// Function with default arguments
fun printMessage(message: String = "Hi") {
    println(message)
}
```

### Control Flow
```kotlin
// If-else as an expression
val max = if (a > b) a else b

// When (like switch in Java)
when (x) {
    1 -> println("One")
    2 -> println("Two")
    else -> println("Other")
}

// Loops
for (i in 1..5) { // Range
    println(i)
}

while (x > 0) {
    println(x)
    x--
}
```

---

## **2. Classes and Objects**

### Defining a Class
```kotlin
class Person(val name: String, var age: Int) {
    fun introduce() {
        println("Hi, I am $name and I am $age years old.")
    }
}

val john = Person("John", 25)
john.introduce()
```

### Inheritance
```kotlin
open class Animal {
    open fun sound() {
        println("Some generic sound")
    }
}

class Dog : Animal() {
    override fun sound() {
        println("Bark")
    }
}

val dog = Dog()
dog.sound()
```

---

## **3. Null Safety**
```kotlin
var nullableName: String? = null

// Safe call
println(nullableName?.length)

// Elvis operator
val length = nullableName?.length ?: 0

// Non-null assertion
println(nullableName!!.length) // Throws exception if null
```

---

## **4. Collections**

### Lists
```kotlin
val items = listOf("apple", "banana", "cherry") // Immutable
val mutableItems = mutableListOf("apple", "banana") // Mutable
mutableItems.add("cherry")
```

### Maps
```kotlin
val map = mapOf(1 to "one", 2 to "two") // Immutable
val mutableMap = mutableMapOf(1 to "one") // Mutable
mutableMap[2] = "two"
```

### Filtering and Mapping
```kotlin
val numbers = listOf(1, 2, 3, 4, 5)
val evenNumbers = numbers.filter { it % 2 == 0 }
val squaredNumbers = numbers.map { it * it }
```

---

## **5. Higher-Order Functions**
```kotlin
fun calculate(x: Int, y: Int, operation: (Int, Int) -> Int): Int {
    return operation(x, y)
}

val sum = calculate(5, 3) { a, b -> a + b }
println(sum) // Output: 8
```

---

## **6. Coroutines (Asynchronous Programming)**
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("World!")
    }
    println("Hello,")
}
```

---

## **7. Interoperability with Java**
```kotlin
// Calling Java from Kotlin
val list = ArrayList<String>()
list.add("Kotlin")

// Calling Kotlin from Java
public class Main {
    public static void main(String[] args) {
        Person person = new Person("John", 25);
        person.introduce();
    }
}
```

---

## **8. Extensions**
```kotlin
fun String.capitalizeFirst(): String {
    return this.replaceFirstChar { it.uppercase() }
}

println("kotlin".capitalizeFirst()) // Output: Kotlin
```

---

## **9. DSLs (Domain Specific Languages)**
Kotlin’s concise syntax is ideal for building DSLs.
```kotlin
fun html(block: Tag.() -> Unit): Tag {
    val tag = Tag("html")
    tag.block()
    return tag
}

class Tag(val name: String) {
    private val children = mutableListOf<Tag>()
    fun tag(name: String, block: Tag.() -> Unit) {
        val child = Tag(name)
        child.block()
        children.add(child)
    }
}

html {
    tag("head") {}
    tag("body") {
        tag("h1") {}
    }
}
```

---

## **10. Resources to Learn More**
- [Official Kotlin Documentation](https://kotlinlang.org/docs/home.html)
- [Kotlin Playground](https://play.kotlinlang.org/)
- [JetBrains Academy](https://www.jetbrains.com/academy/)

---

Dive into coding and enjoy Kotlin!
