## QUESTION ONE: The Difference between Enums and Sealed Classes
**Enums** are represent a constant set of possible options or a concrete set of constant values hold values that are always item-specific.The power of enum is that those items are specific and constant. Therefore we can get all the items using values() function, or by type using enumValueOf function. We can also read enum from String using valueOf(String) or by type using enumValueOf, therefore iterating over enum values is easy. It is most convenient to define an extension function:

```kotlin
import java.math.BigDecimal
//Enum Declaration


enum class carChoices {
    TOYOTA,
    HONDA,
    CHEVROLET;

    var fee: BigDecimal = BigDecimal.ZERO
}

fun carChoices.checkFee(transaction: TransactionData) {
    when (this) {
        carChoices.HONDA -> showCarChoiceInfo(transaction)
        carChoices.TOYOTA -> moveToToyotaChoicePage(transaction)
        carChoices.CHEVROLET -> {
            showCarChangeRequest()
            setupFeeCheck(transaction)
        }
    }
}
```
**Sealed Classes** are abstract classes with a concrete number of subclasses all defined. The advantage of sealed classes over enum is that subclasses can hold instance-specific data. Each item can be either a class or an object (created using the object declaration). What sealed modifier does is that it is impossible to define another subclass of this class outside of the file.

```kotlin
import java.math.BigDecimal

//Sealed class 


sealed class CarRental
data class RentToyota(val fee: BigDecimal, val rentalId: Int): CarRental()
data class RentBenz(val fee: BigDecimal, val rentalId: Int, ): CarRental()
data class RentAcura(val fee: BigDecimal, val rentalId: Int): CarRental()

fun process(rental: CarRental) {
    val rentalReceipt = when (rental) {
        is RentToyota -> {
            println("Renting Toyota")
        }
        is RentBenz -> {
            println("Renting Benz")
        }
        is RentAcura -> {
            println("Renting Acura")
        }
    }
    println(rentalReceipt)
}
```
## QUESTION 2: Why is Kotlin interoperable with Java?

**Interoperability** means files in both languages can be used together in same application since they can call functions from each other. This is as a result of how Java codes and Kotlin codes are handled at run time. This takes place in two parts; The compile time and the run time. The compiler converts the java file with java codes into byte codes in the .class file which is accessible by any jvm which originally makes java a “WORA” language. In Kotlin, the kotlin compiler converts the kotlin “.kt” file containing kotlin codes into a “.class” file containing byte codes. At this point, both the Java and Kotlin codes have been converted to byte codes and the JVM executes both at runtime, Viola!


## QUESTION 3: Difference between procedural and object oriented programming?

**Procedural Programming** takes on applications by solving problems *from the top of the code down to the bottom*. This happens when a program starts with a problem and then breaks that problem down into smaller sub-problems or sub-procedures. While **Object-oriented Programming** uses *classes and objects*, which can be *instanciated and their functions called at any point in the program*, from any part of the code structure.
