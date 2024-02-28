# 에러처리

> 런타임 에러를 파악해 올바르게 처리한다.

### throws 키워드

> 에러를 던질 수 있는 함수를 나타낸다.

```swift
func checking(a: Int) throws {
    if a < 10 {
        throws Error
    }
}
```

### 에러 프로토콜이 있다.

아래 코드와 같이 해당 프로토콜을 채택해 구현해야 한다.

```swift
enum NetworkError: Error {
    case aError
    case bError
}
```

### 에러 처리 방법 3가지

```swift
// 1번 (do-try) : 모든 에러 발생의 에외적인 경우를 디테일하게 처리 가능
do {
    try checking(a: 5)
} catch {
    // 에러처리 구문
}

// 2번 (try?) : 옵셔널 타입으로 리턴하기에, 언래핑해야 함
let data = try? checking(a: 5)

// 3번 (try!) : 에러가 발생할 가능성이 없는 경우에 제한적으로 사용한다.
let data = try! checking(a: 5)
```

### rethrowing 함수

에러를 던지는 함수를 파라미터로 받았을 경우, rethrows 키워드를 붙여 에러를 다시 던질 수 있게 한다.

```swift
func someFunction(callback: (Int) throws -> Void) rethrows {
    do {
        try callback(5)
    } catch {
        throw NetworkError.aError
    }
}
```

### defer

> 어떤 스코프 내의 동작 마무리를 위한 것이다.

```swift
func doSomething() {
    defer {
        print("1")
    }
    print("2")
}
// 2
// 1
```

근데 무조건 defer가 불린 적이 있어야 실행이 된다.

```swift
func doSomething() {
    if true {
        print("1")
        return
    }
    defer {
        print("2")
    }
}
// 1
```
