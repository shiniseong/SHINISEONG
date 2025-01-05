![header](https://capsule-render.vercel.app/api?type=waving&color=auto&height=300&section=header&text=Welcome!&fontSize=50&fontColor=FFFFFF&animation=fadeIn&fontAlignY=38&desc=신희성의%20깃%20허브%20저장소에%20오신것을%20환영합니다&descAlignY=55&descAlign=50&descSize=35)

# 신희성 | Backend Developer

## 👋 Intro
백엔드 개발자 신희성입니다. 

운영중인 시스템의 문제점을 개선하기 위해 라이브러리를 개발하고, 더 나은 구조를 위해 아키텍처를 설계하는 등 **시스템의 품질 향상**에 관심이 많습니다.

## 💼 경력 사항
### 아이엠티소프트 (2023.08 ~ 현재)
- 안드로이드 POS, 안드로이드 TableOrder 윈도우즈 KIOSK 등 오프라인 결제 솔루션 개발
- BridgeApi, DDL-DSL, persistence-code-generator 등 사내 라이브러리 개발 
- 멀티플랫폼 POS 프로젝트 아키텍처 설계

## 🎯 주요 성과
- 영속성 관련 보일러플레이트 코드 94% 감소를 통한 개발 생산성 향상
- 3개의 사내 라이브러리 개발 및 성공적인 도입
- 헥사고날 아키텍처 도입을 통한 시스템 품질 향상
 
## 🚀 신규 개발 프로젝트

### 아이포스: 멀티플랫폼 POS 프로젝트 아키텍처 설계 및 비즈니스 로직 개발 리딩
**프로젝트 기간: 2024.09 ~ 진행중**

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
- 장바구니 처리 백엔드 코드 작성
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

## 🛠️ 운영 및 유지보수 프로젝트
### 서브웨이 키오스크
**운영 기간: 2023.08 ~ 진행 중**

### 파파이스 키오스크
**운영 기간: 2023.08 ~ 진행 중**

### 윙스탑 키오스크
**운영 기간: 2023.08 ~ 진행 중**

### 단체급식 입장관리 DIT
**운영 기간: 2023.08 ~ 진행 중**

### 써브웨이 고객 호출 DID
**운영 기간: 2023.08 ~ 진행 중**

## 📚라이브러리

### persistence-code-generator 라이브러리 개발
**개발 기간: 2024.08 ~ 2024.09**

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

#### 주요 역할 및 성과
- 웹뷰와 네이티브 코드 간 통신을 위한 브릿지 API 개발
- REST API 스타일의 직관적인 인터페이스 제공
- 라우팅 로직 최적화를 통한 성능 2배 향상 달성

#### 사용 기술
- Kotlin, TypeScript
- Android WebView



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

## 📚 Education
- 네이버 클라우드 캠프 2기 (2022.12 ~ 2023.06)
  - 교육 기관: 비트캠프
  - Java 기반 웹 풀스택 과정
  - Spring Boot, React 실무 프로젝트 수행

## 📞 연락처
- Email: hss275989@gmail.com
- Github: https://github.com/shiniseong
- Blog: https://shin-e-dog.tistory.com/
- Kakao: https://open.kakao.com/o/shucDW8g
