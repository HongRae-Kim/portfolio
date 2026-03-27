# 김홍래 | Backend Developer

> **부하 테스트와 운영 이슈 분석을 통해 시스템 병목을 측정하고 개선하는 백엔드 개발자**

기능 구현에 그치지 않고,  
**실시간 통신, 인증, 캐싱, 데이터 처리 구조에서 발생하는 병목을 직접 확인하고 개선하는 과정**에 집중해왔습니다.  
프로젝트에서는 사용자 기능 구현뿐 아니라 **성능 개선, 운영 환경 검증, 안정적인 서비스 흐름 설계**까지 경험했습니다.

<br/>

## Projects

---

## 🎮 MatchMyDuo | 게임 플레이어 듀오/파티 매칭 플랫폼

> **실시간 채팅, 인증, 캐싱, 부하 테스트 기반 성능 개선을 수행한 게임 듀오/파티 매칭 플랫폼**

### 프로젝트 소개
Riot 전적 정보, 1:1 채팅, 파티 초대를 결합해  
사용자가 **신뢰 기반으로 듀오/파티를 찾을 수 있도록 만든 실시간 매칭 서비스**입니다.

### 핵심 성과
- `party_add_members` API 처리 구조 개선으로 **p95 54.50ms → 20.01ms** 단축
- refresh token 저장 구조를 **MySQL → Redis**로 전환해 **stress 테스트 실패율 99% → 0%** 개선
- **k6, Prometheus, Grafana** 기반 부하 테스트 및 모니터링 환경 구성
- **WebSocket(STOMP)** 기반 채팅에 단계별 인증·인가 검증 적용

### 기간 / 인원
- **2025.12.10 ~ 2026.01.07**
- **백엔드 6명**

### 담당 역할
- WebSocket(STOMP) 기반 1:1 실시간 채팅 구현
- STOMP CONNECT / SUBSCRIBE / SEND 단계별 인증·인가 처리
- Redis 기반 unread count 캐시 적용
- 로그인 및 파티 참여 API 부하 테스트 수행
- 병목 분석 및 성능 개선
- 운영 환경 인증 이슈 해결

### 기술적 문제 해결

#### 1. 로그인 병목 개선
- **문제**: 로그인 요청 집중 시 refresh token 저장 과정에서 DB write 병목 발생
- **해결**: MySQL upsert 방식에서 Redis 저장 방식으로 전환
- **결과**: stress 테스트 실패율 **99% → 0%**

#### 2. 파티 참여 API 성능 개선
- **문제**: `party_add_members` API에서 개별 조회/저장으로 인한 응답 지연 발생
- **해결**: 배치 조회 + `saveAll()` 구조로 변경
- **결과**: p95 응답 시간 **54.50ms → 20.01ms**

#### 3. 실시간 채팅 인증·인가 강화
- **문제**: WebSocket 환경에서 비인가 사용자의 채팅방 접근 가능성 존재
- **해결**: STOMP CONNECT / SUBSCRIBE / SEND 단계별 인증·권한 검증 적용
- **결과**: 채팅 연결, 구독, 메시지 전송 전 과정에서 권한 검증 수행

#### 4. 안 읽은 메시지 수 조회 최적화
- **문제**: 반복 조회 시 unread count 계산 비용 증가 가능성
- **해결**: Redis 캐시 도입 및 읽음 처리 시 캐시 갱신 구조 적용
- **결과**: 채팅 목록 조회 성능 개선 및 읽음 상태 관리 효율 향상

#### 5. 운영 환경 인증 이슈 해결
- **문제**: 배포 환경에서 쿠키 / SameSite / Proxy 설정 차이로 인증 문제 발생
- **해결**: 프록시 및 쿠키 전달 흐름 점검, 인증 설정 수정
- **결과**: 운영 환경 로그인 및 채팅 흐름 안정화

### 부하 테스트 및 모니터링
- **부하 테스트**: k6
- **메트릭 수집**: Prometheus
- **시각화**: Grafana
- **검증 기준**: 평균 응답 시간보다 **p95, 실패율, 처리 안정성** 중심으로 확인

### 기술 스택
**Main Stack**  
Java, Spring Boot, Spring Security, JWT, JPA/Hibernate, MySQL, Redis, WebSocket/STOMP

**Applied Tools**  
Docker, AWS EC2/S3, Nginx, k6, Prometheus, Grafana

**Exposure**  
Terraform, Vercel

#### 성능 개선 결과
![party_add_members p95 비교](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE/raw/main/load-test/images/party-add-members-p95.svg)

> 혼합 부하 테스트에서 병목으로 확인된 `party_add_members` API를  
> 배치 조회 + `saveAll()` 구조로 개선해 p95 응답 시간을 **54.50ms → 20.01ms**로 단축했습니다.

### 링크
- [Team Repo](https://github.com/prgrms-web-devcourse-final-project/WEB7_9_FinalScreening_BE)
- [My Fork](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE)
- [Load Test Report](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE/blob/main/load-test/README.md)

### 회고
이 프로젝트를 통해  
**부하 테스트로 병목을 확인하고, 원인을 분석한 뒤, 구조를 개선하고, 동일 조건에서 다시 검증하는 과정**이  
백엔드 개발에서 중요하다는 점을 배웠습니다.

---

## 🏠 UniMate | 대학생 생활 기반 룸메이트 매칭 서비스

> **매칭 상태 전이와 조건 필터 구조를 설계해 서비스 흐름의 일관성과 유지보수성을 높인 룸메이트 매칭 서비스**

### 프로젝트 소개
대학생의 생활 패턴과 선호 조건을 반영해  
룸메이트를 탐색하고 매칭 상태를 관리할 수 있도록 만든 서비스입니다.

### 기간 / 인원
- **2025.10.10 ~ 2025.11.20**
- **백엔드 5명**

### 프로젝트 특징
- 기존 Java 프로젝트를 **Kotlin으로 마이그레이션**

### 담당 역할
- 매칭 상태 전이 설계 및 구현
- 필터링 구조 개선
- 리뷰 기능 구현

### 기술적 문제 해결

#### 1. 매칭 상태 전이 설계
- **문제**: 요청, 응답, 확정, 거절 흐름에서 상태 관리 기준이 불명확하면 잘못된 상태 변경 가능성 존재
- **해결**: 상태 전이 모델을 정의해 요청 → 응답 → 확정/거절 흐름을 구조화
- **결과**: 매칭 흐름 일관성 확보 및 잘못된 상태 변경 방지

#### 2. 필터링 구조 개선
- **문제**: 필터 조건이 늘어날수록 로직 책임이 한곳에 몰려 유지보수성 저하
- **해결**: 자동 필터와 사용자 선택 필터 책임 분리 및 모듈화
- **결과**: 조건 추가 시 변경 범위 축소, 유지보수성 향상

#### 3. 검증 로직 및 트랜잭션 강화
- **문제**: 중복 요청, 동시성 상황에서 상태 불일치 가능성 존재
- **해결**: 트랜잭션 경계와 검증 로직 강화
- **결과**: 상태 일관성 개선 및 도메인 규칙 신뢰성 향상

### 기술 스택
**Main Stack**  
Kotlin, Spring Boot, Spring Data JPA, MySQL

**Applied Tools**  
Redis, Docker

**Also Used**  
Java

### 링크
- [UniMate Java Repo](https://github.com/prgrms-be-devcourse/NBE7-9-2-Team10)
- [UniMate Kotlin Repo](https://github.com/HongRae-Kim/NBE7-9-2-Team10)

### 회고
이 프로젝트를 통해  
기능 구현만큼 중요한 것은 **상태를 어떻게 정의하고, 예외 상황에서도 일관성을 유지하도록 설계하는가**라는 점을 배웠습니다.

---

## Education

### 프로그래머스 데브코스 | 클라우드 기반 백엔드 엔지니어링
**2025.07 ~ 2026.01**

- 팀 프로젝트 4회 수행, 2회 팀장 경험
- Spring Boot, JPA, Redis, Docker, AWS 기반 서비스 설계 및 구현 경험
- 협업 문서화, 코드 리뷰, 테스트 기반 개발 경험

---

## Contact
- GitHub: [HongRae-Kim](https://github.com/HongRae-Kim)
- Portfolio: [portfolio](https://github.com/HongRae-Kim/portfolio)
