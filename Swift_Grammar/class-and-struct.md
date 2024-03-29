# 클래스와 구조체 비교

> 가장 큰 차이는 '상속'이라는 것만 일단 알고 진행하자

### 초기화

> 구조체와 클래스는 모두 초기화를 해줘야 실질적인 데이터 역할이 가능해진다.

```swift
class Dog {
    var name: String
    var weight: Double

    init(name: String, weight: Double) {
        self.name = name
        self.weight = weight
    }
}
```

`init`으로 초기화를 하는 메서드를 구현해야 한다.
해당 메서드를 사용해, 인스턴스를 생성한다.

초기화 메서드 실행의 목적은 모든 저장 속성 초기화를 통한 인스턴스 생성이다.
즉, 모든 저장 속성에 값이 저장되어야 생성이 완료된다는 뜻이다.

#### 멤버와이즈 이니셜라이즈

> 구조체는 클래스와 다르게 초기화 함수를 적지 않으면, 인스턴스를 생성할 때 자동으로 가지고 있는 속성을 초기화해주는 초기화 함수를 지원한다.

```swift
struct Dog {
    var name: String
    var weight: Double
}

var bori = Dog(name: "", weight: 0.0)
```

### 사용 이유

1. 사용하려는 모델을 설계한다.
2. 애플이 미리 설계해 놓은 클래스/구조체를 잘 사용하기 위함이다. (프레임 워크)

### 객체 지향 특징

1. 추상화

   사용하려는 데이터에서 공통된 특성을 뽑아내 속성과 메서드를 정의하는 것 (모델링 한다는 것)

2. 캡슐화

   연관이 있는 데이터를 하나의 클래스 혹은 구조체 타입으로 묶어 정의하는 것

3. 상속성 (구조체는 뺴고)

   자식 클래스가 부모 클래스에서 정의한 속성이나 메서드를 사용할 수 있다는 것

4. 다형성

   하나의 객체가 여러 타입의 형태로 저장될 수 있다는 것 (다운캐스팅, 업캐스팅)

### 속성에도 종류가 있다

1. 저장 속성

   기본 속성이다.

2. 지연 저장 속성

   `lazy` 키워드를 붙이고, 값이 없을 때는 `nil`이 할당되기 때문에 항상 `var`로 선언되어야 한다.
   해당 속성은 메모리에 당장 올라가진 않고, 사용할 떄 올라간다.

   다른 저장 속성을 사용해야 할 때 사용한다.
   아니면, 계산하는 데 메모리르 꽤 잡아먹을 것 같을 때도 사용한다.

```swift
class Dog {
    var name = "강아지"
    lazy var nameLength = self.name.count
}
```

3. 타입 속성

   타입 자체에 대한 속성이다.
   인스턴스에서 접근은 불가능하다.
   전역 변수와 같이 데이터 영역에 존재한다.

4. 속성 감시자

   타입이 바뀌는 타이밍을 알 수 있다.
   이제 곧 바뀔 건지 (willSet), 이미 바뀌었는지 (didSet)

5. 계산 속성

   속성 형태를 가진 실질적 메서드다.
   `get`블록은 필수 구현 요소고, `set`블록은 선택이다.

### 메서드에도 종류가 있다.

1. 인스턴스 메서드

   인스턴스에는 메모리 공간이 포함되어 있지 않다.
   그렇지만, 접근할 때는 인스턴스에서 접근해야 한다.

   구조체에서는 특성이 하나 있다.
   자기가 가진 속성 값을 변경시켜야 한다면, `mutating` 키워드를 붙여야 한다.

```swift
struct Dog {
    var name = "강아지"

    mutating func changeName(_ a: String) {
        self.name = a
    }
}
```

2. 타입 메서드

   타입에 해당하는 보편적인 동작의 경우다.
   해당 메서드를 상속하려면, `static` 대신에 `class` 키워드를 사용하면 된다.

3. 서브스크립트

   대괄호를 사용해 메서드를 사용해 나온 값을 반환한다.
   계산 속성과 동일하게 `get`은 필수, `set`은 선택이다.
   타입 서브스크립트도 구현 가능하다.

4. 생성자

   모든 저장 속성을 초기화해야 한다는 게 기본 정의다.

- 구조체에만 존재하는 멤버와이즈 생성자

- 클래스에만 존재하는 편의 생성자

  지정 생성자보다 더 적은 갯수의 파라미터로 보다 편리하게 생성하기 위한 서브개념의 생성자다.
  이는 반드시 지정 생성자에 의존하고 있으므로, 호출해야 한다.

  초기화 과정을 간편하게 제공하기 위함이다.

- 클래스에만 존재하는 필수 생성자

  `required` 키워드를 붙이면, 하위 클래스는 반드시 해당 생성자를 구현해야 한다.
  `override` 키워드 없이 `required` 키워드만 붙이면 된다.
  다른 지정 생성자를 구현하지 않으면 자동으로 필수 생성자가 상속된다.

- 지정생성자

- 실패가능생성자

  `init?()` / `init!()` 은 유사하게 취급하면 된다.
  인스턴스 생성에 실패하면 `nil`을 반환한다.

  실패 가능 생성자는 다른 실패 가능 생성자를 호출할 수 없다.
  실패 불가능 생성자를 실패 가능하게 재정의가 불가능하다. (반대는 가능)

5. 소멸자

   인스턴스 해제시, 즉 인스턴스가 메모리에서 제거되기 직전에 자동으로 호출되는 메서드다.

> 클래스에서만 존재함

### 싱글톤 패턴

```swift
class DataManager {
    static let shared = DataManager()

    var userInfoId = 12345

    private init() {}
}
```

위와 같이 생성해 사용한다.
`private init()`을 사용해 외부에서는 새로운 객체 생성을 막는다.

### is 연산자

> 타입을 체크하는 연산자

`부모 클래스`에서 `자식 클래스`를 상대로 하면 true가 나온다.

### as 연산자

> 타입의 힌트를 변경하는 연산자

해당 타입에만 있는 저장 속성이나 메서드를 사용해야 할 경우에 사용한다.

#### 업캐스팅

> 무조건 성공한다.

항상 상속을 받은 클래스를 향하기 때문이다.

#### 다운캐스팅

> 실패 가능성이 있다. 그래서 직접 사용하려면 언래핑이 필요하다.

```swift
class Person {
    var name = "사람"
}

class Student: Person {
    var name2 = "학생"
}

var p = Person() as? Student // nil

if let person2 = p {
    person2.name2
}
```

### 다형성

> 하나의 객체가 여러가지 타입 형태로 표현될 수 있다. 이는 클래스 상속과 깊은 연관성이 있다.

만약 하나의 인스턴스가 업캐스팅된 타입으로 인식되고 호출되더라도 실제 인스턴스 형태에 따라 재정의된 메서드가 호출되고 실행된다.

### Any, AnyObject 타입

> 불특정 타입을 다룰 수 있는 타입이다.

#### Any

> 그 어떤 타입의 인스턴스나 값을 표현할 수 있다.

#### AnyObject

> 그 어떤 클래스 타입의 인스턴스도 표현할 수 있다.

```swift
switch item {
   case is Int:
      print("is int")
   default:
      print("is the other type")
}
```

### 확장

> 수직으로 확장하는 상속과 다르게, 수평으로 확장하는 개념이다. 즉, 새로운 타입을 만드는 게 아니라 현재 존재하는 타입에 메서드를 추가하는 것이다.
> 저장 속성을 확장하는 건 불가능하다. 또한, 상속받은 객체가 재정의할 수는 없다.

1. 메서드 형태만 가능하다.

2. 새로운 생성자도 가능하다.

   구조체에서는 지정 생성자도 가능하다.
   단, 본체에 생성자가 없을 경우에만 가능하다.
   멤버와이즈 생성자는 불가능하다.

   다만, 클래스에서는 편의 생성자만 가능하다.

```swift
struct Person {
    var name = "person"
}

extension Person {
    init(n: String) {
        self.name = n
    }
}

let p = Person(name: "aaa")
let p2 = Person(n: "aa")
```

3. 서브스크립트 생성 가능하다.

4. 새로운 중첩 타입 정의 및 사용이 가능하다.

5. 프로토콜 채택 및 프로토콜 관련 메서드도 가능하다.
