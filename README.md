# Ejercicios-TDD
--------------------------------------------------------------------------------
Ejercicio Cedula:
fun main() {
    testFunction()
    testFunctionFailed()
}

fun validateCedula(cedula: String): Boolean {
    if (cedula.length != 10 || !cedula.matches(Regex("\\d{10}"))) {
        return false
    }

    val digits = cedula.substring(0, 9).map { it.toString().toInt() }
    val factors = listOf(2, 1, 2, 1, 2, 1, 2, 1, 2)
    var sum = 0

    for (i in 0 until digits.size) {
        var result = digits[i] * factors[i]
        if (result >= 10) {
            result = result / 10 + result % 10
        }
        sum += result
    }

    val remainder = sum % 10
    val expectedDigit = if (remainder == 0) 0 else 10 - remainder
    val lastDigit = cedula[9].toString().toInt()

    return expectedDigit == lastDigit
}

fun testFunction() {
    val actualValue = validateCedula("1712345670")
    val expectedValue = true
    
    if (actualValue == expectedValue) {
        println("Success")
    } else {
        println("Failed")
    }
}

fun testFunctionFailed() {
    val actualValue = validateCedula("1712345671")
    val expectedValue = false
    
    if (actualValue == expectedValue) {
        println("Success")
    } else {
        println("Failed")
    }
}
--------------------------------------------------------------
Ejercicio placa

fun main() {
    testFunction()
    testFunctionFailed()
}

fun validateVehicle(plate: String): Boolean {
    val regex = Regex("[A-Z]{3}\\d{4}")
    return regex.matches(plate)
}

fun testFunction() {
    val plate = "AAA1234"
    val expectedValue = true 
    
    val actualValue = validateVehicle(plate)
    
    if (actualValue == expectedValue)
        println("Success")
    else 
        println("Failed")
}
fun testFunctionFailed() {
    val plate = "AAD123" // Placa con formato incorrecto
    val expectedValue = false
    
    val actualValue = validateVehicle(plate)
    
    if (actualValue == expectedValue)
        println("Success")
    else 
        println("Failed")
}

