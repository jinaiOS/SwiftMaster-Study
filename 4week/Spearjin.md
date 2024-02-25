### 클래스(참조 유형)와 구조체(값 유형) 간의 메모리 관리 차이를 설명합니다.(인스턴스의 복사와 관련하여 설명할것)

```swift
class Dog {
    func bark() {
        print("월월!!!")
    }
}

let myDog = Dog()

myDog.bark() 
```

### "Dog" 클래스에 "품종(breed)"를 나타내는 정적 속성을 추가하고, 이 값을 출력하는 타입 메서드를 작성하세요.

```swift
class Dog {
	static var breed: String = "비숑"

	static func printBreed() {
		print(\(self.breed))
	}
}
```

### 서브스크립트에 대해 설명하고 관련 예제를 작성하세요.

- 서브스크립트는 **`subscript`** 키워드를 사용하여 정의하며, 하나 이상의 입력 매개변수와 반환 타입이 있습니다. 이 입력 매개변수는 서브스크립트를 호출할 때 사용되며, 인스턴스에 대한 접근을 제어합니다.
    
    ```swift
    class MyArray {
        var elements: [Int] = [0, 1, 2, 3]
        
        subscript(index: Int) -> Int {
            get {
                return elements[index]
            }
            set(newValue) {
                elements[index] = newValue
            }
        }
    }
    ```
    

### Car 클래스를 만들고, 속도(speed) 속성에 대한 private 접근 제어를 적용하세요. 속도를 변경하는 인스턴스 메서드를 추가하고 해당 메서드에 public 접근 제어를 적용한 예제를 작성하세요.

```swift
class Car {
	private var speed: Int = 0

	public func getSpeed() -> Int {
		return self.speed
	}

	public func setSpeed(_, newSpeed: Int) {
		self.speed = newSpeed
	}
}

let myCar = Car()

myCar.setSpeed(100)

print("속도: \(myCar.getSpeed())km/h")
```

### Logger라는 이름의 클래스를 만들고, 싱글턴 패턴을 적용하여 앱 전체에서 하나의 인스턴스만 사용할 수 있도록 작성하세요.

```swift
class Logger {
    static let shared = Logger()
    
    private init() {}
    
    func print(message: String) {
        print("Log: \(message)")
    }
}

let logger = Logger.shared
logger.print(message: "앱 실행 중")

let anotherLogger = Logger.shared
anotherLogger.print(message: "다른 메시지") 
```

### Vehicle 클래스를 만들고 Car 클래스와 Bicycle 클래스가 이를 상속하는 예제를 작성하세요.

```swift
class Vehicle {
    var brand: String
    
    init(brand: String) {
        self.brand = brand
    
}

class Car: Vehicle {
    var numberOfSeats: Int
    
    init(brand: String, numberOfSeats: Int) {
        self.numberOfSeats = numberOfSeats
        super.init(brand: brand)
    }
 }

class Bicycle: Vehicle {
    var numberOfWheels: Int
    
    init(brand: String, numberOfWheels: Int) {
        self.numberOfWheels = numberOfWheels
        super.init(brand: brand)
    
}

let myCar = Car(brand: "BMW", numberOfSeats: 4)
let myBicycle = Bicycle(brand: "삼천리", numberOfWheels: 2)
```

### Vehicle 클래스에 drive() 메서드를 추가하고, Car 클래스와 Bicycle 클래스에서 이를 오버라이드하여 적절한 동작을 구현하는 예제를 작성하세요.

```swift
class Vehicle {
    var brand: String
    
    init(brand: String) {
        self.brand = brand
    }
    
    func drive() {
        print("이동")
    }
}

class Car: Vehicle {
    var numberOfSeats: Int
    
    init(brand: String, numberOfSeats: Int) {
        self.numberOfSeats = numberOfSeats
        super.init(brand: brand)
    }
    
    override func drive() {
        print("차량 운전 중")
    }
}

class Bicycle: Vehicle {
    var numberOfWheels: Int
    
    init(brand: String, numberOfWheels: Int) {
        self.numberOfWheels = numberOfWheels
        super.init(brand: brand)
    }
    
    override func drive() {
        print("자전거 운행 중")
    }
}

let myCar = Car(brand: "BMW", numberOfSeats: 4)
myCar.drive()

let myBicycle = Bicycle(brand: "삼천리", numberOfWheels: 2)
myBicycle.drive()
```

### 상속 관계의 클래스들이 메모리에서 어떻게 배치되는지 설명하세요.

- 상속 관계의 클래스들이 메모리에서는 부모 클래스와 자식 클래스가 각각의 데이터 영역 존합재니다.
    
    하위 클래스는 부모 클래스의 모든 멤버 변수와 메서드를 포함하며, 추가적으로 자신만의 멤버 변수와 메서드를 가질 수 있습니다. 이러한 상속된 멤버 변수와 메서드는 연속적으로 메모리에 배치됩니다.
    
    메서드는 일반적으로 메모리의 다른 부분에 저장됩니다. 부모 클래스의 메서드는 부모 클래스의 메서드 테이블에 저장되고, 하위 클래스의 메서드는 그 아래에 추가됩니다.
    

### Car 클래스에 생성자를 추가하여 속도 값을 초기화할 수 있도록 예제를 작성하세요.
```
class Car {
    var speed: Int
    
    init(speed: Int) {
        self.speed = speed
    }
}

let myCar = Car(speed: 60)
```
