# 5주차 Jina
# Swift의 메서드 디스패치에 대해 설명합니다.

- 컴파일러와 런타임이 메서드 호출을 어떻게 처리하고, 구체적인 메서드 구현을 어떻게 선택하는지를 결정합니다.
- Direct Dispatch(직접 디스패치) - static
- Table Dispatch(동적 디스패치)
- Message Dispatch(메시지 디스패치)

# Swift에서 'self' 키워드와 'Self' 키워드의 차이점은 무엇인지 설명합니다.

- ‘self’ 인스턴스 자체를 나타내며, 인스턴스의 프로퍼티나 메서드에 접근할 때 사용합니다.
- ‘Self’ 타입 자체를 나타내며, 주로 프로토콜이나 제네릭 코드에서 사용합니다.

# 두 숫자의 합을 계산하는 클로저를 작성하고 변수에 할당하는 예제를 작성하세요.

```swift
let sum: (Int, Int) -> Int = { (num1, num2) in
    return num1 + num2
}

print(sum(1, 2)) // 3
```

# 클로저를 함수의 인수로 사용하는 예를 작성하고 이 상황에서 클로저를 사용하는 이유를 설명하십시오.

- 함수 호출 이후를 체크하여 커스터마이징할 수 있습니다.

```swift
func performOperation(with numbers: (Int, Int), operation: (Int, Int) -> Int) -> Int {
    return operation(numbers.0, numbers.1)
}

let sumResult = performOperation(with: (5, 3)) { $0 + $1 }
print(sumResult)  // 8
```

# 두 숫자의 합을 계산하는 클로저를 가져와서 후행 클로저 구문과 파라미터 및 생략등의 간소화 방법을 사용하여 구문을 최적화하는 예제를 작성합니다.

```swift
let sum = performOperation(with: (5, 3)) { $0 + $1 }
print(sum)  // 8
```

# 주변 컨텍스트에서 변수 및 상수에 대한 참조를 캡처하고 저장하는 예제를 작성하고 이와 관련하여 Swift에서 클로저의 메모리 구조를 설명합니다.

- 클로저는 참조 타입입니다. 메모리에서 참조 유형을 사용하여 변수 및 상수를 관리합니다.

```swift
func makeIncrementer(amount: Int) -> () -> Int {
    var total = 0
    let incrementer: () -> Int = {
        total += amount
        return total
    }
    return incrementer
}

let incrementByTen = makeIncrementer(amount: 10)
incrementByTen() // 10
incrementByTen() // 20
```

# 클로저와 함께 @escaping 및 @autoclosure 키워드를 함수 매개변수로 사용하는 두개의 함수 예제를 작성하십시오.

- @escaping: 함수의 실행이 끝난 상태에서 호출합니다.
    
    ```swift
    func requestLogin(completion: @escaping () -> Void) {
        
    }
    ```
    
- @autoclosure: 자동으로 클로저를 생성해줍니다.
    
    ```swift
    func loginIfTrue(_ predicate: @autoclosure () -> Bool) {
    
    }
    ```
