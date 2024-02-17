# 옵셔널 타입

> 값이 없을 수 있음을 알려주는 타입이다.

### nil은 무엇인가

> Swift의 옵셔널 타입(열거형으로 만들어졌음) 중에서 값이 없음을 나타내는 케이스이자, 값이 없음을 나타낸다.

#### null point exception

    Swift에서 오류는 메모리에 실제 값이 없을 때, 앱을 꺼뜨리는 에러가 발생하는 걸 의미한다.
    이런 오류를 방지하기 위해, 임시 타입을 "열거형" 으로 만들어 변수를 옵셔널 타입으로 선언했지만 할당이 되지 않았다면 nil을 자동으로 할당한다.

#### Optional 타입의 .none과 nil에는 무슨 차이가 있을까

> 공통점

`.none`과 `nil`은 임시 타입으로, 내부에 값이 없음을 표현한다.

> 차이점

`.none`은 실제 내부의 원시 형태이며, 구체화된 형태다.
`nil`은 `.none`의 리터럴 값 형태이며, 포괄적인 표현이다.

### 옵셔널 타입 변수 언래핑

> 해당 타입을 명시적으로 하지 않으면 Optional(5) 이런 식으로 나오기 때문에 언래핑을 해줘야 한다.

#### 강제 언래핑

> 이를 시도했다가 값이 없다면, 오류를 발생시키고, 앱을 꺼뜨린다.

```swift
var ifInt: Int? = 10

var maybeInt = ifInt!
```

#### if문으로 처리하기

```swift
var ifInt: Int?

if ifInt != nil {
    print(ifInt)
}
```

#### if let 바인딩

> if-else문과 동일하게 처리할 수 있다.

```swift
var ifInt: Int?

if let maybeInt = ifInt {
    print(maybeInt)
}
```

#### guard let 바인딩

> 이는 해당 값이 nil일 경우를 먼저 판단해 처리한다.

```swift
var ifInt: Int?

func getInt(_ a: Int?) -> Int? {
    guard let maybeInt = ifInt else { return nil }
    print(maybeInt)
}

getInt(ifInt)
```

#### nil coalescing

> 값이 nil이라면, 기본값을 제공해준다.

```swift
var ifInt: Int?

var maybeInt = ifInt ?? 10
```
