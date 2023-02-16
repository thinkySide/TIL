# Method Dispatch 메서드 디스패치

## Direct Dispatch
- 메서드 자체에 함수 메모리 주소를 심어서 바로 찾아감.
- struct(구조체)가 direct dispatch 방식으로 동작.
- 바로 찾아가기 때문에, 메서드 디스패치 중 가장 속도가 빠름.

## Table Dispatch
- 배열 형태의 메서드 테이블을 만들어 찾아가는 방식.
- class(클래스), protocol(프로토콜)이 table dispatch 방식으로 동작.
- Dynamic Dispatch라고도 불림.
- class의 경우 virtual table을, protocol의 경우 witness table 생성.

## protocol을 채택한 class의 경우 어떻게 동작할까?
virtual, witness 2가지 table이 만들어진다. 실제 동작은 타입 여부에 따라 달리진다.
~~~swift
// 프로토콜
protocol SomeProtocol {
    func doSomething()
}

// 클래스 [우선순위 1]
class SomeClass: SomeProtocol {
    func doSomething() {
        print("doSomething!")
    }
}

let virtual: SomeClass = SomeClass()
virtual.doSomething() // virtual table 사용

let witness: SomeProtocol = SomeClass()
witness.doSomething() // witness table 사용
~~~
※ extension을 사용해 기본구현을 할 경우, Direct Dispatch로 동작한다.
~~~swift
// 확장 [우선순위 2 (class 구현이 없을 경우 extension 기본 구현 사용)]
extension SomeProtocol { 
    func doSomething() {
        print("doSomething Extension") // Direct Dispatch
    }
}
~~~