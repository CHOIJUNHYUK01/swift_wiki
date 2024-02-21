# 클로저

> 함수를 일급 객체로 취급한다. 익명 함수이기도 하다.

함수와 기능은 완전히 동일하다. 형태만 다르다.

### 함수는 타입이다.

    1) "함수"를 변수에 할당할 수 있다.
    2) 함수를 호출할 때, "함수"를 파라미터로 전달할 수 있다.
    3) 함수에서 "함수"를 반환할 수 있다.

```swift
// 동일한 함수다.

func add(a: Int, b: Int) -> Int {
    let result = a + b
    return result
}

{ (a,b) in
    let result = a + b
    return result
}
```

### 콜백함수로 활용

> 함수를 실행하면서 파라미터로 전달하는 함수다. 호출하는 함수의 결과를 받아 콜백함수를 다시 실행한다.

```swift
func closureCaseFunction(a: Int, b: Int, closure: (Int) -> Void) {
    let c = a+b
    closure(c)
}

closureCaseFunction(a: 5, b: 4) { a in
    print(a)
}
```

### 문법 최적화

```swift
func closureCaseFunction(a: Int, b: Int, closure: (Int) -> Void) {
    let c = a+b
    closure(c)
}

closureCaseFunction(a: 5, b: 4) { print($0) }
```

위와 같이 매개변수를 엄청 간단하게 표현할 수 있다.
index와 같이 첫 번째 매개변수는 `$0`, 두 번째 매개변수는 `$1` 등으로 사용이 가능하다.

### 메모리 구조

> 클로저는 참조타입이다.

그래서 캡처현상이 일어나기도 한다.

#### 캡처현상이 뭔데

> 자신이 참조하는 외부 변수를 캡처해 저장하는 현상이다.

```swift
var stored = 0

let closure = { (number: Int) -> Int in
    stored += number
    return stored
}

closure(1) // 1
closure(3) // 4
closure(4) // 8
```

### @escaping 키워드

> 해당 클로저를 다른 변수에 담아 해당 클로저를 포함하는 스택이 종료가 되어도 활용하겠다는 걸 의미한다.

그래서 힙에 저장된다. 오래 사용하기 위해서.

### @autoclosure

> 클로저 형태로 전달하지 않아도, 자동으로 클로저로 만들어 주는 키워드다.
