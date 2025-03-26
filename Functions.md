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

## Single-expression functions

코드를 더 간결하게 만들려면 *단일 표현식 함수*를 사용할 수 있습니다. 예를 들어 `sum()` 함수를 단축할 수 있습니다.
```kotlin
fun sum(x: Int, y: Int): Int {
    return x + y
}

fun main() {
    println(sum(1, 2))
    // 3
}
```

`{}`중괄호를 제거하고 `=`할당 연산자를 사용하여 함수 본문을 선언할 수 있습니다. `=`할당 연산자를 사용하는 경우 Kotlin은 타입 추론을 사용하므로 반환 유형ㅇ르 생략할 수도 있습니다. 그러면 `sum()` 함수는 한 줄이 됩니다.

```kotlin
fun sum(x: Int, y: Int) = x + y

fun main() {
    println(sum(1, 2))
    // 3
}
```

그러나 다른 개발자가 코드를 빠르게 이해할 수 있도록 하려면 `=`할당 연산자를 사용할 때에도 반환 유형을 명시적으로 정의하는 것이 좋습니다.

> `{}`중괄호를 사용하여 함수 본문을 선언하는 경우 반환 유형도 선언해야 합니다 (반환 `Unit`유형이 아닌 경우).


## Early returns in functions

함수의 코드가 특정 지점을 넘어 처리되는 것을 막으려면 `return` 키워드르 사용합니다. 이 예에서는 `if`조건 식이 참인 경우 함수에서 일찍 반환하는데 사용됩니다.

```kotlin
// A list of registered usernames
val registeredUsernames = mutableListOf("john_doe", "jane_smith")

// A list of registered emails
val registeredEmails = mutableListOf("john@example.com", "jane@example.com")

fun registerUser(username: String, email: String): String {
    // Early return if the username is already taken
    if (username in registeredUsernames) {
        return "Username already taken. Please choose a different username."
    }

    // Early return if the email is already registered
    if (email in registeredEmails) {
        return "Email already registered. Please use a different email."
    }

    // Proceed with the registration if the username and email are not taken
    registeredUsernames.add(username)
    registeredEmails.add(email)

    return "User registered successfully: $username"
}

fun main() {
    println(registerUser("john_doe", "newjohn@example.com"))
    // Username already taken. Please choose a different username.
    println(registerUser("new_user", "newuser@example.com"))
    // User registered successfully: new_user
}
```

## Lambda expressions

Kotlin에서는 *람다 표현식(lambda expressions)*을 사용하여 함수의 코드를 더 간결하게 작성할 수 있습니다.
예를 들어, 다음 `uppercaseString()`함수가 있습니다.
```kotlin
fun uppercaseString(text: String): String {
    return text.uppercase()
}
fun main() {
    println(uppercaseString("hello"))
    // HELLO
}
```

람다 표현식으로도 작성할 수 있습니다.
```kotlin
fun main() {
    val upperCaseString = { text: String -> text.uppercase() }
    println(upperCaseString("hello"))
    // HELLO
}
```

람다 표현식은 언뜻 보기에 이해하기 어려울 수 있으므로 분석해 보겠습니다. 람다 표현식은 중괄호 안에 작성됩니다.

람다 표현식 내에는 다음과 같이 작성합니다.
- 매개변수 뒤에 `->` 이 붙습니다.
- 함수 본문은 `->` 뒤에 옵니다.

이전 예에서:
- `text` 함수 매개변수입니다.
- `text` 타입이 `string` 입니다.
- 이 함수는 `text`에서 호출된 `.uppercase()` 함수의 결과를 반환합니다.
- 전체 람다 식은 대입 연산자 `=`를 사용하여 `upperCaseString`변수에 할당됩니다.
- 람다 쵸현식은 함수처럼 `upperCaseString` 변수를 사용하고 문자열 "hello"를 매개변수로 사용하여 호출됩니다.
- `println()` 함수는 결과를 인쇄합니다.
> 매개변수 없이 람다를 선언한느 경우 `->`을 사용할 필요가 없습니다. 예를 들어
> ```kotlin
> { println("Log message") }
> ```

람다 표현식은 여러가지 방법으로 사용할 수 있습니다. 다음을 수행할 수 있습니다:
- 람다 표현식을 다른 함수의 매개변수로 전달
- 함수에서 람다 표현식을 반환
- 자체적으로 람다 표현식 호출하기

### Pass to another function(다른 함수로 전달)

람다 식을 함수에 전달하는 것이 유용한 경우의 좋은 예는 컬렉션에서 `.filter()` 함수를 사용하는 것입니다:
```kotlin
val numbers = listOf(1, -2, 3, -4, 5, -6)


val positives = numbers.filter ({ x -> x > 0 })

val isNegative = { x: Int -> x < 0 }
val negatives = numbers.filter(isNegative)

println(positives)
// [1, 3, 5]
println(negatives)
// [-2, -4, -6]

```
`.filter()` 함수는 람다식을 술어로 받아 들입니다: 

- `{ x -> x > 0 }`목록의 각 요소를 가져와서 양수인 요소만 반환합니다.
- `{ x -> x < 0 }`목록의 각 요소를 가져와서 음수인 요소만 반환합니다.

이 예제는 람다 표현식을 함수에 전달하는 두 가지 방법을 보여줍니다.
- 양수의 경우 이 예제에서는 `.filter()` 함수에서 직접 람다 표현식을 추가합니다.
- 음수의 경우 이 예제에서는 람다 식을 `isNegative` 변수에 할당합니다. 그런 다음 `.filter()` 함수에서 `isNegative` 변수가 함수 매개변수로 사용됩니다. 이경우 람다 표현식에 함수 매개변수 유형 (`x`)을 지정해야합니다.
> 람다 식이 유리한 함수 매개변수인 경우 함수 괄호 `()`를 생략할 수 있습니다.
> ``` kotlin
> val positives = numbers.filter { x -> x > 0 }
> ```
> 이는 이 장의 마지막 부분에서 자세히 설명하는 후행 람다의 예입니다.

또 다른 조흔 예는 `.map()` 함수를 사용하여 컬렉션의 항목을 변환하는 것입니다:

```kotlin
val numbers = listOf(1, -2, 3, -4, 5, -6)
val doubled = numbers.map { x -> x * 2 }

val isTripled = { x: Int -> x * 3 }
val tripled = numbers.map(isTripled)

println(doubled)
// [2, -4, 6, -8, 10, -12]
println(tripled)
// [3, -6, 9, -12, 15, -18]

```
`.map()` 함수는 람다 표현식을 트랜스폼 함수로 받아들입니다.
- `{ x -> x * 2 }`는 목록의 각 요소를 가져와 해당 요소에 2를 곲한 값을 반환합니다.
- `{ x -> x * 3 }`는 목록의 각 요소를 가져와 해당 요소에 3을 곲한 값을 반환합니다.

### Function types

함수에서 람다 식을 바환하려면 먼저 함수 타입을 이해해야합니다.

기본 타입에 대해 이미 학습했지만 하수 자체에도 타입이 있습니다. Kotlin의 타입 추론은 매개 변수 타입에서 함수의 타입을 추론할 수 있습니다. 하지만 함수 타입을 명시적으로 지정해야 하는 경우가 있을 수 있습니다. 컴파일러는 해당 함수에 허용되는 것과 허용되지 않는 것을 알기 위해 함수 타입이 필요합니다.

함수 타입의 구문은 다음과 같습니다:

- 각 매개변수의 유형은 괄호`()` 안에 작성하고 쉽표`,`로 구분합니다.
- 반한 유형은 `->` 뒤에 작성됩니다.
예 : `(String) -> String` or `(Int, Int) -> Int`.

`upperCaseString()`의 함수 유형이 정의된 경우 람다 식은 이렇게 생겼습니다:
```kotlin
val upperCaseString: (String) -> String = { text -> text.uppercase() }

fun main() {
    println(upperCaseString("hello"))
    // HELLO
}
```
람다 표현식에 매개변수가 없는 경우 괄호`()`는 비워 둡니다. 예: `() -> Unit`.

> 매개변수 및 반환 타입을 람다 표현식 또는 함수타입으로 선언해야 합니다. 그렇지 않으면 컴파일러가 람다 표현식의 타입을 알 수 없습니다.
> 에를 들어, 다음과 같은 예는 작동하지 않습니다.
> ```Kotlin
> val upperCaseString = { str -> str.uppercase() }
> ```

### Return from a function

람다 표현식은 함수에서 반활될 수 있습니다. 컴파일러가 바환된 람다 표현식이 어떤 유형인지 이해할 수 있도록 함수 유형을 선언해야 합니다.

다음 예제에서 `toSeconds()` 함수는 항상 `Int` 타입의 매개변수를 취하고 `Int` 값을 반환하는 람다식을 반환하므로 함수 타입이 `(Int) -> Int` 입니다.

이 예제에서는 `when` 표현식을 사용하여 `toSeconds()`가 호출될 때 반환된는 람다 표현식을 결정합니다:
```kotlin
fun toSeconds(time: String): (Int) -> Int = when (time) {
    "hour" -> { value -> value * 60 * 60 }
    "minute" -> { value -> value * 60 }
    "second" -> { value -> value }
    else -> { value -> value }
}

fun main() {
    val timesInMinutes = listOf(2, 10, 15, 1)
    val min2sec = toSeconds("minute")
    val totalTimeInSeconds = timesInMinutes.map(min2sec).sum()
    println("Total time is $totalTimeInSeconds secs")
    // Total time is 1680 secs
}
```


