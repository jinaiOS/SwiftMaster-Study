## 클로저가 주변 컨텍스트에서 변수와 상수에 대한 참조를 캡처하고 저장하는 방법과 이것이 메모리 관리에 어떤 영향을 미칠 수 있는지 설명합니다.
클로저 내부에서 변수와 상수를 원활히 사용하기 위해 캡처하고 있다. 이를 값 캐처라고 한다.
값 캡처가 발생하면 RC가 하나 증가하므로 강력한 순환 참조가 발생한다.
이를 방지하기 위해 캡처리스트를 사용할 수 있다.

weak : 참조가 존재하더라도 메모리에서 해제될 수 있다. 따라서 nil이 될수도 있다.
<br/>
unowned : 클로저의 수명동안 항상 존재한다고 취금하며 RC를 증가시키지 않는다.

## 클로저에 의해 캡처된 값의 캡처 시맨틱을 정의하기 위해 Swift에서 캡처 목록을 사용하는 방법을 설명합니다.
```swift
class SimpleClass{
    var value: Int = 0
}

var x: SimpleClass? = SimpleClass()
var y = SimpleClass()

let closure = { [weak x, unowned y] in
	print(x?.value, y.value)
}

x.value = 3
y.value = 20

closure() // 3, 20
```
## 개체 내의 클로저에서 self 키워드를 사용하여 개체에 대한 약한 참조를 캡처하는 예제를 작성하고 이에 대해 설명합니다.
```swift
func someMethod(handler: @escaping () -> Void) {
  handler { [weak self] in
    guard let strongSelf = self else { return }
  }
}
```
## Swift에서 에러 처리의 목적은 무엇인지 설명하고 에러 타입을 어떻게 정의하는지 예제를 작성합니다.
프로그램 실행중에 발생하는 오류를 정의하고 관리하기위해 사용된다.
```swift
enum APIError: Error {
case keyNotFound
case valueNotFound
case invalidURL
}
```

## 함수에 throws 키워드를 사용하는 예제를 작성하고 throws 키워드의 의미에 대해 설명합니다.
함수 내부에서 오류를 발생시킬 수 있다는 의미
```swift
func someMethod(_ throwError: Bool) throws {
    if throwError { fatalError() }
    print("is Not Throw Error")
}
```
