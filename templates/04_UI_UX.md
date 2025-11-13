# UI/UX 명세

> **AI 활용 팁:** Wireframe 이미지와 섹션별 역할을 명확히 작성하면, Claude가 정확한 UI를 생성합니다.

---

## 디자인 원칙 (Laws of UX)

프로젝트에 적용할 UX 법칙을 체크하세요. ([Laws of UX 참고](https://lawsofux.com/))

- [ ] **Hick's Law**: 선택지 최소화 (예: 버튼 3개 이하)
- [ ] **Miller's Law**: 정보 그룹화 (예: 메뉴 3-4개 카테고리)
- [ ] **Fitts's Law**: 주요 버튼 크기 충분히 (예: 최소 44x44px)
- [ ] **Jakob's Law**: 익숙한 UI 패턴 사용 (예: 검색은 우측 상단)
- [ ] **Law of Proximity**: 관련 정보 가까이 배치
- [ ] **Aesthetic-Usability Effect**: 깔끔한 디자인 유지
- [ ] **Parkinson's Law**: 명확한 CTA 버튼

<!--
예시 작성:
- [x] Hick's Law: 대시보드에 핵심 기능 5개만 노출
- [x] Fitts's Law: 주요 CTA 버튼 높이 48px로 설정
-->

---

## 디자인 시스템

### 색상
```css
Primary: #007bff      /* 주요 브랜드 색상 */
Secondary: #6c757d    /* 보조 색상 */
Success: #28a745      /* 성공 메시지 */
Danger: #dc3545       /* 경고/에러 */
Background: #f8f9fa   /* 배경 */
Text: #212529         /* 본문 텍스트 */
```

### 타이포그래피
```
H1: 32px, 굵게 (bold)
H2: 24px, 중간 굵기 (semi-bold)
Body: 16px, 보통 (regular)
Caption: 14px, 보통
```

### Spacing (8px 단위 사용)
```
xs: 8px
sm: 16px
md: 24px
lg: 32px
xl: 48px
```

---

## 페이지별 UI/UX 설계

### 페이지 1: [페이지명 - 예: 대시보드]

#### Wireframe 이미지
![Wireframe](../assets/images/page1-wireframe.png)
<!-- Figma, Excalidraw 등에서 작성한 wireframe을 첨부하세요 -->

#### 섹션(블록) 구조 및 역할

**섹션 1: Header**
- **역할**: 로고, 네비게이션, 사용자 정보 표시
- **권장 선택자**: `header.main-header` 또는 `#app-header`
- **구성 요소**:
  - 로고 (좌측, 클릭 시 홈 이동) - 선택자: `.logo`
  - 메뉴: "홈", "프로젝트", "설정" (중앙) - 선택자: `nav.main-nav`
  - 사용자 아바타 + 이름 (우측) - 선택자: `.user-profile`
- **스타일**: 흰색 배경, 높이 64px, 하단 회색 구분선 1px
- **동작**:
  - 메뉴 hover: Primary 색상으로 변경
  - 아바타 클릭: 드롭다운 메뉴 (프로필, 로그아웃)

**섹션 2: Sidebar**
- **역할**: 주요 기능 네비게이션
- **권장 선택자**: `aside.sidebar` 또는 `#main-sidebar`
- **구성 요소**:
  - 아이콘 + 텍스트: "대시보드", "작업 목록", "통계" - 선택자: `.nav-item`
- **스타일**: 연회색 배경 (#f8f9fa), 너비 240px
- **동작**:
  - 클릭 시 해당 페이지로 이동
  - 현재 페이지는 Primary 색상 배경 강조

**섹션 3: Main Content**
- **역할**: 핵심 콘텐츠 표시
- **권장 선택자**: `main.content` 또는 `#main-content`
- **구성 요소**:
  - Card 1 "최근 프로젝트": 제목, 진행률 바, 날짜 - 선택자: `.card.recent-projects`
  - Card 2 "진행 중인 작업": 작업명, 담당자, 상태 뱃지 - 선택자: `.card.ongoing-tasks`
  - Card 3 "알림": 메시지 리스트 (최대 5개) - 선택자: `.card.notifications`
- **스타일**: 각 카드 흰색 배경, 그림자 효과, 간격 16px
- **동작**:
  - Card hover: 그림자 진하게 (0 4px 12px rgba)
  - Card 클릭: 상세 페이지 이동

**섹션 4: Footer**
- **역할**: 저작권, 링크
- **권장 선택자**: `footer.main-footer` 또는 `#app-footer`
- **구성 요소**: "© 2025 프로젝트명", "도움말", "문의"
- **스타일**: 연회색 배경, 높이 48px, 텍스트 중앙 정렬

#### 반응형 (Responsive)
```
Desktop (≥1200px): 위 레이아웃 그대로
Tablet (768-1199px): Sidebar 접기, 햄버거 메뉴로 전환
Mobile (<768px): Card 1열 배치, H1 폰트 24px로 축소
```

---

### 페이지 2: [페이지명]

#### Wireframe 이미지
![Wireframe](../assets/images/page2-wireframe.png)

#### 섹션(블록) 구조 및 역할

**섹션 1: [섹션명]**
- **역할**: [이 섹션의 주요 기능 설명]
- **권장 선택자**: `[클래스명 또는 ID]` (예: `.section-name` 또는 `#section-id`)
- **구성 요소**: [버튼, 입력폼, 리스트 등 나열]
- **스타일**: [배경색, 크기, 간격 등]
- **동작**: [hover, 클릭, 포커스 시 동작]

<!-- 필요한 만큼 섹션 추가 -->

---

## 공통 UI 컴포넌트

### Button
```
Primary:
  - 배경 #007bff, 텍스트 흰색, border-radius 8px
  - hover: 배경 #0056b3
  - 높이 40px, padding 좌우 24px

Secondary:
  - 배경 투명, 테두리 1px solid #007bff, 텍스트 #007bff
  - hover: 배경 연파랑 (#e7f1ff)

Danger:
  - 배경 #dc3545, 텍스트 흰색
  - hover: 배경 #c82333
```

### Input Field
```
기본:
  - 테두리 1px solid #ced4da, border-radius 4px
  - 높이 40px, padding 12px
  - 폰트 16px

Focus:
  - 테두리 #007bff, 약한 파란색 그림자

Error:
  - 테두리 #dc3545, 하단 에러 메시지 빨간색 표시
```

### Modal
```
구조:
  - 배경: 반투명 검정 (rgba(0,0,0,0.5))
  - 모달창: 흰색, 최대 너비 600px, 중앙 배치
  - 제목, 본문, 버튼 영역으로 구분

동작:
  - 열기: fade-in 애니메이션 (250ms)
  - ESC 키 또는 배경 클릭: 닫기
```

<!-- 필요한 컴포넌트 추가 -->

---

## UX 플로우 (주요 사용자 시나리오)

### 시나리오 1: [예: 회원가입]
```
1. 메인 페이지 진입
   ↓
2. "시작하기" 버튼 클릭
   ↓
3. 회원가입 폼 표시 (이메일, 비밀번호 입력)
   ↓ (실시간 검증: 이메일 형식, 비밀번호 8자 이상)
4. "가입 완료" 버튼 클릭
   ↓ (로딩 스피너 3초)
5. 성공 토스트 메시지 + 자동 로그인
   ↓
6. 대시보드로 이동
```

**각 단계별 UI:**
- Step 2: 버튼 hover 시 scale 1.05
- Step 3: Input focus 시 레이블 위로 이동
- Step 4: 버튼 비활성화, 스피너 표시
- Step 5: 녹색 토스트 "가입 완료!" (3초 후 자동 사라짐)

---

## 애니메이션 & 트랜지션

```
페이지 전환: 300ms ease-in-out, fade + 약간 슬라이드
버튼 hover: 150ms, scale 1.05
모달 열기/닫기: 250ms fade-in/out
```

---

## 접근성 체크리스트

- [ ] 모든 이미지에 alt 텍스트
- [ ] 키보드 네비게이션 지원 (Tab, Enter, ESC)
- [ ] 포커스 인디케이터 명확히 표시
- [ ] 색상 대비 4.5:1 이상 (WCAG AA)
- [ ] 버튼/링크에 aria-label 추가
- [ ] 스크린 리더 테스트 완료

---

## 선택자 명명 규칙 (CSS 클래스/ID)

> **중요:** UI 수정을 쉽게 하려면 일관된 선택자 명명이 필수입니다!

### 권장 명명 패턴

**레이아웃 섹션:**
```
header.main-header / #app-header
aside.sidebar / #main-sidebar
main.content / #main-content
footer.main-footer / #app-footer
```

**컴포넌트:**
```
.card (기본)
.card.recent-projects (특정 카드)
.card.user-profile (사용자 프로필 카드)

.btn (버튼)
.btn-primary / .btn-secondary

.form-group (폼 그룹)
.input-field (입력 필드)
```

**페이지별 구분:**
```
.dashboard-page (대시보드 페이지 전체)
.profile-page (프로필 페이지 전체)
```

### 💡 Tip: modification.md 활용
나중에 UI 수정 시 브라우저 개발자 도구에서 이 선택자를 복사해서 `modification.md`에 붙여넣으면 Claude가 정확히 해당 요소만 수정합니다!

---

## 참고 자료

- Laws of UX: https://lawsofux.com/
- Material Design: https://material.io/design
- Human Interface Guidelines: https://developer.apple.com/design/human-interface-guidelines/
