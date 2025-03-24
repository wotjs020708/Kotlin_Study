Functions.md

# Functions

Kotlin에선느 `fun` 키워드를 사용하여 사용자 정의 함수를 선언할 수 있습니다.
```kotlin
fun hello() {
    return println("Hello, world!")
}

fun main() {
    hello()
    // Hello, world!
}
```
코틀린 에서:
- 함수매개변수는 `()` 괄호 안에 작성합니다.
- 각 매개변수의 유형이 있어야 하며, 여러 매개변수는 `,`쉼표로 구분해야 합니다.
- 반환 타입은 함수의 `()`괄호 뒤에 `:`콜롬으로 구분하여 적습니다.
- 함수의 본문은 `{}`중괄호 안에 작성됩니다.
- `return` 키워드는 함수에서 무언가를 종료하거나 반환하는 데 사용됩니다.
> 함수가 반환하지 않는 경우 반환 유형과 반환 `return` 키워드를 생략할 수 있습니다.

다음 예쩨에서는:
- `x` 그리고 `y` 함수 매개변수 입니다.
- `x` 그리고 `y` `Int` 타입입니다.
- 함수의 반환 타입은 `Int` 입니다.
- 해당 함수는 호출되면 `x`와 `y`의 합계를 반환합니다.

```kotlin
fun sum(x: Int, y: Int): Int {
    return x + y
}

fun main() {
    println(sum(1, 2))
    // 3
}
```
> 코딩 규칙에서는 함수 이르을 소문자로 시작하고 밑줄 없이 카멜 표기법을 사용할 것을 권장합니다.
## Named arguments

간결한 코드의 경우 함수를 호출할 때 매개변수 이름을 포함할 필요가 없습니다. 하지만 매개변수 이름을 포함하면 코드를 더 일기 쉽게 만들 수 있습니다. 이를 *명령된 인수(`named arguments`)*를 사용한다고 합니다. 매개변수 이름을 포함함녀 어떤 순서로든 매개변수를 작성할 수 있습니다.

> 다음 예제에서는 문자열 텐플릿 ($)을 사용하여 매개변수 값에 액세스하고 이를 문자열 유형으로 변환한 다음 인쇄용 문자열로 연결합니다.

```Kotlin
fun printMessageWithPrefix(message: String, prefix: String) {
    println("[$prefix] $message")
}

fun main() {
    // Uses named arguments with swapped parameter order
    printMessageWithPrefix(prefix = "Log", message = "Hello")
    // [Log] Hello
}
```

## Default parameter values

함수 매개변수에 대한 기본값을 정희할 수 있습니다. 기본값이 있는 매개변수는 함수를 호출할 떄 생략할 수 있습니다. 기본값을 선언하려면 타입 뒤에 `=`할당 연산자를 사용합니다.
```kotlin
fun printMessageWithPrefix(message: String, prefix: String = "Info") {
    println("[$prefix] $message")
}

fun main() {
    // Function called with both parameters
    printMessageWithPrefix("Hello", "Log") 
    // [Log] Hello
    
    // Function called only with message parameter
    printMessageWithPrefix("Hello")        
    // [Info] Hello
    
    printMessageWithPrefix(prefix = "Log", message = "Hello")
    // [Log] Hello
}
```

## Functions without return

함수가 유용한 값을 반환하지 않는 경우 반혼 유형은 `Unit`입니다. 단위는 값이하나만 있는 타입입니다. 함수 본문에서 `Unit`이 반환된다는 것을 명시적으로 선언할 필요는 없습니다. 즉, `return`반환 키워드를 사용하거나 반환 유형을 선언할 필요가 없습니다.

```kotlin
fun printMessage(message: String) {
    println(message)
    // `return Unit` or `return` is optional
}

fun main() {
    printMessage("Hello")
    // Hello
}
```





