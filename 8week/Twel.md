## 다음은 Equatable 프로토콜 관련 연습문제입니다.

1. 'Double' 타입인 width 및 height의 두 가지 속성으로 구조체 Rectangle을 정의합니다. 
2. Rectangle이 Equatable 프로토콜을 준수하도록 합니다. 
3. 너비(width)와 높이(height)가 같으면 두 개의 사각형(rectangle)이 같은 것으로 간주되어야 합니다.
```swift
struct Rectangle: Equatable {
  var width: Double
  var height: Double

  static func ==(lhs: Rectangle, rhs: Rectangle) -> Bool {
    return lhs.width == rhs.width && lhs.height == rhs.height
  }
}
```


## 다음은 Comparable 프로토콜 관련 연습문제입니다.

1. 'String' 타입인 name과 'Double' 타입인 price 속성을 가진 Product 구조체를 정의합니다.
2. Product 구조체에 Comparable 프로토콜을 구현하여 두 제품을 가격을 기준으로 비교할 수 있도록 하세요.
3. findCheaperProduct(_:_:)라는 함수를 작성하세요. 이 함수는 두 개의 Product 인스턴스를 매개변수로 받고, 더 낮은 가격을 가진 제품을 반환해야 합니다. 가격을 비교하기 위해 < 연산자를 사용하세요.
```swift
struct Product: Comparable {
  var name: String
  var price: Double

  static func < (lhs: Product, rhs: Product) -> Bool {
    return lhs.price < rhs.price
  }
}

func findCheaperProduct(_ lhs: Product, _ rhs: Product) -> Product {
  return lhs < rhs ? lhs : rhs
}
```

