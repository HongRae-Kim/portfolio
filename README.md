# 김홍래 | Backend Developer

> **부하 테스트와 운영 이슈 분석을 통해 시스템 병목을 측정하고 개선하는 백엔드 개발자**

<br/>

## Projects

### 🎮 MatchMyDuo | 게임 플레이어 듀오/파티 매칭 플랫폼
> **실시간 채팅과 부하 테스트 기반 성능 개선을 수행한 게임 매칭 서비스**

- **기간 / 인원**
  - 2025.12.10 ~ 2026.01.07 / 백엔드 6명

- **담당**
  - WebSocket(STOMP) 기반 1:1 실시간 채팅 구현
  - STOMP CONNECT / SUBSCRIBE 단계 인증·인가 처리
  - Redis unread count 캐시 적용
  - 로그인 / 파티 초대 API 부하 테스트 및 병목 개선

- **핵심 성과**
  - `auth_login` refresh token 저장 구조를 **MySQL → Redis**로 전환해 stress 테스트 실패율 **99% → 0%** 개선
  - `party_add_members`를 **배치 조회 + saveAll() 구조**로 개선해 mixed 부하 기준 **p95 54.50ms → 20.01ms** 개선
  - 이후 realistic_peak 기준 **최신 3회 재측정 모두 p95 40ms 이하** 달성
    - `38.86ms`
    - `35.27ms`
    - `29.75ms`

- **기술적으로 한 일**
  - k6, Prometheus, Grafana 기반 부하 테스트 및 모니터링 환경 구성
  - realistic 시나리오와 write-bank seed/reset 구조를 직접 설계
  - `Party`가 `capacity`, `joinedMemberCount`를 직접 관리하도록 변경해 count query 기반 상태 계산 제거
  - `addMembers()`에서 user 조회를 1회로 통합하고 응답 DTO 생성 시 lazy association 접근 제거

- **성능 개선 결과**
![party_add_members p95 비교](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE/raw/main/load-test/images/party-add-members-p95.svg)

- **기술 스택**
  - Java, Spring Boot, Spring Security, JWT, JPA/Hibernate, MySQL, Redis, WebSocket/STOMP
  - Docker, AWS EC2/S3, k6, Prometheus, Grafana

- **링크**
  - [Team Repo](https://github.com/prgrms-web-devcourse-final-project/WEB7_9_FinalScreening_BE)
  - [My Fork](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE)
  - [Load Test Report](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE/blob/main/load-test/README.md)
  - [Live Service](https://www.matchmyduo.cloud/)
  - [API Docs](https://api.matchmyduo.cloud/swagger-ui/index.html)

---

### 🏠 UniMate | 대학생 생활 기반 룸메이트 매칭 서비스
> **매칭 상태 전이와 조건 필터 구조를 설계해 서비스 흐름의 일관성과 유지보수성을 높인 서비스**

- **기간 / 인원**
  - 2025.10.10 ~ 2025.11.20 / 백엔드 5명

- **담당**
  - 매칭 상태 전이 설계 및 구현
  - 필터링 구조 개선
  - 리뷰 기능 구현

- **핵심 성과**
  - 요청 → 응답 → 확정/거절 흐름의 상태 전이 모델 설계
  - 자동 필터와 사용자 선택 필터를 분리·모듈화해 유지보수성 향상
  - 트랜잭션 경계와 검증 로직을 강화해 상태 일관성 개선

- **기술 스택**
  - Kotlin, Spring Boot, Spring Data JPA, MySQL, Redis, Docker

- **링크**
  - [UniMate Java Repo](https://github.com/prgrms-be-devcourse/NBE7-9-2-Team10)
  - [UniMate Kotlin Repo](https://github.com/HongRae-Kim/NBE7-9-2-Team10)

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
