# 2주차 Jina

# 주어진 숫자의 제곱을 반환하는 함수를 작성하십시오.

```swift
func doubleNum(num1: Int, num2: Int) -> Int {
		return num1 * num2
}
```

# 가드(guard) 문을 사용하여 옵셔널 문자열(String?)을 안전하게 래핑 해제하는 함수를 구현합니다.

```swift
func optionalUnlockWrapping(str: String?) -> String {
		guard let str = str else { return "" }
		return str
}
```

# 옵셔널 변수를 생성하고 옵셔널 바인딩을 사용하여 해당 값을 안전하게 언래핑하는 함수를 작성합니다.

```swift
var optionalStr: String? = 2
func optionalUnwrapping() {
		if let str = optionalStr {
				print(optionalStr)
		}
}
```

# 정수 집합을 받아서 짝수만 포함하는 집합을 반환하는 함수를 작성하세요.

```swift
func evenNum(num: [Int]) -> [Int] {
		return num.filter { $0 % 2 == 0 }
}
```

# 열거형에서 unknown 키워드의 목적을 설명하십시오.

- 모든 케이스를 다루지 않은 경우 경고를 통해 알려줌
- 만약, default를 사용하면 경고가 뜨지 않아 새로 생긴 케이스를 인지할 수 없음

```swift
switch a {
case .b:
	print("b")
@unknown default:
	print("c")
}
```
