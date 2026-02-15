## 📁 Projects

### 🎮MatchMyDuo | 게임 플레이어 듀오/파티 매칭 플랫폼
> - **기간/인원**: 2025.12.10 ~ 2026.01.07 | 6명 (BE 6)
> - **담당**: 채팅 도메인 담당 — 1:1 실시간 채팅(WebSocket/STOMP) 구현, STOMP 연결/구독 단계 인증·권한 처리, Redis 캐시로 채팅방/메시지 조회 성능 개선 
> - **기여**
>   - WebSocket/STOMP로 실시간 채팅 파이프라인 구축, 메시지 전송/구독 흐름을 안정화
>   - Redis 캐시 기반 unread count 집계를 도입해 조회 지연을 줄이고 읽음 상태 정합성을 개선
>   - 채팅방 조회 쿼리 오류/타임존 누락 이슈를 해결하고 테스트를 보강해 운영 리스크를 낮춤
> - **기술 스택**: Java, Spring Boot, MySQL, WebSocket(STOMP), Redis(unread cache), Docker, AWS(EC2/S3)
> - Repo: [MatchMyDuo](https://github.com/prgrms-web-devcourse-final-project/WEB7_9_FinalScreening_BE)

### 🏡 UniMate - 대학생 생활 기반 룸메이트 매칭 서비스 
> - **기간/인원**: 2025.10.10 ~ 2025.11.20 | 5명 (BE 5)
> - 프로젝트 형태: 기존 Java 기반 구현 완료 후, Kotlin으로 마이그레이션
> - **담당**: 매칭 상태 전이 설계·구현, 자동/사용자 선택 필터 개발, 리뷰 기능 구현
> - **기여**
>   - 요청 → 응답 → 확정/거절 → 리뷰 상태 전이 모델을 정의하고, 전이별 검증 로직을 서비스 전반에 일괄 적용
>   - 자동 필터와 사용자 선택 필터를 분리·모듈화해 조건 확장 시 변경 영향 범위를 축소
>   - 중복 요청/동시성 경합 방지를 위해 트랜잭션 경계와 검증 로직을 강화하고 테스트를 보강
> - **기술 스택**: Java, Kotlin, Spring Boot, Spring Data JPA, MySQL, Redis, Docker
> - Repo (Before Migration, Java): [Unimate](https://github.com/prgrms-be-devcourse/NBE7-9-2-Team10)
> - Repo (After Migration, Kotlin): [Unimate - Kotlin](https://github.com/prgrms-be-devcourse/NBE7-9-3-Team10)

---

## 🎓 Education
- 프로그래머스 데브코스 클라우드 기반 백엔드 엔지니어링 (2025.07 ~ 2026.01)
  - 팀 프로젝트 4회 수행, 그 중 2회 팀장 경험
  - 협업 기준 문서화(Notion), 코드 리뷰 운영, CI 환경 자동 테스트 경험
