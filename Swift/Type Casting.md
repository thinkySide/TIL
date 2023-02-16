# Type Casting

## Upcasting
업캐스팅은 상위 데이터를 모두 가지고 있는 것이 확실하기 때문에, 항상 성공한다.
~~~swift
student as Person
~~~

## Downcasting
다운캐스팅은 항상 성공하지 않는다. 인스턴스를 생성할 때 만들어진 데이터 영역에 한정된다.
~~~swift
let person = Student()
person as? Student // 일반적인 다운캐스팅, 옵셔널 타입 반환
person as! Student // 강제 다운캐스팅, 에러 발생 위험

let person = Person()
person as? Student // nil 반환
~~~

## 다형성
인스턴스를 참조하는 변수나 상수가 다른 타입으로 캐스팅 된다 해도, 접근 가능 범위만 바뀔 뿐이다. **즉, 타입 캐스팅에 상관없이 원래 메서드를 실행**한다는 것.

