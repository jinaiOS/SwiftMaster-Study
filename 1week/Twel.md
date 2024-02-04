# 1주차 과제

## 컴퓨터 시스템에서 CPU의 주요 기능은 무엇입니까?
CPU는 메모리에 저장된 명령어를 읽어 들이고, 읽어 들인 명령어를 해석하고, 실행하는 부품입니다. (기억, 해석, 연산, 제어)


## Swift에서 플레이그라운드의 목적은 무엇입니까?
XCode의 실행 없이 단순한 로직을 확인하고 싶을 때 사용합니다. 

## Swift에서 변수와 상수의 차이점은 무엇입니까?
### **변수**
- 초기 값 세팅 이후에도 값 변경이 가능합니다.
- `var`키워드로 선언하여 사용합니다.
``` swift
var <constant name>: <type> = <expression>
```
### **상수**
- 초기 값 세팅 이후 값 변경이 불가능합니다.
- 최초 초기화 후 값 변경이 불가하기 때문에, 반드시 초기화와 함께 작성되어야 합니다.
- `let`키워드로 선언하여 사용합니다.
``` swift
let <constant name>: <type> = <expression>
```
![변수와상수, Swift의 타입 추론에 의해 타입 선언이 생략된 상태](https://github.com/jinaiOS/SwiftMaster-Study/assets/37203919/21331768-9c84-4bfb-8990-518e7ebb4135)

## 프로그래밍에서 경고와 오류의 차이점은 무엇입니까?
### 경고
![warning](https://github.com/jinaiOS/SwiftMaster-Study/assets/37203919/a191926b-dca9-46b9-bcc6-186ad490a3be)

- XCode의 컴파일러에서 개발자에게 수정이 필요한 부분이 있음을 알려줍니다.
- 실제 앱 실행에는 영향을 주지 않습니다.

### 오류
![error](https://github.com/jinaiOS/SwiftMaster-Study/assets/37203919/a2550459-33c4-4895-a9e5-96416b156800)

* XCode의 컴파일러가 컴파일 실행 중 더이상 진행하지 못하는 이슈가 발생함을 알려줍니다.
* 발생한 오류가 해결이 되어야 앱 실행이 가능합니다.
* 앱 실행중에 오류(컴파일 오류X)가 발생하면 앱은 강제 종료 됩니다.

< 앱 실행 중 마주칠 수 있는 오류 >
- Nil Exception
- Forced Unwrapping
- Out of Range


## Swift의 if-else 문에 대해 설명하세요.
``` swift
if <조건문> {
  <조건문이 참일 경우 실행>
} else {
  <조건문이 거짓일 경우 실행>
}

// 옵셔널 추출
let string: String? = nil
if let str = string {
  print(str)
} else {
  print("string값이 nil입니다.")
}

// 참 거짓 확인
let isSelected: Bool = false
if isSelected {
  print("isSelected가 ture일때 실행됩니다.")
} else {
  print("isSelected가 false일때 실행됩니다.")
}
```

## 조건문을 사용하여 간단한 가위바위보 게임을 만듭니다.
> 가위, 바위, 보를 각각 0, 1, 2로 임의 정의합니다.<br/>
> 내가 선택하는 값, 그 값과 비교할 값 모두 random으로 정의되도록 합니다.
``` swift
let RPS = [0, 1, 2]
let computeSelect = RPS.randomElement()!
let mySelect = RPS.randomElement()!

if computeSelect == mySelect {
    print("비겼습니다.")
} else {
    if computeSelect == 0 {
        print(mySelect == 1 ? "이겼습니다." : "졌습니다.")
    } else if computeSelect == 1 {
        print(mySelect == 0 ? "졌습니다." : "이겼습니다.")
    } else {
        print(mySelect == 0 ? "이겼습니다." : "졌습니다.")
    }
}
```

## Swift에서 삼항 연산자의 예를 작성하십시오.
``` swift
// 값 할당
let number: Int = 10
var variable: String = ""

// if-else문 사용
if number > 5 {
  variable = "5 초과"
} else {
  variable = "5 이하"
}

// 삼항 연산자 사용
let constant = number > 5 ? "5 초과" : "5 이하"

// 함수 실행
let isSelected: Bool = false

// if-else문 사용
if isSelected {
  trueFunction()
} else {
  falseFunction()
}

// 삼항 연산자 사용
isSelected ? trueFunction() : falseFunction()
```

## Swift에서 while 루프와 반복-while 루프의 차이점은 무엇입니까?

### while Roop
단일 조건문을 확인하여 조건문의 값이 false가 될때까지 하위 코드 블럭을 실행합니다.
루프를 통과할 때마다 조건을 확인합니다.
> 첫 반복이 시작 되기 전에 반복횟수를 알 수 없을때 가장 잘 사용됩니다.
``` swift
while <단일 조건문> {
  <실행 코드 구문>
}
```

### repeat-While
단일 조건문을 확인하기 전 우선 코드 블럭을 실행합니다. 그 후 단일 조건문의 값이 false가 될때까지 코드 블럭을 실행합니다.
``` swift
repeat {
  <실행 코드 구문>
} while <단일 조건문>
```

## Swift에서 함수의 기본 개념을 설명하십시오.
특정 작업을 수행하는 독립적인 코드 블럭입니다.<br/>
함수를 호출하기 위해 기능을 식별하는 이름을 지정합니다.<br/>
매개별수 및 반환값을 정의할 수 있습니다.<br/>
``` swift
func <함수 식별자 이름>(<매개변수 명>: <매개변수 타입>) -> <반환 타입> {
    <...실행 구문...>
}
```
