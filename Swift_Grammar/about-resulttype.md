# Result 타입

> 보다 진보된 형태의 에러 처리 타입이다.

```swift
enum Result {
    case success
    case faulure
}
```

위와 같이 성공 케이스와 실패 케이스가 존재하는 열거형이다.
`throws`키워드를 사용하지 않아도 되고, 에러 처리를 더 편하게 할 수 있게 해준다.

```swift
enum NetworkError: Error {
    case NotAuthorization
    case NotConnected
}

func getDataFromNetwork() -> Result<Int, NetworkError> {
    let a = 5

    if a < 5 {
        return .success(200)
    }
    return .failure(.NotAuthorization)
}

let response = getDataFromNetwork()
switch response {
case .success(let code):
    print(code) // 200
case .failure(let error):
    print(error) // NotAuthorization
}
```

이렇게 리턴값으로 받아서 switch문으로 깔끔하게 처리가 가능하다.
그리고 `Result<SuccessType, FailureType>`으로 어떤 연관값을 리턴값으로 할지 정의하면 된다.

```swift
let response = getDataFromNetwork()
do {
    try response.get()
} catch {
    print(error)
}
```

이와같이 `get()`메서드로도 처리가 가능하기도 하다.
일반적으로는 `switch`문을 많이 쓰긴 한다. 더 깔끔하니까.
