
# Kotlin Cheat Sheet (Enhanced Version)

## 1. Basic Syntax

```kotlin
fun main() {
    println("Hello, World!")  // Prints a message
}
```

### Variable Declaration:

```kotlin
val name = "Taiyo"  // Immutable (can't change)
var age = 25        // Mutable (can change)
age = 26            // Valid for `var`
```

### Data Types:

```kotlin
val num: Int = 10
val pi: Double = 3.14
val isKotlinFun: Boolean = true
val letter: Char = 'K'
val name: String = "Kotlin"
```

---

## 2. Control Flow

### If-Else:

```kotlin
val a = 10
val b = 20
val max = if (a > b) a else b
println("Maximum: $max")
```

### When:

```kotlin
val x = 3
when (x) {
    1 -> println("One")
    2 -> println("Two")
    in 3..5 -> println("Three to Five")
    else -> println("Other")
}
```

### Loops:

#### For Loop:

```kotlin
for (i in 1..5) {
    println("Number: $i")
}

for (i in 5 downTo 1 step 2) {
    println("Step: $i")
}
```

#### While Loop:

```kotlin
var i = 5
while (i > 0) {
    println(i--)
}
```

---

## 3. Functions

### Regular Function:

```kotlin
fun multiply(a: Int, b: Int): Int {
    return a * b
}
```

### Single-Expression Function:

```kotlin
fun greet(name: String) = "Hello, $name!"
println(greet("Taiyo"))
```

### Default Arguments:

```kotlin
fun printInfo(name: String = "Anonymous", age: Int = 0) {
    println("Name: $name, Age: $age")
}
printInfo("Taiyo", 25)
printInfo()  // Uses default values
```

### Named Arguments:

```kotlin
printInfo(age = 30, name = "Kotlin")
```

---

## 4. Classes and Objects

### Primary Constructor with Properties:

```kotlin
class Person(val name: String, var age: Int) {
    fun introduce() {
        println("Hi, I'm $name, and I'm $age years old.")
    }
}
```

### Secondary Constructor:

```kotlin
class Student(val name: String) {
    var grade: String = "Unknown"

    constructor(name: String, grade: String) : this(name) {
        this.grade = grade
    }
}
```

### Object Creation:

```kotlin
fun main() {
    val person = Person("Taiyo", 25)
    person.introduce()

    val student = Student("Saitama", "A")
    println("${student.name}'s grade is ${student.grade}")
}
```

---

## 5. Collections

### Lists:

```kotlin
val immutableList = listOf("Apple", "Banana", "Cherry")
val mutableList = mutableListOf("Dog", "Cat")

mutableList.add("Parrot")
println(mutableList)
```

### Maps:

```kotlin
val immutableMap = mapOf("name" to "Taiyo", "age" to 25)
val mutableMap = mutableMapOf("language" to "Kotlin")

mutableMap["level"] = "Advanced"
println(mutableMap)
```

### Sets:

```kotlin
val set = setOf(1, 2, 3, 3)  // No duplicates
println(set)
```

---

## 6. Null Safety

```kotlin
var name: String? = null  // Nullable
println(name?.length ?: "Name is null")  // Elvis operator
```

---

## 7. Extension Functions

```kotlin
fun String.addExclamation() = this + "!"
println("Kotlin".addExclamation())
```

---

## 8. Higher-Order Functions

```kotlin
fun operate(x: Int, y: Int, operation: (Int, Int) -> Int): Int {
    return operation(x, y)
}
val result = operate(5, 3) { a, b -> a + b }
println(result)
```

---

## 9. Coroutines

### Simple Coroutine:

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

### Parallel Execution:

```kotlin
fun main() = runBlocking {
    val job1 = async { task1() }
    val job2 = async { task2() }

    println("Result: ${job1.await() + job2.await()}")
}

suspend fun task1(): Int {
    delay(1000L)
    return 10
}

suspend fun task2(): Int {
    delay(1000L)
    return 20
}
```

---

## 10. Data Classes

```kotlin
data class User(val name: String, val age: Int)

fun main() {
    val user = User("Taiyo", 25)
    println(user)
}
```

---

## 11. Lambda Expressions

```kotlin
val square = { x: Int -> x * x }
println(square(4))
```

---

