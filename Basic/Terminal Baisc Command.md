# Terminal Basic Command 터미널 기본 커맨드

## 잡기술

- `clear` : 터미널 창 비우기
    ~~~swift
    // 현재 디렉토리는 유지
    clear
    ~~~

- `option + Mouse` : 편집 위치 지정하기

</br>

## 경로 이동하기
⭐️ tab키와 함께 자동완성으로 활용할 수 있음.

- `cd` : 이전 디렉토리로 이동 (Change Directory)
    ~~~swift
    // thinkyside 폴더로 이동
    cd thinkyside
    ~~~

- `cd ~` : 루트 디렉토리로 이동
    ~~~swift
    // 터미널 실행 시 기본 디렉토리로 이동
    cd ~
    ~~~

- `cd ..` : 이전 디렉토리로 이동
    ~~~swift
    // 현재 위치의 이전 디렉터리로 이동
    cd ..
    ~~~

</br>

## 열기

- `open` : 파일 열기
    ~~~swift
    // mintol.text 파일 열기
    open mintol.text
    ~~~

- `open -a` : 지정한 프로그램으로 파일 열기
    ~~~swift
    // mintol.text Xcode로 파일 열기
    open -a Xcode mintol.text
    ~~~


</br>

## 생성/삭제

- `mkdir` : 새 디렉토리 생성 (make directory)
    ~~~swift
    // mintol 폴더 생성
    mkdir mintol
    ~~~

- `touch` : 새 파일 생성
    ~~~swift
    // mintol.txt 파일 생성
    mkdir mintol.txt
    ~~~

</br>

## 생성/삭제

- `rm` : 파일 삭제 (remove)
    ~~~swift
    // virus.txt 파일 삭제
    rm virus.txt
    ~~~

- `rm \*` : 파일 전체 삭제
    ~~~swift
    // 해당 디렉토리 내 전체 파일 삭제
    rm *
    ~~~

- `rm -r` : 디렉토리 삭제
    ~~~swift
    // thinkyside 디렉토리 삭제
    rm -r thinkyside
    ~~~
