# 제네릭

> 파라미터 개수는 같고, 처리하는 로직도 같은데 타입만 다를 때 사용한다.

한 번의 구현으로 모든 타입을 커버 가능한 문법이다.
유연한(유지보수가 쉽고, 재사용성이 높은) 함수, 구조체, 클래스, 열거형 등을 일반화 가능하게 코드를 작성할 수 있다.

```swift
func printArray<T>(array: [T]) {
    for element in array {
        print(element)
    }
}
```

`<T>`를 타입 파라미터라고 한다.

### 프로토콜에서 사용하고 싶다

연관타입을 사용해야 한다.
채택한 타입에서 `typealias`를 사용할 수 있지만, 생략해도 상관없다.

```swift
protocol RemoteControl {
    associatedtype T
    func change(to: T)
}

class TV: RemoteControl {
    typealias T = Int

    func change(to: T) {
        print(to)
    }
}
```
