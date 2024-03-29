# SwiftMaster-Study

앨런 Swift Master 30기 Study

# 1주차

## 음수는 2의 보수를 사용하여 메모리에 어떻게 표시됩니까?

- 컴퓨터는 2진법으로 설정 되어 있습니다.
- 8자리로 나타낼수 있고 첫번째는 부호를 결정하고 이를 MSB라고 한다 나머지 7자리는 데이터를 나타냅니다.
- 숫자 2를 이진법으로 나타내면`0000 0010` 다음처럼 나타내진다
- 숫자 -2를 첫번째 비트가 부호를 나타낸다고 해서 `1000 0010` 이라고 생각하면 안된다!
- 0을1 1을 0으로 처리한는걸 보수 라고 한다
- `0000 0010` → `1111 1101` 그 다음 1을 더해준다
- `1111 1110` 이게 -2이다

## 프로그래밍에서 일반적으로 사용되는 세 가지 특수 문자를 말하십시오.

- *세미콜론 (;)*: 하나의 코드가 끝낫을때 사용
- *콤마 (,)*: 변수나 배열의 값을 구분하는데 사용
- *따옴표 (' 또는 ")*: 문자열을 나타내는 데 사용

## Swift의 은 타입 앨리어스(Type Alias)는 무엇이며 왜 사용해야 합니까?

- Type Alias는 기존의 타입을 직접 별칭을 지어 타입을 새로 지정하는걸 뜻합니다
- 다음 처럼 선언함으로써 나중에 해당 변수나, 객체가 어떤 데이터를 뜻하는지 쉽게 파악할수 있어서 가독성에 좋습니다.

## 산술 연산의 우선 순위는 무엇입니까?

- 연산을 할때도 각 우선순위가 있다.
- ( ) 가로 > 제곱 >곱셈, 나눗셈 > 더하기, 빼기

## 패턴 매칭과 함께 switch 문을 사용하는 예를 제시하십시오.

- 패턴매칭 연산자: 값이 범위내에 있는지 확인하는 연산자

```swift
var status = 200

switch country
case 200...299:
  print("통신은 성공!!!")
case 400...499:
  print("클라이언트 에러...")
case 500...599:
  print("서버 에러;;")
default:
  print("몬지 모르는 에러")
```

## Swift 함수에서 튜플을 어떻게 사용할 수 있습니까?

- 튜플은 여러변수를 하나로 모아서 사용할때 유용하다
- 함수에서는 여러 방법으로 사용할수 있다

1. 속성으로 사용하기

```swift
var food: (korea: String, japan: String) = ("국밥", "초밥")

print("한식: \(food.korea)")
print("일식: \(food.japan)")

```

2. 튜플로 된 값을 return 하기
```swift
func orderDrink() -> (coffee: String, juice: String) {
  let coffee = "커피"
  let juice = "쥬스"
  return (coffee, juice)
}

var drink = orderDrink()

print("나는 \(drink.coffee) 주문했어")
print("친구는 \(drink.juice) 주문했어")
```

## Swift에서 for-in 루프를 어떻게 생성합니까?

- for (변수) in 범위

```swift
var animals = ["코끼리", "호랑이", "악어", "팽귄"]

print("우리 동물원에는", terminator: " ")

for animal in animals {
  print(animal, terminator: " ")
}

print("있습니다.")
```

## 두 숫자의 곱셈을 계산하는 함수를 작성하십시오.

```swift
func multiply(_ a: Int, _ b: Int) -> Int {
  return a * b
}

multiply(10, 9)
```
