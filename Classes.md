# Classses

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