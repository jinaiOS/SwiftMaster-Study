### Swift의 map, filter, reduce와 같은 고차 함수에 대해 설명하고 사용 예시를 작성하세요.

- map
    - 배열의 각 요소에 대해 주어진 함수 실행하고, 그 결과를 새로운 배열로 반환
    
    ```swift
    let numbers = [1, 2, 3, 4, 5]
    let newNumber = numbers.map { $0 * 2 }
    print(newNumber) // [2, 4, 6, 8, 10]
    ```
    
- filter
    - 배열의 요소 중 주어진 조건을 만족하는 요소들로 이루어진 새로운 배열을 반환
    
    ```swift
    let numbers = [1, 2, 3, 4, 5]
    let newNumber = numbers.map { $0 % 2 == 0 }
    print(newNumber) // [2, 4
    ```
    
- reduce
    - 배열의 요소들을 하나의 값으로 결합시키는 데 사용. 초기값과 클로저를 이용하여 각 요소를 결합하여 최종 결과를 반환
    
    ```swift
    let numbers = [1, 2, 3, 4, 5]
    let sum = numbers.reduce(0) { $0 + $1 }
    print(sum) // 15
    ```
    

### Swift의 forEach, compactMap 및 flatMap와 같은 고차 함수에 대해 설명하고 사용 예시를 작성하세요.

- **forEach**:
    - 배열의 각 요소에 대해 주어진 함수를 실행. 그러나 **`forEach`**는 반환값을 갖지 않음
    
    ```swift
    let numbers = [1, 2, 3, 4, 5]
    numbers.forEach { print($0) // 1, 2, 3, 4, 5
    ```
    
- **compactMap**:
    - 배열의 각 요소에 대해 주어진 값을 실행하고, 그 결과가 nil이 아닌 것들로 새로운 배열을 생성
    
    ```swift
    let strings = ["1", "2", "three", "4", "five"]
    let numbers = strings.compactMap { Int($0) } // [1, 2, 4]
    ```
    
- **flatMap**:
    - 반환값이 옵셔널인 경우 옵셔널 바인딩을 수행하여 옵셔널이 해제된 값들로 이루어진 새로운 배열을 생성
    
    ```swift
    let numbers = [[1, 2], [3, 4], [5, 6]]
    let flattened = numbers.flatMap { $0 } // [1, 2, 3, 4, 5, 6]
    ```
    

### Swift의 함수형 프로그래밍에 대해 설명하세요.

- 프로그램을 작성하는 방식 중 하나로, 함수를 값으로 다루고 함수 조합을 통해 작업을 수행하는 패러다임
- 특징
    1. **함수를 값으로 다룸**: Swift에서는 함수를 일급 객체로 취급합니다. 즉, 함수를 변수에 할당하고 다른 함수의 인자로 전달하거나 함수의 반환값으로 사용할 수 있습니다.
    2. **불변성**: 함수형 프로그래밍에서는 데이터를 변경할 수 없는 것을 선호합니다.
    3. **순수 함수**: 함수형 프로그래밍에서는 부작용이 없는 순수 함수를 선호합니다.
    4. **고차 함수:** 고차 함수는 다른 함수를 인자로 받거나 함수를 반환하는 함수를 말합니다. **`map`**, **`filter`**, **`reduce`**, **`flatMap`** 등의 고차 함수를 제공하여 함수형 프로그래밍을 지원합니다.
    5. **불변성을 유지하는 데이터 구조**: 함수형 프로그래밍에서는 불변성을 유지하는 데이터 구조를 선호합니다.
    6. **재귀**: 함수형 프로그래밍에서는 재귀를 통해 반복 작업을 수행합니다.

### 

### 옵셔널 체이닝(Optional Chaining) 관련 문제입니다. 아래 설명을 참고하여 구현해보세요.

1. author라는 Author 인스턴스를 만듭니다.

2. 제목이 "Swift Programming"인 book이라는 Book 인스턴스를 생성합니다.

3. 이름이 "OpenAI Press"인 publisher라는 Publisher 인스턴스를 만듭니다.

4. author.book 속성에 book 인스턴스를 할당합니다.

5. publisher 인스턴스를 book.publisher 속성에 할당합니다.

6. Optional chaining을 사용하여 저자 책의 출판사 이름을 검색합니다. 결과를 publisherName이라는 상수에 저장합니다.

```swift
struct Author {
    var book: Book?
}

struct Book {
    var title: String
    var publisher: Publisher?
}

struct Publisher {
    var name: String
}

// 1
let author = Author()

// 2
let book = Book(title: "Swift Programming", publisher: nil)

// 3
let publisher = Publisher(name: "OpenAI Press")

// 4
author.book = book

// 5
book.publisher = publisher

// 6
let publisherName = author.book?.publisher?.name
print(publisherName ?? "Publisher not found")
```
