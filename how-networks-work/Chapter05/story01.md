# 웹 서버의 설치 장소

## 사내에 웹 서버를 설치하는 경우

예전에는 사내의 LAN 에 서버를 설치하고, 인터넷에 직접 액세스하는 방식을 사용했지만,  
IP 주소의 부족이나, 보안상의 이유로 방화벽을 두는 방법을 많이 사용한다.

방화벽은 관문의 역할을 하여 특정 서버에서 동작하는 특정 애플리케이션에 액세스하는 패킷만 통과시키고,  
그 외의 패킷은 차단한다.  
이 때문에 애플리케이션에 보안이 허술해도, 위험성이 적어진다.  
하지만 액세스를 허가한 애플리케이션에 보안 구멍이 있으면 공격받을 위험성이 남아있기 때문에 완전히 안전하지는 않다.  
그래도 보안이 전부 무방비 상태가 되는 것에 비하면 위험성이 크게 낮기 때문에 방화벽을 두는 방법을 많이 사용하는 것이다.

## 데이터센터에 웹 서버를 설치하는 경우

웹 서버를 사내에 설치하지 않고, 프로바이더 등이 운영하는 데이터센터라는 시설에 서버를 가지고 들어가 설치하거나,  
프로바이더가 소유하는 서버를 빌려쓰는 형태로 운영하는 경우도 있다.

데이터 센터는 프로바이더의 중심 부분에 있는 NOC 에 직접 접속되었거나 프로바이더들이 상호 접속하는 IX에 직결되어 있다.  
인터넷 중심 부분에 고속 회선으로 접속되었으므로 여기에 서버를 설치하면 고속으로 액세스 할 수 있다.

이 경우는 서버에 대한 액세스가 증가했을 때 효과적이고,  
데이터센터는 보통 내진 구조의 건물에 설치하거나, 자가 발전장치를 비치하거나, 24시간 입실과 퇴실이 관리되는 곳이 많고,  
그 외에 기기의 가동 상태 감시, 방화벽의 설치 운영, 부정 침입 감시라는 부가 서비스를 제공하는 경우가 있어 안정성이 높다.

웹 서버가 데이터센터에 설치된 경우엔 인터넷의 중심 부분에서 데이터센터로 패킷이 흘러가고, 여기에서 서버 머신에 도착한다.  
데이터센터에 방화벽등이 설치되었으면 점검을 받고 나서 서버에 도착한다. 어느 경우든 패킷은 라우터에서 중계되고 최종적으로 서버에  
도착한다는 점은 달라지지 않는다.