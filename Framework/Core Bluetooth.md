# Core Bluetooth 코어 블루투스
애플 공식 문서: https://developer.apple.com/documentation/corebluetooth

## 용어 정리
- **BLE** : Bluetooth Low Energy의 약자. 기존 블루투스 통신의 단점이었던 전력소비를 보완한 저전력 블루투스. Core Bluetooth가 BLE를 쉽게 사용할 수 있도록 애플에서 제공하는 프레임워크.
- **Peripheral**: iOS에 연결하는 주변기기
- **Central**: 제어하는 iOS APP

## Core Bluetooth 특징
- 다른 클래스들의 하위 클래스로 사용될 수 없음.
- Core Bluetooth의 background 실행은 iOS에서만 가능.

## 블루투스 연결 flow
1. Peripheral가 Central이 검색할 수 있도록 광고.
2. Central이 Peripheral을 검색하고 연결을 요청.
3. 연결한 Peripheral에 대한 탐색 시작.
4. Peripheral의 데이터와 상호작용.

## 클래스 & 프로토콜
~~~swift
class CBCentralManager   
// 주변기기를 검색, 연결, 관리하기 위한 하나의 오브젝트.

class CBPeripheral
// 주변기기를 나타내며 이를 통해 데이터를 송수신.

protocol CBCentralManagerDelegate   
// 주변기기를 탐색하고 관리하기 위해 발생되는 Update를 지원하는 프로토콜.

protocol CBPeripheralDelegate
// 주변기기의 서비스를 사용하기 위해 발생하는 Update를 지원하는 프로콜.
~~~

## Peripheral의 데이터 구조
- Peripheral의 데이터는 1개 이상의 Service로 이루어져 있음. Servie는 Peripheral이 가지고 있는 하나의 기능.
- Service는 Characterstic을 가지고 있는데, 이는 Peripheral이 가지고 있는 실질적인 데이터를 나타냄.
다음 클래스로 관리 동작됨.
~~~swift
class CBService
// 장치의 특성 또는 기능을 수행하는 관련 동작과 데이터의 컬렉션.

class CBChracteristic
// 원격 주변기기 서비스의 Characteristic.
~~~

## CBCentralManager 검색 flow
1. Peripheral의 Service 검색
2. Service 내의 Characteristic 검색.
***

### Reference by
- [stacktree 님의 github](https://staktree.github.io/ios/iOS-Bluetooth-01-about-CoreBluetooth/#periphral%EC%9D%98-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EA%B5%AC%EC%A1%B0%EC%99%80-%EC%84%9C%EB%B9%84%EC%8A%A4%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C)