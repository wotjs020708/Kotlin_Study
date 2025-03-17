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
