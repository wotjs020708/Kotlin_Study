HelloWorld.md

# "Hello, world!" 출력 코드

```kotlin
fun main () {
	println("Hello, world!")
	// Hello, world!
}
```

- `fun`함수를 선언한느 데 사용
- 함수`main()`는 프로그램 시작점
- 함수의 본문을 중괄호 안에 작성
- `println()`,`print()`함수는 인수를 표준 출력하는 함수

------

# 변수

- 읽기 전용 변수 `val` *읽기 전용 변수는 값을 지정한 후 변경 불가*
- 변경 가능한 변수 `var`

값을 할당하려면 할당 연산자 사용 `=`.


변수는 프로그램 시작시 main() 함수 외부에서 선언할 수 있습니다.
이렇게 선언된 변수를 최상위 수준에서 선언된 변수라고 합니다. - `전역 변수`

-----

# String templates

문자를 표현할때는 `"` 사용
템플릿 표현식은 항상 달러 기호`$`로 시작

```kotlin
val customers = 10
println("There are $customers customers")
// There are 10 customers

println("There are ${customers + 1} customers")
// There are 11 customers
```

위 내용에서 변수에 대한 선언된 타입이 없다는 것을 알 수 있습니다.
kotlin은 타입 자체를 추론합니다.