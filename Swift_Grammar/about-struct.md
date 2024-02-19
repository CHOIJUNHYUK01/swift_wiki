# 구조체

### 구조체는 어떻게 만들어지는가

> 구조체도 클래스와 비슷하게 속성과 메서드로 이루어진다.

```swift
struct Bird {
    var name = "새"
    var weight = 0.0

    func fly() {
        print("날아갑니다.")
    }
}
```

해당 틀로 만들어진 건, `인스턴스`라고 구분지어 부르겠다. (내 개인적인 선택)

### 구조체 메모리 구조

해당 구조체 틀도 데이터 영역에 존재한다.
해당 틀로 만들어진 인스턴스는 스택에 존재한다.

#### 스택에 인스턴스가 있다는 것

```swift
struct Bird {
    var name = "새"
    var weight = 0.0

    func fly() {
        print("날아갑니다.")
    }
}

var nabi = Bird()
var angdu = nabi

nabi.name = "나비"
```

var와 let 선언이 되면 해당 속성을 바꾸지 못하는 것도 일반 변수와 상수와 똑같이 작용한다.
위와 같이 `nabi` 속성이 바뀐다고 하더라도 `angdu` 속성은 다른 값이기 때문에 바뀌지 않는다.
