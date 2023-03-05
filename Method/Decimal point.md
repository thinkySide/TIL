# Decimal point 소수점 다루기

## 소수점 버리기
~~~ swift
trunc를 사용할수도 있고, Int로 변환하면 소수점이 버려지기도 한다.
trunc(3.141592) // 3.0
Int(3.141592) // 3
~~~

## n번째 소수점까지 출력
String 타입으로 반환하기 때문에 다시 실수형으로 변환해줘야함.
~~~swift
String(format: "%.3f", 3.141592) // 3.141
~~~

### Ref.
- [formestory 님의 tistory](https://formestory.tistory.com/21)