// Main.kt - Kotlin basics demo

// Lớp Dice (có tham số numSides, phương thức roll trả Int ngẫu nhiên)
class Dice(val numSides: Int = 6) {
    fun roll(): Int = (1..numSides).random()
}

// Hàm không có đối số (in lời chào)
fun printHello() {
    println("Hello Kotlin")
}

// Hàm có đối số, có giá trị mặc định
fun printBorder(border: String = "=", timesToRepeat: Int = 23) {
    repeat(timesToRepeat) { print(border) }
    println()
}

// Hàm dùng lồng repeat() để in "đáy bánh"
fun printCakeBottom(age: Int, layers: Int) {
    repeat(layers) {
        repeat(age + 2) { print("@") }
        println()
    }
}

// Hàm trả về chuỗi dựa trên kết quả roll
fun messageForRoll(rollResult: Int): String {
    val luckyNumber = 6
    return when (rollResult) {
        luckyNumber -> "You won!"
        1 -> "So sorry! You rolled a 1. Try again!"
        2 -> "Sadly, you rolled a 2. Try again!"
        3 -> "Unfortunately, you rolled a 3. Try again!"
        4 -> "No luck! You rolled a 4. Try again!"
        5 -> "Don't cry! You rolled a 5. Try again!"
        else -> "Hmm... strange value."
    }
}

// Điểm vào chương trình
fun main() {
    println("Hello, world!")                       // in 1 dòng
    println("This is the text to print!")         // in 1 dòng khác

    // Nhận xét (comments)
    // This is a comment line.
    // This is another comment.

    // Biến: val (không thay đổi), var (có thể thay đổi)
    val age = 5               // Int
    val name = "Rover"        // String
    var roll = 6              // inferred Int
  
    var rolledValue: Int = 4  // explicit type

    // String templates
    println("You are already ${age}!")
    println("You are already ${age} days old, ${name}!")

    // Gọi hàm
    printHello()
    printBorder()             // dùng giá trị mặc định

    // Tạo object từ lớp Dice
    val dice = Dice(6)
    val diceRange = 1..6
    val randomNumber = diceRange.random()
    println("Random from diceRange: $randomNumber")

    // lặp
    repeat(3) { idx ->
        println("Repeating #${idx + 1}")
    }

    // In phần đáy "bánh" dùng lồng repeat
    printCakeBottom(age = 3, layers = 2)

    // Demo roll nhiều lần
    repeat(5) { i ->
        val r = dice.roll()
        println("Roll ${i + 1}: $r -> ${messageForRoll(r)}")
    }

    // Ví dụ đọc input (chú ý: Kotlin Playground có thể không hỗ trợ interactive input)
    // println("Enter your age:")
    // val input = readLine()
    // val enteredAge = input?.toIntOrNull() ?: 0
    // println("You entered: $enteredAge")
}

