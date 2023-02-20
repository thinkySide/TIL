# Error Handling 에러 처리
## 에러 처리의 3단계
1. 에러 정의
~~~swift
enum MyError: Error { // Error 프로토콜 채택
    case invalidName
    case invalidAge
}
~~~
2. 에러 함수 정의
~~~swift
func nameCheck(name: String) throws { // 에러를 던질 수 있는 함수 throw's'
    if name == "민톨" {
        print("valid Name")
    } else {
        throw MyError.invalidName // 에러 던지기 throw
    }
}
~~~
3. 에러 처리
~~~swift
do { // 에러가 나지 않는 경우 실행
    try nameCheck(name: "두톨")
} catch { // 에러가 났을 때 받아주는 곳
    if let error = error as? MyError { // error 상수 기본 제공, 타입캐스팅 후 사용 가능
        print(error.localizedDescription)
    }
}

try? nameCheck(name: "세톨") // 이 문법도 가능함. 대신 오류일 때 nil 리턴

// 에러 -> "invalidName"
~~~

## 에러를 던지는 함수를 처리하는 함수
아래 코드와 같이 콜백함수가 에러를 던지고 있는 함수에서, 다시 에러를 던질 수 있다는 뜻의 키워드 retrows이다.
~~~swift
func rethrowsFunction(callback: () throws -> ()) rethrows {
    do {
        try callback()
    } catch {
        // 에러 다시 던지기
        throw MyError.invalidName
    }
}
~~~