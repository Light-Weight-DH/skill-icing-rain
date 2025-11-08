# 트러블슈팅 가이드

<!-- 프로젝트 개발/실행 중 발생할 수 있는 문제와 해결 방법 -->

---

## 환경 설정 관련

### 문제 1: 의존성 설치 실패

**증상:**
```
pip install 또는 npm install 실행 시 에러 발생
```

**가능한 원인:**
- Python/Node 버전 불일치
- 네트워크 문제
- 권한 문제

**해결 방법:**
```bash
# Python 버전 확인
python --version

# 가상환경 재생성
rm -rf venv
python -m venv venv
source venv/bin/activate

# 캐시 제거 후 재설치
pip cache purge
pip install -r requirements.txt

# 또는 (Node.js)
rm -rf node_modules package-lock.json
npm install
```


---

### 문제 2: 환경 변수 로드 안됨

**증상:**
```
KeyError: 'API_KEY' 또는 환경 변수 관련 에러
```

**원인:**
- .env 파일 누락
- .env 파일 위치 잘못됨
- 환경 변수 이름 오타

**해결 방법:**
```bash
# .env 파일 존재 확인
ls -la .env

# .env 파일이 없다면 생성
cp .env.example .env

# 환경 변수 로드 확인
python -c "from dotenv import load_dotenv; load_dotenv(); import os; print(os.getenv('API_KEY'))"
```


---

## 데이터베이스 관련

### 문제 3: 데이터베이스 연결 실패

**증상:**
```
sqlalchemy.exc.OperationalError: (psycopg2.OperationalError) could not connect to server
```

**원인:**
- 데이터베이스 서버 미실행
- 연결 정보 오류
- 방화벽 문제

**해결 방법:**
```bash
# PostgreSQL 서버 상태 확인
sudo service postgresql status

# Docker로 실행 중이라면
docker ps | grep postgres

# 연결 테스트
psql -h localhost -U username -d database_name

# .env 파일의 DATABASE_URL 확인
cat .env | grep DATABASE_URL
```


---

### 문제 4: 마이그레이션 에러

**증상:**
```
alembic.util.exc.CommandError: Can't locate revision identified by 'xxxxx'
```

**원인:**
- 마이그레이션 파일 충돌
- 데이터베이스 상태와 마이그레이션 불일치

**해결 방법:**
```bash
# 마이그레이션 히스토리 확인
alembic history

# 데이터베이스 리셋 (개발 환경만!)
alembic downgrade base
alembic upgrade head

# 또는 데이터베이스 초기화
dropdb database_name
createdb database_name
alembic upgrade head
```


---

## API/백엔드 관련

### 문제 5: API 호출 시 CORS 에러

**증상:**
```
Access to XMLHttpRequest has been blocked by CORS policy
```

**원인:**
- 백엔드 CORS 설정 누락
- Origin 불일치

**해결 방법:**
```python
# FastAPI 예시
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:3000"],  # 프론트엔드 주소
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```


---

### 문제 6: API 응답 느림

**증상:**
- API 응답 시간이 5초 이상
- 타임아웃 발생

**원인:**
- 데이터베이스 쿼리 비효율
- N+1 쿼리 문제
- 외부 API 호출 대기

**해결 방법:**
```python
# 쿼리 최적화 - eager loading 사용
from sqlalchemy.orm import joinedload

query = session.query(Model).options(joinedload(Model.relation))

# 비동기 처리
import asyncio
results = await asyncio.gather(*[api_call() for _ in range(10)])

# 캐싱
from functools import lru_cache

@lru_cache(maxsize=128)
def expensive_function():
    pass
```


---

## AI/ML 관련 (해당하는 경우)

### 문제 7: 모델 로드 실패

**증상:**
```
torch.load() 관련 에러
OSError: Unable to load weights from pytorch model
```

**원인:**
- torch 버전 불일치
- 모델 파일 손상
- 메모리 부족

**해결 방법:**
```bash
# torch 버전 확인
pip show torch

# safetensors 사용 (보안 문제 해결)
pip install safetensors

# Python 코드에서
model = AutoModel.from_pretrained(
    'model_name',
    use_safetensors=True
)
```


---

### 문제 8: OpenAI API 에러

**증상:**
```
openai.error.RateLimitError: Rate limit exceeded
openai.error.AuthenticationError: Invalid API key
```

**원인:**
- API 키 오류
- 사용량 한도 초과
- API 키 만료

**해결 방법:**
```bash
# API 키 확인
echo $OPENAI_API_KEY

# .env 파일 확인
cat .env | grep OPENAI_API_KEY

# 사용량 확인
# https://platform.openai.com/usage 접속

# 재시도 로직 추가
from tenacity import retry, stop_after_attempt, wait_exponential

@retry(stop=stop_after_attempt(3), wait=wait_exponential(multiplier=1, min=4, max=10))
def call_openai_api():
    pass
```


---

## 프론트엔드 관련

### 문제 9: 빌드 실패

**증상:**
```
npm run build
ERROR in ...
```

**원인:**
- 타입 에러 (TypeScript)
- 모듈 import 오류
- 메모리 부족

**해결 방법:**
```bash
# 캐시 제거
rm -rf node_modules/.cache

# TypeScript 타입 체크
npm run type-check

# 메모리 늘려서 빌드
NODE_OPTIONS=--max-old-space-size=4096 npm run build
```


---

### 문제 10: Hot Reload 안됨

**증상:**
- 코드 수정해도 화면 갱신 안됨

**원인:**
- 개발 서버 문제
- 파일 와처 설정

**해결 방법:**
```bash
# 개발 서버 재시작
npm run dev

# Vite 설정 (vite.config.ts)
export default defineConfig({
  server: {
    watch: {
      usePolling: true
    }
  }
})
```


---

## 배포 관련

### 문제 11: Docker 빌드 실패

**증상:**
```
docker build 실행 시 에러
```

**원인:**
- Dockerfile 오류
- 의존성 설치 실패
- 레이어 캐싱 문제

**해결 방법:**
```bash
# 캐시 없이 빌드
docker build --no-cache -t app:latest .

# 특정 단계까지만 빌드 (디버깅)
docker build --target builder -t app:builder .

# 빌드 로그 상세히 보기
docker build --progress=plain -t app:latest .
```


---

## 일반적인 디버깅 팁

### 로그 확인
```bash
# 백엔드 로그
tail -f logs/app.log

# Docker 로그
docker logs -f container_name

# Systemd 로그 (배포 환경)
journalctl -u app-name -f
```

### 네트워크 디버깅
```bash
# 포트 사용 확인
lsof -i :8000

# 프로세스 종료
kill -9 $(lsof -t -i :8000)

# 네트워크 연결 확인
curl -v http://localhost:8000/api/health
```

### 데이터베이스 디버깅
```bash
# PostgreSQL 연결
psql -U username -d database_name

# 테이블 목록
\dt

# 쿼리 실행 계획
EXPLAIN ANALYZE SELECT ...;
```


---

## 도움 받기

### 이슈 리포트 시 포함할 내용
1. 에러 메시지 전문
2. 재현 방법
3. 환경 정보 (OS, Python/Node 버전 등)
4. 관련 로그

### 유용한 리소스
- 프로젝트 GitHub Issues:
- 공식 문서:
- 커뮤니티:


---

## 추가할 문제

<!-- 프로젝트 진행하면서 발생한 문제와 해결 방법을 계속 추가하세요 -->

### 문제 N: [문제 제목]

**증상:**


**원인:**


**해결 방법:**


