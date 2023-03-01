# MVC 모델 뷰 컨트롤러

## Define
- Model-View-Controller 3가지 로직으로 나누어 설계하는 디자인 패턴.
- Model: 데이터, 비즈니스 핵심 로직
- View: 사용자 인터페이스
- Controller: Model과 View의 중개자. Model에게 데이터를 받아 View에 요청하고, 사용자 액션을 다시 Model로 전달하는 역할을 한다.
- Model과 View는 절대 직접 소통하지 않는다. ViewController를 통해서만 소통.

## 왜 사용하는가?
- 코드의 가독성, 유지보수성, 확장성을 높여줌.
- 각각의 역할이 명확하게 분리되어 개발자가 어떤 부분을 수정해야할지 명확해짐.

## 장단점
### 장점
- 개발 속도가 빠르다. (보편적인 패턴으로 친숙하고 유지보수가 쉽다.)

### 단점
- ViewController가 비대해질 수 있다.

### Ref.
- [zooneon님의 velog](https://velog.io/@zooneon/iOS-MVC-%ED%8C%A8%ED%84%B4%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)