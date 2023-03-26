# Frame-Bounds 프레임과 바운드

## Frame
- `SuperView`의 좌표계에서 View의 위치와 크기를 나타냅니다.
- 즉, Origin은 SuperView의 원점에서 얼마나 떨어져 있는가를 나타낸다.   
   (ex: SuperView top에서 부터 16, SuperView의 leading에서 부터 24 -> (16, 24))
- frame의 width, heigth 값은 View의 `Rotate`에 의해 변할 수 있다.    
   (View 전체를 감싸는 사각형으로 생각해야함 Figma에서 오브젝트 선택했을 때처럼!)

<br>

## Bounds
- `자신의 좌표계`에서 View의 위치와 크기를 나타냅니다.
- 즉, Bounds의 origin은 (0, 0)으로 초기화된다. (물론 변경도 가능)
- Bounds에서는 `Rotate` 하더라도 width, heigth 값은 동일하다.
- `ScrollView`에서 Bounds의 Origin값을 변경함으로써 화면이 이동하는 것처럼 보이게 해준다!
- View 내부에 그림을 그릴 때도 사용하게 된다. (drawRect)

<br>

## 공통점
- UIView의 Instance Property이다.
- CGRect 타입이다.
- View의 위치와 크기를 나타낸다.