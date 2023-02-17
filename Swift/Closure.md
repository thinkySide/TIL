# Closure 클로저

## Define
- 이름이 없는 익명 함수
- 일급객체 
    1. 변수에 할당 가능
    2. 함수를 파라미터로 전달 가능(콜백함수)
    3. 함수에서 함수를 반환할 수 있음)

아래 코드는 완전히 동일한 기능을 가지고 있음.
~~~swift
// function
func sumNumber(a: Int, b: Int) -> {
    return a + b
}

// closure
{ (a: Int, b: Int) -> Int in
    return a + b
}
~~~

## closure를 왜 사용할까?
클로저의 가장 중요한 핵심은 **이미 만들어둔 다른 함수에 기능을 추가하는 등의 사후적 정의로 활용할 수 있다는 것이다.** 함수 자체를 파라미터로 전달할 수 있기 때문에 가능한 것. 이를 callback함수라고 한다.

## closure 문법 경량화
다음과 같은 법칙들이 있음.   
1. trailing closure(후행 클로저)
~~~swift
func doSomething(closure: () -> ()) {
    print("나는야 클로저") 
}

doSomething(closure: {
    // 1단계: 기본 클로저
})

doSomething(closure:) {
    // 2단계: trailing closure 적용
}

doSomething() {
    // 3단계: 파라미터 생략
}

doSomething {
    // 4단계: 괄호 생략
}
~~~
2. 파라미터 생략 및 간소화
~~~swift
func doSomething(closure: (Int) -> Int) {
    closure(10)
}

// 기본 구현
doSomething { (number: Int) -> (Int) in
    return number * number
}

// 1단계: 리턴 타입 생략
doSomething { (number: Int) in
    return number * number
}

// 2단계: 파라미터 타입 생략
doSomething { (number) in
    return number * number
}

// 3단계: 파라미터 생략 및 Shotand Argument Names 사용
doSomething {
    return $0 * $0
}

// 4단계: 한줄 일 때 리턴 키워드 생략
doSomething { $0 * $0 }
~~~