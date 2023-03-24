# String 문자열 다루기

## replacingOccurrences(of:with:option:range:)
문자열의 지정된 범위를 다른 지정된 문자열로 바꿔 반환합니다.
- of: 문자열 범위 지정
- with: 변경 후 문자열

~~~swift
"32 + 4 - 10"
.replacingOccurrences(of: " - ", with: "-")
.replacingOccurrences(of: " + ", with: "+")
// "32+4-10"

"🍓🍌🍓🍌🍓🍌🍓"
    .replacingOccurrences(of: "🍌", with: "🍓")
// 🍓🍓🍓🍓🍓🍓🍓
~~~

<br>

## split(separator:)
지정된 문자열을 기준으로 나누어 컬렉션 형태로 반환합니다.
- separator: 나누는 기준 문자열

~~~swift
"I am iOS Developer!".split(separator: " ")
// ["I", "am", "iOS", "Developer!"]
~~~

`components(separatedBy:)` 와 비슷한 역할인듯?