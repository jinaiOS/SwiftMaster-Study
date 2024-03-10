# 6주차 Jina

# do catch 블록을 사용하여 에러를 처리하는 예제를 작성합니다.

```swift
enum CommonError: Error {
    case invalid(need: Int)
}

func itemsCount() throws {
    let cnt = 2
    guard cnt >= 3 else {
        throw CommonError.invalid(need: 3)
    }
}

do { 
    try itemsCount()
} catch CommonError.invalid(let need) {
    print(need)
}
```

# defer 문에 대해 설명하고 에러가 발생될 수 있는 코드에 defer문이 어떤식으로 사용될 수 있는지 예제를 작성합니다.

- 함수가 끝나기 직전에 꼭 실행해야 하는 코드입니다.

```swift
func processFile(filename: String) {
    print("Start processing the file: \(filename)")
    
    let file = open(filename)
    defer {
        close(file)
        print("File \(filename) was closed.")
    }
    
    if file.isEmpty {
        return
    }
    
    print("Processing...")
}
```

# 아래코드는 영화진흥위원회 api로 데이터를 요청하여 일일 박스오피스 순위와 영화 이름을 출력하는 예제입니다. 아래 코드에서 URL, URLSession, JSONDecoder가 각각 어떤 역할을 하는지 설명합니다.

## URL

- api 주소를 가르킵니다.

## URLSession

- 네트워크 요청을 수행합니다.
- 서버로부터 데이터를 받아옵니다.

## JSONDecoder

- JSON 형식의 데이터를 데이터 모델로 디코딩합니다.

# Swift에서 메인큐인 DispatchQueue.main,  글로벌큐인 DispatchQueue.global(qos:),  커스텀 큐인 DispatchQueue.main(label:"...") 에 대해 설명합니다.

## DispatchQueue.main

- 메인 스레드와 연결된 직렬 큐입니다.
- 모든 UI 작업은 메인 스레드에서 실행 되어야 합니다.

## DispatchQueue.global(qos:)

- 시스템이 관리하는 병렬 큐입니다.
- 백그라운드에서 시간이 오래 걸리는 작업이나, UI와 직접적으로 관련되지 않는 작업일 때 사용합니다.
- 옵션: **`.userInteractive`**, **`.userInitiated`**, **`.utility`**, **`.background`**, **`.default`**, **`.unspecified`**

## DispatchQueue(label:"...")

- 개발자가 직접 생성하는 큐로 병렬, 직렬을 선택할 수 있습니다.
- label은 큐의 식별자입니다.

# Swift에서 GCD를 사용할 때 self 를 이용한 강력한 참조를 사용하는 경우 이러한 참조가 강력한 참조 순환이 발생하지 않게 weak self를 이용할 수 있도록 하는 방법에 대해 설명합니다.

```swift
DispatchQueue.main.async { [weak self] in
    guard let self else { return }
    imageview.image = UIImage(named: "ic_happy")
}
```

- [weak self]를 통해서 클로저 내에 약한 참조를 생성합니다.
- guard let self else { return }을 통해 self가 존재하는 경우에만 강하게 self를 참조하도록 설정합니다.
