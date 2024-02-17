# 함수

> 인수로 호출할 수 있고, 값을 반환할 수 있는 명명된 코드 조각이다. 코드를 구성학 재사용하는 데 도움이 되며, 코드를 이해하고 유지하기 쉽게 만든다.

### 파라미터와 아규먼트 차이

```swift
func sumOfTwoInt(a: Int, b: Int) -> Int {
    return a + b // 해당 a, b 변수가 파라미터. (매개 변수)
}

sumOfTwoInt(a: 10, b: 5) // 함수를 호출할 때 전달되는 변수가 아규먼트. (전달 인자)
```

### 오버로딩과 오버라이딩

#### 오버로딩

> 이름이 같은 함수지만, 파라미터 개수나 타입이 다른 경우 사용한다.

```swift
func paint(a: Int) {
    print("\(a)개가 그려짐")
}

func paint(a: String) {
    print("\(a)가 그려짐")
}

func paint(a: String, b: Int) {
    print("\(a)가 \(b)개 그려짐")
}
```

#### 오버라이딩

> 클래스에서 상속이 된 후, 메서드를 재정의할 때 사용한다.

```swift
class Shape {
    func paint() {
        print("도형이 그려짐")
    }
}

class Circle: Shape {
    override func paint() {
        print("원이 그려짐")
    }
}
```

### 입출력 파라미터 (inout)

> 변수나 상수에도 참조를 이용할 수 있다.

```swift
func swapTwoValue(a: inout Int, b: inout Int) {
    let temp = a
    a = b
    b = temp
}

var first = 10
var second = 12

swapTwoValue(a: &first, b: &second)
```

함수 내부에서는 파라미터가 상수로 선언되어 재할당이 불가능하다.
그걸 가능하게 해주는 키워드가 inout이다.
그래서 함수를 선언할 때, 전달 인자 변수명 앞에 `&`를 붙여줘야 한다.

### 제어전송문

#### break

> 제일 가까운 반복문을 종료시킨다. switch문에서는 case에서 어떤 실행도 없을 경우를 알려준다.

#### fallthrough

> 해당하는 case문 바로 아래 case의 코드 블록을 실행한다.

#### continue

> 반복문에서 사용되며, 함수 실행을 즉시 종료하고 다음 반복문을 진행한다.

#### return

> 함수를 종료시킨다. 리턴값이 없는 함수 (Void 타입 반환 함수)에서는 빈 값을, 타입이 있는 함수라면 해당 타입 값을 반환한다.

#### discardableResult

> 리턴 타입이 있는 함수에서 사용할 수 있는 어트리뷰트다. 해당 리턴값을 사용하지 않아도 될 수 있음을 알려준다.
