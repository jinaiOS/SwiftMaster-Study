# 3주차 Jina

# 스위프트에서 클래스와 구조체의 차이점을 설명합니다.

## class

- 상속이 가능합니다.
- 힙 영역에 저장됩니다.
- 참조 타입입니다.
- ARC로 메모리를 관리합니다.

## struct

- 상속이 불가능합니다.
- 일반적으로 스택의 공간에 저장합니다.
- 값을 전달할 때마다 복사본이 생성됩니다.
- 값 타입입니다.

# 클래스와 구조체의 초기화 과정을 비교해서 설명합니다.

## class

- 상속이 가능하므로 모든 속성이 초기화되어야 합니다.
- 상위 클래스의 초기화를 오버라이드할 수 있고, 호출할 수 있습니다.

## struct

- Memberwise Initializer가 자동 제공됩니다.

```swift
struct Point {
    var x: Int
    var y: Int
}

let point = Point(x: 10, y: 20)
```

# 지연 저장 속성을 사용하는 이유에 대해 설명합니다.

- 불필요한 리소스 사용을 막기 위해서 사용합니다.
- 초기값이 없을 때 사용합니다.

# 타입 속성(Type properties)를 정의하고 관련 예제를 작성합니다.

- 그 타입의 속성에 접근하는 것을 말합니다.

```swift
class Person {
    static var name: String = "jina"
    static var age: Int = 10 // 정적 속성으로, 오버라이드 불가능

    class var isAdult: Bool {
        return age >= 18
    }
}

print(Person.name) // "jina"
print(Person.age)  // 10
print(Person.isAdult) // false
```
