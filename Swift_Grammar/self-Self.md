# self와 Self

> 인스턴스를 가리키는 self, 타입을 가리키는 Self

```swift
// self는 인스턴스를 가리킨다.
struct Dog {
    var name = "강아지"

    func changeName() {
        self.name = "바꾼 이름"
    }
}

// Self는 타입을 가리킨다.
extension Int {
    static let zero: Self = 0
}
```
