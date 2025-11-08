# Project Instruction Template Skill

Claude Code skill for creating standardized project instruction templates.

프로젝트 시작 시 표준화된 instruction 문서를 자동으로 생성해주는 Claude Code 스킬입니다.

---

## What is this?

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
git clone https://github.com/YOUR_USERNAME/instruction-template-skill.git
cd instruction-template-skill
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
@instruction-template-skill/create-instruction.md

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

## 💡 Usage Examples

### Example 1: AI 챗봇 프로젝트

```markdown
# 00_PROJECT.md
---
project:
  name: "Customer Support AI Chatbot"
  type: "web-app"

tech_stack:
  frontend: ["React", "TypeScript", "Tailwind"]
  backend: ["FastAPI", "PostgreSQL"]
  ai: ["OpenAI GPT-4", "LangChain", "FAISS"]
---

## 1줄 요약
고객 문의를 자동으로 답변하는 AI 챗봇 시스템
```

### Example 2: 데이터 분석 CLI 도구

```markdown
# 00_PROJECT.md
---
project:
  name: "Sales Data Analyzer"
  type: "cli"

tech_stack:
  backend: ["Python", "Pandas", "Click"]
---

## 1줄 요약
CSV 판매 데이터를 분석하고 리포트를 생성하는 CLI 도구
```

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
- **핵심**: 단계별 개발 계획

### 04_UI_UX.md
- **목적**: UI/UX 디자인 명세 (web-app만)
- **핵심**: 화면 구성, 사용자 플로우

---

## 🎨 Customization

### 템플릿 수정

`templates/` 폴더의 파일들을 직접 수정할 수 있습니다:

```bash
cd instruction-template-skill/templates
# 원하는 에디터로 수정
code 00_PROJECT.md
```

### 새 템플릿 추가

예: 보안 체크리스트 추가

1. `templates/SECURITY.md` 생성
2. `create-instruction.md` 수정하여 복사 로직 추가

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

## Contributing

개선 아이디어나 버그 리포트는 Issues에 올려주세요!

Pull Requests도 환영합니다.

---

## ⭐ Star this repo!

이 스킬이 유용하다면 ⭐️ Star를 눌러주세요!

---

**Happy Coding! 🚀**

