Basictypes.md

Kotlin의 모든 변수와 데이터 구조에는 `type`이 있다.

kotlin's ability to *infer* the type is called *type inference*.
-  타입을 추론하는 Kotlin의 기능을 타입 추론이라고 합니다.

```kotlin
var customers = 10

// Some customers leave the queue
customers = 8

customers = customers + 3 // Example of addition: 11
customers += 7            // Example of addition: 18
customers -= 3            // Example of subtraction: 15
customers *= 2            // Example of multiplication: 30
customers /= 3            // Example of division: 10

println(customers) // 10

```
> `+=`, `-=`, `*=`, `/=`,및 는 `%=`증강 할당 연산자입니다. 자세한 내용은 <u>증강할당</u>을 참조하세요.

-----
# kotile 기본 유형
| 범주 | 기본유형 | 예제 코드|
|---|---|---|
| 정수 | `Byte`, `Short`, `Int`, `Long` | `val year: Int = 2020` |
| 부호 없는 정수 | 	`UByte`, `UShort`, `UInt`, `ULong` | `val score: UInt = 100u` |
| 부동 소수 점 숫자| `Float`, `Double` | `val currentTemp: Float = 24.5f`, `val price: Double = 19.99` |
| 부울 | `Boolean` | `val = separator: Char = ','` |
| 캐릭터 | `Char` | `val = separator: Char =','` |
| 문자열 | `String` | `val message: String = "Hello, world!"` |


변수를 처음 읽기 전에 초기화하면 kotlin에서 이를 관리할 수 있습니다.

변수를 초기화하지 않고 선언하려면 `:`를 사용하여 유형을 지정합니다. 예를 들어
```kotiln
// Variable declared without initialization
val d: Int
// Variable initialized
d = 3

// Variable explicitly typed and initialized
val e: String = "hello"

// Variables can be read because they have been initialized
println(d) // 3
println(e) // hello
```
변수를 읽기 전에 초기화하지 않으면 오류가 발생합니다.
```kotiln
// Variable declared without initialization
val d: Int

// Triggers an error
println(d)
// Variable 'd' must be initialized
```

