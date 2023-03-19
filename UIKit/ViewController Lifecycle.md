# ViewController Lifecycle 뷰컨트롤러 라이프사이클

## Define
ViewController의 특정 시점을 활용할 수 있도록 메서드로 정의해둔 것.   
라이프사이클은 다음과 같다.
1. `viewDidLoad()`
2. `viewWillAppear()`
3. `viewDidAppear()`
4. `viewWillDisappear()`
5. `viewDidDisappear()`

</br>

## viewDidLoad()
우리가 흔히 쓰는 스토리보드에서 정의한 컴포넌트들인 `IBOutlet`, `IBAction`을 바로 이 시점부터 사용이 가능함.   

[viewDidLoad 공식 문서 참고](https://developer.apple.com/documentation/appkit/nsviewcontroller/1434476-viewdidload)

</br>

## viewWillAppear(), viewWillDisappear()
present된 view에서 이전 view로 되돌아간다 하더라도, viewWillAppear의 메서드는 호출되지 않는다.    
왜냐하면 이전 view는 사라지지않고 아래에 디스플레이 되어있기 때문이다.   
⚠️ 다만 presentation 스타일이 modaly가 아닌 전체화면을 덮는 `fullScreen`으로 동작했을 때는, 작동하게 된다.

</br>

## 재정의할 때는 꼭 상위 메서드 호출하기
ViewController의 모든 라이프사이클 메서드에서는, super.view어쩌구저쩌구를 호출해줘야한다.   
상위 클래스에서 구현된 기본 동작을 유지하기 위함이라고 한다.
~~~
If you override this method, call this method on super at some point 
in your implementation in case a superclass also overrides this method.

이 메서드를 재정의하는 경우 슈퍼클래스도 이 메서드를 재정의하는 경우 
구현의 특정 지점에서 슈퍼에서 이 메서드를 호출합니다.
~~~
