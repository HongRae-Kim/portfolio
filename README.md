# 김홍래 | Backend Developer

## Projects

---

## MatchMyDuo | 게임 플레이어 듀오/파티 매칭 플랫폼
> 모집 상태 동기화, 전적 기반 정보 제공, 1:1 채팅을 통해 게임 유저의 듀오/파티 매칭을 지원하는 서비스

**기간 / 인원**  
2025.12.10 ~ 2026.01.07 / 백엔드 6명

**내 역할**  
- 채팅 도메인 설계 및 구현
- 로그인 / 파티 초대 API 성능 개선
- 부하 테스트 및 모니터링 환경 구성

**주요 기여**  
- WebSocket(STOMP) 기반 1:1 실시간 채팅 기능 구현
- 채팅방 생성, 메시지 송수신, 읽음 상태 처리 로직 구현
- Redis 기반 unread count 캐시 구조 적용
- refresh token 저장 경로를 MySQL에서 Redis로 전환
- `party_add_members` API를 배치 조회 + `saveAll()` 구조로 개선
- k6, Prometheus, Grafana 기반 부하 테스트 및 재측정 환경 구성
- 성능 개선 이후 `Party` write 경로에 동시성 제어 보강

**핵심 성과**  
- refresh token write latency: `2~5ms -> 0.003~0.016ms`
- `party_add_members` p95: `54.50ms -> 24.44ms`
- 혼합 스트레스 테스트 기준: `141.02 req/s`, 전체 `p95 14.61ms`, 실패율 `0%`

**아키텍처**  
- 프론트엔드와 인프라는 분리되어 있지만, 백엔드는 단일 Spring Boot 애플리케이션 기반의 모놀리식 구조로 운영

**기술 스택**  
Java, Spring Boot, Spring Security, JWT, JPA/Hibernate, MySQL, Redis, WebSocket/STOMP, Docker, AWS EC2/S3, k6, Prometheus, Grafana

**링크**  
- [Team Repo](https://github.com/prgrms-web-devcourse-final-project/WEB7_9_FinalScreening_BE)
- [My Fork](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE)
- [Load Test Report](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE/blob/main/load-test/README.md)
- [Live Service](https://www.matchmyduo.cloud/)
- [API Docs](https://api.matchmyduo.cloud/swagger-ui/index.html)

---

## UniMate | 대학생 생활 기반 룸메이트 매칭 서비스
> 대학생의 생활 패턴과 선호 조건을 반영해 룸메이트를 매칭하는 서비스

**기간 / 인원**  
2025.10.10 ~ 2025.11.20 / 백엔드 5명

**내 역할**  
- 매칭 상태 전이 설계 및 구현
- 필터링 구조 개선
- 리뷰 기능 구현

**주요 기여**  
- 요청, 응답, 수락, 거절 흐름을 반영한 매칭 상태 전이 로직 설계 및 구현
- 허용 가능한 상태만 진행되도록 검증 로직 구성
- 자동 필터와 사용자 선택 필터를 분리해 조건 조합 구조 개선
- 필터 책임이 서비스 로직 전반에 흩어지지 않도록 구조 정리
- 리뷰 등록 및 조회 기능 구현

**구조적 성과**  
- 매칭 상태를 `NONE`, `LIKE`, `REQUEST`, `ACCEPTED`, `REJECTED`로 구분해 흐름을 명확하게 관리
- 자동 필터와 선택 필터를 분리해 조건 확장과 유지보수가 쉬운 구조로 개선
- 매칭과 리뷰 기능을 연결해 사용자 신뢰 판단에 필요한 흐름 구현

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
- Spring Boot, JPA, Redis, Docker, AWS 기반 서비스 설계 및 구현 경험
- 협업 문서화, 코드 리뷰, 테스트 기반 개발 경험

---

## Contact
- GitHub: [HongRae-Kim](https://github.com/HongRae-Kim)
- Portfolio: [portfolio](https://github.com/HongRae-Kim/portfolio)
