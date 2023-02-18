# ARC 자동 레퍼런스 카운팅

## Define
- Automatic Reference Counting의 약자.
- swift는 기본적으로 Reference Counting 시스템을 이용해 heap 영역의 데이터를(메모리를) 관리하고, 자동으로 코드에 심어준다.   
 (인스턴스에 refCount 변수를 만들고, 참조가 될 때 마다 카운트를 1씩 올린다.)
- 이전 Objective-C에서는 MRC(Manual Reference Counting)수동 레퍼런스 카운팅 방식을 사용했다.

## Strong Reference Cycles 강한 순환 참조
- 강한 순환 참조 등의 문제로 인스턴스가 해제되지 않아 메모리 누수(Memory Leak)로 이어질 수 있다. 아래 코드는 Apple 공식 문서에서 가져온 강한순환참조로 인한 메모리 누수 예제이다.
~~~swift
class Person {
    let name: String
    var apartment: Apartment? // Apartment 타입 가지고 있음.
    
    init(name: String) {
        self.name = name
    }

    deinit {
        print("\(name) is being deinitialized")
    }
}

class Apartment {
    let unit: String
    var tenant: Person? // Person 타입 가지고 있음.
    
    init(unit: String) {
        self.unit = unit
    }

    deinit {
        print("Apartment \(unit) is being deinitialized")
    }
}
 
var john: Person? = Person(name: "John Appleseed") // john의 RC: 0 -> 1
var unit4A: Apartment? = Apartment(unit: "4A") // unit4A의 RC: 0 -> 1

// 서로가 서로의 RC를 올리고 있음.
john?.apartment = unit4A  // unit4A의 RC: 1 -> 2
unit4A?.tenant = john // john의 RC: 1 -> 2

// 메모리 제대로 해제 되지 않음...(인스턴스가 없어져서 이후에 해제할 방법도 없음)
john = nil // john의 RC: 2 -> 1
unit4A = nil // unit4A의 RC: 2 -> 1
~~~

이 경우 강한순환참조 문제를 해결하기 위해 weak 키워드를 사용할 수 있다. weak로 선언하게 되면, 해당 인스턴스의 RC를 올리지 않는다.
~~~swift
// 하나만 weak를 선언해줘도, 메모리가 정상적으로 해제될 수 있다.
// john이 해제되면서 안에서 가리키고 있던 Apartment 인스턴스의 RC도 -1 되기 때문.
weak var john: Person? = Person(name: "John Appleseed")
var unit4A: Apartment? = Apartment(unit: "4A")

// "John Appleseed is being deinitialized"
// "Apartment 4A is being deinitialized"
~~~

## closure에서의 강한순환참조
- closure에서 발생하는 강한순환참조는 capture list틀 이용해 해결할 수 있다.   

아래 코드는 closure에서 발생하는 강한순환참조 예시이다.
~~~swift
class Dog {
    let name: String
    
    // closure
    lazy var nameCall = {
        print("Dog name is \(self.name)")
    }
    
    init(name: String) {
        self.name = name
    }

    deinit {
        print("\(name) is being deinitialized")
    }
}

var mintol: Dog? = Dog(name: "민톨") // mintol RC: 0 -> 1

// nameCall 클로저가 self(자기 자신 Dog 인스턴스)를 강하게 가리키고 있음.
mintol?.nameCall() // mintol RC: 1 -> 2

// 메모리 해제되지 않음
mintol = nil // mintol RC: 2 -> 1
~~~
이 경우 capture list를 이용해 해결할 수 있다.
~~~swift
lazy var nameCall = { [weak self] in // self를 약하게 가리킴 (RC 올리지 않음)
  print("Dog name is \(self?.name)") // weak 자체가 nil의 가능성 있으므로, 옵셔널 적용
}
~~~