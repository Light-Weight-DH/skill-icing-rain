# Project Instruction Template Skill

Claude Code skill for creating standardized project instruction templates.

프로젝트 시작 시 표준화된 instruction 문서를 자동으로 생성해주는 Claude Code 스킬입니다.

---

## ✨ What's New

### v1.2 - 2025-11-12

**템플릿 단순화 및 실용성 강화**
- ✅ **섹션 기반 Wireframe**: 각 섹션(블록)별 역할 → 구성 요소 → 스타일 → 동작 순서로 명확히 작성
- ✅ **modification.md 추가**: 변경 요청, 에러 로그, 디버깅 지시를 파일로 관리
- ✅ **예시 주석 강화**: 모든 템플릿에 실용적인 작성 예시 추가
- ✅ **ASCII Art 제거**: Wireframe 이미지만 사용하는 방식으로 간소화

**사용성 개선**
- ✅ **CLI 입력 최소화**: `@modification.md`로 긴 에러 로그나 변경사항 전달
- ✅ **더 명확한 가이드**: 각 필드마다 구체적인 작성 예시 제공

### v1.1 - 2025-11-10

**UI/UX 템플릿 대폭 개선**
- ✅ **Wireframe 중심 설계**: 복잡한 CSS 변수 대신 실용적인 wireframe + 설명 방식
- ✅ **Laws of UX 통합**: 7가지 UX 원칙 체크리스트 추가 (Hick's Law, Miller's Law 등)
- ✅ **디자인/기능 분리**: 시각 디자인과 동작 기능을 명확히 구분

**코딩 품질 가이드 추가**
- ✅ **SOLID 원칙**: 객체지향 설계 5대 원칙 체크리스트
- ✅ **Clean Code**: 명명 규칙, 함수 작성 가이드, DRY/KISS/YAGNI
- ✅ **에러 처리 표준**: Good vs Bad 코드 예시
- ✅ **Git 컨벤션**: Conventional Commits 형식 가이드

> 💡 이제 Claude가 instruction을 읽고 **UX 원칙과 코딩 베스트 프랙티스를 자동 적용**한 코드를 생성합니다!

---

## 🎯 What is this?

새 프로젝트를 시작할 때마다:
- 어떤 문서를 작성해야 할지 고민하시나요?
- 프로젝트 구조를 매번 처음부터 설계하시나요?
- 팀원에게 프로젝트 컨텍스트를 전달하기 어려우신가요?

이 스킬은 **표준화된 빈 템플릿**을 자동 생성하여:
- ✅ 일관된 프로젝트 문서 구조 제공
- ✅ 작성 가이드 주석으로 명확한 방향 제시
- ✅ Claude가 읽고 코드 생성할 수 있는 형식
- ✅ 팀 협업 시 컨텍스트 공유 용이

---

## What gets created?

```
project-instructions/
├── 00_PROJECT.md          # 프로젝트 개요, 목표, 배경
├── 01_ARCHITECTURE.md     # 시스템 아키텍처, 기술 스택
├── 02_FEATURES.md         # 기능 명세, 우선순위
├── 03_IMPLEMENTATION.md   # 구현 가이드, 체크리스트
├── 04_UI_UX.md            # UI/UX 디자인 (web-app만)
├── CHANGELOG.md           # 변경 이력
├── TROUBLESHOOTING.md     # 트러블슈팅 가이드
└── assets/
    ├── images/            # UI 스케치, 다이어그램
    ├── data/              # 샘플 데이터, 스키마
    └── code/              # 참고 코드 스니펫
```

---

## 🚀 Quick Start

### 1. Installation

#### Option A: Clone this repo
```bash
git clone https://github.com/Light-Weight-DH/skill-icing-rain.git
cd skill-icing-rain
```

#### Option B: Download ZIP
GitHub에서 ZIP 다운로드 → 원하는 위치에 압축 해제

---

### 2. Usage

#### Claude Code에서 사용

1. 새 프로젝트 폴더 생성 및 이동
```bash
mkdir my-new-project
cd my-new-project
```

2. Claude Code 실행 (VSCode 등)

3. Skill 파일 경로를 Claude에게 제공하고 실행
```
@skill-icing-rain/create-instruction.md

새 프로젝트 instruction 만들어줘
```

4. 프로젝트 타입 선택
- `web-app`: 웹 애플리케이션 (Frontend + Backend)
- `cli`: CLI 도구
- `api`: API 서버
- `library`: 라이브러리/패키지

5. 생성된 템플릿 파일들에 내용 채우기

---

## 📝 How to fill in the templates

### Step 1: 메타데이터 설정 (00_PROJECT.md)

```yaml
---
project:
  name: "My Awesome Project"
  type: "web-app"
  priority: "high"

tech_stack:
  frontend: ["Vue 3", "TypeScript"]
  backend: ["FastAPI", "PostgreSQL"]
  ai: ["OpenAI GPT-4", "LangChain"]
---
```

### Step 2: 각 파일 순서대로 작성

권장 순서:
1. **00_PROJECT.md** - 프로젝트 개요 (왜 만들고, 누가 쓰는지)
2. **01_ARCHITECTURE.md** - 기술 스택 결정 (어떤 기술 쓸지)
3. **02_FEATURES.md** - 기능 목록 (뭘 만들지)
4. **03_IMPLEMENTATION.md** - 구현 계획 (어떻게 만들지)
5. **04_UI_UX.md** - UI 디자인 (어떻게 보일지, web-app만)

### Step 3: 참고 자료 추가

```
assets/
├── images/
│   ├── architecture-diagram.png
│   ├── ui-wireframe.png
│   └── user-flow.png
├── data/
│   ├── sample-data.json
│   └── db-schema.sql
└── code/
    └── example-config.py
```

---

## 🎬 실전 시나리오

### Scenario: AI 이메일 분류 시스템 만들기

**Step 1: Instruction 생성**
```bash
@skill-icing-rain/create-instruction.md

새 프로젝트 instruction 만들어줘. 타입은 web-app.
```

**Step 2: 양식 채우기**

`00_PROJECT.md`:
```yaml
project:
  name: "AI Email Classifier"
  type: "web-app"
tech_stack:
  frontend: ["Vue 3", "TypeScript"]
  backend: ["FastAPI", "PostgreSQL"]
  ai: ["OpenAI GPT-4", "LangChain"]
```

`04_UI_UX.md`:
- Laws of UX 선택: Hick's Law ✅, Jakob's Law ✅, Miller's Law ✅
- Wireframe 이미지 업로드 (Figma/Excalidraw)
- 각 섹션별 역할/구성/스타일/동작 작성

`03_IMPLEMENTATION.md`:
- SOLID 원칙 체크 ✅
- Clean Code 가이드 확인 ✅

**Step 3: Claude와 협업**
```
project-instructions/를 읽고
Laws of UX와 Clean Code 원칙에 맞게 백엔드를 구현해줘
```

**Claude 생성 결과:**
```python
# backend/api/email.py
# ✅ Single Responsibility: 이메일 분류만 담당
# ✅ Clean Code: 명확한 함수명, 3개 이하 파라미터

class EmailClassifier:
    """이메일을 카테고리별로 분류"""

    def classify(self, email: Email) -> Category:
        # ✅ SOLID: 추상에 의존
        # ✅ 에러 처리: 명확한 예외
        try:
            result = self._llm.classify(email.content)
            return Category(result)
        except ClassificationError as e:
            logger.error(f"Classification failed: {e}")
            raise UserFriendlyException("분류 중 오류가 발생했습니다.")
```

**결과:**
- ✅ SOLID 원칙을 따르는 깔끔한 코드
- ✅ Laws of UX를 고려한 API 설계 (선택지 최소화)
- ✅ 일관된 에러 핸들링
- ✅ 표준 Git 커밋 메시지

**Step 4: 에러 발생 시 modification.md 활용**

프로젝트 중 500 에러 발생!

`modification.md` 작성:
```markdown
### 에러 1: 이메일 업로드 시 500 에러

**에러 로그:**
```
Error: File size exceeds limit
  at uploadEmail (/src/upload/email.ts:42)
```

**해결 방안:**
- 파일 크기 제한 10MB로 상향
- 클라이언트 사이드 검증 추가
```

Claude에게:
```
@modification.md 읽고 에러 수정해줘
```

→ Claude가 즉시 에러 원인 파악 및 수정 코드 생성!

---

## 🤖 Using with Claude

템플릿을 작성한 후, Claude에게 이렇게 요청할 수 있습니다:

```
project-instructions/ 폴더의 instruction 파일들을 읽고,
이 프로젝트의 backend를 구현해줘.
```

Claude가 할 일:
1. Instruction 파일들 읽기
2. 프로젝트 구조 파악
3. 기술 스택에 맞는 boilerplate 생성
4. 기능 명세에 따라 코드 작성

---

## 🔄 기존 프로젝트에 적용하기

### Step 1: Instruction 생성
```bash
@skill-icing-rain/create-instruction.md
"기존 프로젝트용 instruction 만들어줘"
```

### Step 2: 기존 코드 복사
```bash
project-instructions/
└── reference/
    ├── backend/          # 기존 백엔드 프로젝트 통째로 복사
    └── frontend/         # 기존 프론트엔드 프로젝트 통째로 복사
```

**그냥 프로젝트 폴더를 통째로 복사하세요!**

### Step 3: Claude에게 요청
```
reference/backend/의 코드 스타일을 참고해서,
새로운 결제 기능을 추가해줘.
```

→ Claude가 기존 패턴을 파악하고 일관된 스타일로 코드 생성!

---

## 🎨 UI 수정 워크플로우 (자연어로 수정)

### Step 1: 브라우저에서 요소 찾기
1. **F12** (개발자 도구) 열기
2. 요소 선택 도구(화살표 아이콘) 클릭
3. 수정하고 싶은 카드/버튼/div 클릭
4. 선택자 복사 (예: `.card-container`, `#user-profile`)

### Step 2: modification.md 작성
```markdown
## UI 요소 수정

### UI 수정 1: 프로필 카드 크기 조정

**선택자:** `.card.user-profile`

**원하는 변경:**
- 카드를 좀 더 크게 만들어주세요
- 글자를 더 진하게 해주세요
- 모서리를 둥글게 해주세요

**⚠️ 중요:**
- 이 카드만 수정하고 다른 요소는 건드리지 마세요
- 추가 div 절대 추가하지 말 것
```

### Step 3: Claude에게 전달
```bash
@modification.md 읽고 UI 수정해줘
```

**장점:**
- ✅ "padding", "border-radius" 같은 기술 용어 몰라도 OK
- ✅ 자연어로 요청 (예: "좀 더 크게", "간격 벌려줘")
- ✅ 추가 코드 없이 기존 요소만 수정 (엉킴 방지)
- ✅ 여러 페이지 동시 수정 가능

---

## 📋 Template Files Guide

### 00_PROJECT.md
- **목적**: 프로젝트의 전체 맥락 제공
- **핵심**: 왜, 누구를 위해, 무엇을 만드는지

### 01_ARCHITECTURE.md
- **목적**: 기술적 구조 설계
- **핵심**: 어떤 기술을 어떻게 조합할지

### 02_FEATURES.md
- **목적**: 기능 명세 및 우선순위
- **핵심**: 뭘 만들고, 어느 것부터 할지

### 03_IMPLEMENTATION.md
- **목적**: 구현 가이드 및 체크리스트
- **핵심**: 단계별 개발 계획, SOLID/Clean Code 원칙

### 04_UI_UX.md
- **목적**: UI/UX 디자인 명세 (web-app만)
- **핵심**: 섹션별 Wireframe, Laws of UX 적용

### modification.md (NEW!)
- **목적**: 프로젝트 변경/디버깅 지시
- **핵심**: 에러 로그, 변경 요청, 개선사항 기록
- **사용법**: `@modification.md`로 Claude에게 전달

---

## 🎨 Customization

### 템플릿 수정

`templates/` 폴더의 파일들을 직접 수정할 수 있습니다:

```bash
cd skill-icing-rain/templates
# 원하는 에디터로 수정
code 00_PROJECT.md
```

### 새 템플릿 추가

예: 보안 체크리스트 추가

1. `templates/SECURITY.md` 생성
2. `create-instruction.md` 수정하여 복사 로직 추가

---

## 🌟 Key Features

### 1. 섹션 기반 Wireframe 설계
**Before:** 복잡한 CSS 변수와 ASCII art
**After:** 섹션(블록) 중심의 명확한 구조

- Wireframe 이미지로 전체 레이아웃 표현
- 각 섹션별로: **역할 → 구성 요소 → 스타일 → 동작** 순서로 작성
- 예: "섹션 1: Header - 역할: 로고/네비게이션, 구성: 메뉴 3개, 동작: hover 시 색상 변경"

### 2. Laws of UX 적용
7가지 UX 원칙을 체크리스트로 제공:
- **Hick's Law**: 선택지 최소화로 빠른 결정
- **Miller's Law**: 정보 그룹화 (7±2개 항목)
- **Fitts's Law**: 클릭 영역 최적화
- **Jakob's Law**: 익숙한 패턴 사용
- **Law of Proximity**: 관련 요소 그룹화
- **Aesthetic-Usability Effect**: 시각적 완성도
- **Parkinson's Law**: 명확한 마감 표시

### 3. 코딩 품질 보장
**SOLID 원칙**
- Single Responsibility, Open/Closed, Liskov Substitution
- Interface Segregation, Dependency Inversion

**Clean Code 가이드**
- 명명 규칙 (변수, 함수, 클래스)
- 함수 작성 (한 가지 일만, 최대 20줄, 매개변수 3개 이하)
- DRY, KISS, YAGNI 원칙

**에러 처리 & Git 컨벤션**
- Good vs Bad 코드 예시
- Conventional Commits 형식

### 4. 변경/디버깅 지시서 (modification.md)
- **에러 로그**, 변경 요청, 개선사항을 파일로 관리
- CLI나 익스텐션에 긴 내용 입력하지 않아도 됨
- `@modification.md`로 Claude에게 전달하면 즉시 이해

### 5. AI 친화적 구조
- Claude가 읽고 **바로 코드 생성** 가능
- **UX 원칙과 코딩 표준 자동 적용**
- 프롬프트 엔지니어링 불필요

---

## 🤝 Benefits

### For Solo Developers
- ✅ 프로젝트 시작 시 구조화된 계획
- ✅ 나중에 돌아와도 컨텍스트 파악 쉬움
- ✅ Claude에게 코드 생성 요청 시 명확한 지침 제공

### For Teams
- ✅ 일관된 프로젝트 문서 형식
- ✅ 새 팀원 온보딩 용이
- ✅ 코드 리뷰 시 참고 자료

### For AI Collaboration
- ✅ Claude가 이해하기 쉬운 구조
- ✅ Instruction → Code 생성 자동화
- ✅ 프롬프트 엔지니어링 불필요

---

## 📂 Real-world Examples

이 스킬은 다음 프로젝트들에서 사용된 패턴을 바탕으로 만들어졌습니다:

1. **Vision Contact** - 실시간 교통 표지판 인식 시스템
2. **Copy RAG** - 저작권법 판례 AI 챗봇
3. **5PL 물류 시스템** - AI 기반 지능형 물류 관리

각 프로젝트는 instruction 파일을 통해:
- 프로젝트 범위 명확화
- 기술 스택 표준화
- 개발 일정 관리

---

## 🔄 Workflow

```
1. Skill 실행
   ↓
2. 프로젝트 타입 선택
   ↓
3. 템플릿 파일 생성됨
   ↓
4. 템플릿 내용 채우기 (10-60분)
   ↓
5. Claude에게 코드 생성 요청
   ↓
6. 개발 진행하며 instruction 업데이트
   ↓
7. CHANGELOG.md에 변경사항 기록
```

---

##  Requirements

- Claude Code (또는 Claude API 접근 가능한 환경)
- Git (선택사항, 버전 관리용)
- Text Editor (VSCode, Cursor 등)

---

## License

MIT License - 자유롭게 사용하고 수정하세요!

---

## ❓ FAQ

### Q: Claude Code 없이도 사용할 수 있나요?
A: 네, 템플릿을 수동으로 복사해서 사용 가능합니다. 하지만 Claude Code와 함께 사용하면 자동화와 코드 생성의 이점을 얻을 수 있습니다.

### Q: 모든 파일을 다 채워야 하나요?
A: 아니요, 필요한 파일만 작성하세요. 예를 들어:
- CLI 프로젝트 → 04_UI_UX.md 불필요
- 간단한 스크립트 → 01_ARCHITECTURE.md만으로 충분
- 필요한 섹션만 채우고 나머지는 삭제해도 됩니다

### Q: 기존 프로젝트에도 적용 가능한가요?
A: 네! 기존 프로젝트에 `project-instructions/` 폴더를 추가하여 문서화에 활용할 수 있습니다. 레거시 코드 리팩토링 시 특히 유용합니다.

### Q: Laws of UX를 모두 적용해야 하나요?
A: 아니요, 프로젝트에 맞는 원칙만 선택하세요. 체크리스트는 가이드일 뿐이며, 2-3개만 선택해도 충분합니다.

### Q: SOLID 원칙을 잘 모르는데 사용할 수 있나요?
A: 네! 03_IMPLEMENTATION.md에 각 원칙의 간단한 설명이 있습니다. Claude에게 "SOLID 원칙을 적용해서 구현해줘"라고 요청하면 Claude가 알아서 적용합니다.

### Q: 여러 프로젝트에서 재사용할 수 있나요?
A: 물론입니다! 한 번 채운 instruction을 복사해서 다른 프로젝트의 시작점으로 사용할 수 있습니다. 기술 스택이나 구조가 비슷한 프로젝트에 특히 유용합니다.

---

## 💬 Contributing

개선 아이디어나 버그 리포트는 [Issues](https://github.com/Light-Weight-DH/skill-icing-rain/issues)에 올려주세요!

Pull Requests도 환영합니다.

---

## ⭐ Star this repo!

이 스킬이 유용하다면 ⭐️ Star를 눌러주세요!

---

**Happy Coding! 🚀**

