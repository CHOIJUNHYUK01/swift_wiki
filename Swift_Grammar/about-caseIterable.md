# CaseIterable 프로토콜

> 열거형에서 적용할 수 있는 프로토콜이다.

모든 케이스를 배열로 리턴해준다.

```swift
enum Color:CaseIterable {
    case red
    case blue
    case green
}

for c in Color.allCases {
    print(c) // red, blue, green
}

```
