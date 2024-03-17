# 7주차 Jina
# 제네릭 문법의 필요성에 대해 설명합니다.

- 코드를 재사용하기에 용이합니다.
- 유연하고 확장 가능해집니다.

# 제네릭 'Box' 구조체를 만듭니다. 이 구조체는 모든 타입의 item을 보유할 수 있어야합니다.

> Box 구조체에는 다음이 있어야합니다.
> 

> item 을 저장하는 item 이라는 저장속성을 정의합니다. 이 속성은 제네릭 형식이어야 합니다.
> 

> 제네릭 타입의 항목을 가져와서 item 속성에 저장하는 생성자를 정의합니다.
> 

> item 을 반환하는 getItem 이라는 메서드를 작성합니다. 반환타입(return type)은 제네릭이어야 합니다.
> 

> 제네릭 'Box' 구조체를 정의했으면 Box 의 두 인스턴스를 만듭니다. 하나는 Int 타입의 Box 구조체이고, 다른 하나는 String 타입의 Box 구조체입니다.
getItem 메서드를 사용해서 Box인스턴스 생성시 저장한 item 항목을 찾고 출력하는 예제를 작성합니다.
> 

```swift
struct Box<T> {
    var item: T
    
    init(item: T) {
        self.item = item
    }

    func getItem() -> T {
        return item
    }
}

let intBox = Box(item: 7)
let stringBox = Box(item: "Hi")

intBox.getItem() // 7
stringBox.getItem() // "Hi"
```

# 다음은 프로토콜에서 제네릭 구문을 사용하는 간단한 연습문제입니다.

> 연관된 타입(associatedtype)인 'Item' 을 포함하는 'Container' 라는 프로토콜을 정의합니다.
컨테이너 프로토콜에는 다음 두가지 기능의 요구사항을 정의합니다.
> 

> associatedtype 의 item 을 가져와서 Container에 추가하는 'add(item:)' 메서드
> 

> 컨테이너에서 item을 제거하고 반환하는 'remove() -> Item' 메서드
> 

> 다음으로 'Container' 프로토콜을 준수하는 'Basket' 클래스를 만듭니다. Basket 은 문자열 타입의 item을 가져야합니다.
Basket 클래스는 items 라는 빈 배열을 가집니다. var items = [String](notion://www.notion.so/7-Jina-74f17c69f27d4b328be8fb2c1019f177)
그리고 Basket 클래스가 Container 프로토콜을 준수할 수 있도록 정의된 요구사항을 구현합니다.
> 

> 마지막으로 Basket 클래스의 인스턴스를 만들고 'add(item:)' 메서드를 사용하여 일부 item 을 추가하고
'remove()' 메서드를 사용하여 배열의 마지막 항목을 제거하고 반환된 item을 인쇄하는 예제를  작성합니다.
> 

```swift
protocol Container {
    associatedtype Item
    mutating func add(item: Item)
    mutating func remove() -> Item
}

class Basket: Container {
    var items = [String]()
    
    func add(item: String) {
        items.append(item)
    }
    
    func remove() -> String {
        return items.removeLast()
    }
}

var basket = Basket()
basket.add(item: "Hi")
basket.add(item: "Hello")
basket.add(item: "People")
print(basket.items) // ["Hi", "Hello", "People"]
basket.remove()
print(basket.items) // ["Hi", "Hello"]
```
