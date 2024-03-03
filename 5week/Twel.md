## Swift에서 프로토콜의 개념을 설명합니다.
어떤 기능에 적합한 특정 메서드, 기타 요구사항을 정의한 '약속'
클래스, 구조체, 열거형에 채택될 수 있으며 프로토콜에 정의된 기능들을 구현해야만 한다.

## Swift에서 프로토콜을 정의하는 간단한 예제를 작성해보세요.
```swift
protocol SomePortocol: AnyObject {
  func someMethod()
}

final class SomeClass: SomeProtocol {
  func someMethod() { ... }
}
```

## 간단한 프로토콜인 "Animatable"을 만들고 "animate()"라는 메서드 요구사항을 가지도록 예제를 작성하세요.

```swift
protocol Animatable: AnyObject {
  func animate()
}
```

## "Printable"이라는 프로토콜을 생성하고 인수가 없는 초기화 메서드를 가지도록 예제를 작성하세요.
```swift
protocol Printable: AnyObject {
  init() { }
}
```

## 아래의 지침을 사용하여 "Indexed" 프로토콜과 이를 구현하는 "MyArray" 클래스의 사용법을 보여주는 Swift 코드 예제를 작성합니다.
1. 연관 유형(associatedtype) 'Element'를 사용하여 주어진 인덱스에서 요소를 반환하기 위한 서브스크립트 요구 사항이 있는 "Indexed"라는 프로토콜을 정의합니다.
2. "Indexed" 프로토콜을 구현하는 "MyArray"라는 클래스를 만듭니다.
3. "MyArray" 클래스에서 "elements"라는 private 속성을 선언하여 정수 배열을 저장합니다.
4. "MyArray" 클래스에서 서브스크립트 요구 사항을 구현하여 인덱스가 유효한 범위 내에 있으면 지정된 인덱스에 있는 요소를 반환하고 인덱스가 범위를 벗어나면 nil을 반환합니다.
5. "MyArray" 클래스의 인스턴스를 만들고 정의된 서브스크립트를 사용하여 해당 요소에 액세스하는 방법을 보여줍니다.
```swift
protocol Indexed: AnyObject {
  associatedtype Element
  subscript(index: Int) -> Element? { get }
}

class MyArray: Indexed {
  private var elements = [1, 2, 3, 4, 5]

  subscript(index: Int) -> Element? {
    if index >= 0 && index < elements.count { return elements[index] }
    else { return nil }
  }
}

var array = MyArray()
array[0] // 1 출력
array[9] // nil 출력
```

## Drawble 프로토콜을 아래의 요구사항에 맞게 작성
1. "draw"라는 메서드 요구 사항으로 "Drawable"이라는 프로토콜을 정의합니다.
2. "Drawable" 프로토콜을 준수하는 두 개의 클래스 "Circle" 및 "Rectangle"을 만듭니다.
3. 각 클래스에 대해 "draw" 메서드를 구현하여 그려지는 도형에 대한 설명을 print 함수로 작성합니다.
4. "Drawable" 프로토콜을 준수하는 배열을 인수로 사용하고 각 개체에서 "draw" 메서드를 호출하는 "drawShapes"라는 함수를 만듭니다.
5. "Circle" 및 "Rectangle" 인스턴스를 생성하고 이러한 인스턴스를 포함하는 배열로 "drawShapes" 함수를 호출합니다.
```swift
protocol Drawable: AnyObject {
  func draw()
}

class Circle: Drawable {
  func draw() {
    print("Circle")
  }
}

class Rectangle: Drawable {
  func draw() {
    print("Rectangle")
  }
}

func drawShapes(_ drawable: [Drawable]) {
  drawable.forEach { $0.draw() }
}
drawShapes[Circle(), Rectangle()]
```

## "Drivable"이라는 프로토콜이 다른 프로토콜인 "Steerable"을 상속하는 예제를 작성하세요.
```swift
protocol Steerable {
  func someMethod()
}

protocol Drivable: Steerable {
  func otherMethod()
}
```

## "@objc" 속성을 사용하여 "Flyable" 프로토콜에 선택적 요구사항을 구현하고, 이 프로토콜을 채택하는 클래스를 예제로 작성하세요.
```swift
@objc protocol Flyable: AnyObject {
  func essentialMethod()
  @objc optional func someMethod()
}

class Fly: Flyable {
  func essentialMethod() { ... }
}
```

## Drawble 프로토콜 정의
1. "Drawable" 프로토콜을 정의하고 "draw()" 메서드 요구 사항을 작성합니다.
2. "Drawable" 프로토콜을 확장하여 "draw()" 메서드에 대한 기본 구현을 제공합니다.
3. "Drawable" 프로토콜을 준수하는 "Circle" 구조체를 만듭니다.
4. "Circle" 구조체의 인스턴스를 만들고 "draw()" 메서드를 호출합니다.
5. "Circle" 구조체에 "draw()" 메서드의 사용자 지정 구현이 제공되지 않을 때 "draw()" 메서드의 기본 구현이 호출되는지 확인합니다.
```swift
protocol Drawable {
  func draw()
}

extension Drawable {
  func draw() { ... }
}

struct Circle: Drawable {}
Cricle().draw() // 가능
```


## Swift에서 프로토콜 지향 프로그래밍이란 무엇인지 설명합니다.
필요한 기능만을 프로토콜로 분리하고, 다중 프로토콜을 상속받을 수 있도록 함.


## Swift의 프로토콜 확장에는 어떤 제한이 적용되는지 설명합니다.
```swift
protocol SomeProtocol: AnyObject { }

// 프로토콜 채택을 UIViewController 타입만 가능하도록 제한
extension SomeProtocol where Self: UIViewController {
}
```
