## 이름은 같지만 매개변수 유형이 다른 두 개의 함수를 만들어 함수 오버로딩을 구현하십시오.
```swift
func add(_ a: Int, _ b: Int) -> Int {
  return a + b
}

func add(_ a: CGFloat, _ b: CGFloat) -> CGFloat {
  return a + b
}
```

## 주어진 숫자의 팩토리얼을 계산하는 재귀 함수를 작성하십시오.
```swift
var rst: Int = 1
func factorial(_ num: Int) {
    if num <= 0 { print("result : \(rst)") }
    else { rst *= num; factorial(num - 1) }
}
```

## 정수 배열을 만들고 요소를 추가하고, 요소를 제거하고, 특정 인덱스에 있는 요소에 액세스하는 방법을 보여줍니다.
```swift
var intArray = [Int]()

// 요소 추가
intArray.append(3)
// 배열 요소 추가
intArray.append(contentsOf: [1, 2, 3, 4, 5, 6, 7])
// 첫번째 인덱스 삭제
intArray.removeFirst()
// 특정 인덱스 접근
intArray[3]  // 4
```

## 원시 값으로 열거형을 구현하고 열거형 케이스의 원시 값에 접근하는 방법을 설명합니다.
```swift
// 원시 값이 문자열인 Size 열거형 생성
enum Size: String {
  case S = "small"
  case M = "medium"
  case L = "large"
  case XL = "extra large"
}

Size.M.rawValue // medium
```

