# 3주차 과제

## 구조체의 상수 인스턴스를 선언하는 방법을 보여주고 속성이 변경되었을 때 그 동작을 설명합니다.
```swift
struct SomeStruct {
    let someVal: String
}

var struct = SomeStruct(someVal: "SomeValue")
struct.somVal = "Change Value" // 오류 발생
```
상수로 선언된 인스턴스는 초기화와 함께 값 세팅한 이후로는 변경이 불가능합니다.
따라서, 변경을 시도하면 'Cannot assign to property: 'someVal'is a 'let' constant'라는 오류 발생합니다.

## 저장 속성(Stored properties)의 개념을 설명하고 저장 속성을 사용한 예제를 작성합니다.
클래스 및 구조체에서만 사용 가능하며, 상수 혹은 변수로 값을 저장합니다.
```swift
struct SomeStruct {
    let someVal: String = "Some Value"
    var someNum: Int
}

class SomeClass {
    let someVal: String
    var somNum: Int
}
```

## 계산 속성(Computed properties)를 정의하고 관련 예제를 작성하여 설명합니다.
클래스와 구조체, 열거형에서 사용 가능하며 어떠한 연산을 처리한 후 값을 저장합니다.
```swift
class SomeClass {
    var height: CGFloat = 50.0
    var scrollHeight: CGFloat {
        get {
            return height
        }
        set {
            height = newValue * 2.0
        }
    }
}
```
'get'으로 저장된 값을 리턴합니다.
'set'으로 저장된 값을 업데이트합니다.

```swift
var simpleScrollHeight: CGFloat { return height * 2.0 }
```
get은 생략 가능합니다. 다만 set은 생략 불가합니다.

## 속성 감시자의(Property observers) 개념을 설명하고 클래스 또는 구조체에서 속성 감시자를 사용하는 예제를 작성합니다.
프로퍼티의 값의 변화를 관찰하며, 값이 변경될때마다 응답합니다.
지연 프로퍼티를 제외한 모든 프로퍼티에 Observer 선언이 가능합니다.

```swift
class SomeClass {
    var timer: Timer? {
        willSet {
            timer?.invalidate()
        }
    }
}
```
willSet은 값이 변경되기 전 호출됩니다.
예시에선 timer의 값이 변경될 때 기존의 timer을 invalidate하고 있습니다.

```swift
class CustomLabel: UILabel {
    var title: String? {
        didSet {
            text = title
        }
    }
}
```
didSet은 값이 변경된 후 호출됩니다.
예시에선 개발자가 생성한 Label에 Title이란 프로퍼티를 선언하고, 해당 값이 변경되면 Label의 text값을 변경하고 있습니다.
