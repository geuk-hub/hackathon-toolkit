# Hackathon Toolkit

제한된 시간의 실무형 AI 코딩 과제에서 **요구사항 파악 → 작동하는 구현 → 오류 수정 → 검증·제출**에 사용하는 한국어 프롬프트와 범용 스킬 모음입니다. 특정 문제의 완성 답안이나 예상 기출을 제공하지 않습니다.

## 가장 빠른 사용법

1. 대회에서 공개 자료 다운로드가 허용되는지 확인합니다. 실제 과제 README·당일 공지가 우선입니다.
2. 공개 저장소를 **읽기 전용 참고자료**로 다운로드합니다. 아래 명령은 저장소가 공개된 뒤 사용합니다. 기존 과제 폴더를 덮어쓰지 않도록 별도 경로를 사용합니다.

```bash
git clone --depth 1 https://github.com/geuk-hub/hackathon-toolkit.git /tmp/hackathon-toolkit
```

`/tmp/hackathon-toolkit`이 이미 있으면 다른 빈 경로를 사용하세요. GitHub 접근이 막히면 우회하지 말고 Cofa Helper에 허용 경로를 확인합니다. 다운로드된 자료는 임시 경로이므로 세션이 초기화되면 사라질 수 있습니다.

3. 제공된 Codex에 다음을 입력합니다. 실제 작업 경로·남은 시간을 채우세요.

```text
과제 작업 폴더: <실제 경로>
남은 구현 시간: <분>
/tmp/hackathon-toolkit/prompts/00-start.md를 읽고 적용해줘.
과제 README와 지시사항을 먼저 확인하고, 요구사항 표를 만든 뒤 핵심 기능 구현과 검증까지 진행해줘.
참고자료 폴더가 아니라 과제 작업 폴더에서 작업해줘.
```

파일 읽기를 못 하면 [시작 프롬프트](prompts/00-start.md)의 코드 블록을 허용된 작업 환경 안에서 직접 사용합니다. 외부 복사·붙여넣기의 허용 여부는 과제 안내를 따르세요. 스킬 자동 설치는 필수가 아닙니다.

## 상황별 선택

| 상황 | 사용할 파일 | 핵심 결과 |
|---|---|---|
| 처음 시작 | [00-start](prompts/00-start.md) | 요구사항·환경 파악, 핵심 구현 착수 |
| 지시사항이 모호함 | [01-triage](prompts/01-triage.md) | 수락 기준, 업무 담당자 질문 |
| 구현 진행 | [02-build](prompts/02-build.md) | 입력부터 출력까지 작동하는 기능 |
| 데이터 처리·분석 | [03-data](prompts/03-data.md) | 데이터 검증, 누수 없는 평가 |
| 오류 발생 | [04-debug](prompts/04-debug.md) | 재현·최소 수정·회귀 확인 |
| 동작 확인 | [05-verify](prompts/05-verify.md) | 요구사항별 검증 근거 |
| 마감 20분 전 | [06-finish](prompts/06-finish.md) | 제출 파일·재실행·한계 점검 |
| 대화가 길어지거나 재시작 | [07-resume](prompts/07-resume.md) | 사실 기반 인수인계·이어가기 |

## 재사용 스킬

스킬은 반복 사용할 작업 절차이고, 프롬프트는 지금 수행할 요청입니다. 한 번에 모든 파일을 읽히지 말고 필요한 것만 사용하세요.

- [hackathon-triage](skills/hackathon-triage/SKILL.md): 요구사항·데이터·시간·우선순위 결정
- [hackathon-build](skills/hackathon-build/SKILL.md): 최소 기능 구현, 계약·오류·경계값 처리
- [hackathon-debug](skills/hackathon-debug/SKILL.md): 증거 기반 오류 진단과 최소 수정
- [hackathon-deliver](skills/hackathon-deliver/SKILL.md): 요구사항 검증·재현 문서·제출 점검

```text
/tmp/hackathon-toolkit/skills/hackathon-debug/SKILL.md를 읽고 적용해줘.
과제 경로는 <경로>, 오류는 <오류>, 재현 명령은 <명령>, 남은 시간은 <분>이야.
```

자동 검색 경로는 응시 환경의 Codex 설정에 따라 다를 수 있으므로 이 저장소는 특정 설치 경로를 강제하지 않습니다. `agents/openai.yaml`은 호환 도구용 메타데이터이며, 파일이 있다는 사실만으로 자동 로딩되지는 않습니다.

## 템플릿과 운영 가이드

- [요구사항 표](templates/REQUIREMENTS.md)
- [결정·검증 기록](templates/WORKLOG.md)
- [제출 README](templates/SUBMISSION_README.md)
- [선택 적용 작업 규칙](templates/AGENTS.md): 기존 AGENTS.md가 있으면 덮어쓰지 말고 필요한 규칙만 병합
- [시간 배분·막힘 대응](docs/PLAYBOOK.md)
- [후속 서술형 사전 연습](docs/REFLECTION_PRACTICE.md)
- [대회 사용 조건](docs/USAGE_BOUNDARIES.md)

모든 문서를 제출할 필요는 없습니다. 실제 과제에서 요구한 파일과 형식만 제출하세요. 템플릿의 빈칸·예시는 실제 구현과 검증 결과로 바꿉니다.

## 품질 원칙

- 실행하지 않은 테스트를 성공했다고 기록하지 않습니다.
- 예시 데이터와 실제 결과를 구분합니다. 하드코딩으로 정상 동작을 가장하지 않습니다.
- 기존 스택·잠금 파일·제출 계약을 우선합니다.
- 중요한 변경에는 작게 실행 가능한 검증을 연결합니다.
- 시험 작업물·비밀·개인 API 키를 이 공개 저장소에 올리지 않습니다.

이 저장소의 자료는 사전 준비용이며, 공식 안내서나 출제 예측 자료가 아닙니다.
