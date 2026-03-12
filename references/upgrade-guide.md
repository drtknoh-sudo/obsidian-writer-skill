# Obsidian MCP 업그레이드 가이드

## 현재 상태 분석

### 현재 설치된 MCP 서버
**obsidian (local MCP)** - 기본 파일 기반 로컬 서버

제공 기능:
- `list_notes`: 노트 목록 조회 (폴더 필터, limit 옵션)
- `get_note`: 노트 내용 읽기
- `create_note`: 새 노트 생성 (자동 frontmatter)
- `update_note`: 노트 수정 (modified 날짜 자동 업데이트)
- `search_notes`: 제목 기반 검색
- `full_text_search`: 전문 검색
- `list_folders`: 폴더 구조 조회
- `get_tags`: 태그 목록 조회
- `delete_note`: 노트 삭제 (.trash 이동)
- `get_vault_info`: 볼트 통계

### 평가
| 항목 | 점수(5점 만점) | 비고 |
|------|:---:|------|
| 기본 CRUD 기능 | 4.5 | 충분히 안정적 |
| 검색 기능 | 3.0 | 키워드 기반만 지원, 시맨틱 검색 없음 |
| 태그/메타데이터 관리 | 3.0 | 읽기 가능, 자동 분류 없음 |
| 성능 | 4.0 | 로컬 파일시스템 기반으로 빠름 |
| 보안 | 4.5 | 로컬 전용, 외부 API 불필요 |
| 확장성 | 2.5 | 시맨틱 검색, 그래프 탐색, 임베딩 미지원 |

**종합: 3.5/5** — 기본 기능은 안정적이나 AI 활용 극대화를 위한 고급 기능 부재

---

## 시장의 대안 솔루션 비교

### Tier 1: 고급 (시맨틱 검색 + 메모리)

#### Claudesidian MCP (→ Nexus)
- 시맨틱 검색 (sqlite-vec 벡터 검색)
- Agent-Mode 아키텍처
- 메모리 시스템 (대화 이력 관리)
- 멀티 볼트 지원
- **단점**: 실험적 단계, 메모리 기능 불안정

#### obsidian-mcp-tools (jacksteamdev)
- 시맨틱 검색 (의미 기반)
- Templater 통합
- 보안 중시 (직접 파일 접근 차단)
- **단점**: 메인테이너 부재, 개발 중단 위험

### Tier 2: 기능 풍부

#### cyanheads/obsidian-mcp-server
- 포괄적 CRUD + frontmatter 관리
- 인메모리 볼트 캐시
- 정규식 검색/치환
- periodic notes 지원
- **장점**: 가장 완성도 높은 기능 세트

#### obsidian-semantic-mcp (aaronsb)
- 20+ 도구를 5개 시맨틱 작업으로 압축
- 그래프 네비게이션 (링크 따라가기)
- 컨셉 디스커버리
- **장점**: AI 친화적 인터페이스

### Tier 3: 특수 목적

#### bitbonsai/mcp-obsidian
- 14개 메서드, 보안 최우선
- YAML frontmatter 보호
- 경로 순회 방지
- **장점**: 가장 안전한 옵션

#### dbmcco/obsidian-mcp
- 자연어 쿼리
- 백링크 분석
- 스토리 경로 (linked notes 순회)
- 노트 감사(auditing)

---

## 업그레이드 권장 전략

### 추천 1: 현재 MCP 유지 + Claude Skill로 보완 (즉시 적용 가능)

**이유**:
- 현재 MCP의 기본 기능이 안정적
- 시맨틱 검색은 Claude의 추론 능력으로 상당 부분 보완 가능
- 별도 설치/설정 불필요
- 스킬이 다층 검색 전략을 제공하여 기능 격차 해소

**방법**:
이 `obsidian-writer` 스킬을 설치하면 현재 MCP 도구를 최대한 활용하는
지능형 워크플로우가 즉시 적용됨

### 추천 2: cyanheads/obsidian-mcp-server로 교체 (중기)

**이유**:
- 가장 완성도 높은 도구 세트
- frontmatter 전용 관리 기능
- 인메모리 캐시로 성능 향상
- 정규식 검색/치환

**설치 방법**:
1. Obsidian Local REST API 플러그인 설치
2. `npx obsidian-mcp-server` 또는 Docker로 실행
3. Claude Desktop/Cowork 설정에 MCP 서버 추가

### 추천 3: Nexus (Claudesidian 후속) 설치 (장기)

**이유**:
- 시맨틱 검색이 성숙되면 검색 품질 획기적 향상
- 메모리 시스템으로 대화 이력 기반 컨텍스트 유지
- 로컬 임베딩 (Ollama)으로 비용 무료

**주의**: 아직 실험적 단계이므로 안정화 후 적용 권장

---

## 결론

현 시점에서 가장 효율적인 전략은 **추천 1 (현재 MCP + 스킬)을 즉시 적용**하고,
**추천 2를 중기적으로 준비**하는 것이다. 현재 MCP는 기본기가 탄탄하며,
부족한 부분(시맨틱 검색, 자동 분류)은 Claude의 추론 능력 + 스킬 워크플로우로
90% 이상 보완 가능하다.
