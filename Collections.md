Collections.md

# Collection

프로그래밍할 때 나중에 처리할 수 있도록 데이터를 구조로 구룹화할 수 있는 것이 유용합니다.
kotlin은 바로 이 목적을 위해 컬랙션을 제공합니다.

|컬렉션 유형| 설명|
|---|---|---|
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