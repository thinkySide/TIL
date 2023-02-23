# WebKit 웹킷

## Define
- Apple 공식 문서 : https://developer.apple.com/documentation/webkit
- 웹 콘텐츠를 앱에 원활하게 통합하고 앱의 요구사항에 맞게 콘텐츠 상호 작용을 사용자 지정합니다.

## WebView
Webkit 프레임워크에 내장된 웹브라우저 컴포넌트로 View의 형태로 앱에 삽입하는 것.

## WKWebView
- 가장 많이 사용하는 WebView
- iOS 9 이상 버전 지원
- 쿠키 허용 설정 및 고급 캐시 설정 지원 X (앱 종료 시 HTML5 로컬 스토리지 삭제) 
(이거 할려면 SFSafariView 찾아보기)

## WebView 애플 심사 관련
- 안그래도 까다로운 심사 중에서도 특히 WebView 타입에서 리젝율이 높다고 한다.
- 다음과 같은 이유들로 많이 리젝이 된다고 한다.
   - Push 알림 기능 단순 추가
   - 결제 처리시 외부 연동 및 포인트 정책 현황 (폐쇄형, B2V 쇼핑몰 등은 반드시 테스트 계정도 알려주어야 한다고 함.)
   - 웹서비스 자체와 연관없는 앱 기능
   - 인앱서비스에 대한 외부 홍보
   - 앱이라기 보다는 웹에 가까우니 기능 추가 후 심사

### Ref.
- [thoonk 님의 블로그](https://thoonk.tistory.com/87)