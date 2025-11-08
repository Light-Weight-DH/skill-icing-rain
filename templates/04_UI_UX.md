# UI/UX 명세

<!-- 웹 애플리케이션의 UI/UX 디자인 및 사용자 경험 가이드 -->
<!-- 주의: 이 파일은 web-app 타입 프로젝트에만 해당됩니다 -->

---

## 디자인 시스템

### 색상 팔레트

```css
/* Primary Colors */
--primary-100: #       /* 가장 밝은 */
--primary-200: #
--primary-300: #
--primary-400: #
--primary-500: #       /* 메인 색상 */
--primary-600: #
--primary-700: #
--primary-800: #
--primary-900: #       /* 가장 어두운 */

/* Secondary Colors */
--secondary-500: #

/* Neutral Colors */
--gray-50: #
--gray-100: #
--gray-200: #
--gray-500: #
--gray-900: #

/* Semantic Colors */
--success: #
--warning: #
--error: #
--info: #

/* Background */
--bg-primary: #
--bg-secondary: #

/* Text */
--text-primary: #
--text-secondary: #
--text-disabled: #
```


---

### 타이포그래피

```css
/* Headings */
--font-family-heading:
--font-size-h1:
--font-size-h2:
--font-size-h3:

/* Body */
--font-family-body:
--font-size-base:
--font-size-sm:
--font-size-lg:

/* Code */
--font-family-mono:
```


---

### Spacing

```css
--spacing-xs: 4px
--spacing-sm: 8px
--spacing-md: 16px
--spacing-lg: 24px
--spacing-xl: 32px
--spacing-2xl: 48px
```


---

### Border & Radius

```css
--border-width: 1px
--border-radius-sm: 4px
--border-radius-md: 8px
--border-radius-lg: 16px
--border-radius-full: 9999px
```


---

### Shadow

```css
--shadow-sm:
--shadow-md:
--shadow-lg:
```


---

## 레이아웃

### 전체 레이아웃 구조

```
┌─────────────────────────────────────┐
│            Header/Nav                │
├──────────┬──────────────────────────┤
│          │                          │
│ Sidebar  │      Main Content        │
│ (선택)   │                          │
│          │                          │
│          │                          │
├──────────┴──────────────────────────┤
│            Footer (선택)             │
└─────────────────────────────────────┘
```

### 반응형 브레이크포인트

```css
/* Mobile First */
--breakpoint-sm: 640px   /* Mobile */
--breakpoint-md: 768px   /* Tablet */
--breakpoint-lg: 1024px  /* Desktop */
--breakpoint-xl: 1280px  /* Large Desktop */
```


---

## 페이지별 명세

### 1. [페이지명 - 예: 홈 페이지]

**경로:** `/`

#### 레이아웃

```
┌─────────────────────────────────────┐
│  Header                              │
│  ├─ Logo                             │
│  ├─ Navigation Menu                  │
│  └─ User Menu                        │
├─────────────────────────────────────┤
│                                      │
│  Hero Section                        │
│  ├─ Title                            │
│  ├─ Description                      │
│  └─ CTA Button                       │
│                                      │
├─────────────────────────────────────┤
│                                      │
│  Main Content                        │
│  └─ [컨텐츠 설명]                    │
│                                      │
└─────────────────────────────────────┘
```

#### 주요 컴포넌트

**Header**
- Logo (클릭 시 홈으로)
- Navigation Menu
- User Avatar/Login Button

**Hero Section**
- 제목:
- 설명:
- CTA 버튼:

**Main Content**
<!-- 주요 콘텐츠 영역 설명 -->


#### 사용자 플로우

```
1. 페이지 진입
   ↓
2. Hero Section 확인
   ↓
3. CTA 버튼 클릭
   ↓
4. [다음 액션]
```

#### 상태 관리
- Loading State: (로딩 중일 때 표시할 내용)
- Empty State: (데이터 없을 때)
- Error State: (에러 발생 시)


---

### 2. [페이지명 - 예: 대시보드]

**경로:** `/dashboard`

#### 레이아웃

```
┌─────────────────────────────────────┐
│  Header                              │
├────────┬────────────────────────────┤
│        │                            │
│ Side   │  Dashboard Content         │
│ Nav    │  ├─ Stats Cards            │
│        │  ├─ Charts                 │
│ ├─ Menu│  └─ Recent Activity        │
│ ├─ Menu│                            │
│ └─ Menu│                            │
│        │                            │
└────────┴────────────────────────────┘
```

#### 주요 컴포넌트

**Sidebar**
- Menu Items:
  -
  -

**Stats Cards**
- Card 1: (예: 총 사용자 수)
- Card 2: (예: 오늘 방문자)
- Card 3:

**Charts**
<!-- 차트 종류 및 표시할 데이터 -->


#### 사용자 플로우


#### 상호작용
<!-- 사용자가 클릭하거나 상호작용할 수 있는 요소 -->


---

### 3. [페이지명]

**경로:**

#### 레이아웃


#### 주요 컴포넌트


#### 사용자 플로우


---

## 공통 컴포넌트

### Button

**Variants:**
- Primary: 주요 액션
- Secondary: 보조 액션
- Outline: 테두리만
- Ghost: 배경 없음
- Danger: 삭제 등 위험한 액션

**Sizes:**
- Small
- Medium (기본)
- Large

**States:**
- Default
- Hover
- Active
- Disabled
- Loading


---

### Input

**Types:**
- Text
- Email
- Password
- Number
- Textarea

**States:**
- Default
- Focus
- Error
- Disabled


---

### Modal/Dialog

**구조:**
```
┌─────────────────────────┐
│  [X] Title               │
├─────────────────────────┤
│                         │
│  Content                │
│                         │
├─────────────────────────┤
│  [Cancel]  [Confirm]    │
└─────────────────────────┘
```


---

### Card

**구조:**
```
┌─────────────────────────┐
│  Header                  │
├─────────────────────────┤
│                         │
│  Content                │
│                         │
├─────────────────────────┤
│  Footer (선택)           │
└─────────────────────────┘
```


---

## 사용자 경험 (UX)

### 로딩 상태
<!-- 데이터 로딩 중 사용자에게 보여줄 것 -->
- Skeleton Screen
- Spinner
- Progress Bar

### 빈 상태 (Empty State)
<!-- 데이터가 없을 때 -->
- 아이콘:
- 메시지: "아직 데이터가 없습니다"
- CTA: "새로 추가하기"

### 에러 상태
<!-- 에러 발생 시 -->
- 에러 메시지 표시
- 재시도 버튼
- 도움말 링크

### 성공 피드백
<!-- 작업 성공 시 -->
- Toast 알림
- Success 메시지
- 자동 redirect (필요시)


---

## 애니메이션 및 트랜지션

```css
--transition-fast: 150ms ease-in-out
--transition-base: 250ms ease-in-out
--transition-slow: 350ms ease-in-out
```

### 사용 예시
- 페이지 전환:
- 모달 열기/닫기:
- 드롭다운:
- 호버 효과:


---

## 접근성 (Accessibility)

### 체크리스트
- [ ] 키보드 네비게이션 지원
- [ ] 포커스 인디케이터
- [ ] ARIA 레이블 사용
- [ ] 적절한 색상 대비 (WCAG AA 이상)
- [ ] Alt 텍스트 제공
- [ ] 스크린 리더 지원


---

## 다크 모드 (선택)

### 색상 변경
```css
[data-theme="dark"] {
  --bg-primary: #
  --text-primary: #
  /* ... */
}
```


---

## 참고 이미지 및 와이어프레임

<!-- assets/images/ 폴더에 UI 스케치, 와이어프레임, 디자인 시안 저장 -->

- 메인 화면: [assets/images/main-wireframe.png](../assets/images/main-wireframe.png)
- 대시보드: [assets/images/dashboard-wireframe.png](../assets/images/dashboard-wireframe.png)
-


---

## 참고 디자인 시스템

<!-- 영감을 받거나 참고한 디자인 시스템 -->
-
-

