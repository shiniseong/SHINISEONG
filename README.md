# 신희성 | 오프라인 결제 솔루션 개발자

## 👋 소개
오프라인 결제 솔루션 개발자 신희성입니다. 

운영중인 시스템의 문제점을 개선하기 위해 라이브러리를 개발하고, 더 나은 구조를 위해 아키텍처를 설계하는 등 **시스템의 품질 향상**에 관심이 많습니다.

학습과 인지 심리학, 뇌 과학 서적을 즐깁니다.

올바른 기록법에 관심을 가지기 시작한지 세 달 정도 지난 요즈음은 **기록의 즐거움**에 푹 빠져있습니다.
[기술블로그](https://shin-e-dog.tistory.com/)

## 💪 강점
##### 학습 및 응용 능력
 - 부트캠프 수료 후 신입 1년 동안 KSP, 리플렉션 등을 학습하여 4개의 사내 공용 라이브러리를 제작하고, 사내 최중요 프로젝트 중 하나를 설계하였습니다.
 - 자세한 내용은 아래 프로젝트와 라이브러리 부분을 참조 부탁드립니다.(관련된 블로그 포스팅도 링크되어 있습니다.)
##### 친화력
  - 그냥 사람들과 어울리는 걸 좋아합니다.
  - 처음 입사했을 때, 서로 인사도 하지 않던 팀 분위기를 180도 바꾸었습니다.(라고 동료 분이 말씀해 주셨습니다. 진짜로요..!)
##### 기여 욕구와 열정
 - 관종이라고 불리울 수 있지만, 제가 속한곳에 능력으로 기여하는 것에 큰 보람을 느낍니다.
 - 사내 주요 프로젝트 중 하나였던 테이블 오더 개발시 POS 기기에 설치되어 예하의 테이블오더를 제어하고 외부 기기와의 연동을 담당하는 JVM 기반 윈도우 앱을 제작해야 했습니다. 
이 때 Swing을 사용하자는 지시 대신, 밤새 컴포즈 멀티플랫폼을 배우고 간단한 목업을 만들어 가서 컴포즈로 만든 윈도우 앱을 성공리에 프로덕션 출시한 경험이 있습니다.
 - 신입이었음에도 사내 라이브러리 등의 제작에 열을 올린 이유이기도 합니다. 라이브러리의 경우도 퇴근 후 개인 시간에 많은 부분을 개발하였습니다.

## 💼 경력 사항
### 아이엠티소프트 (2023.08 ~ 현재)
- 안드로이드 POS, 안드로이드 TableOrder 윈도우즈 KIOSK 등 오프라인 결제 솔루션 개발
- BridgeApi, DDL-DSL, persistence-code-generator 등 사내 라이브러리 개발 
- 멀티플랫폼 POS 프로젝트 아키텍처 설계

## 🎯 주요 문제 해결 사례

### 1. 레거시 아키텍처 개선

**문제 상황**
- 계층형 아키텍쳐 외부 의존성이 많은 오프라인 결제 솔루션을 제대로 표현하기 힘들어, 서비스 레이어가 비대해지는 문제 
- 비즈니스 로직 계층(core)이 외부 의존성을 직접 참조하는 의존성 흐름의 구조적 문제(클린 아키텍쳐만이 정답이라고 생각하는 광신도는 아닙니다..!)
- 서비스 레이어의 책임과 역할이 불명확
- 빈약한 도메인 모델로 인한 비즈니스 로직 산재

**해결 방안**
- 헥사고날 아키텍처 도입으로 계층 간 의존성 명확화
- Port & Adapter 패턴을 통한 외부 시스템과의 명확한 경계 설정
- 도메인 주도 설계 원칙 적용으로 비즈니스 로직 응집도 향상

**결과**
- 다양한 외부 의존 관계를 모듈 레벨에서 표현
- 비즈니스 로직의 순수성 확보
- 테스트 용이성 향상
- 다양한 오프라인 결제 솔루션에서 핵심 비즈니스 로직 재사용 가능

[아키텍쳐 설계 도전기 블로그 포스팅](https://shin-e-dog-ex63b.tistory.com/131)

### 2. 영속성 계층 보일러플레이트 코드 문제
**문제 상황**
- 멤버 프로퍼티가 다섯개 정도인 간단한 도메인 엔티티 하나 추가시에도 KTORM 엔티티, KTORM 테이블 정의, DDL SQL 문 등 200~300줄 이상의 반복 코드 필요
- 휴먼 에러 발생 가능성이 높은 수동 코드 작성

**해결 방안**
- KSP를 활용한 코드 생성기(persistence-code-generator) 개발
- 멀티 RDBMS 지원을 위한 DDL-DSL 개발
- 도메인 엔티티에 어노테이션 기반의 메타데이터 정의 방식 도입

**결과**
- 보일러플레이트 코드 최대 94% 감소 (300줄 → 20줄)
- 데이터베이스 스키마 변경 시 발생하는 휴먼 에러 방지
- 타 팀 프로젝트에도 도입되어 개발 생산성 향상에 기여

[KSP 기반 코드 생성기 개발 수기 블로그 포스팅](https://shin-e-dog.tistory.com/116)

[DDL-DSL 개발 수기 블로그 포스팅](https://shin-e-dog.tistory.com/113)

### 3. WebView JavaScript Bridge 인터페이스 표준화
**문제 상황**
- 웹뷰와 네이티브 코드 간 통신을 위한 수많은 JavascriptInterface 메서드 노출
- 직렬화/역직렬화 로직이 비즈니스 로직과 뒤섞임
- 공통된 에러 처리 부재
- RN이 아닌 React를 그대로 사용해 안드로이드와 윈도우즈 두 플랫폼을 쉽게 지원할 수 있어야 함. (인력 수급의 문제로 RN 개발자를 추가로 고용할 수 없는 상황이었습니다. 또한, 빼곡한 개발 일정으로 프론트 엔드 개발자 분들이 RN을 학습하여 개발하기도 어려운 상황이었습니다.)

**해결 방안**
- JS Bridge를 통해 안드로이드 네이티브 코드를 REST API 스타일로 호출할 수 있도록 도와주는 Bridge API 라이브러리 개발
- 라우터 시스템 도입으로 요청/응답 처리 일원화
- 중앙화된 에러 핸들링 시스템 구현

**결과**
- 웹 개발자에게 친숙한 REST API 스타일 인터페이스 제공
- 코드의 구조화 및 유지보수성 향상
- 안드로이드 네이티브 코드도 REST API 형태로 호출함으로서, 클라이언트 라이브러리만 axios등으로 교체하는 것만으로(method와 uri는 그대로 사용) 크로스플랫폼 지원 가능

[BridgeApi 개발 수기 블로그 포스팅](https://shin-e-dog.tistory.com/105)

[BridgeApi 소스 저장소](https://github.com/shiniseong/bridge-api)

 
## 🚀 신규 개발 프로젝트

### 아이포스: 멀티플랫폼 POS 프로젝트 아키텍처 설계 및 비즈니스 로직 개발 리딩
**프로젝트 기간: 2024.09 ~ 진행중**

[아키텍쳐 설계 도전기 블로그 포스팅](https://shin-e-dog-ex63b.tistory.com/131)

#### 주요 역할 및 성과
- 헥사고날 아키텍처 설계 및 적용
- 비즈니스 로직 개발 리딩
- 도메인 주도 설계 원칙 도입으로 비즈니스 로직 응집도 향상
- 인터페이스를 통한 외부 시스템과의 명확한 경계 설정
- 플랫폼 독립적인 설계로 크로스플랫폼 지원 용이성 확보

#### 사용 기술 및 아키텍쳐
- Kotlin Multiplatform
- Hexagonal Architecture

### 지미존스 키오스크: Windows 키오스크 프로젝트 개발
**프로젝트 기간: 2024.03 ~ 2424.06**
**이후 운영 및 유지보수 진행중**

####  주요 역할 및 성과
- 주문 처리 백엔드 코드 작성
- 결제 처리 및 결제 데이터 생성 코드 작성
- 주방 모니터 및 프린터 연동 코드 작성

#### 사용 기술
- Kotlin, Spring

### 아임오더: 안드로이드 테이블오더 프로젝트 개발
**프로젝트 기간: 2024.01 ~ 2024.03**
**이후 운영 및 유지보수 진행중**

####  주요 역할 및 성과
- 테이블 오더 기기를 중앙에서 관리하는 Windows Desktop App 개발
- KMP를 활용한 UI 개발의 패키지 구조 및 전역 상태 관리 등을 포함한 프론트 아키텍쳐 설계
- 다양한 도메인 이벤트를 관리하는 이벤트 시스템 개발
- 주문 처리 및 주문 데이터 외부 연동 개발

#### 사용 기술
- Kotlin, Armeria, Kotlin Multi Platform, Compose

### 아트밸리 썰매 입장 관리: 입장관리 DIT 프로젝트 개발
####  주요 역할 및 성과
- Angular를 사용한 화면 개발
- 프린터 연동 코드 개발
- Nice Van사 연동 결제 코드 개발

#### 사용 기술
- Kotlin, Angular, Undertow


## 📚라이브러리

### persistence-code-generator 라이브러리 개발
**개발 기간: 2024.08 ~ 2024.09**

[개발 수기 블로그 포스팅](https://shin-e-dog.tistory.com/116)

#### 주요 역할 및 성과
- KSP(Kotlin Symbol Processing)를 활용한 영속성 계층 코드 자동 생성
- 보일러플레이트 코드 94% 감소 달성
- 데이터베이스 스키마 변경 시 발생하는 휴먼 에러 방지
- 타 팀 프로젝트에도 도입되어 개발 생산성 향상에 기여

#### 사용 기술
- Kotlin, KSP(Kotlin Symbol Processing)
- KTORM(ORM), DDL-DSL(자체 제작 라이브러리)

### DDL-DSL 라이브러리 개발
**프로젝트 기간: 2024.07 ~ 2024.08**

[개발 수기 블로그 포스팅](https://shin-e-dog.tistory.com/113)

#### 주요 역할 및 성과
- SQLite, MS-SQL 등 다양한 RDBMS 지원을 위한 DDL DSL 개발
- 플루언트 DSL API를 통한 직관적인 테이블 정의 기능 제공
- 코틀린의 타입 시스템을 활용한 컴파일 타임 타입 안전성 확보
- 타 팀 프로젝트에도 도입되어 개발 생산성 향상에 기여

#### 사용 기술
- Kotlin DSL
- SQLite, MS-SQL

### BridgeApi 라이브러리 개발 
**프로젝트 기간: 2024.06 ~ 2024.07**

[개발 수기 블로그 포스팅](https://shin-e-dog.tistory.com/105)
[BridgeApi 저장소](https://github.com/shiniseong/bridge-api)

#### 주요 역할 및 성과
- 웹뷰와 네이티브 코드 간 통신을 위한 브릿지 API 개발
- REST API 스타일의 직관적인 인터페이스 제공
- 웹뷰를 통한 멀티플랫폼 구현에 편의성 제공

#### 사용 기술
- Kotlin, TypeScript
- Android WebView

### Epson 써멀 프린터 라이브러리 개발

[개발 수기 블로그 포스팅](https://shin-e-dog.tistory.com/125)

#### 주요 역할 및 성과
- 네트워크, 시리얼, USB 등 다양한 연결 방식 지원 개발
- 텍스트, 바코드, QR코드, 이미지 등 다양한 출력 기능 제공
- 연결 상태 모니터링 및 에러 처리 시스템 제공

#### 사용 기술
- Kotlin

## 🛠️ 운영 및 유지보수 프로젝트
### 서브웨이 키오스크
**운영 기간: 2023.08 ~ 진행 중**

### 파파이스 키오스크
**운영 기간: 2023.08 ~ 진행 중**

### 윙스탑 키오스크
**운영 기간: 2023.08 ~ 진행 중**

### 단체급식 입장관리(DIT)
**운영 기간: 2023.08 ~ 진행 중**

### 써브웨이 고객 호출 모니터(DID)
**운영 기간: 2023.08 ~ 진행 중**

## 🔧 기술 스택

### Backend
- Kotlin
- Spring Boot, Ktor
- KTORM, JPA

### Database
- SQLite, MS-SQL

### Architecture & Design
- Hexagonal Architecture
- Domain-Driven Design

## 자격증
- NAVER CLOUD PLATFORM Certified Expert

## 📚 교육
- 네이버 클라우드 캠프 2기 (2022.12 ~ 2023.06)
  - 교육 기관: 비트캠프
  - Java 기반 웹 풀스택 과정
  - Spring Boot, React 실무 프로젝트 수행

## 📞 연락처
- Email: hss275989@gmail.com
- Github: https://github.com/shiniseong
- Blog: https://shin-e-dog.tistory.com/
- Kakao: https://open.kakao.com/o/shucDW8g
