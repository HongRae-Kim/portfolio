## 📁 Projects

### 🎮MatchMyDuo | 게임 플레이어 듀오/파티 매칭 플랫폼
> - **기간/인원**: 2025.12.10 ~ 2026.01.07 | 6명 (BE 6)
> - **담당**: 채팅 도메인 담당 — 1:1 실시간 채팅(WebSocket/STOMP) 구현, STOMP 연결/구독 단계 인증·권한 처리, Redis 캐시로 채팅방/메시지 조회 성능 개선
> - **기여**
>   - WebSocket/STOMP 기반 1:1 채팅 파이프라인을 구축해 전송/구독 흐름의 불안정 구간을 해소
>   - CONNECT/SUBSCRIBE 단계 인증·권한 검증을 분리 적용해 비인가 접근을 차단하고 보안 경계를 명확화
>   - Redis `unread count` 캐시를 도입해 채팅방/메시지 목록 조회 병목을 완화하고 읽음 상태 정합성을 유지
>   - 타임존 처리 누락 및 조회 쿼리 오류를 수정하고 테스트를 보강해 운영 리스크를 최소화
> - **기술 스택**: Java, Spring Boot, MySQL, WebSocket(STOMP), Redis(unread cache), Docker, AWS(EC2, S3)
> - Repo: [MatchMyDuo](https://github.com/prgrms-web-devcourse-final-pr성oject/WEB7_9_FinalScreening_BE)

### 🏡 UniMate - 대학생 생활 기반 룸메이트 매칭 서비스 
> - **기간/인원**: 2025.10.10 ~ 2025.11.20 | 5명 (BE 5)
> - **프로젝트 형태**: Java 구현을 Kotlin으로 마이그레이션
> - **담당**: 매칭 상태 전이 설계·구현 / 필터링 모듈화 / 리뷰 기능 구현
> - **기여**
>   - 요청 → 응답 → 확정/거절 → 리뷰로 이어지는 상태 전이 모델을 정의하고, 단계별 검증 규칙을 서비스 전반에 일관되게 적용
>   - 자동 필터와 사용자 선택 필터의 책임을 분리·모듈화해, 조건 확장 시 수정 범위를 필터 모듈로 한정 
>   - 중복 요청·동시성 경합을 방지하기 위해 트랜잭션 경계와 검증 로직을 강화하고 관련 테스트를 보강
> - **기술 스택**: Java, Kotlin, Spring Boot, Spring Data JPA, MySQL, Redis, Docker
> - Repo (Before Migration, Java): [Unimate](https://github.com/prgrms-be-devcourse/NBE7-9-2-Team10)
> - Repo (After Migration, Kotlin): [Unimate - Kotlin](https://github.com/prgrms-be-devcourse/NBE7-9-3-Team10)

---

## 🎓 Education
- 프로그래머스 데브코스 클라우드 기반 백엔드 엔지니어링 (2025.07 ~ 2026.01)
  - 팀 프로젝트 4회 수행, 그 중 2회 팀장 경험
  - 협업 기준 문서화(Notion), 코드 리뷰 운영, CI 환경 자동 테스트 경험
