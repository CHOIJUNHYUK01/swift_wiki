# 중첩 타입

> 타입 내부에서 얼마든지 다른 타입을 선언 할 수 있다.

```swift
class Aclass {
    struct Bstruct {
        enum Cenum {
            case aCase
            case bCase
        }

        var name: Cenum
    }
}

let aClass: Aclass = Aclass()
let bStruct: Aclass.Bstruct = Aclass.Bstruct(name: .aCase)
let cEnum: Aclass.Bstruct.Cenum = .bCase
```

`Bstruct`
특정 타입과만 연관성이 있는 타입은 해당 특정 타입 내부에 선언해 사용 범위를 한정할 수 있다.

`Aclass`
타입 간의 연관성을 명확히 구분하고, 내부 구조를 디테일하게 설계가 가능하다.

### 여기에서 클래스 안에 구조체가 있다면, 메모리 구조는 어떻게 되는가?

구조체가 더 내부에 있기 때문에, 클래스 메모리를 따른다.
