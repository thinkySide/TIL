# Collection 컬렉션 다루기

## Array(repeating:count:)
특정 element를 n번 반복한 배열로 반환하기
[init(repeating:count:)](https://developer.apple.com/documentation/swift/array/init(repeating:count:)-5zvh4)

### parameters
- repeating: 반복할 element
- count: 반복할 횟수  
~~~swift
Array(repeating: 0, count: 4) // [0, 0, 0, 0]
Array(repeating: "mintol", count: 3) // ["mintol", "mintol", "mintol"]
Array(repeating: [2, 4], count: 3) // [[2, 4], [2, 4], [2, 4]]
~~~

<br>

## <#Collection#>.min
- 요소를 비교하며 시퀀스의 최소 요소를 반환합니다.
- 옵셔널 값으로 반환합니다.
~~~swift
let array = [1, 50, 100].min { lhs, rhs in
    print("좌변은 \(lhs), 우변은 \(rhs)입니다.")
    return lhs < rhs
}
// 첫번째 반복 -> 좌변은 50, 우변은 1입니다.
// 두번째 반복 -> 좌변은 100, 우변은 1입니다.
// Optional(1)

let array = [1, 50, 100].min { lhs, rhs in
    return lhs > rhs // 부호 반대로 썼음.
}
// Optional(100) -> 부호 반대로 쓰면 최대값 반환
~~~

<br>

## ArraySlice
- 요소를 잘라 배열에 추가 후 리턴합니다. (문자열만 확인)
~~~swift
ArraySlice("Mintol love ❤️")
// ["M", "i", "n", "t", "o", "l", " ", "l", "o", "v", "e", " ", "❤️"]
~~~

<br>

## swapAt(i:j:)
- 컬렉션의 지정된 인덱스에서 값을 교환 후 반환합니다.

~~~swift
mutating func swapAt(
    _ i: Self.Index, // 첫번째 교환값 인덱스
    _ j: Self.Index // 두번째 교환값 인덱스
)
~~~

~~~swift
var array = ["🍎", "🍏"]
array.swapAt(1, 0)
// ["🍏", "🍎"]
~~~