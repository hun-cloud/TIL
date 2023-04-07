# OSI 7 레이어 모델 개념
OSI 7 레이어 모델 국제표준화기구에서 개발한 모델로 복잡한 네트워크 동작 과정을 7개 계층으로 나누어 네트워크 통신 흐름을 한눈에
알아보고 이해할 수 있게 도와주는 역할을 합니다. 계층별로 하위 계층의 기능을 이용하고 상위 계층으로 기능을 제공하는 상하 관계를
맺고 있습니다.

## OSI 7 레이어 계층 설명
![osi7layer](https://user-images.githubusercontent.com/89080095/230551832-c95b67c1-f47a-4ee9-a56e-581cb52979a6.PNG)
TCP/IP 프로토콜이란 네트워크를 통해 통신하는데 쓰이는 통신 규약의 모음입니다.

### 1Layer - physical 계층
Physical 계층은 물리 계층으로 네트워크 하드웨어 전송 기술을 말합니다. 물리적인 링크의 연결, 유지, 해제를 담당합니다.
* Ethernet
* Wi-Fi
* Modem
* Cable

### 2Layer - Data Link 계층
Data Link 계층은 Physical 계층에서 송수신되는 정보의 오류와 흐름을 관리하여 데이터의 전달을 수행하는 역할을 합니다. 
OSI 1계층과 OSI 2 계층을 TCP/IP 프로토콜 상 Network Interface 계층으로 분류하며, 해당 계층에는 Ethernet, Wi-Fi, 물리적인
케이블 등이 포함됩니다.

### 3Layer - Network계층
Network 계층의 핵심은 데이터를 목적지까지 빠르고 안전하게 전달(라우팅)하기 위한 것으로 여러 노드를 거칠 때마다 최적의 경로를
찾아주는 역할을 합니다.
* Ip
* ARP
* ICMP

### 4Layer - Transport 계층
Transport 계층은 전송 계층으로 종단의 사용자 간 데이터를 통신을 다루는 최상위 계층으로
데이터 전달의 유효성과 효율성을 보장받습니다.
* TCP
* UDP

### 5Layer - Session 계층
Session 계층은 종단의 사용자 간의 응용 프로세스 통신을 관리하기 위한 방법을 제공합니다.
데이터의 통신을 위한 논리적인 연결을 말합니다.

### 6Layer - Presentation 계층
Presentation 계층은 데이터의 형식상 차이에 대해 송/수신자 간 이해할 수 있는 형태로 데이터를 표현하는
기능을 담당합니다. 데이터 암호화 및 압축 등을 수행합니다.

### 7Layer - Application 계층
Application 계층은 응용 프로세스와 직접 연계하여 실제 응용 프로그램을 사용하게 하는 계층입니다.
* HTTP
* SSH
* FTP
* DHCP







