Enums are represent a constant set of possible options or a concrete set of constant values 
hold values that are always item-specific.The power of enum is that those items are specific 
and constant. Therefore we can get all the items using values() function, or by type using 
enumValueOf function.
We can also read enum from String using valueOf(String), or by type using enumValueOf, 
therefore iterating over enum values is easy.
It is most convenient to define an extension function,

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
//in the main function
fun main() {
    val car1 = carChoices.HONDA
    val car2 = carChoices.TOYOTA
    print(car1 == car2) // This is TRUE, because it is the same object

    car1.fee = BigDecimal.TEN
    print(car2.fee) // 10

    val total = carChoices.CHEVROLET
    print(total.fee) // 0, because `fee` is per-item
}


Sealed Classes are abstract classes with a concrete number of subclasses all defined.
The advantage of sealed classes over enum is that subclasses can hold instance-specific data
Each item can be either a class or an object (created using the object declaration).
What sealed modifier does is that it is impossible to define another subclass of this class 
outside of the file.

import java.math.BigDecimal
//Sealed class 
sealed class CarRental
data class RentToyota(val fee: BigDecimal, val rentalId: Int): CarRental()
data class RentBenz(val fee: BigDecimal, val rentalId: Int, ): CarRental()
data class RentAcura(val fee: BigDecimal, val rentalId: Int): CarRental()

fun process(rental: CarRental) {
    val rentalReceipt = when (rental) {
        is RentToyota -> {
            showCarInfo(rental.fee, rental.rentalId)
        }
        is RentBenz -> {
            showCarInfo(rental.fee, rental.rentalId)
        }
        is RentAcura -> {
            showCarInfo(rental.fee, rental.rentalId)
        }
    }
    println(rentalReceipt)
}
