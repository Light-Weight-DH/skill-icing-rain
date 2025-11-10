# 구현 가이드

<!-- 프로젝트 구현을 위한 단계별 가이드와 체크리스트 -->

---

## 코딩 원칙 및 베스트 프랙티스

<!-- 코드 작성 시 따라야 할 기본 원칙들 -->

### SOLID 원칙 적용
<!-- 객체지향 설계의 5대 원칙 -->

**적용할 원칙:**
- [ ] **S**ingle Responsibility: 하나의 클래스는 하나의 책임만
- [ ] **O**pen/Closed: 확장에는 열려있고, 수정에는 닫혀있게
- [ ] **L**iskov Substitution: 자식 클래스는 부모 클래스를 대체 가능
- [ ] **I**nterface Segregation: 인터페이스는 작고 구체적으로
- [ ] **D**ependency Inversion: 구체가 아닌 추상에 의존


### Clean Code 원칙

**명명 규칙:**
- 변수명: 의미있고 발음 가능한 이름 사용
- 함수명: 동사로 시작 (get, set, create, update, delete)
- 클래스명: 명사 사용
- 불린 변수: is, has, can 등으로 시작

**함수 작성:**
- 한 함수는 한 가지 일만 (Single Responsibility)
- 함수 길이: 최대 20줄 권장
- 매개변수: 최대 3개 권장 (그 이상이면 객체로 묶기)
- 사이드 이펙트 최소화

**코드 구조:**
- DRY (Don't Repeat Yourself): 중복 제거
- KISS (Keep It Simple, Stupid): 단순하게 유지
- YAGNI (You Aren't Gonna Need It): 필요한 것만 구현


### 에러 처리

**원칙:**
- 예외는 예외적인 상황에만 사용
- 에러 메시지는 명확하고 구체적으로
- 에러 로깅 필수
- 사용자에게는 친절한 메시지, 로그에는 디버깅 정보

**구현 예시:**
```python
# Bad
try:
    result = risky_operation()
except:
    pass  # 에러 무시

# Good
try:
    result = risky_operation()
except SpecificException as e:
    logger.error(f"Operation failed: {e}", exc_info=True)
    raise UserFriendlyException("작업 중 오류가 발생했습니다. 다시 시도해주세요.")
```


### 코드 리뷰 체크리스트

**기능:**
- [ ] 요구사항 충족
- [ ] 엣지 케이스 처리
- [ ] 에러 핸들링

**코드 품질:**
- [ ] 읽기 쉬운 코드
- [ ] 적절한 주석 (why, not what)
- [ ] 네이밍 일관성
- [ ] 중복 코드 없음

**성능:**
- [ ] N+1 쿼리 문제 없음
- [ ] 불필요한 반복문 없음
- [ ] 적절한 캐싱

**보안:**
- [ ] SQL Injection 방어
- [ ] XSS 방어
- [ ] 민감 정보 로깅 금지
- [ ] 인증/인가 적용


### Git Commit 컨벤션

**Commit Message 형식:**
```
<type>: <subject>

<body>

<footer>
```

**Type:**
- `feat`: 새 기능
- `fix`: 버그 수정
- `docs`: 문서 수정
- `style`: 코드 포맷팅 (기능 변경 없음)
- `refactor`: 리팩토링
- `test`: 테스트 추가/수정
- `chore`: 빌드, 설정 파일 수정

**예시:**
```
feat: 사용자 인증 API 추가

- JWT 기반 인증 구현
- 로그인/로그아웃 엔드포인트 추가
- 리프레시 토큰 발급 기능

Closes #123
```


---

## Phase 1: 환경 설정

### 필요 사항
<!-- 개발 환경에 필요한 소프트웨어 및 도구 -->

**개발 도구:**
- IDE/Editor:
- 버전 관리: Git
- 기타:

**런타임 환경:**
- Python: (버전 명시)
- Node.js: (버전 명시)
- 기타:

**외부 서비스:**
- API 키 필요: (예: OpenAI, AWS 등)
- 데이터베이스: (예: PostgreSQL 15+)


---

### 환경 변수 설정

```bash
# .env 파일 생성

# 데이터베이스
DATABASE_URL=
DB_HOST=
DB_PORT=
DB_NAME=
DB_USER=
DB_PASSWORD=

# API 키
OPENAI_API_KEY=
GOOGLE_API_KEY=

# 애플리케이션 설정
APP_ENV=development
APP_PORT=
SECRET_KEY=

# 기타
```


---

### 초기 설정 체크리스트

- [ ] Git 레포지토리 초기화
- [ ] .gitignore 설정
- [ ] .env 파일 생성 (템플릿 참조)
- [ ] 가상환경 생성
- [ ] 의존성 설치


---

### 의존성 설치

#### Backend
```bash
# 가상환경 생성 (Python)
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 의존성 설치
pip install -r requirements.txt

# 또는 개별 설치
pip install fastapi uvicorn sqlalchemy pydantic python-dotenv
```

#### Frontend (해당하는 경우)
```bash
# Node 패키지 설치
npm install

# 또는
yarn install
```


---

## Phase 2: Backend 구현

### 데이터베이스 설정

#### 체크리스트
- [ ] 데이터베이스 스키마 설계
- [ ] 모델 클래스 구현
- [ ] 마이그레이션 설정
- [ ] 초기 데이터 시드

#### 주요 파일
```
backend/
├── models/
│   ├── __init__.py
│   ├── user.py            # 구현 필요
│   ├── [model_name].py    # 구현 필요
│   └── ...
└── database.py            # 구현 필요
```

#### 구현 가이드
<!-- 데이터베이스 관련 구현 시 참고할 내용 -->


---

### API 엔드포인트 구현

#### 체크리스트
- [ ] 라우터 설정
- [ ] CRUD 엔드포인트 구현
- [ ] 요청/응답 스키마 정의 (Pydantic)
- [ ] 에러 핸들링
- [ ] 인증/인가 미들웨어

#### 주요 파일
```
backend/
└── api/
    ├── __init__.py
    ├── auth.py            # 인증 관련 API
    ├── [resource].py      # 리소스별 API
    └── ...
```

#### API 구현 가이드
<!-- API 구현 시 참고할 코드 스니펫이나 패턴 -->


---

### 비즈니스 로직 구현

#### 체크리스트
- [ ] 서비스 계층 구현
- [ ] 비즈니스 로직 분리
- [ ] 유효성 검증
- [ ] 예외 처리

#### 주요 파일
```
backend/
└── services/
    ├── __init__.py
    ├── [service_name]_service.py    # 구현 필요
    └── ...
```


---

### AI/ML 통합 (해당하는 경우)

#### 체크리스트
- [ ] 모델 로드 및 초기화
- [ ] 임베딩 생성 로직
- [ ] RAG 파이프라인 구현
- [ ] 벡터 DB 연동
- [ ] 프롬프트 엔지니어링

#### 주요 파일
```
backend/
└── services/
    ├── ai/
    │   ├── embedding_service.py
    │   ├── rag_service.py
    │   └── llm_service.py
    └── ...
```


---

### 테스트 작성

#### 체크리스트
- [ ] 유닛 테스트 작성
- [ ] 통합 테스트 작성
- [ ] API 테스트 작성
- [ ] 테스트 커버리지 확인

```bash
# 테스트 실행
pytest
pytest --cov=app tests/
```


---

## Phase 3: Frontend 구현 (해당하는 경우)

### 프로젝트 설정

#### 체크리스트
- [ ] 프레임워크 초기화 (Vue/React)
- [ ] 라우터 설정
- [ ] 상태 관리 설정 (Pinia/Redux)
- [ ] API 클라이언트 설정 (Axios)
- [ ] 스타일링 설정 (CSS/Tailwind)


---

### 컴포넌트 구현

#### 체크리스트
- [ ] 공통 컴포넌트 구현
- [ ] 페이지 컴포넌트 구현
- [ ] 레이아웃 컴포넌트 구현
- [ ] 폼 컴포넌트 구현

#### 주요 파일
```
frontend/src/
├── components/
│   ├── common/
│   │   ├── Button.vue
│   │   ├── Input.vue
│   │   └── ...
│   └── [feature]/
│       └── ...
└── views/
    ├── HomeView.vue
    ├── [Page]View.vue
    └── ...
```


---

### 상태 관리

#### 체크리스트
- [ ] Store 구조 설계
- [ ] State 정의
- [ ] Actions 구현
- [ ] Getters 구현

#### 주요 파일
```
frontend/src/
└── stores/
    ├── app.ts
    ├── user.ts
    ├── [feature].ts
    └── ...
```


---

### API 연동

#### 체크리스트
- [ ] API 클라이언트 설정
- [ ] API 호출 함수 구현
- [ ] 에러 핸들링
- [ ] 로딩 상태 관리

#### 구현 예시
```typescript
// api/client.ts
const API_URL = import.meta.env.VITE_API_URL

export const api = {
  get: async (url: string) => { },
  post: async (url: string, data: any) => { },
}
```


---

### 스타일링

#### 체크리스트
- [ ] 디자인 시스템 변수 정의
- [ ] 공통 스타일 작성
- [ ] 반응형 디자인 구현
- [ ] 다크모드 지원 (선택)


---

## Phase 4: 통합 및 배포

### 통합 테스트

#### 체크리스트
- [ ] Frontend-Backend 통합 확인
- [ ] E2E 테스트 작성
- [ ] 크로스 브라우저 테스팅
- [ ] 성능 테스트


---

### 성능 최적화

#### 체크리스트
- [ ] 데이터베이스 쿼리 최적화
- [ ] API 응답 시간 최적화
- [ ] Frontend 번들 크기 최적화
- [ ] 이미지 최적화
- [ ] 캐싱 전략 구현


---

### 배포 설정

#### Docker 설정 (선택)

```yaml
# docker-compose.yml
version: '3.8'

services:
  backend:
    build: ./backend
    ports:
      - "8000:8000"
    env_file:
      - .env

  frontend:
    build: ./frontend
    ports:
      - "3000:3000"

  database:
    image: postgres:15
    environment:
      POSTGRES_DB: ${DB_NAME}
      POSTGRES_USER: ${DB_USER}
      POSTGRES_PASSWORD: ${DB_PASSWORD}
```

#### 체크리스트
- [ ] Docker 이미지 생성
- [ ] docker-compose 설정
- [ ] 환경 변수 설정
- [ ] 빌드 및 테스트


---

### CI/CD 파이프라인 (선택)

#### 체크리스트
- [ ] GitHub Actions 설정
- [ ] 자동 테스트 실행
- [ ] 자동 배포 설정
- [ ] 배포 알림 설정

```yaml
# .github/workflows/deploy.yml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: |
          # 테스트 명령
      - name: Deploy
        run: |
          # 배포 명령
```


---

### 배포

#### 체크리스트
- [ ] 프로덕션 환경 변수 설정
- [ ] 데이터베이스 마이그레이션
- [ ] SSL 인증서 설정
- [ ] 도메인 설정
- [ ] 모니터링 설정
- [ ] 백업 설정


---

## 전체 구현 체크리스트

### Phase 1: Setup
- [ ] 환경 설정 완료
- [ ] 의존성 설치 완료
- [ ] Git 설정 완료

### Phase 2: Backend
- [ ] 데이터베이스 구현 완료
- [ ] API 구현 완료
- [ ] 테스트 작성 완료

### Phase 3: Frontend
- [ ] 컴포넌트 구현 완료
- [ ] 상태 관리 구현 완료
- [ ] API 연동 완료

### Phase 4: Deploy
- [ ] 통합 테스트 완료
- [ ] 성능 최적화 완료
- [ ] 배포 완료


---

## 참고 코드 및 리소스

<!-- 구현 시 참고할 수 있는 코드 스니펫이나 외부 리소스 -->

### 유용한 링크
-
-

### 코드 스니펫
<!-- assets/code/ 폴더에 참고 코드 저장 -->
-

