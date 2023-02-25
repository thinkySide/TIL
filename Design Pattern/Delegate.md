# Delegate 델리게이트

## Define
### - 애플 공식 문서 속 정의
이 디자인 패턴은 위임된 책임을 캡슐화하는 프로토콜을 정의하여 구현 되며, 준수하는 유형(대리자)이 위임된 기능을 제공하도록 보장됩니다.
### - 내가 정리한 정의
프로토콜 채택으로 해당 기능 구현이 되어있음 확신하고, 그 프로토콜을 타입으로 받는 delegate(대리자) 프로퍼티를 이용해 메서드 실행을 대리자에게 위임하여 결론적으로 내부 로직은 숨기면서 해당 기능을 사용할 있게 만들어주는 패턴.

## 데이터 전달 목적의 Delegate 패턴 로직
1. 프로토콜 구현
~~~swift
protocol DataDeliverDelegate: AnyObject { // AnyObject를 통해 클래스 객체만 채택가능하도록 설정
    func deliveData(dataLabel: String)
}
~~~
2. delegate 변수 생성 - 데이터 전달해주는 곳 (SecondViewController)
~~~swift
protocol DataDeliverDelegate: AnyObject { // AnyObject를 통해 클래스 객체만 채택가능하도록 설정
    func deliveData(dataLabel: String)
}
~~~
3. delegate 변수를 통한 함수 실행 - 데이터 전달해주는 곳 (SecondViewController)
~~~swift
@IBAction func sendButton(_ sender: UIButton) {
    delegate?.deliveData(data: "데이터 전달")
    dismiss(animated: true)
}
~~~
4. delegate 프로토콜 채택 - 데이터 전달 받는 곳 (FirstViewController)
~~~swift
class FirstViewController: UIViewController, DataDeliverDelegate {}
~~~
5. 실제 구현부 - 데이터 전달 받는 곳 (FirstViewController)
~~~swift
func deliveData(data: String) {
    print("전달받은 데이터는 \(data)입니다.")
}
~~~
6. delegate 위임 받기 ⭐️⭐️⭐️ - 데이터 전달 받는 곳 (FirstViewController)
~~~swift
@IBAction func presentButton(_ sender: UIButton) {
    let vc = storyboard?.instantiateViewController(withIdentifier: "SecondViewController") as! SecondViewController
    vc.delegate = self
    present(vc, animated: true)
    }
~~~
※ Delegate를 위임하는 곳에서 가장 실수를 많이 한다. 만약 Delegate 패턴이 작동하지 않는 다면, 객체.delegate = self 이 구문에서 객체가 정확하게 전달되고 있는지 확인해보면 해결이 가능할 때가 많다. (ex: 해당 구문에서 vc를 let vc = SecodnViewController()로 만든다면 위임 받는 객체가 다른 객체이기 때문에 작동하지 않는다.)