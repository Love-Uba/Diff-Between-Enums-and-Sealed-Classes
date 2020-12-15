Lazy: 
This entails deferring of a variable initialization till a later time, meaning you do not need to create the object until you need it and the object will only be created when its called. Since this is declared using val and initialization Is done at most once when it is called, it is suitable when you need a single instance of a variable repeatedly accessed but not changed.

```
class SeaObjectsClass {

//some cases may not require this object of the class

private val seaAntiques: SeaAntiquesClass by lazy {
        println(“Sea antiques has been activated“)
        HeavyClass()
    } 
//a function is made to access the object of the lazy function
Fun getStuff(){
		println(seaAntiques)
		}
}
//at this point the item is initialized and created
fun main(args: Array<String>) {
    val seaObjectClass = SeaObjectClass()
    println(“SeaObjectClass is now initialized")
    seaObjectClass.accessObject()
```

LateInit:  This means the variable is not initialized at the time of declaration, but when its usage or access is required; these variables are created using var, yet a default value is not assigned since it can be modified and a nullable type isn’t used to make it non-nullable. This makes it the most suitable to use a late init modifier telling the compiler the variable will be initialized later in the program, which after being initialized can be be used. At the point of usage, the variable should then be initialized and referred to from within its class. This can be used when there are dependencies on frame works that needs to be supplied later in the program.


```kotlin
private lateinit var plateNumber: String

// demo function to get carDetails name using the plateNumberscanner

fun fetchCarDetails(plateNumber: String) {
    plateNumber = carRegistrationRepository.getPlateNumber(plateNumber)
    //  at this point, the variable is initialized when called in the function
}
```

Val: This is the immutable declaration of an item; with access to read only and not to be edited or reassigned, hence the Value cannot be changed.

```kotlin
val myAge = 45

myName += 1  //won’t work since variables declared with val cannot be reassigned
``` 

Var: This is a mutable variable declaration command, which can be changed, incremented and reassigned with new values.

```kotlin
var myAge = 45

//one year later...

MyAge += 1
```

//value of my age is incremented by one and a new value is reassigned

println(myAge) //outputs 46

