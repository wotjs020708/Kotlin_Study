Collections.md

# Collection

프로그래밍할 때 나중에 처리할 수 있도록 데이터를 구조로 구룹화할 수 있는 것이 유용합니다.
kotlin은 바로 이 목적을 위해 컬랙션을 제공합니다.

| 컬렉션 유형 | 설명 |
| --- | --- |
| Lists| 순차적 항목 모움 |
| Sets | 고유한 순서 없는 항목 컬렉션 |
| Maps | 키가 고유하고 하나의 값에만 매핑되는 키-값 쌍 세트|
각 컬렉션 유형은 변경 가능하거나 읽기 전용일 수 있습니다.
-----
# Lsit
`Lsit`는 항목을 추가도니 순서대로 저장하며 중복된 항목을 허용합니다.
읽기 전용 목록(`List`)을 만들려면 `listOf()` 함수를 사용면 된다.
변경 가능한 목록(`MutableList`)을 생성하려면 `mutableListOf()` 함수를 사용하면 된다.

```kotlin
// Read only list
val readOnlyShapes = listOf("triangle", "square", "circle")
println(readOnlyShapes)
// [triangle, square, circle]

// Mutable list with explicit type declaration
val shapes: MutableList<String> = mutableListOf("triangle", "square", "circle")
println(shapes)
// [triangle, square, circle]
```
> 원치 않는 수정을 방지할면 변경 가능한 목록에 할당하여 읽기 전용 보기를 만들 수 있다.
>```kotlin
>val shapes: MutableList<String> = mutableListOf("triangle", "square", "circle")
>val shapesLocked: List<String> = shapes
>```
> 이것을 *캐스팅* 이라고한다.

`List`는 정렬되어 있으므로 `List` 항목에 액세스하려면 `index` 연산자를 `[]` 사용한다.
```kotlin
val readOnlyShapes = listOf("triangle", "square", "circle")
println("The first item in the list is: ${readOnlyShapes[0]}")
// The first item in the list is: triangle
```
`List`에 첫번째 항목이나 마지막 항목을 가져오려면 각각 `.first()`, `.last()` 함수를 사용한다.

> `.first()` 그리고 `.last()` 함수는 확장 함수의 예입니다. 객체에서 확장 함수를 호출하려면 객체 뒤에 `.`마침표를 붙인 함수 이름을 써야한다.

`List`에 있는 항목의 개수를 구하려면 `.count()`함수를 사용한다.
```kotiln
val readOnlyShapes = listOf("triangle", "square", "circle")
println("This list has ${readOnlyShapes.count()} items")
// This list has 3 items
```
항목이 `List`에 있는지 확인하려면 다음 `in`연산자를 사용한다.
```kotlin
val readOnlyShapes = listOf("triangle", "square", "circle")
println("circle" in readOnlyShapes)
// true
```
변경 가능한 `List`에 항목을 추가하거나 제거하려면 각각 `.add()`, `.remove()`함수를 사용한다.
```kotlin
val shapes: MutableList<String> = mutableListOf("triangle", "square", "circle")
// Add "pentagon" to the list
shapes.add("pentagon") 
println(shapes)  
// [triangle, square, circle, pentagon]

// Remove the first "pentagon" from the list
shapes.remove("pentagon") 
println(shapes)  
// [triangle, square, circle]
```
-----
# Set
*정렬되어있지 않고 고유한 항목 만 저장합니다.*

읽기 전용 세터(`Set`)를 생성하려면 `setOf()` 함수를 사용
변경 가능한 세트(`MutableSet`)를 생성하려면 `mutableSetOf()` 함수 사용

```kotlin
// Read-only set
val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")
// Mutable set with explicit type declaration
val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")

println(readOnlyFruit)
// [apple, banana, cherry]
```
이전 예에서 볼 수 있듯이 집합은 고유한 요소만 포함하므로 증복된`"cherry"`항목은 삭제된다.
>원치 않는 수정을 방지하려면 다음을 지정하여 변경 가능한 세트의 읽기 전용 뷰를 만들 수 있다.
>```kotlin
>val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")
>val fruitLocked: Set<String> = fruit
>```

>집합은 *순서가 없으므로* 특정 인덱스의 항목에 액세스할 수 없습니다.

세트에 있는 항목의 개수를 구하려면 다음 `.count()`함수를 사용
```kotlin
val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")
println("This set has ${readOnlyFruit.count()} items")
// This set has 3 items
```
항목이 세트에 있는지 확인할면 다음 `in`연산자를 사용
```kotlin
val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")
println("banana" in readOnlyFruit)
// true
```
변경 가능한 세트에서 항목을 추가하거 제거하라면 각각 `.add()`, `.remove()` 함수 사용
```kotlin
val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")
fruit.add("dragonfruit")    // Add "dragonfruit" to the set
println(fruit)              // [apple, banana, cherry, dragonfruit]

fruit.remove("dragonfruit") // Remove "dragonfruit" from the set
println(fruit)              // [apple, banana, cherry]
```

# Map

맵은 항목을 키-값으로 저장합니다. 키를 참조하여 값에 액세스합니다.
예를 들어 음식 메뉴를 맵을 사용하면 먹고 싶은 음식(키)을 찾으면 가격(값)을 찾을 수 있습니다.
맵은 `List`와 같이 번호가 매겨진 인덱스를 사용하지 않고 값을 찾으려는 경우에 유용합니다.

> - Kotlin이 사용자가 얻곶자 하는 값이 무엇인지 이해할 수 있도록 맵의 각 키는 고유해야합니다.
> - 맵에는 증복된 값이 있을 수 있습니다.

읽기 전용 맵(`Map`)을 생성하려면 `mapOf()`함수를 사용

변경 가능한 맵(`MutableMap`)을 생성하라면  `mutableMapOf()`함수를 사용

맵을 만들 때 Kotlin은 저장된 항목의 유형을 유추할 수 있습니다. 명시적으로 선언할 수 있습니다.

맵은 만드는 가장 쉬운 방법은 각 키와 관련 값 사이에 `to`을 사용하는 것입니다.
```kotlin
// Read-only map
val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println(readOnlyJuiceMenu)
// {apple=100, kiwi=190, orange=100}

// Mutable map with explicit type declaration
val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println(juiceMenu)
// {apple=100, kiwi=190, orange=100}
```
>원치 않는 수정을 방지하려면 변경 가능한 맵에 다음을 할당 하여 ㅇ릭기 전용 뷰를 만들 수 있습니다.
>```kotlin
>val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
>val juiceMenuLocked: Map<String, Int> = juiceMenu
>```
맵의 값에 액세스하려면 해당 키와 함께 인덱싱된 액세스 연산자 `[]`를 사용합니다:
```kotlin
// Read-only map
val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println("The value of apple juice is: ${readOnlyJuiceMenu["apple"]}")
// The value of apple juice is: 100
```
> 맵에 *존재하지 않는 키*를 사용하여 액세스하려고 하면 `null` 값이 표시됩니다.

또한`[]`연산자를 사용하여 변경가능한 맵에 항목을 추가할 수 있습니다.
```kotlin
val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
juiceMenu["coconut"] = 150 // Add key "coconut" with value 150 to the map
println(juiceMenu)
// {apple=100, kiwi=190, orange=100, coconut=150}
```

변경 가능한 맵에서 항목을 제거하려면 `.remove()` 함수를 사용
```kotlin
val juiceMenu: MutableMap<String, Int> = mutableMapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
juiceMenu.remove("orange")    // Remove key "orange" from the map
println(juiceMenu)
// {apple=100, kiwi=190}
```

맵에 있는 항목의 개수를 구하려면 `.count()` 함수를 사용
```kotlin
// Read-only map
val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println("This map has ${readOnlyJuiceMenu.count()} key-value pairs")
// This map has 3 key-value pairs
```

특정 키가 이미 맵에 존재하는 확인하려면 `.containsKey()`함수를 사용
```kotlin
val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println(readOnlyJuiceMenu.containsKey("kiwi"))
// true
```

맵의 키 또는 값을 얻으려면 각각 `keys`, `values` 속성을 사용
```kotlin
val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println(readOnlyJuiceMenu.keys)
// [apple, kiwi, orange]
println(readOnlyJuiceMenu.values)
// [100, 190, 100]
```

키 또는 값이 맵에 있는지 확인하라면  다음 `in`연산자를 사용

```kotlin
val readOnlyJuiceMenu = mapOf("apple" to 100, "kiwi" to 190, "orange" to 100)
println("orange" in readOnlyJuiceMenu.keys)
// true

// Alternatively, you don't need to use the keys property
println("orange" in readOnlyJuiceMenu)
// true

println(200 in readOnlyJuiceMenu.values)
// false
```


