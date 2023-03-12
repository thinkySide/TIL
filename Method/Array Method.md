# Array 배열 다루기

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