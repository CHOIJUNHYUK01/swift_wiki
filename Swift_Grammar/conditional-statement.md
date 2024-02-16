# 조건문

> if문과 switch문의 활용

### if문은 무엇인가

else와 같이 쓰이며, 주어진 조건이 참인지 거짓인지에 따라 다른 코드 블록을 실행할 수 있게 한다.

```swift
if true {
    // 참일 경우 실행되는 코드 블록
} else {
    // 거짓일 경우 실행되는 코드 블록
}
```

### switch문은 무엇인가

단일 표현식의 값에 따라 다른 코드 블록을 실행할 수 있게 한다.

패턴 매칭과 함께 사용하는 예제를 보자

```swift
let score = 90

switch score {
    case 80...100:
        print("A")
    case 60..<80:
        print("B")
    case 40..<60:
        print("C")
    case 0..<40:
        print("Fail")
    default:
        print("Input Error") // 타입이 Int기 때문에 음수거나 100 초과되는 수가 등장하면 처리를 해줘야 함
}
```

#### switch문과 fallthorugh

`fallthrough`는 switch문에서 사용할 수 있다.
해당 조건 코드 블록에 적용하면, 바로 아래에 있는 조건에 해당하는 코드 블록을 실행시킨다.
그 아래에 있는 조건에도 `fallthrough`가 붙어있다면, 그 조건 아래에 있는 조건문의 코드 블록을 실행한다.

```swift
let score = 68

switch score {
    case 80...100:
        print("A")
    case 60..<80:
        print("B")
        fallthrough
    case 40..<60:
        print("C")
    case 0..<40:
        print("Fail")
    default:
        print("Input Error")
}

// 결과는 B, C 가 나온다.
```
