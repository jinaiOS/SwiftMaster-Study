## Result Type 에 대해 설명합니다.
Enum 타입으로 경우에 따른 연관값을 포함하여, 성공과 실패를 나타내는 값입니다.

## 다음은 Result Type을 사용하는 간단한 연습문제입니다.
1. Error 프로토콜을 준수하는 StringError 열거형을 만듭니다. 이 열거형에는 String을 허용하는 하나의 케이스 .generic 가 있어야 합니다.
2. Bool 타입인 success를 인수로 취하고 Result<String, StringError> 를 반환하는 processData(success:) 함수를 정의합니다.
success가 true이면 "Data processed successfully" 이라는 문자열과 함께 .success 케이스를 반환합니다. 
success가 false인 경우 "Data processing failed"라는 문자열을 포함하는 StringError.generic 값과 함께 .failure 케이스를 반환합니다.
3. true 및 false로 processData(success:) 함수를 호출하고 switch 문을 사용하여 Result 를 처리합니다.
결과가 .failure 인 경우 오류 메시지를 출력합니다.

```swift
enum StringError: Error {
  case generic(String)
}

func processData(success: Bool) -> ResultType<String, StringError> {
  if success { return .success("Data processed successfully") }
  else  { return .failure(.generic("Data processing failed")) }
}

switch process(success: true) {
  case .success(let msg): print(msg)
  case .failure(let error):
    switch error {
      case .generic(let msg): print(msg)
    }
}

switch process(success: false) {
  case .success(let msg): print(msg)
  case .failure(let error):
    switch error {
      case .generic(let msg): print(msg)
    }
}
```

## 다음은 스위프트에서 날짜 및 시간을 처리하는 것과 관련된 연습문제입니다.
1. 현재 날짜와 시간을 나타내는 'Date' 타입의 인스턴스를 만듭니다. 이 날짜를 출력해보세요.
2. 현재 날짜에서 7일(1주일) 전 날짜를 계산합니다. 이 날짜를 출력해보세요. Calendar.current.date(byAdding: ,value: , to: ) 메서드를 이용합니다.
3. DateFormatter 타입의 인스턴스를 생성하고 현재 날짜를 "MM-dd-yyy HH:mm" 형식의 문자열 형식으로 지정합니다. 이 문자열을 출력해보세요.
```swift
let date = Date()
print(date)

let aWeekDate = Calendar.current.date(byAdding: .day, value: -7, to: date)
print(aWeekDate)

let dateFormatter = DateFormatter()
dateFormatter.format = "MM-dd-yyy HH:mm"
print(dateFormatter.string(from date))
```

## 접근제어자 에 대해 설명합니다.
소스파일 간, 모듈 간 접근을 제한할 수 있는 기능입니다.

- Open:
가장 넓은 범위로 지정된 요소는 어디서든 사용 가능합니다.
클래스에서만 사용이 가능하며, subclassing 및 override에 제약이 없습니다.
 
- Public:
클래스가 정의된 모듈 내에서만 subclassing 및 override 할 수 있습니다.
 
- Internal:
자동으로 지정되는 기본값입니다.
모듈 내부에서는 어디서든 사용 가능합니다.
 
- FilePriavte:
해당 소스파일 내부에서만 사용 가능합니다. (모듈이 같아도 다른 소스파일에서는 사용불가)
 
- private
가장 한정적인 범위입니다. 해당 요소를 정의한 범위 내에서만 사용가능합니다.
