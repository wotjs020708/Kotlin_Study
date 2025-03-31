# Nullsafety

Kotlin에는 `null` 값을 가질 수 있습니다. Kotlin은 누락되었거나 아직 설정되지 않은 항목이 있을 떄 `null` 값을 사용합니다. 이미 컬렉션 챔터에서 맵에 존재하지 않는 키로 키-값에 엑세스하려고할 때 kotlin이 `null` 값을 반환하는 예제를 보셧을 것입니다. 이러한 방식으로 널 값을 사용한느 것이 유용하지만 코드가 이를 처리할 준비가 되어 있지 않은 경우 문제가 발생할 수 있습니다.

프로그램에서 `null`값으로 인한 문제를 방지하기 위해 kotlin에는 `null` 안전 기능이 있습니다. Null safety은 런타임이 아닌 컴파일 타임에 `null` 값의 잠재적 문제를 감지합니다.

null safety은 여러 기능을 조합하여 사용할 수 있는 기능입니다.

- 프로그램에서 `null` 값이 허용되는 경우를 명시적으로 선언합니다.
- `null` 값을 확인합니다.
- `null`값을 포함할 수 있는 속성이나 함수에 대한 안전 호출을 사용합니다.

## Nullable types

kotlin은 선언된 유형이 널 값을 가질 수 있도록 허용하는 Nullable types을 지원합니다. 기본적으로 `null` 값을 허용하지 않습니다. Nullable types는 타입 선언 뒤에 명시적으로 `?`을 추가하여 선언 합니다.

예를 들어:
```kotlin
fun main() {
    // neverNull has String type
    var neverNull: String = "This can't be null"

    // Throws a compiler error
    neverNull = null

    // nullable has nullable String type
    var nullable: String? = "You can keep a null here"

    // This is OK
    nullable = null

    // By default, null values aren't accepted
    var inferredNonNull = "The compiler assumes non-nullable"

    // Throws a compiler error
    inferredNonNull = null

    // notNull doesn't accept null values
    fun strLength(notNull: String): Int {                 
        return notNull.length
    }

    println(strLength(neverNull)) // 18
    println(strLength(nullable))  // Throws a compiler error
}
```
> `length`는 문자열 내의 문자 수를 포함하는 문자열 클래스의 속성입니다.

## Check for null values

조건식 내에는 `null`값의 존재 여부를 확인할 수 있습니다. 다음 예제에는 `describeString()` 함수에는 `mybeString`이 `null`이 아닌지, 그 길이가 0보다 큰지 확인하는 if문이 있습니다:
```kotlin
fun describeString(maybeString: String?): String {
    if (maybeString != null && maybeString.length > 0) {
        return "String of length ${maybeString.length}"
    } else {
        return "Empty or null string"
    }
}

fun main() {
    val nullString: String? = null
    println(describeString(nullString))
    // Empty or null string
}
```