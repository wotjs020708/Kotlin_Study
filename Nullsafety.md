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

## Use safe calls

`null` 값을 포함할 수 있는 객체의 프로퍼티에 안전하게 액세스하려면 안전 호출연산자`?`를 사용합니다. 안전호출 연산자는 객체 또는 액세스한 속성 중 하나가 `null`인 경우 `null`을 반환합니다. 이 연산자는 코드에서 오류를 유발하는 `null` 값의 존재를 방지하려는 경우에 유용합니다.

다음 예제에서 `lengthString()` 함수는 안전 호출을 사용하여 문자열의 길이 또는 `null`을 반환합니다:
```kotlin
fun lengthString(maybeString: String?): Int? = maybeString?.length

fun main() { 
    val nullString: String? = null
    println(lengthString(nullString))
    // null
}
```
> 안전 호출을 연결하여 객체의 프로퍼티에 `null`값이 포함된 경우 오류가 발생하지 않고 `null`이 반환되도록 할 수 있습니다. 예를 들어:
>```kotlin
>person.company?.address?.country
>```

안전호출 연산자는 확장 또는 멤버 함수를 안전하게 호출하는 데에도 사용할 수 있습니다. 이 경우 함수가 호출되기 전에 `null` 검사가 수행됩니다. 검사에서 `null` 값이 감지되면 호출이 건너뛰고 `null`이 반환됩니다.

다음 예제에서는 `nullString`이 `null`이므로 `.uppercase()`호출을 건너뛰고 `null`을 반환합니다.

```kotlin
fun main() {
    val nullString: String? = null
    println(nullString?.uppercase())
    // null
}
```

## Use Elvis operator

Elvis operator`?:`를 사용하여 `null`값이 감지될 경우 안환할 기본값을 제공할 수 있습니다.

Elvis operator의 왼쪽에 `null` 값에 대해 검사해야 할 항목을 적습니다. `null`값이 감지되면 반환해야하는 값은 Elvis operator의 오른쪽에 적습니다.

다음 예제에서는 `nullString`이 `null`이므로 `lenght` 속성에 액세스하기 위한 안전 호출이 `null` 값을 반환합니다. 결과적으로 elvis operator는 0을 반환합니다:

```kotlin
fun main() {
    val nullString: String? = null
    println(nullString?.length ?: 0)
    // 0
}
```