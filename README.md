## 견고한 설계 철학과 높은 구현 생산성을 보유한 백엔드 개발자

- Portfolio web: https://shiniseong.github.io/
- LinkedIn: [https://www.linkedin.com/in/희성-신-7a5916281/](https://www.linkedin.com/in/%ED%9D%AC%EC%84%B1-%EC%8B%A0-7a5916281/)
- Email: [hss275989@gmail.com](mailto:hss275989@gmail.com)
- GitHub: https://github.com/shiniseong
- Blog: [https://shin-e-dog.tistory.com](https://shin-e-dog.tistory.com/)

---

## Summary

- 2년차 회고: https://shin-e-dog.tistory.com/170
- Kotlin과 Spring 기반으로 결제, 인증, 외부 기기·외부 API 연동이 많은 서버 시스템을 설계하고 개발해 왔습니다.
- 최근에는 디지털 치료제 클릭리스의 의료진용 대시보드 백엔드, 환자용 DTx 백엔드, 인증 서버를 새로 설계·개발하며 레거시 구조를 운영 가능한 형태로 다시 세우는 일을 맡았습니다.
- 10개월간 약 **11만줄 상당의 3개 서버를 구축**하여 높은 생산성을 입증한 경험이 있습니다.
- 그 과정에서 **헥사고날 아키텍쳐 설계,** 도메인 모델 재설계, 멀티모듈 모노레포 구성, 배치 파이프라인 설계, R2DBC+jOOQ 트랜잭션 트러블슈팅 등을 수행했습니다.
- 식약처 등 관련 기관과 직접 소통하며 **사이버 보안 가이드 라인에 대응**하여 디지털 의료기기 인허가에 기여한 경험이 있습니다.
- KSP 기반 코드 생성 라이브러리 개발로 **보일러 플레이트 코드를 94% 감축**시킨 경험이 있습니다.
- 이전 회사에서는 POS·키오스크·테이블오더 도메인에서 **사내 공용 라이브러리와 멀티플랫폼 아키텍처를 설계**하며 개발 생산성과 구조 품질을 높이는 일에 집중했습니다.다.

---

## Core Skills

- Language: **Kotlin**, SQL
- Backend: **Spring Boot**, Spring WebFlux, gRPC, Armeria
- Data: **R2DBC, jOOQ,** Redis, SQLite, MS-SQL, MySQL
- Auth / Integration: AWS Cognito, JWT, SMS OTP, 본인인증, 외부 기기 연동
- Architecture: **Hexagonal Architecture, 멀티모듈 모노레포**, Batch / Outbox
- Tooling: **Gradle**, KSP, Git, AWS

---

## Experience

### 비욘드메디슨 | Backend Developer

2025.04 ~ 현재

### 클릭리스 백엔드 설계 및 개발

- 입사 직후 인수인계와 기준이 거의 없는 상태에서 **클릭리스** 의료진용 대시보드 백엔드, 환자용 DTx 백엔드, 인증 서버의 기술 스택과 아키텍처 기준을 직접 정하고 구현했습니다.
- 2025년 4월 입사 후 9월 **GAMEX** 일정에 맞춰 의료진용 웹 백엔드를 구축했고, 이어 3~4개월 내 환자용 앱 백엔드와 공통 인증 서버까지 개발했습니다.
- 레거시에서 **환자-처방-활동기록** 관계가 잘못 모델링되어 재처방과 기능 확장이 어려운 문제를 확인하고, 도메인 경계를 다시 세운 뒤 **멀티모듈 모노레포와 헥사고날 아키텍처**로 구조를 설계했습니다.
- 인증 서버에는 **AWS Cognito**, **JWT**, **SMS OTP**, 본인인증 흐름을 통합했고, 대시보드·DTx 서버가 공통으로 사용할 수 있는 인증 경계를 별도 서비스로 분리했습니다.
- 구조를 다시 세우는 과정에서 gRPC 메타데이터 규약, proto 관리 기준까지 함께 정리해 이후 변경이 한 저장소 안에서 설명 가능하게 만들었습니다.

### 알림 배치 설계

- 기존 알림 배치는 전체 활성 처방 조회, 대상 선정, 알림 저장, 외부 FCM 호출이 한 스케줄러에 섞여 있어 규모가 커질수록 실패 복구와 중복 실행 제어가 어려운 상태였습니다.
- 이 구조를 **NotificationBatchJob → Materializer → PushOutbox → Dispatch** 파이프라인으로 나누어, 스케줄러는 작업 생성만 담당하고 실제 발송은 상태 기반으로 처리되도록 재설계했습니다.
- 대상 선정 단계에서 “지금 실제로 보내도 되는 사용자”만 반환하게 바꾸고, 로그아웃 사용자·중복 실행·부분 실패를 구조적으로 흡수할 수 있게 했습니다.
- 외부 FCM 호출에는 청크 제한, 토큰 단위 결과 수집, 상태 기반 재시도, 작업 전체 상태 추적을 도입해 운영 가능한 배치 흐름으로 바꿨습니다.
- 이 경험을 통해 단순한 기능 구현보다 **실패를 상태로 다루는 구조**, **외부 의존성을 가볍게 다루지 않는 설계**를 중요하게 보게 되었습니다.

### 트러블슈팅 및 규제 대응

- **@Transactional suspend fun** 내부에서 **R2dbcEntityTemplate**은 롤백되지만 jOOQ insert는 남는 문제를 재현 테스트와 커넥션 식별 로그로 추적해, 두 경로의 커넥션 획득 방식이 다르다는 원인을 확인했습니다. 이후 Spring이 관리하는 커넥션을 직접 회수해 jOOQ 실행 경로를 맞추는 공통 방식으로 정리해 트랜잭션 일관성을 확보했습니다.
- gRPC-Web 요청이 CORS 문제로 실패하는 문제를 해결했습니다. CORS의 preflight가 OPTIONS 메서드를 사용하기 때문에 POST 기반인 gRPC 스펙의 AWS LB 타깃 그룹에 제대로 전달되지 않는 문제였습니다.
- 식약처 디지털 의료기기 인허가 대응에서는 **사이버보안 가이드라인을 실제 구현과 연결해 해석**하고, 왜 해당 증적이 충분한지 직접 설명하는 역할을 맡았습니다.
- 코드 작성뿐 아니라 범위 결정, 근거 문서 정리, 타 팀과의 설명 책임까지 맡으며 “기술적 정답”보다 “설명 가능한 기준과 합의”가 중요한 상황을 여러 번 경험했습니다.

**Tech:** Kotlin, Spring Boot, WebFlux, gRPC, Armeria, R2DBC, jOOQ, Redis, AWS Cognito, JWT, SMS OTP, AWS

---

### 아이엠티소프트 | Backend Developer

2023.08 ~ 2025.03

### 멀티플랫폼 POS 아키텍처 및 비즈니스 로직 리딩

- 사수 퇴사 이후 회사의 핵심 프로젝트 중 하나인 **멀티플랫폼 POS의 아키텍처 설계**와 비즈니스 로직 개발을 맡았습니다.
- 외부 의존성이 많은 오프라인 결제 솔루션을 기존 계층형 구조로는 표현하기 어렵다고 판단해, 헥사고날 아키텍처와 Port-Adapter 구조로 핵심 비즈니스 로직과 외부 연동 경계를 분리했습니다.
- 그 결과 다양한 외부 의존 관계를 모듈 수준에서 설명할 수 있게 되었고, 핵심 로직의 재사용성과 테스트 용이성을 높였습니다.

### 사내 공용 라이브러리 개발

- **persistence-code-generator**를 개발해 엔티티 추가 시 반복되던 영속성 계층 코드를 크게 줄였습니다.
- 도메인 엔티티에 어노테이션으로 메타데이터를 정의하고, KSP 기반 코드 생성으로 KTORM 엔티티, 테이블 정의, DDL 생성을 자동화했습니다.
- **DDL-DSL**을 함께 개발해 SQLite, MS-SQL 등 여러 RDBMS에서 사용할 DDL을 타입 안전한 Kotlin DSL로 작성할 수 있게 했습니다.
- **BridgeApi**를 개발해 Android WebView와 네이티브 코드 간 통신을 REST API 스타일로 정리했고, 직렬화/에러 처리/라우팅을 한 경계로 모아 크로스플랫폼 구현 부담을 낮췄습니다.
- 이 라이브러리들은 개인 시간까지 투자해 완성도를 높였고, 다른 팀 프로젝트에도 도입되어 개발 생산성 향상에 기여했습니다.

### 주문·결제·외부 기기 연동 개발

- **지미존스 키오스크** 프로젝트에서 주문 처리 백엔드, 결제 데이터 생성, 주방 모니터·프린터 연동 코드를 작성했습니다.
- **아임오더** 프로젝트에서는 Windows Desktop App 개발, 프론트 아키텍처 설계, 이벤트 시스템 개발, 주문 처리와 외부 연동을 맡았습니다.
- 테이블오더용 Windows 앱 개발 당시 Swing 대신 Compose Multiplatform을 빠르게 학습해 목업을 제안했고, 실제 프로덕션 출시까지 연결했습니다.
- 입사 2개월 차에는 EPSON 써멀 프린터 라이브러리를 직접 만들어 네트워크, 시리얼, USB 등 다양한 연결 방식과 바코드·QR·이미지 출력 기능을 공통화했습니다.

**Tech:** Kotlin, Spring, KMP, Compose Multiplatform, KSP, KTORM, SQLite, MS-SQL, Android WebView

---

## Selected Projects / Libraries

### 클릭리스 백엔드 설계 및 구현

- 기간: 2025.04 ~ 현재
- 역할: 대시보드 백엔드, DTx 백엔드, 인증 서버 설계·개발
- 핵심 성과: 잘못된 도메인 모델을 재정의하고, 멀티모듈 모노레포 + 헥사고날 구조 + 공통 인증 경계로 재구성
- 링크:
    - https://shin-e-dog.tistory.com/171
    - https://shin-e-dog.tistory.com/172

### 클릭리스 알림 배치 설계

- 기간: 운영 중 개선
- 역할: 레거시 알림 배치 문제 분석 및 파이프라인 재설계
- 핵심 성과: 대상 선정, 생성, 외부 발송, 재시도를 분리해 실패 복구와 운영 가시성을 확보
- 링크:
    - https://shin-e-dog.tistory.com/176
    - https://shin-e-dog.tistory.com/179

### persistence-code-generator

- 기간: 2024.08 ~ 2024.09
- 역할: KSP 기반 영속성 코드 생성기 설계·개발
- 핵심 성과: 반복 코드와 수동 스키마 반영 비용을 줄이고, 영속성 계층 변경을 더 안전하게 만들었습니다.
- 링크:
    - https://shin-e-dog.tistory.com/116

### DDL-DSL

- 기간: 2024.07 ~ 2024.08
- 역할: 다중 RDBMS 대상 DDL DSL 설계·개발
- 핵심 성과: SQLite, MS-SQL 등 환경 차이를 감싸는 타입 안전한 Kotlin DSL 제공
- 링크:
    - https://shin-e-dog.tistory.com/113

### BridgeApi

- 기간: 2024.06 ~ 2024.07
- 역할: WebView-네이티브 브리지 라이브러리 설계·개발
- 핵심 성과: REST API 스타일 인터페이스로 브리지 경계를 정리하고 크로스플랫폼 구현 부담을 낮춤
- 링크:
    - https://shin-e-dog.tistory.com/105
    - https://github.com/shiniseong/bridge-api

---

## Writing / Proof

- [클릭리스 백엔드 설계편 - 1] 왜 다시 만들어야 했는가?
    
    https://shin-e-dog.tistory.com/171
    
- [알림 배치 설계편 - 1] 레거시 문제점 파악
    
    https://shin-e-dog.tistory.com/176
    
- [알림 배치 설계편 - 4] PushOutbox 처리 로직
    
    https://shin-e-dog.tistory.com/179
    
- [jOOQ, R2DBC] 같은 @Transactional 인데 왜 R2dbcEntityTemplate 은 롤백되고 jOOQ는 남았을까?
    
    https://shin-e-dog.tistory.com/180
    
- [인허가, 사이버 보안] 식약처 디지털 의료기기 인허가 통과 경험: 개발자의 업무 영역은 코드에서 끝나지 않는다
    
    https://shin-e-dog.tistory.com/182
    

---

## Education / Certificate

- NAVER CLOUD PLATFORM Certified Expert
- 네이버 클라우드 캠프 2기, 비트캠프 Java 기반 웹 풀스택 과정 수료 (2022.12 ~ 2023.06)
- 디지털미디어고등학교 졸업
- 성균관대학교 사회학과 중퇴
