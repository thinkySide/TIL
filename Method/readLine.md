# readLine 입력 받기

## 사용법
- 실행 시, CLT(Command Line Tool)에서 값을 입력받을 수 있다.
- 옵셔널 String 타입으로 반환한다.
~~~swift
// INPUT: Mintol

let input = readLine()
 // OUTPUT: optional("Mintol")

let forcedInput = readLine()!
 // OUTPUT: "Mintol"
~~~

## 띄어브기로 구분하여 입력 받기
components(seperatedBy:) 파라미터에 넣은 값을 기준으로 구분하여 배열로 반환한다.
~~~swift
// INPUT: M i n t o l
let input = readLine()!.components(separatedBy: " ")
// OUTPUT: ["M", "i", "n", "t", "o", "l"]

// INPUT: M*i*n*t*o*l
let starInput = readLine()!.components(separatedBy: "*")
// OUTPUT: ["M", "i", "n", "t", "o", "l"]
~~~

### Ref.
- [감자 님의 tistory](https://didu-story.tistory.com/177)