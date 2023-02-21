# GCD 쓰레드 관련 작업 처리

## Define
- Grand Central Dispatch의 약자.
- task 정의 후 Dispatch queue에 넣어주면 OS가 알아서 적절한 쓰레드에 할당.

## Queue의 종류: Serial / Concurrent
- Serial(직렬): 이전 작업이 끝나면 다음 작업을 실행.
- Concurrent(병렬): 동시에 작업을 실행.
~~~swift
// Serial Queue, UI업데이트와 관련된 모든 task는 main Queue에서 실행
DispatchQueue.main.async {}

// Concurrent Queue, 전체 시스템에서 공유됨
DispatchQueue.global().async {}
~~~

## Qos (작업우선순위) 설정
- 작업의 중요도를 설정해 우선순위 지정이 가능하다.
~~~swift
DispatchQueue.global(qos: userInteractive).async {
    // [1순위] 사용자 인터랙티브와 관련된 작업
}

DispatchQueue.global(qos: userInitated).async {
    // [2순위] 사용자 요청과 관련된 작업
}

DispatchQueue.global(qos: default).async {
    // [3순위] qos를 지정해주지 않으면 이게 기본값
}

DispatchQueue.global(qos: utility).async {
    // [4순위] 사용자와 상호작용하지 않으면서 오랜 시간 작업을 수행할 때
}

DispatchQueue.global(qos: background).async {
    // [5순위] background 실행과 관련된 작업
}
~~~