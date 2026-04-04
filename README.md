# 김홍래 | Backend Developer

> **부하 테스트와 운영 이슈 분석을 통해 시스템 병목을 측정하고 개선하는 백엔드 개발자**

<br/>

## Projects

---

## 🎮 MatchMyDuo | 게임 플레이어 듀오/파티 매칭 플랫폼
> 게임 이용자의 듀오/파티 매칭과 실시간 소통을 지원하는 서비스

**기간 / 인원**  
2025.12.10 ~ 2026.01.07 / 백엔드 6명

**역할**  
- 채팅 도메인 설계 및 구현
- 로그인 / 파티 초대 API 성능 개선
- 부하 테스트 및 모니터링 환경 구성

**구현 및 책임 범위**  
- WebSocket(STOMP) 기반 **1:1 실시간 채팅 기능 설계 및 구현**
- 채팅방 생성, 메시지 송수신, 읽음 상태 처리 로직 작성
- **Redis 기반 unread count 캐시 구조 적용**
- refresh token 저장 경로를 분석하고 **MySQL → Redis**로 재구성
- 파티 초대 API를 **배치 조회 + `saveAll()` 구조**로 리팩토링
- k6, Prometheus, Grafana 기반 **부하 테스트 / 재측정 환경 구성**
- realistic 시나리오와 write-bank seed/reset 흐름 설계

**문제 상황 및 기술적 판단**  
- 로그인 시 refresh token을 MySQL에 저장하면서 write latency가 발생
- 토큰 저장은 관계형 조회보다 빠른 저장/갱신이 중요하다고 판단해 **Redis**로 전환
- `party_add_members` API는 유저별 반복 조회/저장으로 mixed 테스트에서 p95 지연 발생
- 캐시 적용보다 **write-path의 DB 접근 횟수 축소가 우선**이라고 판단
- 배치 조회와 `saveAll()` 적용 후, `Party`가 `capacity`, `joinedMemberCount`를 직접 관리하도록 구조를 조정해 조회 흐름 단순화

**수치 기반 결과**  
- refresh token write latency: **2~5ms → 0.003~0.016ms**
- `party_add_members` legacy mixed p95: **54.50ms → 24.44ms**
- realistic peak 기준 최신 3회 재측정 모두 **p95 40ms 이하**
  - 35.76ms
  - 36.64ms
  - 29.95ms
- 최신 3회 재측정에서 **성공 표본 104건, 실패율 0%** 유지

**기술 스택**  
Java, Spring Boot, Spring Security, JWT, JPA/Hibernate, MySQL, Redis, WebSocket/STOMP, Docker, AWS EC2/S3, k6, Prometheus, Grafana

**링크**  
- [Team Repo](https://github.com/prgrms-web-devcourse-final-project/WEB7_9_FinalScreening_BE)
- [My Fork](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE)
- [Load Test Report](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE/blob/main/load-test/README.md)
- [Live Service](https://www.matchmyduo.cloud/)
- [API Docs](https://api.matchmyduo.cloud/swagger-ui/index.html)

---

## 🏠 UniMate | 대학생 생활 기반 룸메이트 매칭 서비스
> 대학생의 생활 패턴과 선호 조건을 반영해 룸메이트를 매칭하는 서비스

**기간 / 인원**  
2025.10.10 ~ 2025.11.20 / 백엔드 5명

**역할**  
- 매칭 상태 전이 설계 및 구현
- 필터링 구조 개선
- 리뷰 기능 구현

**구현 및 책임 범위**  
- 요청 / 응답 / 확정 / 거절 흐름을 반영한 **매칭 상태 전이 로직 설계 및 구현**
- 허용 가능한 상태만 통과하도록 검증 로직 작성
- 자동 필터와 사용자 선택 필터를 분리해 **조건 조합 구조 재설계**
- 필터 책임이 서비스 로직 곳곳에 분산되지 않도록 구조 정리
- 리뷰 등록 / 조회 기능 구현
- 매칭 확정 이후 채팅 연결 조건 분리

**문제 상황 및 기술적 판단**  
- 매칭 요청, 수락/거절, 확정 이후 기능이 한 흐름에 섞이면 상태 전이 검증과 예외 처리가 복잡해지는 문제가 있었음
- 단순 조건문 추가 방식은 기능 확장 시 분기 복잡도가 계속 커진다고 판단
- 매칭 흐름을 상태 중심으로 분리하고, 각 상태에서 가능한 동작을 검증하는 구조 적용
- 자동 필터와 선택 필터가 섞여 있어 조건 추가 시 수정 범위가 커지는 문제를 확인
- 조건 누적 방식보다 **필터 책임 분리 구조가 확장에 유리**하다고 판단해 필터 축을 분리

**수치 기반 결과**  
- 매칭 상태를 **5단계(`NONE`, `LIKE`, `REQUEST`, `ACCEPTED`, `REJECTED`)**로 구분
- 자동 필터 / 선택 필터를 **2개 축으로 분리**
- 매칭 상태 전이, 필터링, 리뷰 기능 범위를 담당하며 핵심 도메인 흐름 구현

**기술 스택**  
Kotlin, Spring Boot, Spring Data JPA, MySQL, Redis, Docker

**링크**  
- [UniMate Java Repo](https://github.com/prgrms-be-devcourse/NBE7-9-2-Team10)
- [UniMate Kotlin Repo](https://github.com/HongRae-Kim/NBE7-9-2-Team10)

---

## Education

### 프로그래머스 데브코스 | 클라우드 기반 백엔드 엔지니어링
**2025.07 ~ 2026.01**

- 팀 프로젝트 4회 수행
- 2회 팀장 경험
- Spring Boot, JPA, Redis, Docker, AWS 기반 서비스 설계 및 구현
- 협업 문서화, 코드 리뷰, 테스트 기반 개발 경험

---

## Contact
- GitHub: [HongRae-Kim](https://github.com/HongRae-Kim)
- Portfolio: [portfolio](https://github.com/HongRae-Kim/portfolio)
