>[!properties]
>Created : `=this.file.cday`
>Modified : `=this.file.mday`
>Tags : #Spring #스파르타_내일배움캠프

# Spring Cloud 란?
- 마이크로 서비스 개발을 위한 다양한 도구와 서비스를 제공하는 Spring Framework의 확장으로, MSA를 쉽게 구현 및 운영할 수 있도록 돕는다.
## 주요 기능
- 서비스 등록 및 디스커버리
	- *Eureka*, Consul, Zookeeper
- 로드 밸런싱
	- *Ribbon*, Spring Cloud LoadBalancer
- 서킷 브레이커
	- *Hystrix*, Resilience4j
- API 게이트웨이
	- Zuul, *Spring Cloud Gateway*
- 구성 관리
	- Spring Cloud Config
- 분산 추적
	- Spring Cloud Sleuth, Zipkin
- 메시징
	- Spring Cloud Stream

## Spring Cloud 주요 모듈
### 서비스 등록 및 디스커버리
**Eureka**
- 넷플릭스가 개발한 서비스 디스커버리 서버로, MSA 아키텍처에서 각 서비스의 위치를 동적으로 관리한다.
- 서비스 레지스트리: 모든 서비스 인스턴스의 위치를 저장하는 주장 저장소
- 헬스체크(Health check: 서비스 인스턴스의 상태를 주기적으로 확인하여 가용성을 보장)

### 로드 밸런싱
**Ribbon**
- 넷플릭스가 개발한 클라이언트사이드 로드 밸런서로, 서비스 인스턴스간의 부하를 분산한다.
- 서버 리스트 제공자 : Eureka로부터 서비스 인스턴스 리스트를 제공받아 로드 밸런싱에 사용
- 로드 밸런싱 알고리즘 : 라운드 로빈, 가중치 기반 등 다양한 로드 밸런싱 알고리즘 지원
- Failover : 요청 실패시 다른 인스턴스로 자동 전환

### 서킷 브레이커
**Hystrix**
- 넷플릭스가 개발한 서킷 브레이커 라이브러리로, 서비스 간의 호출 실패를 감지하고 시스템의 전체적인 안정성을 유지
- 서킷 브레이커 상태 : 클로즈드, 오픈, 하프-오픈 상태를 통해 호출 실패를 관리
- Fallback : 호출 실패 시 대체 로직을 제공하여 시스템 안정성 확보
- 모니터링 : Hystirx Dashboard를 통해 서킷 브레이커 상태 모니터링

**Resilience4j**
- 자바 기반의 경량 서킷 브레이커 라이브러리로, 넷플릭스 Hystrix의 대안으로 개발
- 서킷 브레이커 : 호출 실패를 감지하고 서킷을 열어 추가적인 호출을 차단하여 시스템의 부하를 줄임
- Fallback : 호출 실패 시 대체 로직을 제공하여 시스템 안정성 확보
- 타임아웃 설정 : 호출의 응답 시간을 설정하여 느린 서비스 호출에 대응할 수 있음
- 재시도 : 재시도 기능을 지원하여 일시적인 네트워크 문제 등에 대응할 수 있음
## Spring Cloud 구성 요소의 활용
### API 게이트웨이
**Zuul**
- 넷플릭스가 개발한 API 게이트웨이로, 모든 서비스 요청을 중앙에서 관리
- 라우팅
- 필터 : 요청 전후에 다양한 작업을 수행할 수 있는 필터 체인 제공
- 모니터링 : 요청 로그 및 메트릭을 통해 서비스 상태 모니터링 할 수 있음

**Cloud gateway**
- Spring Cloud에서 제공하는 API gateway로, MSA에서 필수적인 역할을 수행
- *루팅 및 필터링* : 요청을 받아 특정 서비스로 라우팅하고, 필요한 인증 및 권한 부여를 수행
- *보안* : 외부 요청으로부터 애플리케이션을 보호하고, 보안 정책을 적용
- *효율성* : MSA에서 필요한 요청 처리 및 분산 환경의 관리를 효율적으로 수행

### 구성 관리
**Spring Cloud Config**
- 분산된 환경에서 중앙 집중식 설정 관리를 제공
- *Config 서버* : 중앙에서 설정 파일을 관리하고 각 서비스에 제공
- *Config 클라이언트* : Config 서버에서 설정을 받아서 사용하는 서비스 -> app
- *설정 갱신* : 설정 변경 시 서비스 재시작 없이 실시간으로 반영

> Spring Cloud 공식 Doc : https://spring.io/projects/spring-cloud

---

