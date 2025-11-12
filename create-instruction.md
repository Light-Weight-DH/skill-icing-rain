# Create Project Instruction

당신은 프로젝트 instruction 파일을 생성하는 전문가입니다.

사용자가 새 프로젝트를 시작할 때, 표준화된 instruction 템플릿 파일들을 자동으로 생성하여 프로젝트 문서화를 돕습니다.

---

## Instructions

### 1. 프로젝트 타입 확인

먼저 사용자에게 다음 중 프로젝트 타입을 선택하도록 요청하세요:

- **web-app**: 웹 애플리케이션 (Frontend + Backend)
- **cli**: CLI 도구 또는 스크립트
- **api**: API 서버만
- **library**: 라이브러리 또는 패키지

타입을 명시하지 않았다면 사용자에게 물어보세요.

---

### 2. 현재 날짜 확인

프로젝트 생성일을 기록하기 위해 현재 날짜(YYYY-MM-DD 형식)를 확인하세요.

---

### 3. 폴더 구조 생성

`project-instructions/` 폴더와 하위 구조를 생성하세요:

```
project-instructions/
├── 00_PROJECT.md
├── 01_ARCHITECTURE.md
├── 02_FEATURES.md
├── 03_IMPLEMENTATION.md
├── 04_UI_UX.md          (web-app 타입만)
├── CHANGELOG.md
├── TROUBLESHOOTING.md    (선택사항)
└── assets/
    ├── images/
    ├── data/
    └── code/
```

**중요:**
- `04_UI_UX.md`는 **web-app 타입일 때만** 생성
- `TROUBLESHOOTING.md`는 선택사항이지만 권장
- `assets/` 폴더는 항상 생성 (하위 폴더 포함)

---

### 4. 템플릿 파일 복사

`instruction-template-skill/templates/` 폴더의 템플릿 파일들을 읽어서 `project-instructions/` 폴더에 복사하세요.

각 파일을 Read 도구로 읽은 후, Write 도구로 `project-instructions/` 폴더에 동일한 내용으로 생성합니다.

**복사할 파일 목록:**
- templates/00_PROJECT.md → project-instructions/00_PROJECT.md
- templates/01_ARCHITECTURE.md → project-instructions/01_ARCHITECTURE.md
- templates/02_FEATURES.md → project-instructions/02_FEATURES.md
- templates/03_IMPLEMENTATION.md → project-instructions/03_IMPLEMENTATION.md
- templates/04_UI_UX.md → project-instructions/04_UI_UX.md (web-app만)
- templates/CHANGELOG.md → project-instructions/CHANGELOG.md
- templates/TROUBLESHOOTING.md → project-instructions/TROUBLESHOOTING.md
- templates/modification.md → project-instructions/modification.md

---

### 5. 메타데이터 업데이트

`project-instructions/00_PROJECT.md` 파일의 YAML 프론트매터를 수정하세요:

```yaml
---
project:
  name: ""
  type: "[사용자가 선택한 타입]"    # web-app | cli | api | library
  status: "planning"
  priority: "high"

tech_stack:
  frontend: []
  backend: []
  database: []
  ai: []
  other: []

timeline:
  created: "[현재 날짜 YYYY-MM-DD]"
  updated: "[현재 날짜 YYYY-MM-DD]"
  version: "0.1.0"
---
```

**중요:**
- `type`은 사용자가 선택한 프로젝트 타입으로 설정
- `created`와 `updated`는 현재 날짜로 설정
- 나머지는 템플릿 그대로 유지

---

### 6. CHANGELOG.md 업데이트

`project-instructions/CHANGELOG.md`의 첫 번째 버전 섹션을 현재 날짜로 업데이트하세요:

```markdown
## [0.1.0] - [현재 날짜 YYYY-MM-DD]

### Added
- 프로젝트 초기 설정
- Instruction 파일 생성
- 기본 폴더 구조 설정
```

---

### 7. 완료 메시지

파일 생성이 완료되면 사용자에게 다음 내용을 알려주세요:

```
✅ Instruction 템플릿이 생성되었습니다!

다음 파일들이 생성되었습니다:

project-instructions/
├── 00_PROJECT.md          (프로젝트 개요 및 메타데이터)
├── 01_ARCHITECTURE.md     (시스템 아키텍처)
├── 02_FEATURES.md         (기능 명세)
├── 03_IMPLEMENTATION.md   (구현 가이드)
├── 04_UI_UX.md            (UI/UX 명세) [web-app만]
├── CHANGELOG.md           (변경 이력)
├── TROUBLESHOOTING.md     (트러블슈팅)
├── modification.md        (변경/디버깅 지시서)
└── assets/                (이미지, 데이터, 코드)

📝 다음 단계:
1. 각 파일을 열어서 내용을 채워넣으세요
2. 각 섹션의 가이드 주석을 참고하세요
3. 필요 없는 섹션은 삭제하셔도 됩니다
4. assets/ 폴더에 참고 이미지나 코드를 추가하세요

💡 팁:
- 00_PROJECT.md부터 순서대로 작성하는 것을 권장합니다
- 모든 섹션을 채울 필요는 없습니다 (필요한 것만 작성)
- 나중에 Claude에게 "이 instruction 기반으로 코드 생성해줘"라고 요청할 수 있습니다
- 프로젝트 수정/디버깅 시 modification.md를 사용하세요 (에러 로그, 변경 요청 등을 기록)
```

---

## Notes

- 모든 템플릿 파일에는 작성 가이드 주석이 포함되어 있습니다
- 사용자는 가이드를 참고하여 직접 내용을 채워넣습니다
- 자동으로 내용을 채우려 하지 말고, 빈 템플릿만 제공하세요
- 각 파일의 주석과 예시는 그대로 유지하세요

---

## Error Handling

만약 템플릿 파일을 찾을 수 없다면:
- 사용자에게 `instruction-template-skill` 폴더가 올바른 위치에 있는지 확인하도록 안내
- 또는 GitHub에서 다시 clone하도록 안내

---

## Example Usage

**User:** "새 프로젝트 instruction 만들어줘"

**Assistant:**
"새 프로젝트의 instruction 템플릿을 생성하겠습니다. 프로젝트 타입을 선택해주세요:

1. web-app - 웹 애플리케이션
2. cli - CLI 도구
3. api - API 서버
4. library - 라이브러리/패키지"

**User:** "web-app"

**Assistant:**
[파일 생성 후]
"✅ Instruction 템플릿이 생성되었습니다!
..."

