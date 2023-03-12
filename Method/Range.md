# Range 범위 다루기

## indices 컬렉션에서 유효한 범위 반환
- 인스턴스 프로퍼티
~~~swift
let array = [0, 1, 2, 3, 4, 5]

array.indices // 0..<6

// 반복문 활용
for i in array.indices { print(i) }
// 0, 1, 2, 3, 4, 5
~~~
