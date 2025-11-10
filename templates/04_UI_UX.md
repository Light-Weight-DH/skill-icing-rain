# UI/UX 명세

<!-- 웹 애플리케이션의 UI/UX 디자인을 wireframe과 설명으로 정리 -->
<!-- 주의: 이 파일은 web-app 타입 프로젝트에만 해당됩니다 -->

---

## 디자인 원칙 (Laws of UX 기반)

<!-- https://lawsofux.com/ 참고 -->

### 적용할 UX 법칙
<!-- 프로젝트에 적용할 주요 UX 원칙을 선택하세요 -->

**선택한 법칙:**
- [ ] **Hick's Law**: 선택지가 많을수록 결정 시간이 길어짐 → 선택지 최소화
- [ ] **Miller's Law**: 단기 기억은 7±2개 항목만 유지 → 정보 그룹화
- [ ] **Fitts's Law**: 클릭 대상이 크고 가까울수록 빠름 → 버튼 크기 충분히
- [ ] **Jakob's Law**: 사용자는 다른 사이트의 UX에 익숙함 → 익숙한 패턴 사용
- [ ] **Law of Proximity**: 가까이 있는 요소들은 관련있다고 인식 → 그룹화
- [ ] **Aesthetic-Usability Effect**: 아름다운 디자인이 사용성 좋다고 인식 → 시각적 완성도
- [ ] **Parkinson's Law**: 작업은 주어진 시간만큼 확장됨 → 명확한 마감 표시


---

## 디자인 시스템

### 색상
```css
Primary: #
Secondary: #
Accent: #
Background: #
Text: #
```

### 타이포그래피
- Heading:
- Body:
- Code/Mono:

### Spacing
- 기본 간격: 8px 단위 사용
- 주요 간격: 8px, 16px, 24px, 32px, 48px

---

## 페이지별 디자인

### 페이지 1: [페이지명]

#### Wireframe
<!-- assets/images/ 폴더에 wireframe 이미지를 저장하고 링크하세요 -->
![Wireframe](../assets/images/page1-wireframe.png)

<!-- 또는 간단한 ASCII art로 표현 -->
```
┌─────────────────────────────────────┐
│  Header                              │
│  [Logo]  [Nav]          [User]      │
├─────────────────────────────────────┤
│                                      │
│  Hero Section                        │
│  ├─ Title                            │
│  ├─ Description                      │
│  └─ [CTA Button]                     │
│                                      │
├─────────────────────────────────────┤
│  Main Content                        │
│  [Content Area]                      │
│                                      │
└─────────────────────────────────────┘
```

#### 디자인 설명
<!-- wireframe을 보며 각 영역을 설명하세요 -->

**Header 영역:**
- 위치: 화면 최상단, 고정 (스크롤 시에도 유지)
- 구성:
  - 왼쪽: 로고 (클릭 시 홈으로)
  - 중앙: 주요 네비게이션 메뉴 (3-5개)
  - 오른쪽: 사용자 아바타 또는 로그인 버튼
- 스타일:
  - 배경: 흰색 또는 투명
  - 높이: 64px
  - 그림자: 약한 하단 그림자

**Hero Section:**
- 위치: Header 바로 아래
- 구성:
  - 제목: 큰 폰트 (48px), 굵게
  - 부제목: 설명 텍스트 (18px)
  - CTA 버튼: 주요 액션 버튼 (예: "시작하기")
- 스타일:
  - 배경: 그라데이션 또는 이미지
  - 패딩: 상하 80px

**Main Content:**
- 실제 콘텐츠가 표시되는 영역
- (구체적으로 설명)


#### 동작 기능 설명
<!-- 사용자가 어떻게 상호작용하는지 설명하세요 -->

**Header 네비게이션:**
- 메뉴 항목 hover 시: 색상 변경 (Primary 색상)
- 현재 페이지 메뉴는 밑줄 표시
- 모바일: 햄버거 메뉴로 전환

**CTA 버튼:**
- 클릭 시: /signup 페이지로 이동
- Hover: 버튼 확대 (scale 1.05)
- 로딩 중: 스피너 표시

**스크롤 동작:**
- Header는 항상 고정
- 스크롤 다운: Header에 그림자 추가
- 부드러운 스크롤 애니메이션


#### 반응형 (모바일)
<!-- 모바일에서 어떻게 변경되는지 -->

- 768px 이하:
  - 네비게이션 → 햄버거 메뉴
  - Hero 제목 폰트 크기 → 32px
  - 패딩 축소


---

### 페이지 2: [페이지명]

#### Wireframe
![Wireframe](../assets/images/page2-wireframe.png)

```
┌─────────────────────────────────────┐
│  Header                              │
├─────────┬───────────────────────────┤
│ Sidebar │  Content Area             │
│         │                           │
│ [Nav]   │  [Main Content]           │
│ [Nav]   │                           │
│ [Nav]   │                           │
│         │                           │
└─────────┴───────────────────────────┘
```

#### 디자인 설명

**Sidebar:**
- 위치: 왼쪽 고정
- 너비: 240px
- 구성:
  - 메뉴 항목들
  - 하단: 설정 버튼
- 스타일:
  - 배경: 연한 회색
  - 선택된 메뉴: Primary 색상 배경


**Content Area:**
- 위치: Sidebar 오른쪽
- 구성:
  - (구체적으로 설명)


#### 동작 기능 설명

**Sidebar 메뉴:**
- 클릭 시: Content Area 내용 변경 (페이지 새로고침 없이)
- 활성 메뉴: 하이라이트 표시


**Content Area:**
- (구체적인 동작 설명)


---

### 페이지 3: [필요한 만큼 추가]

...


---

## 공통 컴포넌트

### Button

**디자인:**
- Primary: 배경색 Primary, 텍스트 흰색, border-radius 8px
- Secondary: 배경 투명, 테두리 Primary, 텍스트 Primary
- 크기: 높이 40px (기본), padding 좌우 24px

**동작:**
- Hover: 약간 어두워짐 (opacity 0.9)
- Active: scale 0.98
- Disabled: opacity 0.5, 클릭 불가


### Input Field

**디자인:**
- 테두리: 1px solid 회색
- border-radius: 4px
- 높이: 40px
- padding: 12px

**동작:**
- Focus: 테두리 Primary 색상, 약한 그림자
- Error: 테두리 빨간색, 하단에 에러 메시지 표시


### Modal

**디자인:**
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

**동작:**
- 배경: 반투명 검은색 (opacity 0.5)
- 애니메이션: 페이드 인/아웃
- ESC 키: 닫기
- 배경 클릭: 닫기


---

## UX 플로우

### 주요 사용자 플로우 1: [예: 회원가입]

```
1. 메인 페이지 진입
   ↓
2. "시작하기" 버튼 클릭
   ↓
3. 회원가입 폼 표시
   ↓ (입력 중 실시간 검증)
4. "가입 완료" 버튼 클릭
   ↓ (로딩 표시)
5. 완료 메시지 + 자동 로그인
   ↓
6. 대시보드로 이동
```

**각 단계별 UI 설명:**
- Step 2: 버튼 hover 시 확대 효과
- Step 3: 각 필드마다 placeholder 제공, 포커스 시 레이블 위로 이동
- Step 4: 버튼 비활성화, 스피너 표시
- Step 5: 성공 토스트 메시지 (3초 후 자동 사라짐)


---

## 애니메이션 & 트랜지션

### 페이지 전환
- Duration: 300ms
- Easing: ease-in-out
- 효과: 페이드 + 약간의 슬라이드

### 버튼 Hover
- Duration: 150ms
- 효과: scale 1.05, 색상 변경

### 모달 열기/닫기
- Duration: 250ms
- 효과: fade-in/out + scale

---

## 접근성 (Accessibility)

### 체크리스트
- [ ] 모든 이미지에 alt 텍스트
- [ ] 키보드만으로 전체 네비게이션 가능
- [ ] 포커스 인디케이터 명확히 표시
- [ ] 색상 대비 WCAG AA 기준 충족 (최소 4.5:1)
- [ ] ARIA 레이블 사용
- [ ] 스크린 리더 테스트

---

## 참고 이미지

<!-- assets/images/ 폴더에 저장한 이미지들 -->

- 메인 페이지 wireframe: [page1-wireframe.png](../assets/images/page1-wireframe.png)
- 대시보드 wireframe: [page2-wireframe.png](../assets/images/page2-wireframe.png)
- UI 참고 디자인: [reference-design.png](../assets/images/reference-design.png)


---

## 디자인 참고 자료

<!-- 영감을 받은 사이트나 디자인 시스템 -->
-
-

---

## Notes

<!-- 추가 고려사항이나 아이디어 -->
-

