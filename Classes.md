# Classes

Kotlin은 클래스와 객체를 사용하여 객체 지향 프로그래밍을 지원합니다. 객체는 프로그램에서 데이터를 저장하는 데 유용합니다. 클래스를 사용하면 객체에 대한 특성 집합을 선언할 수 있습니다. 클래스에서 객체를 만들면 이러한 특성을 매번 선언할 플요가 없으므로 시간과 노력을 절약합니다.

클래스를 선언하려면 `class` 키워드를 사용합니다.

```kotlin
class Customer
```

## Proprties

클래스 객체의 특성은 프로퍼티로 선언할 수 있습니다. 클래스의 속성을 선언할 수 있습니다:

- 클래스 이름 뒤에 괄호`()` 안에 입력합니다.

```kotlin
class contact(val id: Int, var email: String)
```

- 중괄호 `{}`로 정의된 클래스 본문.
```kotlin
class Contact(val id: Int, var email: String) {
	val category: String ""
}
```

클래스 인스턴스가 생성된 후 변경해야 하는 경우가 아니라면 프로퍼티를 일기 전용(`val`)으로 선언하는 것이 좋습니다.

괄호 안에 `val` 또는 `var` 없이 프로퍼티를 선언할 수 있지만 인스턴스가 생성된 후에는 이러한 프로퍼티에 액세스할 수 없습니다.

> - 괄호`()` 안에 포함된 콘텐츠를 클래스 해더라고 합니다.
> - 클래스 프로퍼티를 선언할 때 후행 쉼표를 사용할 수 있습니다.

함수 매개변수와 마찬가지로 클래스 프로퍼티에도 기본값이 있을 수 있습니다.:

```Kotlin
class Contact(val id: Int, var email: String = "example@gmail.com") {
	val = category: String "work"
}
```

## Create instance

클래스에서 객체를 만들려면 생성자를 사용하여 클래스 인스턴스를 선언합니다.

기본적으로 Kotlin은 클래스 헤더에 선언된 매개변수를 사용하여 생성자를 자동으로 생성합니다.

예를 들어: 
```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")
}
```

에를 들어:
- `Contact` 클래스입니다.
- `Contact`는 `Contact` 클래스의 인스턴스 입니다.
- `id`와 `email`은 속성(properties)입니다.
- `id`와 `email`은 기본 생성자와 함께 연락처를 생성하는 데 사용됩니다.

Kotlin 클래스에는 사용자가 직접 정의한 생성자를 포함하여 많은 생성자가 있을 수 있습니다. 여러 생성자를 서언하는 방법에 대해 자세히 알아보려면 [생성자](https://kotlinlang.org/docs/classes.html#constructors)를 참조하세요.

## Access properties

인스턴스의 속성에 액세스하려면 은스턴스 이름 뒤에 마침표`.`가 붙은 속성 이름을 작성합니다.

```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")
    
    // Prints the value of the property: email
    println(contact.email)           
    // mary@gmail.com

    // Updates the value of the property: email
    contact.email = "jane@gmail.com"
    
    // Prints the new value of the property: email
    println(contact.email)           
    // jane@gmail.com
}
```
> 속성 값을 문자열의 일부로 연결하려면 문자열 템프릿(`$`)을 사용할 수 있ㅇ릇브니다. 예를 들어:
> ```Kotlin
> println("Their email address is: ${contact.email}")
> ```

## Member functions

객체 특성의 일부로 프로퍼티를 선언하는 것 외에도 멤버 함수를 사용하여 객체의 동작을 정의할 수도 있습니다.

Kotlin에서 멤버 함수는 클래스 본문 내에서 선언해야 합니다. 인스턴스에서 멤버 함수를 호출하려면 인스턴스 ㅇ치름 뒤에 마침표`.`가 붙은 함수 이름을 작성합니다. 예를 들어:
```kotlin
class Contact(val id: Int, var email: String) {
    fun printId() {
        println(id)
    }
}

fun main() {
    val contact = Contact(1, "mary@gmail.com")
    // Calls member function printId()
    contact.printId()           
    // 1
}
```

## Data classes

Kotlin에는 데이터를 저장하는 데 특히 유요한 데이터 클래스가 있습니다. 데이터 클래스는 클래스와 동일한 기능을 갖지만 추가 멤버 함수가 자동으로 제공됩니다. 이러한 멤버 함수를 사용하면 인스턴스를 읽기 가능한 출력으로 쉽게 인쇄하고, 클래스의 인스턴스를 비교하고, 인스턴스를 복사하는 등의 작업을 수행할 수 있습니다. 이러한 함수는 자동으로 사용할 수 있으므로 각 클래스에 대해 동일한 상용구 코드를 작성한는 데 시간을 들일 필요가 없습니다.

데이터 클래스를 선언하려면 `data` 키워드를 사용합니다:

```kotlin
data class User(val name: String, val id: Int)
```

데이터 클래스의 가장 유용한 미리정의도니 멤버 함수는 다음과 같습니다:

| Fucntion | Descriptions |
| --- | --- | 
| `toString()` | 클래스 인스턴스와 그 프로퍼티의 일기 가능한 문자열을 출력합니다.|
| `equals()` or `==` | 클래스의 인스턴스를 비교합니다. |
| `copy` | 다른 속성을 가진 클래스 인스턴스를 복사하여 클래스 인스턴스를 생성합니다. |

각 기능의 사용 방법에 대한 예는 다음 섹션을 참조하세요:

-  [Print as String](https://kotlinlang.org/docs/kotlin-tour-classes.html#print-as-string)
- [Compare instances](https://kotlinlang.org/docs/kotlin-tour-classes.html#compare-instances)
- [Copy instance](https://kotlinlang.org/docs/kotlin-tour-classes.html#copy-instance)

