# 열거형

> 타입 자체를 한정된 사례 안에서 정의할 수 있는 타입이며, 개발자가 커스텀할 수 있는 타입이다.

```swift
enum Days {
    case monday
    case tuesday
    case wednesday
    case thursday
    case friday
    case saturday
    case sunday
}
```

### 원시값

> Raw Value(원시값)을 가진 열거형

```swift
enum Weekday: Int {
    case mon, tue, wed, thu, fri, sat, sun
}

var today: Weekday? = Weekday(rawValue: 3) // thu
```

### 연관값

> Associated Value(연관값)을 가진 열거형

```swift
enum Computer {
    case cpu(core: Int, ghz: Double)
}

var mine: Computer = Computer.cpu(core: 10, ghz: 3.6)

switch mine {
case Computer.cpu(let core, let ghz):
    print(core, ghz)
}
```

해당 연관값을 let으로 선언하고 구분해서 사용이 가능하다.

### unknown 키워드

> 열거형에는 unknown 키워드가 ㅇ벗다. 그러나 열거형에 향후 추가되는 switch문에서 @unknown 키워드를 참조하고 있을 수 있다.

```swift
enum Color {
    case red, green, blue
}

let color: Color = .green

switch color {
case .red:
    print("Color is Red")
case .green:
    print("Color is Green")
case .blue:
    print("Color is Blue")
@unknown default:
    print("Unknown Color")
}
```
