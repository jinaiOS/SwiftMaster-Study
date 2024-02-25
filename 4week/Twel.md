## Bicycle 클래스에 생성자를 추가하여 속도 값을 초기화할 수 있도록 예제를 작성하세요.
```swift
class Bicycle {
    var color: UIColor
    var mile: CGFloat
    
    init(color: UIColor, mile: CGFloat) {
        self.color = color
        self.mile = mile
    }
}
```

## Car 클래스에 지정 생성자와 편의 생성자를 추가하세요. 지정 생성자를 사용하여 모든 속성을 초기화하고, 편의 생성자를 사용하여 일부 속성의 기본값을 제공하는 예제를 작성하세요.
```swift
class Car {
    var maker: String
    var sheets: Int
    
    required init(maker: String, sheets: Int) {
        self.maker = maker
        self.sheets = sheets
    }
    
    convenience init(maker: String) {
        self.init(maker: maker, sheets: 4)
    }
}
```

## 지정 생성자 / 편의 생성자 상속과 재정의 규칙 에 대해 설명하세요.
 1. 클래스 혹은 구조체는 하나 이상의 지정생성자를 가져야함
 2. 지정생성자에서 모든 프로퍼티 초기화 필요
 3. 편의 생성자는 특정 상황에서 편리한 초기화 방법을 제공하기 위해 사용. 상속 안됨
 4. 구조체는 상속이 불가능
 5. 하위 클래스에서 하나 이상의 지정 생성자를 정의하지 않을 시, 상위 클래스의 지정 생성자를 상속받음
 6. 하위 클래스에서 상위 클래스의 지정생성자 재정의가 필요할 때에는 override 키워드 사용 해야함

## 지정 생성자 / 편의 생성자 상속의 예외사항 에 대해 설명하세요.
 1. 하위 클래스에서 상위 클래스의 편의 생성자 접근이 불가
 2. 하위 클래스에서 하나 이상의 지정 생성자를 제공하면, 상위 클래스의 지정 생성자 상속받지 않음

## 필수 생성자가 있는 MyBaseClass를 작성하고, MySubClass가 MyBaseClass를 상속받아 필수 생성자를 구현하도록하세요.
```swift
class MyBaseClass {
    var name: String
    var type: String
    
    init(name: String, type: String) {
        self.name = name
        self.type = type
    }
}

class MySubClass: MyBaseClass {
    var subType: String
    
    init(subType: String) {
        self.subType = subType
        super.init(name: "sub", type: "type")
    }
}
```

## 실패 가능 생성자를 사용하여 Person 클래스를 구현하세요. Person 클래스는 이름과 나이를 저장하는 속성을 가지고 있으며, 이 속성들은 모두 초기화가 필요합니다. 나이는 0보다 작거나 같은 값이 들어올 경우 초기화가 실패합니다.
```swift
class Person {
    var name: String
    var age: Int
    
    init(name: String, age: Int) throws {
        if age <= 0 { fatalError("나이는 0보다 작을 수 없습니다.") }
        self.name = name
        self.age = age
    }
}
```

## Car 클래스에 소멸자(Deinitializer)를 추가하고, 클래스와 구조체의 주요 차이점을 설명하세요.
구조체는 deinitializer 사용이 불가능합니다.
```swift
class Car {
    deinit { print("메모리에서 해제됨") }
}
```

## is 연산자와 as 연산자의 사용법과 이유를 설명하세요.
-  is 연산자는 객체가 특정 클래스의 인스턴스(타입)인지 확인할 때 사용
-  as 연산자는 객체를 다른 타입으로 변환할 때 사용
