# Preprocessor Statement 전처리문

## What is Preprocessor Statement?
컴파일 이전에 미리 처리되는 문장을 의미. `#`으로 시작한다.

<br>

## #if DEBUG
디버그 모드에서만 실행되는 구문을 정의해 줄 때 사용, Release 버전에서는 해당 코드가 적용되지 않는다.

~~~swift
#if DEBUG
print("디버그 모드에서만 실행!")
#endif
~~~


