# Singleton 싱글톤

## 사용 목적
인스턴스(객체)를 하나만 만들어 공유해서 사용.
***


## Swift에서 Singleton 만들기
```swift
// class로 생성
class Singleton {
    
    // 타입 프로퍼티에 나 자신의 객체를 담음 (보통 shared 많이 씀)
    static let shared = Singleton()
    
    // 외부에서 새로운 객체를 생성하지 못하도록 접근제어
    private init() {}
    
}

// Singleton 생성
let singleton = Singleton.shared
```
***

## Struct로는 만들 수 없을까?
struct(구조체)는 인스턴스를 value(값)타입으로 생성한다.   
즉, 값 복사가 일어나게 되는데 이는 Singleton의 목적(하나의 객체 공유)에 어긋난다.   
한마디로 singleton을 만들면서 struct로 만드는 것은 딱히 의미가 없어져 버리는 것.