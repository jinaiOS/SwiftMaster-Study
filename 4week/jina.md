# 4주차 Jina

# 다운캐스팅의 개념에 대해 설명하고 다운캐스팅을 사용하는 이유도 같이 설명하세요.

- 부모 클래스의 인스턴스를 자식 클래스의 인스턴스로 변환합니다
- 업캐스팅은 반드시 성공할 때 사용이 가능하다. 다운캐스팅은 실패를 해도 optional로 보호할 수 있습니다.

# 다형성이란 무엇이며, 클래스 상속과 관련된 프로그래밍 예제를 작성하세요.

- 하나의 인스턴스가 여러가지의 타입의 형태로 표현될 수 있습니다.

```swift
class Animal {
    func sound() {
        print("동물이 소리를 냅니다")
    }
}

class Dog: Animal {
    override func sound() {
        print("멍멍")
    }
}

class Cat: Animal {
    override func sound() {
        print("야옹")
    }
}

func makeSound(for animal: Animal) {
    animal.sound()
}

let myAnimal: Animal = Dog()
makeSound(for: myAnimal) // 멍멍

let myAnimal: Animal = Cat()
makeSound(for: myAnimal) // 야옹
```

# Any와 AnyObject 타입을 사용하여 다양한 데이터 타입을 저장하고 캐스팅하는 예제를 작성하세요.

## Any

```swift
var some: Any = "Swift"

(some as? String).count // 타입캐스팅해야지만 문자열 개수를 출력할 수 있다.

let array: [Any] = [0, "hi", 3.5, Person(), {(name: String) in return name}]

(array[1] as! String).count
```

### 옵셔널값의 Any 변환

```swift
let number: Int? = 3
print(number as Any) // optional 타입도 포함해서 경고를 없앰
```

## AnyObject

```swift
let array: [AnyObject] = [Person(), Superman(), NSString()]

(array[0] as! Person).name
```

```swift
switch item {
case is Int:
    // item이 Int 타입일 경우 여기가 실행된다.
    break
case let num as Double:
    // item을 Double 타입으로 캐스팅할 수 있다면, 그 값을 num 변수에 할당하고 여기가 실행된다.
    break
case is String:
    // item이 String 타입일 경우 여기가 실행된다.
    break
case let person as Person:
    // item을 Person 타입으로 캐스팅할 수 있다면, 그 값을 person 변수에 할당하고 여기가 실행된다.
    break
case is (String) -> String:
    // item이 String을 매개변수로 받고 String을 반환하는 함수 타입일 경우 여기가 실행된다.
    break
default:
    break
}
```

# 확장(Extension)의 개념에 대해 설명하고 Int 타입에 확장을 추가하여, 짝수인지 판별하는 계산속성(get)을 구현하세요.

- 이미 존재하는 타입에 메서드를 **추가**하는 것입니다.
- 상속은 되지만 재정의는 불가합니다.

```swift
extension Int {
    var isEven: Bool {
        return self % 2 == 0
    }
}
```

# Int 타입에 확장을 추가하여, 숫자를 두 배로 곱하는 메서드를 구현하세요.

```swift
extension Int {
    func doubled() -> Int {
        return self * 2
    }
}
```

# 확장에서 생성자에 대한 규칙을 참조타입(클래스)과 값타입(구조체열거형)으로 구분하여 설명하시오.

## 참조 타입

- 편의 생성자만 추가 가능합니다
- 지정생성자를 추가 할 수 없습니다. 본래의 클래스에 구현해야 합니다.
- 소멸자를 추가 할 수 없습니다. 본래의 클래스에 구현해야 합니다.

## 값타입

- 생성자를 추가 할 수 없습니다.
- 그러나 추가적인 생성자를 구현할 수 있으며, 이때 모든 저장 프로퍼티가 초기화해야 합니다.

# Int 타입에 대한 확장을 이용하여 주어진 인덱스 위치에 있는 자리수 값을 반환하는 서브스크립트를 구현하세요.

```swift
extension Int {
    subscript(index: Int) -> Int? {
        let intArr = String(self).map { Int(String($0)) }
        guard index >= 0 && index < intArr.count else { return nil }
        return intArr[index]
    }
}
```

# Int 타입에 대한 확장으로 중첩타입을 이용하여 양수인지 음수인지 판별하는 기능을 구현하세요.

```swift
extension Int {

    enum NumberType {
        case positive, negative, zero
    }
    
    var numberType: NumberType {
        if self > 0 {
            return .positive
        } else if self < 0 {
            return .negative
        } else {
            return .zero
        }
    }
}
```
