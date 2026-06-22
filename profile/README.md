# 🐾 For-Pets

<p align="center">
  <img width="380" height="270" alt="프로젝트_커버_380x270_화질개선 (1)" src="https://github.com/user-attachments/assets/aabf79f4-24dc-4878-8c69-ad0015914f02" />
</p>

<p align="center">
  반려동물 보호자와 펫시터를 연결하는 돌봄 예약 플랫폼
</p>

<p align="center">
  예약 · 실시간 채팅 · 쿠폰 · 결제 · 알림 · AI 리뷰 요약
</p>

---

<p align="center">
  <img src="https://img.shields.io/badge/Java-21-red?logo=openjdk&logoColor=white">
  <img src="https://img.shields.io/badge/Spring_Boot-3.5.14-6DB33F?logo=springboot&logoColor=white">
  <img src="https://img.shields.io/badge/MySQL-8.4-4479A1?logo=mysql&logoColor=white">
  <img src="https://img.shields.io/badge/Redis-7-DC382D?logo=redis&logoColor=white">
  <img src="https://img.shields.io/badge/Kafka-3.7.0-231F20?logo=apachekafka&logoColor=white">
  <img src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white">
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?logo=githubactions&logoColor=white">
</p>

---

## 📚 목차

- [👀 프로젝트 소개](#-프로젝트-소개)
- [👥 Our Team](#-our-team)
- [🔗 Links](#-links)
- [✨ 프로젝트 기능](#-프로젝트-기능)
- [🛠 적용 기술](#-적용-기술)
- [⚙ Development Environment](#-development-environment)
- [🚨 Trouble Shooting](#-trouble-shooting)
- [🌐 Architecture](#-architecture)
- [📋 ERD Diagram](#-erd-diagram)
- [📝 Technologies & Tools](#-technologies--tools)

---

## 👀 프로젝트 소개

**For-Pets**는 반려동물 보호자와 펫시터를 연결하는 **반려동물 돌봄 예약 플랫폼**입니다.

보호자는 자신의 반려동물을 등록하고 원하는 일정에 맞춰 돌봄을 요청할 수 있습니다.
펫시터는 돌봄 서비스와 스케줄을 관리하고, 예약 요청을 확인하며 보호자와 실시간 채팅으로 소통할 수 있습니다.

단순 예약 기능뿐만 아니라 쿠폰, 결제, 알림, 후기, AI 리뷰 요약 기능까지 포함하여 실제 서비스 흐름에 가깝게 구현했습니다.

<details>
<summary><b>✅ 서비스 미리보기</b></summary>

<br>

추후 이미지 추가 예정

<!-- 이미지가 준비되면 아래 주석을 해제해서 사용하면 됩니다. -->

<!--
<p align="center">
  <img src="docs/images/main_preview.png" width="80%">
</p>
-->

</details>

---

## 👥 Our Team

| 이름 | GitHub | 역할 | 담당 |
| :---: | :---: | :---: | :--- |
| 최길중 | [@giljung8228](https://github.com/giljung8228?tab=repositories) | TL / BE | 인증/인가, 채팅, 쿠폰 |
| 권지원 | [@jiwon-e-e](https://github.com/jiwon-e-e) | BE | 순방향/역방향, 관리자, 예약, 동시성, 모니터링 |
| 박영수 | [@ml5153](https://github.com/ml5153?tab=repositories) | BE / Infra | CI/CD, 배포 |
| 선경안 | [@grown-tree](https://github.com/grown-tree) | BE | 조회, 성능개선, 캐싱, 인덱싱, 리뷰, 모니터링 |
| 이지민 | [@jiiimni](https://github.com/jiiimni) | BE / FE | 결제, AI 기능 |


---

## 🔗 Links

* 👊 [프로젝트 노션 바로가기](https://www.notion.so/teamsparta/35e2dc3ef514805b8349f59a239ded0b)
* 💻 [프론트엔드 GitHub 바로가기](https://github.com/Housekeeper-for-pets/for-pets-frontend)
* 💻 [백엔드 GitHub 바로가기](https://github.com/Housekeeper-for-pets/for-pets-project)

---

# ✨ 프로젝트 기능

## 🔐 인증 / 인가

JWT 기반 인증을 통해 사용자를 식별하고 권한을 검증합니다.

* 회원가입
* 로그인
* Access Token 기반 인증
* 사용자 권한 검증
* 인증 사용자 정보 조회

<details>
<summary><b>✅ 미리보기</b></summary>

<br>

<img width="1080" height="1080" alt="download" src="https://github.com/user-attachments/assets/24c6600e-9de8-4443-8948-ce059e8d727e" />


<!--
<p align="center">
  <img src="docs/images/preview_auth.png" width="80%">
</p>
-->

</details>

---

## 🐶 반려동물 관리

보호자는 자신의 반려동물 정보를 등록하고 관리할 수 있습니다.

* 반려동물 등록
* 반려동물 목록 조회
* 반려동물 상세 조회
* 반려동물 정보 수정
* 반려동물 삭제

<details>
<summary><b>✅ 미리보기</b></summary>

<br>

<img width="1080" height="1080" alt="download (1)" src="https://github.com/user-attachments/assets/e15a1148-67b9-43ad-a9ea-6dbb89d33d9d" />

<!--
<p align="center">
  <img src="docs/images/preview_pet.png" width="80%">
</p>
-->

</details>

---

## 🐕 펫시터 / 돌봄 서비스

펫시터는 자신의 프로필, 돌봄 서비스, 스케줄을 관리할 수 있습니다.

* 펫시터 프로필 등록
* 돌봄 서비스 등록
* 스케줄 관리
* 돌봄 요청 조회
* 돌봄 제안 관리

<details>
<summary><b>✅ 미리보기</b></summary>

<br>

추후 이미지 추가 예정

<!--
<p align="center">
  <img src="docs/images/preview_sitter.png" width="80%">
</p>
-->

</details>

---

## 📅 예약 기능

보호자는 원하는 일정에 맞춰 돌봄 예약을 요청할 수 있습니다.

* 돌봄 요청 생성
* 제안 수락
* 예약 생성
* 예약 상태 변경
* 예약 취소
* 예약 당시 반려동물 정보 Snapshot 저장

<details>
<summary><b>✅ 미리보기</b></summary>

<br>

추후 이미지 추가 예정

<!--
<p align="center">
  <img src="docs/images/preview_reservation.png" width="80%">
</p>
-->

</details>

---

## 💬 실시간 채팅

보호자와 펫시터가 예약 전후로 실시간 소통할 수 있습니다.

* 채팅방 생성
* 채팅방 목록 조회
* 채팅방 나가기
* 실시간 메시지 전송
* 메시지 저장 및 조회
* JWT 기반 WebSocket 인증

<details>
<summary><b>✅ 미리보기</b></summary>

<br>

추후 이미지 추가 예정

<!--
<p align="center">
  <img src="docs/images/preview_chat.png" width="80%">
</p>
-->

</details>

---

## 🎫 쿠폰 기능

선착순 쿠폰 발급 상황에서 쿠폰 수량이 초과 발급되지 않도록 동시성 제어를 적용했습니다.

* 쿠폰 생성
* 쿠폰 발급
* 쿠폰 사용
* 쿠폰 수량 관리
* Redis 분산락 기반 동시성 제어

<details>
<summary><b>✅ 미리보기</b></summary>

<br>

추후 이미지 추가 예정

<!--
<p align="center">
  <img src="docs/images/preview_coupon.png" width="80%">
</p>
-->

</details>

---

## 💳 결제 기능

예약과 연결된 결제 흐름을 처리합니다.

* 결제 요청
* 결제 승인
* 결제 상태 관리
* 결제 취소
* PortOne 연동

<details>
<summary><b>✅ 미리보기</b></summary>

<br>

추후 이미지 추가 예정

<!--
<p align="center">
  <img src="docs/images/preview_payment.png" width="80%">
</p>
-->

</details>

---

## 🔔 알림 기능

예약, 채팅, 쿠폰 등 사용자에게 필요한 이벤트를 알림으로 제공합니다.

* 예약 상태 변경 알림
* 채팅 알림
* 쿠폰 알림
* Kafka 기반 알림 이벤트 처리

<details>
<summary><b>✅ 미리보기</b></summary>

<br>

추후 이미지 추가 예정

<!--
<p align="center">
  <img src="docs/images/preview_notification.png" width="80%">
</p>
-->

</details>

---

## 🤖 AI 기능

리뷰 데이터를 기반으로 펫시터 정보를 더 쉽게 확인할 수 있도록 AI 기능을 적용했습니다.

* 리뷰 요약
* AI 채팅
* RAG 기반 검색
* Qdrant 벡터 저장소 활용
* Gemini API 연동

<details>
<summary><b>✅ 미리보기</b></summary>

<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/724af58f-0b66-45b6-b235-5031549040bd" width="80%" alt="AI 기능 미리보기" />
</p>

</details>

---

# 🛠 적용 기술

## ◻ QueryDSL

정렬, 검색 조건에 따른 동적 쿼리 작성을 위해 QueryDSL을 도입했습니다.

펫시터 목록 조회, 예약 조회 등 조건이 동적으로 바뀌는 API에서 활용했습니다.

---

## ◻ Redis

쿠폰 발급 동시성 제어와 캐시 처리를 위해 Redis를 사용했습니다.

선착순 쿠폰 발급 상황에서 동시에 많은 요청이 들어와도 쿠폰 수량보다 많이 발급되지 않도록 Redis 기반 분산락을 적용했습니다.

---

## ◻ Redisson

쿠폰 발급 요청을 쿠폰 ID 단위로 제어하기 위해 Redisson 분산락을 적용했습니다.

DB에 접근하기 전에 Redis에서 락을 획득하도록 하여 쿠폰 초과 발급을 방지했습니다.

---

## ◻ WebSocket

보호자와 펫시터 간 실시간 채팅을 위해 WebSocket을 적용했습니다.

HTTP 요청/응답 방식이 아니라 연결을 유지한 상태에서 메시지를 주고받을 수 있도록 구현했습니다.

---

## ◻ Kafka

예약, 채팅, 쿠폰 등 여러 도메인에서 발생하는 이벤트를 알림 기능과 분리하기 위해 Kafka 기반 이벤트 구조를 적용했습니다.

---

## ◻ GitHub Actions

빌드, 테스트, Docker 이미지 생성, 배포 과정을 자동화하기 위해 GitHub Actions를 사용했습니다.

---

## ◻ Nginx

운영 환경에서 애플리케이션 요청을 분산하고 Blue/Green 형태의 멀티 인스턴스 구성을 위해 Nginx를 사용했습니다.

---

## ◻ Prometheus & Grafana

애플리케이션 상태와 쿠폰 발급 지표를 확인하기 위해 Prometheus와 Grafana를 사용했습니다.

응답 시간, 에러율, DB 커넥션 상태 등을 확인할 수 있도록 구성했습니다.

---

# ⚙ Development Environment

## 🧩 Backend

```text
Java 21
Spring Boot 3.5.14
Spring Data JPA
Spring Security
QueryDSL 5.1.0
JWT 0.12.6
MySQL 8.4
Redis 7
Redisson 3.27.2
Kafka 3.7.0
WebSocket
Qdrant 1.9.7
```

## 🚀 Infra / DevOps

```text
Docker
Docker Compose
Nginx
GitHub Actions
AWS EC2
AWS ECR
Prometheus
Grafana
k6
```

---

# 🚨 Trouble Shooting

## ◻ BE
### 최길중
- 🔐 [인증/WebSocket 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/giljung/auth-websocket-issues.md)  
  만료 토큰 로그아웃 처리 및 WebSocket 인증 로직 개선

- 💬 [채팅 동시성 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/giljung/chat-concurrent-issues.md)  
  마지막 메시지 갱신 문제와 채팅방 중복 생성 문제 해결

- ⚡ [채팅 쿼리 최적화 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/giljung/chat-query-optimization.md)  
  채팅방 목록 조회 N+1 문제와 메모리 페이징 개선
---
### 권지원

- 💳 [PG 부분환불 불가 문제](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/jiwon/payment-partial-cancel-issue.md)  
  PG 부분취소 정책 제한을 우회한 내부 정산 분리 처리

- 🔒 [Lock과 Transaction의 Race Condition](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/jiwon/race-condition-issue.md)  
  Lock이 Transaction을 감싸야 하는 이유와 다계층 방어 전략

- 🔗 [Spring AOP 체이닝 바인딩 버그](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/jiwon/aop-chaining-binding-issue.md)  
  Advice 2개 체이닝 시 JoinPointMatch 누락 → Reflection으로 해결

- 🕐 [멀티 인스턴스 스케줄러 중복 실행 방지](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/jiwon/multi-instance-shedlock.md)  
  ShedLock 도입으로 스케줄러 단일 실행 보장 및 2계층 락 구조 설계

---
### 박영수
- 🔔 [Redis Streams Consumer Group 메시지 미소비 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/youngsue/notification/notification-01-redis-stream-consumer-group-offset.md)  
  Redis Stream에는 알림 메시지가 쌓였지만 Consumer Group offset 설정 문제로 DB 저장과 SSE 전송이 이어지지 않던 문제 해결

- 📡 [멀티 인스턴스 SSE 알림 누락 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/youngsue/notification/notification-02-multi-instance-sse-pubsub-fanout.md)  
  단일 EC2 내부 멀티 인스턴스 환경에서 SSE 연결이 인스턴스별 메모리에 분리되어 실시간 알림이 누락되던 문제를 Redis Pub/Sub fan-out 구조로 해결

- 📊 [Prometheus Target 환경 분리 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/youngsue/monitoring/monitoring-01-prometheus-target-env-split.md)  
  로컬 싱글, 로컬 멀티, 운영 멀티 환경의 컨테이너 이름과 네트워크 기준이 달라 Prometheus scrape가 실패하던 문제를 환경별 설정 분리로 해결

- 🚀 [단일 EC2 내부 멀티 인스턴스 운영 전환 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/youngsue/infra/infra-01-single-ec2-multi-instance-compose.md)  
  `docker run` 기반 배포가 복잡해지면서 운영 컨테이너 구성이 CI 스크립트에 섞이던 문제를 `docker-compose.prod.yml`과 Nginx upstream 구조로 개선

- 🐳 [EC2 Docker Compose 플러그인 누락 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/youngsue/infra/infra-02-docker-compose-plugin-missing.md)  
  EC2에 Docker Engine은 설치되어 있었지만 Compose v2 플러그인이 없어 운영 배포가 실패하던 문제를 CI 배포 스크립트의 사전 점검 및 자동 설치로 해결

---
### 선경안
- 💬 [캐시 hit/miss 적중률 측정 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/kyeongan/monitoring/monitor-01-cache-hit-miss-instrumentation.md)  
  @Cacheable 프록시 구조 한계를 MeteredCacheManager로 해결
  
- 🎯 [운영 데이터 분포(skew) 반영 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/kyeongan/performance/perf-04-realistic-data-distribution.md)  
  CLOSED 누적 분포로 데이터를 반영하니 인덱스 설계가 통째로 뒤집힘
  
- 🛡 [Graceful Degradation 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/kyeongan/cache/cache-01-graceful-degradation.md)  
  Redis가 죽어도 DB 폴백으로 서비스는 멈추지 않게 처리
  
---
### 이지민
- 🤖 [AI 리뷰 요약 프롬프트 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/jimin/ai/ai-01-review-summary-prompt-template-missing.md)  
  배포 환경에서 활성화된 프롬프트 템플릿이 없어 AI 리뷰 요약 생성이 실패한 문제 해결

- 🧩 [Qdrant 배포 설정 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/jimin/ai/ai-02-rag-qdrant-prod-config.md)  
  배포 환경에서 Qdrant base url 설정 누락으로 RAG 검색이 실패한 문제 해결

- 🔎 [RAG 관리자 인덱싱 트러블슈팅](https://github.com/Housekeeper-for-pets/docs/blob/main/troubleshooting/jimin/ai/ai-03-rag-admin-indexing-permission-and-failure.md)  
  관리자 전용 RAG 인덱싱 버튼의 권한 처리와 부분 실패 카운트 표시 개선

---

# 🌐 Architecture

### V1(MVP)
<img width="1382" height="818" alt="image" src="https://github.com/user-attachments/assets/3268b7b6-7ed9-47e4-a711-2e7853a89524" />

### V2
<img width="1657" height="1022" alt="image" src="https://github.com/user-attachments/assets/809a302c-d5d7-488c-bcbe-e5dfad53238b" />


---

# 📋 ERD Diagram
### V1(MVP)
<img width="3741" height="1733" alt="image" src="https://github.com/user-attachments/assets/2250aef5-1641-437a-aaaf-c917c39ef011" />

### V2
<img width="4720" height="2774" alt="image" src="https://github.com/user-attachments/assets/cb74458c-a584-4af4-a84c-e3084bcf0281" />


---

# 📝 Technologies & Tools

|       Category       | Stack                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| :------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|      🧩 Backend      | <img src="https://img.shields.io/badge/Java-21-red?logo=openjdk&logoColor=white"> <img src="https://img.shields.io/badge/Spring_Boot-3.5.14-6DB33F?logo=springboot&logoColor=white"> <img src="https://img.shields.io/badge/Spring_Web-6DB33F?logo=spring&logoColor=white"> <img src="https://img.shields.io/badge/Spring_Data_JPA-6DB33F?logo=spring&logoColor=white"> <img src="https://img.shields.io/badge/Spring_Security-6DB33F?logo=springsecurity&logoColor=white"> <img src="https://img.shields.io/badge/QueryDSL-0769AD"> <img src="https://img.shields.io/badge/JWT-000000?logo=jsonwebtokens&logoColor=white"> <img src="https://img.shields.io/badge/Lombok-BC4521"> |
|      🗄 Database     | <img src="https://img.shields.io/badge/MySQL-8.4-4479A1?logo=mysql&logoColor=white"> <img src="https://img.shields.io/badge/H2-1021FF">                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|    ⚡ Cache / Lock    | <img src="https://img.shields.io/badge/Redis-7-DC382D?logo=redis&logoColor=white"> <img src="https://img.shields.io/badge/Redisson-3.27.2-DC382D">                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|     📩 Messaging     | <img src="https://img.shields.io/badge/Kafka-3.7.0-231F20?logo=apachekafka&logoColor=white">                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|     💬 Real-time     | <img src="https://img.shields.io/badge/WebSocket-010101"> <img src="https://img.shields.io/badge/STOMP-6A1B9A">                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|         🤖 AI        | <img src="https://img.shields.io/badge/Spring_AI-6DB33F"> <img src="https://img.shields.io/badge/Gemini_API-4285F4?logo=google&logoColor=white"> <img src="https://img.shields.io/badge/Qdrant-1.9.7-DC244C">                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|   🚀 Infra / DevOps  | <img src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white"> <img src="https://img.shields.io/badge/Docker_Compose-2496ED?logo=docker&logoColor=white"> <img src="https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white"> <img src="https://img.shields.io/badge/AWS_EC2-FF9900?logo=amazonec2&logoColor=white"> <img src="https://img.shields.io/badge/AWS_ECR-FF9900?logo=amazonaws&logoColor=white"> <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?logo=githubactions&logoColor=white">                                                                                                                                     |
| 📊 Test / Monitoring | <img src="https://img.shields.io/badge/JUnit_5-25A162?logo=junit5&logoColor=white"> <img src="https://img.shields.io/badge/k6-7D64FF?logo=k6&logoColor=white"> <img src="https://img.shields.io/badge/Prometheus-E6522C?logo=prometheus&logoColor=white"> <img src="https://img.shields.io/badge/Grafana-F46800?logo=grafana&logoColor=white"> <img src="https://img.shields.io/badge/Actuator-6DB33F"> <img src="https://img.shields.io/badge/Micrometer-1F8ACB">                                                                                                                                                                                                                 |
|   🛠 Collaboration   | <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white"> <img src="https://img.shields.io/badge/Notion-000000?logo=notion&logoColor=white"> <img src="https://img.shields.io/badge/IntelliJ_IDEA-000000?logo=intellijidea&logoColor=white"> <img src="https://img.shields.io/badge/Postman-FF6C37?logo=postman&logoColor=white">                                                                                                                                                                                                                                                                                                                         |


