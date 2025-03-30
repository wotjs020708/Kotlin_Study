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

