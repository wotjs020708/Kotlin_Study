ControlFlow.md

# Conditional expressions

Kotlin은 조건식을 `if` 와 `when`을 제공합니다.
> `if`와 `when`를 선택해야 하는 경우 `when`를 사용하는 것이 좋습니다. 그 이유는 다음과 같습니다.
> - 코드를 읽기 쉽게 만든다.
> - 다른 지점을 더 쉽게 추가할 수 있다.
> - 코드에서 실수가 줄어 든다.

## If

`if`를 사용하려면 조건식을 `()`괄호 안에 추가하고, 결과가 참일 때 수행할 작업을 `{}`중괄호 안에 추가합니다.
```kotlin
val d: Int
val check = true

if (check) {
    d = 1
} else {
    d = 2
}

println(d)
// 1
```
Kotlin에는 삼항연산자가 없습니다. 대신 `if`표현식으로 사용할 수 있습니다. 액션당 코드가 한 줄만 있는 경우 `{}`중괄호는 선택 사항입니다.
```kotlin
val a = 1
val b = 2

println(if (a > b) a else b) // Returns a value: 2
```

## When

`when`은 여러개의 분기가 있는 조건식이 있는 경우 사용합니다.

`when` 사용법
- 평가하려는 값을 괄호`()`안에 넣습니다.
- 중괄호 `{}` 안에 분기를 배치합니다.
- 각 분기에서 ->을 사용하여 각 검사와 검사 성공시 수행할 작업을 구분합니다.
`when`문장이나 표현식으로 사용할 수 있습니다. 문장은 아무것도 반환하지 않고 대신 작업을 수행한다.

```kotlin
val obj = "Hello"

when (obj) {
    // Checks whether obj equals to "1"
    "1" -> println("One")
    // Checks whether obj equals to "Hello"
    "Hello" -> println("Greeting")
    // Default statement
    else -> println("Unknown")     
}
// Greeting
```
> 모든 분기 조건은 그 중 하나가 충족될 때까지 순차적으로 확인 됩니다. 따라서 첫 번째 적합한 분기만 실행 됩니다.

표현식은 나중에 코드에서 사용할 수 있는 값을 반환합니다.

다음은 `when`을 표현식으로 사용하는 예시입니다.
`when` 표현식은 나중에 `println()` 함수와 함꼐 사용되는 변수에 즉시 할당됩니다

```kotlin
val obj = "Hello"    

val result = when (obj) {
    // If obj equals "1", sets result to "one"
    "1" -> "One"
    // If obj equals "Hello", sets result to "Greeting"
    "Hello" -> "Greeting"
    // Sets result to "Unknown" if no previous condition is satisfied
    else -> "Unknown"
}
println(result)
// Greeting
```

지금까지 살표본 `when`의 예에는 모두 주어인 `obj`가 있습니다. 하지만 `when`는 주어 없이도 사용할 수 있습니다.

이 예에서는 주어가 없는 `when` 표현식을 사용하여 일련의 부울 표현식을 확인 합니다.

```kotlin
fun main() {
    val trafficLightState = "Red" // This can be "Green", "Yellow", or "Red"

    val trafficAction = when {
        trafficLightState == "Green" -> "Go"
        trafficLightState == "Yellow" -> "Slow down"
        trafficLightState == "Red" -> "Stop"
        else -> "Malfunction"
    }

    println(trafficAction)
    // Stop
}
```
그러나 동일한 코들르 사용하되 제목을 trafficLightState로 지정할 수 있습니다.
```kotlin
fun main() {
    val trafficLightState = "Red" // This can be "Green", "Yellow", or "Red"

    val trafficAction = when (trafficLightState) {
        "Green" -> "Go"
        "Yellow" -> "Slow down"
        "Red" -> "Stop"
        else -> "Malfunction"
    }

    println(trafficAction)  
    // Stop
}
```
주어와 `when`을 사용하면 코드를 더 쉽게 읽고 유지 관리할 수 있습니다.
`when` 표현식과 함께 주어를 사용하면 Kotlin이 가능한 모든 경우를 포함하는지 확인하는 데 도움이 됩니다. 
그렇지 않으면 `when` 표현식과 함께 주어를 사용하지 않는 경우 다른 분기를 제공해야 합니다.

-----

# Ranges

루프에 대해 이야기 하기전, 반복할 루프의 범위를 구성하는 방법을 아는 것이 좋습니다.

Kotlin에서 범위를 만드는 가장 일반적인 방법은 `..`연산자를 사용하는 것입니다. 예를 들어 `1, 2, 3, 4`는 `1..4`와 동일 합니다.

끝 값을 포함하지 않는 범위를 선언하려면 `..<`연산자를 사용합니다. 예를 들어 `1, 2, 3`는 `1..<4`와 동일합니다.

역순으로 범위를 선언하려면 `downTo`을 사용합니다. 예를 들어 `4, 3, 2, 1`는 4 `4 downTo 1`과 동일합니다.

1이 아닌 단계로 븡가하는 범위를 선언하려면 `step`및 원하는 증가 값을 사용합니다. 예를 들어 `1, 3, 5`는 `1..5 step 2`과 동일합니다.

`char` 범위에서도 똑같은 작업을 수행할 수 있습니다.

- `'a', 'b', 'c', 'd'` 와`'a'..'b'`와 동등하다.
- `'z', 'x', 'v', 't'` 와 `'z' downTo 's' step 2`와 동등하다.

## Loops

프로그래밍에서 가장 흔한 두 가지 루프 구조는 `for`와 `while`입니다.
값 범위를 반복하고 직업을 수행하는 데 사용합니다.
`while` 특정 조건이 충족될때까지 작없을 수행합니다.


### For
범위에 대한 새로운 지식을 활용하여 `for` 1 부터 5까지 숫자를 반복하고 매번 숫자를 출력하는 루프를 만들수 있습니다.

반복자와 범윌르 `in` 키워드로 `()`괄호 안에 넣습니다 완료하려는 작업을 `{}` 중괄호 안에 추가합니다.
```kotlin
for (number in 1..5) { 
    // number is the iterator and 1..5 is the range
    print(number)
}
// 12345
```

컬렉션은 루프를 통해 반복될 수 있습니다.

```kotlin
val cakes = listOf("carrot", "cheese", "chocolate")

for (cake in cakes) {
    println("Yummy, it's a $cake cake!")
}
// Yummy, it's a carrot cake!
// Yummy, it's a cheese cake!
// Yummy, it's a chocolate cake!
```

### While
`while`두 가지 방법을 사용할 수 있습니다.
- 조건식이 참인 동안 코드 블록을 실행합니다.(`while`)
- 먼저 코드 블록을 실행한 다음 조건식을 확인합니다 (`do-while`)

첫 번째 사용 사례(`while`):
- while 루프의 조건식을 `()`괄호 안에서 계속되도록 선언합니다.
- 완료하려는 작업을 `{}`중괄호 안에 추가합니다.
> 다음 예제에서는 증가 연산자를 `++` 사용하여 `cakesEaten`변수의값을 증가 시킵니다.
```kotlin
var cakesEaten = 0
while (cakesEaten < 3) {
    println("Eat a cake")
    cakesEaten++
}
// Eat a cake
// Eat a cake
// Eat a cake
```

두 번쨰 사용 사례(`do-while`):
- while 루프의 조건식을 `()`괄호 안에서 계속되도록 선언합니다.
- `{}`중괄호 안에 `do` 키워드를 사용하여 완료하려는 작ㅇ업을 정의합니다.
```kotlin
var cakesEaten = 0
var cakesBaked = 0
while (cakesEaten < 3) {
    println("Eat a cake")
    cakesEaten++
}
do {
    println("Bake a cake")
    cakesBaked++
} while (cakesBaked < cakesEaten)
// Eat a cake
// Eat a cake
// Eat a cake
// Bake a cake
// Bake a cake
// Bake a cake
```
