<div align="center">

<!-- 로고 이미지가 있다면 아래 src를 교체해 주세요. -->
<img width="220" alt="ForPets Logo" src="https://github.com/user-attachments/assets/60c305dc-8fd2-45e9-b9cc-7c546a00cd61" />

# ForPets (포펫츠)

### 반려동물 보호자와 펫시터를 연결하는 양방향 케어 매칭 플랫폼

**순방향 요청 · 역방향 제안 · 예약 중심 상태 관리 · 실서비스형 백엔드 구조**

**TEAM 집사조**

[![API](https://img.shields.io/badge/API-Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)](#)
[![Docs](https://img.shields.io/badge/Docs-Project-181717?style=for-the-badge&logo=github&logoColor=white)](#)
[![GitHub](https://img.shields.io/badge/Repository-ForPets-181717?style=for-the-badge&logo=github&logoColor=white)](#)

</div>

---

## 목차

* [프로젝트 정보](#프로젝트-정보)
* [Getting Started](#getting-started)
* [프로젝트 비전](#프로젝트-비전)
* [주요 기능](#주요-기능)
* [핵심 비즈니스 플로우](#핵심-비즈니스-플로우)
* [팀 구성](#팀-구성)
* [개발 기간](#개발-기간)
* [기술 스택](#기술-스택)
* [시스템 아키텍처](#시스템-아키텍처)
* [데이터베이스 설계](#데이터베이스-설계)
* [대표 문서](#대표-문서)
* [향후 업데이트 계획](#향후-업데이트-계획)
* [라이선스 및 문의](#라이선스-및-문의)

---

## 프로젝트 정보

| 항목 | 내용 |
| --- | --- |
| **팀명** | **집사조** |
| **프로젝트명** | **ForPets (포펫츠)** |
| **플랫폼명** | **ForPets** — 반려동물 케어 매칭 플랫폼 |
| **버전** | v1.0.0 (MVP) |
| **개발 기간** | v1 개발 완료 목표 ~ 2026-06-22 |
| **팀 구성** | 백엔드 개발자 5명 |
| **Base URL** | `/api` |
| **인증 방식** | JWT Bearer Token |
| **프로덕션 URL** | 추후 연결 |
| **로컬 개발 URL** | Backend: [http://localhost:8080](http://localhost:8080) |

---

## Getting Started

### 백엔드 실행

```bash
./gradlew bootRun
# http://localhost:8080
```

### Docker 실행 예시

```bash
docker compose up -d
```

### API 문서

```text
Swagger UI: http://localhost:8080/swagger-ui/index.html
Base URL: /api
```

---

## 프로젝트 비전

반려동물을 키우는 보호자는 여행, 출장, 출근, 갑작스러운 일정 등으로 인해 반려동물을 직접 돌보기 어려운 상황을 자주 마주합니다.

기존 펫시터 서비스는 대부분 보호자가 직접 시터를 검색하고 신청하는 방식에 가깝습니다. 이 구조는 보호자가 원하는 조건에 맞는 시터를 직접 찾아야 하므로 시간이 오래 걸릴 수 있고, 시터 입장에서도 자신에게 맞는 케어 요청을 먼저 찾기 어렵다는 한계가 있습니다.

**ForPets**는 이러한 문제를 해결하기 위해 보호자가 직접 시터를 검색해 요청하는 **순방향 매칭(CareRequest)** 과, 보호자가 케어 공고를 등록하면 시터가 직접 제안하는 **역방향 매칭(Post → Proposal)** 을 함께 제공합니다.

또한 단순 CRUD 구현을 넘어서, 예약 충돌, 결제 지연, 중복 요청, 예약 만료, 상태 전이처럼 실제 서비스에서 중요한 백엔드 문제를 **Reservation 중심 설계**로 해결하는 것을 목표로 합니다.

### 핵심 가치 제안

| 가치 | 설명 |
| --- | --- |
| **양방향 매칭** | 보호자의 직접 요청과 시터의 제안 방식을 모두 지원 |
| **유연한 선택 구조** | 보호자는 직접 요청하거나 여러 제안을 비교해 선택 가능 |
| **Reservation 중심 구조** | 모든 매칭 흐름을 Reservation 생성과 상태 전이로 통합 |
| **예약 충돌 관리** | CONFIRMED 예약 기준으로 중복 예약과 시간 충돌 방지 |
| **실서비스 기반 확장성** | v1 핵심 예약 흐름 이후 결제, 알림, 채팅, AI 추천으로 확장 가능 |

---

## 주요 기능

### 1. 회원 / 인증 관리

* 회원가입 / 로그인 / 로그아웃
* JWT 기반 인증 / 인가
* Access Token 블랙리스트 기반 로그아웃 처리
* Refresh Token Redis 저장 및 Rotation 전략
* 내 정보 조회 / 수정
* 비밀번호 변경
* Soft Delete 기반 회원 탈퇴
* MEMBER / SITTER / ADMIN 역할 관리

### 2. 반려동물 관리

* 반려동물 등록 / 조회 / 수정 / 삭제
* 회원별 최대 10마리 등록 제한
* 진행 중 예약, OPEN 공고, PENDING 요청에 포함된 반려동물 삭제 제한
* PetSnapshot 기반으로 요청·공고·예약 당시 반려동물 정보 보존

### 3. 시터 프로필 / 스케줄 관리

* 시터 프로필 등록 / 조회 / 수정 / 삭제
* 시터 프로필 등록 시 MEMBER → SITTER 역할 전환
* RESERVABLE / NON_RESERVABLE 예약 가능 상태 관리
* 시터 주간 가능 시간 전체 교체 방식 관리
* 요일별 1개 시간대, 최대 7개 스케줄 등록
* 지역, 가능 동물 종류, 크기, 가격 조건 기반 시터 검색

### 4. 공고(Post) / 역방향 매칭

* 보호자 공고 등록 / 조회 / 수정 / 삭제
* 공고 상태 관리: OPEN / CLOSED / DELETED
* 반려동물과 TimeSlot을 포함한 케어 공고 작성
* 시터가 공고에 Proposal 등록
* 보호자가 Proposal 수락 / 거절
* Proposal 수락 시 Reservation 자동 생성

### 5. 돌봄 요청(CareRequest) / 순방향 매칭

* 보호자가 특정 시터에게 돌봄 요청 생성
* 시터가 받은 요청 조회
* 보호자가 보낸 요청 조회
* 요청 상세 조회
* 요청 수락 / 거절 / 취소
* 요청 수락 시 Reservation 자동 생성

### 6. 예약(Reservation) 관리

* CareRequest 수락 또는 Proposal 채택 시 예약 자동 생성
* 예약 상태 관리: PENDING / CONFIRMED / COMPLETED / CANCELED / EXPIRED
* 예약 확정 시 CONFIRMED 예약 충돌 검사
* 예약 취소 시 취소 사유와 취소 카테고리 관리
* Scheduler 기반 PENDING 예약 만료 처리
* 케어 완료 처리

### 7. 조회 최적화 / 캐싱

* QueryDSL 기반 동적 검색
* Redis 기반 시터 목록 검색 캐싱
* Redis 기반 시터 상세 조회 캐싱
* Redis 기반 공고 목록 검색 캐싱
* 캐시 무효화 및 Redis 장애 시 DB 조회 폴백

---

## 핵심 비즈니스 플로우

### 1. 순방향 매칭 — CareRequest

```text
1. 보호자(MEMBER)가 조건 기반으로 시터를 검색한다.
2. 보호자가 원하는 시터에게 CareRequest를 전송한다.
3. 시터(SITTER)가 받은 요청을 확인한다.
4. 시터가 요청을 수락하거나 거절한다.
5. 수락 시 Reservation이 PENDING 상태로 자동 생성된다.
6. 보호자와 시터가 각각 결제를 진행한다.
7. 양측 결제 완료 시 Reservation이 CONFIRMED 상태로 전환된다.
8. 케어 완료 후 시터가 COMPLETED 처리한다.
```

### 순방향 매칭 정책

| 항목 | 정책 |
| --- | --- |
| 요청 대상 | RESERVABLE 상태 시터에게만 요청 가능 |
| 본인 요청 | 본인의 시터 프로필에는 요청 불가 |
| 중복 요청 | 동일 시터 + 동일 petIds 조합의 PENDING 요청 중복 차단 |
| 예약 생성 | CareRequest ACCEPT 시 Reservation 자동 생성 |
| 충돌 검증 | 수락 시 CONFIRMED 예약과 충돌하면 차단 |

---

### 2. 역방향 매칭 — Post → Proposal

```text
1. 보호자(MEMBER)가 케어 공고를 등록한다.
2. 시터(SITTER)가 열린 공고 목록을 조회한다.
3. 시터가 가능한 공고에 Proposal을 제출한다.
4. 보호자가 들어온 제안을 비교한다.
5. 보호자가 Proposal 1건을 채택한다.
6. Proposal ACCEPT 시 Reservation이 PENDING 상태로 자동 생성된다.
7. 양측 결제 완료 시 Reservation이 CONFIRMED 상태로 전환된다.
8. Reservation CONFIRMED 시 Post는 CLOSED 처리된다.
9. 같은 공고의 나머지 PENDING Proposal은 REJECTED 처리된다.
```

### 역방향 매칭 정책

| 항목 | 정책 |
| --- | --- |
| 제안 가능 공고 | OPEN 상태 공고에만 Proposal 등록 가능 |
| 본인 공고 | 본인 공고에는 제안 불가 |
| 중복 제안 | 동일 공고에 동일 시터는 중복 제안 불가 |
| 예약 생성 | Proposal ACCEPT 시 Reservation 자동 생성 |
| 만료 처리 | Reservation EXPIRED 시 ACCEPTED Proposal은 PENDING 복원 |

---

## 팀 구성

| 역할 | 이름 | 주요 담당 기능 |
| --- | --- | --- |
| **Post / Proposal** | **권지원** | 공고 등록·조회·수정, PostTimeSlot, 역방향 매칭 흐름 |
| **Infra / CI/CD / Concurrency** | **박영수** | 배포, GitHub Actions, AWS, 동시성 제어, Kafka |
| **Query / Cache / Performance** | **선경안** | QueryDSL, 성능 병목 개선, Redis 캐싱 전략 |
| **AI / Payment / Frontend** | **이지민** | LLM 구조화 출력, Tool Calling, AI 장애 격리, 결제, 프론트엔드 초기 세팅 및 MVP 화면 구현 |
| **Auth / Realtime / Concurrency** | **최길중** | 회원가입, JWT, 권한 처리, 실시간 메시징, 동시성 |

### 공통 담당

* 테스트 코드 작성
* 도메인 설계 및 CRUD 구현
* 계층형 아키텍처 적용
* 부하 테스트
* ERD / API 문서 수정 및 통합

---

## 개발 기간

| 구분 | 주요 내용 |
| --- | --- |
| **Planning** | 프로젝트 개요서, 정책 문서, ERD, API 명세 작성 |
| **MVP Core** | 인증/인가, 회원, 반려동물, 시터, 공고, 요청, 제안, 예약 기능 구현 |
| **Optimization** | QueryDSL 검색, Redis 캐싱, 예약 충돌 검증, 성능 병목 개선 |
| **Deploy & QA** | Docker, AWS, GitHub Actions 기반 배포 및 테스트 |

---

## 기술 스택

### 백엔드

| 구분 | 기술 |
| --- | --- |
| **Language** | ![Java](https://img.shields.io/badge/Java-21-007396?style=for-the-badge&logo=openjdk&logoColor=white) |
| **Framework** | ![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-6DB33F?style=for-the-badge&logo=springboot&logoColor=white) |
| **ORM / Query** | ![Spring Data JPA](https://img.shields.io/badge/Spring%20Data%20JPA-59666C?style=for-the-badge&logo=hibernate&logoColor=white) ![QueryDSL](https://img.shields.io/badge/QueryDSL-5.x-0078D4?style=for-the-badge) |
| **Security** | ![Spring Security](https://img.shields.io/badge/Spring%20Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white) ![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white) |
| **Scheduler** | ![Scheduler](https://img.shields.io/badge/Scheduler-Reservation%20Expire-6DB33F?style=for-the-badge) |
| **AI** | ![LLM](https://img.shields.io/badge/LLM-Tool%20Calling-412991?style=for-the-badge) |

### 데이터베이스 / 캐시 / 메시징

| 구분 | 기술 |
| --- | --- |
| **RDBMS** | ![MySQL](https://img.shields.io/badge/MySQL-8-4479A1?style=for-the-badge&logo=mysql&logoColor=white) |
| **Cache / Token Store** | ![Redis](https://img.shields.io/badge/Redis-7-DC382D?style=for-the-badge&logo=redis&logoColor=white) |
| **Messaging** | ![Kafka](https://img.shields.io/badge/Kafka-Event%20Driven-231F20?style=for-the-badge&logo=apachekafka&logoColor=white) |

### 인프라 및 배포

| 구분 | 기술 |
| --- | --- |
| **Container** | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![Docker Compose](https://img.shields.io/badge/Docker%20Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white) |
| **Cloud** | ![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white) ![S3](https://img.shields.io/badge/AWS%20S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white) |
| **CI/CD** | ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white) |

### 프론트엔드

| 구분 | 기술 |
| --- | --- |
| **Language** | ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white) |
| **Library** | ![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB) |
| **Build Tool** | ![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=FFD62E) |
| **Routing** | ![React Router](https://img.shields.io/badge/React_Router-CA4245?style=for-the-badge&logo=reactrouter&logoColor=white) |
| **API Communication** | ![Axios](https://img.shields.io/badge/Axios-5A29E4?style=for-the-badge) |
| **Styling** | ![TailwindCSS](https://img.shields.io/badge/TailwindCSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white) |  

### 협업 / 문서화

| 구분 | 기술 |
| --- | --- |
| **Version Control** | ![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white) |
| **API Docs** | ![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black) |
| **Test** | ![JUnit5](https://img.shields.io/badge/JUnit5-25A162?style=for-the-badge&logo=junit5&logoColor=white) ![Mockito](https://img.shields.io/badge/Mockito-000000?style=for-the-badge) |

---

## 시스템 아키텍처

### 전체 구조

```text
[Client]
   ↓ HTTPS
[Spring Boot Application]
   ├─ Auth / Member Domain
   ├─ Pet Domain
   ├─ Sitter Domain
   ├─ Post Domain
   ├─ CareRequest Domain
   ├─ Proposal Domain
   ├─ Reservation Domain
   ├─ AI Domain
   │
   ├─ Redis
   │   ├─ JWT Blacklist
   │   ├─ Refresh Token
   │   ├─ Sitter Search Cache
   │   ├─ Sitter Detail Cache
   │   └─ Post Search Cache
   │
   ├─ Scheduler
   │   └─ Reservation Expire Job
   │
   └─ MySQL
       ├─ Member / Pet
       ├─ SitterProfile / SitterSchedule
       ├─ Post / Proposal
       ├─ CareRequest
       └─ Reservation
```

### 예약 상태 전이

```text
PENDING ── 양측 결제 완료 ──▶ CONFIRMED ── 케어 완료 ──▶ COMPLETED
   │                              │
   │                              └── 취소 ──▶ CANCELED
   │
   ├── 취소 ──▶ CANCELED
   │
   └── 2시간 초과 ──▶ EXPIRED
```

### Reservation 생성 경로

```text
[순방향]
CareRequest ACCEPT
   ↓
Reservation(PENDING)

[역방향]
Proposal ACCEPT
   ↓
Reservation(PENDING)
```

### 캐싱 전략

```text
Sitter List Search
   └─ cache:sitters:{조건해시} / TTL 1시간

Sitter Detail
   └─ cache:sitter:{sitterId} / TTL 1시간

Post List Search
   └─ cache:postings:{조건해시} / TTL 5분

Redis 장애 발생
   └─ DB 직접 조회로 폴백
```

---

## 데이터베이스 설계

### 핵심 엔티티

| 도메인 | 주요 엔티티 |
| --- | --- |
| **회원** | Member |
| **반려동물** | Pet |
| **시터** | SitterProfile, SitterSchedule |
| **순방향 요청** | CareRequest, CareRequestPet, CareRequestTimeSlot |
| **공고** | Post, PostPet, PostTimeSlot |
| **제안** | Proposal |
| **예약** | Reservation, ReservationPet, ReservationTimeSlot |

### 관계 요약

```text
Member (1) ──< (N) Pet
Member (1) ──< (1) SitterProfile
SitterProfile (1) ──< (N) SitterSchedule

Member (1) ──< (N) CareRequest >── (1) SitterProfile
CareRequest (1) ──< (N) CareRequestPet
CareRequest (1) ──< (N) CareRequestTimeSlot

Member (1) ──< (N) Post
Post (1) ──< (N) PostPet
Post (1) ──< (N) PostTimeSlot
Post (1) ──< (N) Proposal >── (1) SitterProfile

Member (1) ──< (N) Reservation >── (1) SitterProfile
Reservation (1) ──< (N) ReservationPet
Reservation (1) ──< (N) ReservationTimeSlot
```

### 데이터 스냅샷 전략

| 스냅샷 | 적용 테이블 | 목적 |
| --- | --- | --- |
| **PetSnapshot** | post_pet, care_request_pet, reservation_pet | 요청·공고·예약 당시 반려동물 정보 보존 |
| **TimeSlotInfo** | post_time_slot, care_request_time_slot, reservation_time_slot | 돌봄 날짜와 시간대 구조 표준화 |

---

## 대표 문서

### 요구사항 및 기획

* [프로젝트 개요서](#) — 서비스 배경, 목적, 핵심 가치 제안 정리
* [정책 문서](#) — 회원, 인증, 시터, 공고, 요청, 제안, 예약 정책 정리
* [API 명세서](#) — 도메인별 API 요청/응답 및 에러 코드 정리

### 설계 및 아키텍처

* [ERD](#) — 핵심 엔티티, 관계, 인덱스 권장사항 정리
* [시스템 아키텍처](#) — 전체 구조, Redis, Scheduler, MySQL 구성 정리
* [캐싱 전략](#) — 시터/공고 조회 캐싱 및 무효화 정책 정리

### 운영 및 확장

* [배포 가이드](#) — Docker, AWS, GitHub Actions 배포 절차
* [테스트 전략](#) — 단위 테스트, 통합 테스트, 시나리오 테스트 정리
* [AI 기능 설계](#) — LLM 구조화 출력, Tool Calling, 장애 격리 전략 정리

---

## 향후 업데이트 계획

### Phase 1 — MVP 안정화

* 핵심 도메인 CRUD 완성
* CareRequest / Proposal / Reservation 플로우 안정화
* 예약 충돌 검증 및 EXPIRED 스케줄러 적용
* Redis 캐싱 및 캐시 무효화 적용
* CI/CD 기반 배포 자동화

### Phase 2 — 서비스 고도화

* Portone 결제 연동 및 Payment 테이블 구현
* 실시간 케어 일지
* WebSocket STOMP 기반 1:1 채팅
* SSE 기반 예약 / 결제 알림
* 후기 및 평점 기능
* 모니터링 도입

### Phase 3 — AI 확장

* AI 시터 프로필 자동 생성
* Tool Calling 기반 AI-백엔드 API 연동
* AI 시터 추천 챗봇
* RAG 기반 후기·프로필 시맨틱 검색
* AI 장애 격리 및 비용 인식 설계

---

## 라이선스 및 문의

Copyright (c) 2026 집사조. All Rights Reserved.

### 팀

* 권지원 — Post / Proposal
* 박영수 — Infra / CI/CD / Concurrency
* 선경안 — QueryDSL / Cache / Performance
* 이지민 — AI / Payment / Frontend
* 최길중 — Auth / Realtime / Concurrency

### 문의

* **GitHub Organization**: 추후 연결
* **Repository**: 추후 연결
* **Docs**: 추후 연결
* **API Docs**: Swagger 연결 예정

---

**작성자:** 집사조
