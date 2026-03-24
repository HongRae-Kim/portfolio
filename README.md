## 📁 Projects

### 🎮 MatchMyDuo | 게임 플레이어 듀오/파티 매칭 플랫폼
- **한 줄 소개**: Riot 전적 정보, 1:1 채팅, 파티 초대를 결합해 신뢰 기반으로 파티를 찾을 수 있게 만든 실시간 매칭 서비스
- **기간 / 인원**: 2025.12.10 ~ 2026.01.07 | 6명 (BE 6)
  - 팀 프로젝트 종료 후 개인 fork 환경에서 부하테스트 기반 병목 개선과 배포 환경 작업을 이어서 진행했습니다.
- **팀 프로젝트 담당**
  - 1:1 실시간 채팅(WebSocket/STOMP) 구현
  - STOMP CONNECT / SUBSCRIBE 단계 인증·권한 처리
  - Redis unread count 캐시를 적용해 채팅방/메시지 조회 성능 개선
- **개인 후속 개선**
  - `auth_login`에서 refresh token 저장소를 DB upsert 방식에서 Redis로 전환해 불필요한 DB write 병목 제거
  - `party_add_members`를 개별 조회/저장에서 배치 조회 + `saveAll()` 구조로 변경해 mixed 부하 기준 `p95 54.50ms → 20.01ms` 개선
  - k6, Prometheus, Grafana 기반 부하테스트를 구성하고 개선 전/후를 동일 조건으로 재측정
  - 배포 환경에서 쿠키 도메인, SameSite, Proxy JWT 처리 문제를 해결해 실제 로그인/채팅 흐름을 안정화
- **기술 스택**: Java, Spring Boot, MySQL, Redis, WebSocket(STOMP), Docker, AWS(EC2, S3), Vercel, k6, Prometheus, Grafana, Terraform
- **링크**
  - Team Repo: [MatchMyDuo Project](https://github.com/prgrms-web-devcourse-final-project/WEB7_9_FinalScreening_BE)
  - Fork Repo: [My Fork](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE)
  - Load Test Report: [부하테스트 및 병목 개선 보고서](https://github.com/HongRae-Kim/WEB7_9_FinalScreening_BE/blob/main/load-test/README.md)
  - Live: [서비스 바로가기](https://www.matchmyduo.cloud)
  - Demo Video: [시연 영상](https://www.youtube.com/watch?v=n2shYvIcOKE)

![MatchMyDuo Load Test Comparison](https://raw.githubusercontent.com/HongRae-Kim/WEB7_9_FinalScreening_BE/main/load-test/images/mixed-endpoint-p95-run6-vs-run8.svg)

> k6 기반 부하테스트로 병목을 식별하고, `party_add_members p95`를 `54.50ms → 20.01ms`로 개선했습니다.  
> `auth_login`은 refresh token 저장소를 Redis로 전환해 불필요한 DB write 병목을 제거하고, 스트레스 테스트 실패율을 `99% → 0%`로 낮췄습니다.

---

### 🏡 UniMate | 대학생 생활 기반 룸메이트 매칭 서비스
- **한 줄 소개**: 대학생 생활 패턴과 선호 조건을 반영해 룸메이트를 탐색하고 매칭 상태를 관리할 수 있도록 만든 서비스
- **기간 / 인원**: 2025.10.10 ~ 2025.11.20 | 5명 (BE 5)
- **프로젝트 형태**: Java 구현을 Kotlin으로 마이그레이션
- **담당**
  - 매칭 상태 전이 설계 및 구현
  - 필터링 모듈화
  - 리뷰 기능 구현
- **문제 해결**
  - 요청 → 응답 → 확정/거절 → 리뷰로 이어지는 상태 전이 모델을 정의해, 잘못된 상태 변경과 중복 요청이 서비스 전반에 퍼지지 않도록 설계했습니다.
  - 자동 필터와 사용자 선택 필터의 책임을 분리·모듈화해, 조건이 추가되더라도 필터 모듈만 수정하면 되도록 구조를 단순화했습니다.
  - 중복 요청과 동시성 경합을 줄이기 위해 트랜잭션 경계와 검증 로직을 강화하고 관련 테스트를 보강했습니다.
- **기술 스택**: Java, Kotlin, Spring Boot, Spring Data JPA, MySQL, Redis, Docker
- **링크**
  - Repo (Java): [UniMate](https://github.com/prgrms-be-devcourse/NBE7-9-2-Team10)
  - Repo (Kotlin): [UniMate - Kotlin](https://github.com/prgrms-be-devcourse/NBE7-9-3-Team10)

---

## 🎓 Education
- **프로그래머스 데브코스 클라우드 기반 백엔드 엔지니어링** (2025.07 ~ 2026.01)
  - 팀 프로젝트 4회 수행, 2회 팀장 경험
  - Spring Boot, JPA, Redis, Docker, AWS 기반 서비스 설계 및 구현 경험
  - 협업 기준 문서화, 코드 리뷰 운영, CI 기반 자동 테스트 경험
