---
name: simsool-uiux-guide
description: SimSool UIUX Guide v1.0 마스터 디자인 시스템 전체 명세. #FCFDFE 소프트 서페이스, 단색(Solid) 컬러 매트릭스, Pretendard 타이포그래피 스케일(최소 13px 하한선) 및 국·영문·코드 자간 분리, 12컬럼 B-Contents 그리드 및 8pt 간격, 5단계 엘리베이션 및 모션 이징, 버튼 5단계 크기·22px 스테퍼·28px 토글·탭, 54px 인풋 7대 상태·48px 아코디언, 22px 체크박스/라디오·커머스 배지 7종·별점, 플로팅 에디터 툴바·미디어 캐러셀 바·52px 스쿼클 아이콘, 360px 모달·375×375 정방형 카드, WCAG 2.1 대비 기준, UX 라이팅 Do/Don't 및 CSS/JSON 디자인 토큰을 모두 포함한다.
---

# SimSool UIUX Guide v1.0 — Master Design System Specification

> "여러 번 반복 학습하세요. UX 디자인은 시각보다 사용성이다."

---

## 0. 오버뷰 & 핵심 시각 원칙 (Overview & Core Principles)

1. **Soft White Surface (`#FCFDFE`)**:
	- 눈부심과 피로를 유발하는 순백색(`#FFFFFF`)을 배제하고 기본 카드·사이드바·모달·인풋 배경 서페이스로 **`#FCFDFE`**(`--bg-surface`)를 사용한다.
	- 앱 전체 캔버스 배경은 **`#F1F4F9`**(`--bg-app`), 보조 컨테이너 및 셀 배경은 **`#F5F7FB`**(`--bg-subtle`), 다크 프리뷰 카드는 **`#0F172A`**(`--bg-dark-card`)를 사용한다.
2. **단색(Solid) 컬러 전용 (Zero Gradients)**:
	- 배경, 버튼, 배지, 구분선, 스와치 등 모든 UI 요소에 그라디언트 효과를 일절 사용하지 않고 명확한 **단색(Solid)** 컬러 토큰만 사용한다.
3. **글로우(Glow) 효과 배제**:
	- 로고나 CTA 버튼에 컬러 번짐(Glow) 그림자를 넣지 않고, 중립적인 슬레이트 기반 엘리베이션 그림자(`--shadow-xs` ~ `--shadow-lg`)만 사용한다.
4. **아이콘 기반 사이드바 네비게이션 (`292px`)**:
	- 사이드바 폭은 `292px` 고정(`sticky`, `100vh`)이며, `01`, `02` 같은 숫자 인덱스 대신 직관적인 **Phosphor Icons (`ph-bold`)** 18px 아이콘과 레이블(`14px`) 조합을 사용한다.
5. **스펙 태그 (`.spec-tag`)**:
	- 원색 핑크 배지 대신 주변 UI와 자연스럽게 어우러지는 중립 슬레이트 배지(`#F5F7FB` 배경, `1px solid #DCE0E8` 보더, `#434A5B` 텍스트, `13px`, `padding: 4px 10px`, `border-radius: 6px`)를 사용한다.

---

## 1. 타이포그래피 스케일 & 국문·영문·코드 자간 분리 (Pretendard Typography)

### 1.1 단일 폰트 패밀리
- 국문, 영문, 숫자, 코드(`--font-sans`, `--font-mono`) 모두 **`Pretendard`**를 사용한다.
	- `--font-sans: "Pretendard", -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif;`
	- `--font-mono: "Pretendard", -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif;`
- 코드와 수치 데이터(`code`, `pre`, 카운터, 명도 대비율 등)에는 반드시 `font-variant-numeric: tabular-nums`와 `letter-spacing: 0em`을 적용한다.
- 국문 본문 및 타이틀에는 어절 중간 끊김을 방지하기 위해 `word-break: keep-all`을 기본 적용한다.
- 사용 굵기(Weight): `Regular 400`, `Medium 500`, `SemiBold 600`, `Bold 700`, `ExtraBold 800`.

### 1.2 타이포그래피 크기 스케일 (최소 하한선 13px · 소수점 `.5px` 폐기)
- 가독성을 해치는 `9px ~ 12px` 초소형 텍스트와 `.5px` 단수를 전면 금지한다.
- UI 보조 설명 기본 크기는 **`14px`**(`--fs-label`), 배지·상단 고정 라벨·코드 토큰의 최소 하한선은 **`13px`**(`--fs-caption`)로 유지한다.

| Token | Role | Size / Line-Height | Weight | KR 자간 (`--ls-kr-*`) | EN 자간 (`--ls-en-*`) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `--fs-display` | Display (히어로 대제목) | `40px / 130% (1.3)` | `800` | `-0.03em` (`--ls-kr-display`) | `-0.015em` (`--ls-en-display`) |
| `--fs-h1` | Headline 1 | `32px / 135% (1.35)` | `800` | `-0.03em` (`--ls-kr-display`) | `-0.015em` (`--ls-en-display`) |
| `--fs-h2` | Headline 2 | `28px / 135% (1.35)` | `700` | `-0.02em` (`--ls-kr-title`) | `-0.01em` (`--ls-en-title`) |
| `--fs-h3` | Headline 3 | `24px / 140% (1.4)` | `700` | `-0.02em` (`--ls-kr-title`) | `-0.01em` (`--ls-en-title`) |
| `--fs-title-lg` | Title Large (섹션·모달 헤더) | `20px / 140% (1.4)` | `800` | `-0.02em` (`--ls-kr-title`) | `-0.01em` (`--ls-en-title`) |
| `--fs-title-md` | Title Medium (카드 타이틀) | `18px / 145% (1.45)` | `700~800` | `-0.02em` (`--ls-kr-title`) | `-0.01em` (`--ls-en-title`) |
| `--fs-body-lg` | Body Large (리드 본문) | `16px / 160% (1.6)` | `400~500` | `-0.015em` (`--ls-kr-body`) | `0em` (`--ls-en-body`) |
| `--fs-body-md` | Body Medium (인풋·버튼·기본 본문) | `15px / 155% (1.55)` | `500~600` | `-0.015em` (`--ls-kr-body`) | `0em` (`--ls-en-body`) |
| `--fs-label` | Label / Sub-UI (사이드바·카드 보조 설명) | `14px / 150% (1.5)` | `600` | `-0.005em` (`--ls-kr-caption`) | `0em` (`--ls-en-body`) |
| `--fs-caption` | Caption Min (배지·고정 라벨·코드 하한선) | `13px / 145% (1.45)` | `600~700` | `-0.005em` (`--ls-kr-caption`) | `0em` / Caps `+0.05em` |

### 1.3 국문 vs 영문 vs 코드 자간 분리 규칙
1. **국문 (Korean Hangul)**: 네모꼴 음절 블록 밀도가 높아 대제목에서는 `-0.03em`, 타이틀 `-0.02em`, 본문 `-0.015em`로 조여 시선 분산을 막고, `13~14px` 소형 크기에서는 받침 뭉침 방지를 위해 `-0.005em`로 풀어준다.
2. **영문 (English Latin)**: 소문자 비례폭(Proportional Kerning) 유지를 위해 본문은 `0em`(`--ls-en-body`), 영문 타이틀은 `-0.01em`(`--ls-en-title`), 대문자 캡션(`FOUNDATIONS`, `JEWELRY` 등)은 `+0.05em`(`--ls-en-caps`)을 적용한다.
3. **코드 & 수치 (Monospace / Numeric)**: 토큰명(`--shadow-xs`), HEX(`#FCFDFE`), 치수(`54px`, `375×375`)는 음수 자간을 상속하지 않도록 `letter-spacing: 0em`(`--ls-mono`)과 `tabular-nums`를 강제한다.

---

## 2. 컬러 시스템 & 스와치 매트릭스 (Solid Color System)

### 2.1 Primary & Brand / Semantic Solid Tokens
- **Primary Blue Ramp**:
	- `50`: `#EBF3FF` | `100`: `#D1E4FF` | `200`: `#A6CAFF` | `300`: `#73ACFF` | `400`: `#3B89FF`
	- `500 (Main)`: **`#0062FF`** | `600 (Hover)`: **`#0051D5`** | `700`: `#003FA8` | `800`: `#002E7A` | `900`: `#001D4D`
- **Brand & Semantic Accents (4 Solid Bars + Status)**:
	- **Primary Brand Blue**: `#0062FF` (Hover `#0051D5`, Soft `#EBF3FF`) — 주요 CTA, 활성 탭, 포커스 링, 선택 컨트롤
	- **Accent Electric Violet**: `#5200FF` (Hover `#4100CC`, Soft `#F3EBFF`, `100` `#E2CEFF`)
	- **Secondary Cyan Highlight**: `#09B1EC` (Hover `#0284C7`, Soft `#E0F2FE`)
	- **Positive / Success Emerald**: `#03B666` (Hover `#029352`, Soft `#E8FBF2`, `100` `#C2F5DD`) — 입력 완료 검증, 성공 토스트, 사은품 배지
	- **Warning Amber**: `#FF9500` (Hover `#D97706`, Soft `#FFF8EB`, `100` `#FFE8BF`)
	- **Danger / Critical Red**: `#FF3B30` (Hover `#E0281E`, Soft `#FFF1F0`, `100` `#FFDAD7`) — 필수 입력(`*`), 에러 보더, 파괴적 액션

### 2.2 16단계 그레이스케일 & `#FCFDFE` 서페이스 램프
- `Black`: `#08090C` | `950`: `#111318` | `900`: `#191C24` | `850`: `#222630` | `800`: `#2C313D` | `750`: `#373D4B` | `700`: `#434A5B` | `650`: `#51596C` | `600`: `#616A7E` | `550`: `#737C91` | `500`: `#868FA4` | `450`: `#9AA2B5` | `400`: `#B0B7C6` | `350`: `#C6CCD8` | `300`: `#DCE0E8` | `250`: `#EBEEF3` | `200`: `#F3F5F8` | `100`: `#F5F7FB` | `Surface`: **`#FCFDFE`**

### 2.3 시맨틱 텍스트·보더·다크 모드 토큰
- **Light Mode**:
	- Surface: `--bg-app: #F1F4F9`, `--bg-surface: #FCFDFE`, `--bg-subtle: #F5F7FB`, `--bg-elevated: #FCFDFE`
	- Text: `--text-primary: #111318`, `--text-secondary: #434A5B`, `--text-tertiary: #737C91`, `--text-disabled: #9AA2B5`, `--text-inverse: #FCFDFE`
	- Border: `--border-subtle: #E6EAF2`, `--border-default: #DCE0E8`, `--border-strong: #B0B7C6`, `--border-focus: #0062FF`
- **Dark Mode (`[data-theme="dark"]`)**:
	- Surface: `--bg-app: #0B0D13`, `--bg-surface: #131722`, `--bg-subtle: #1A1F2E`, `--bg-elevated: #1E2436`
	- Text: `--text-primary: #F3F5F8`, `--text-secondary: #B0B7C6`, `--text-tertiary: #737C91`, `--text-disabled: #51596C`, `--text-inverse: #111318`
	- Border: `--border-subtle: #222630`, `--border-default: #2C313D`, `--border-strong: #434A5B`

### 2.4 14 Hue × 9 Lightness (`900–100`) 스펙트럼 매트릭스
- **Red**: `#7F1D1D`, `#991B1B`, `#B91C1C`, `#DC2626`, `#EF4444`, `#F87171`, `#FCA5A5`, `#FECACA`, `#FEE2E2`
- **Coral**: `#7C2D12`, `#9A3412`, `#C2410C`, `#EA580C`, `#F97316`, `#FB923C`, `#FDBA74`, `#FED7AA`, `#FFEDD5`
- **Amber**: `#78350F`, `#92400E`, `#B45309`, `#D97706`, `#F59E0B`, `#FBBF24`, `#FCD34D`, `#FDE68A`, `#FEF3C7`
- **Yellow**: `#713F12`, `#854D0E`, `#A16207`, `#CA8A04`, `#EAB308`, `#FACC15`, `#FDE047`, `#FEF08A`, `#FEF9C3`
- **Lime**: `#365314`, `#3F6212`, `#4D7C0F`, `#65A30D`, `#84CC16`, `#A3E635`, `#BEF264`, `#D9F99D`, `#ECFCCB`
- **Green**: `#14532D`, `#166534`, `#15803D`, `#16A34A`, `#22C55E`, `#4ADE80`, `#86EFAC`, `#BBF7D0`, `#DCFCE7`
- **Emerald**: `#064E3B`, `#065F46`, `#047857`, `#059669`, `#03B666`, `#34D399`, `#6EE7B7`, `#A7F3D0`, `#D1FAE5`
- **Teal**: `#134E4A`, `#115E59`, `#0F766E`, `#0D9488`, `#14B8A6`, `#2DD4BF`, `#5EEAD4`, `#99F6E4`, `#CCFBF1`
- **Cyan**: `#164E63`, `#155E75`, `#0E7490`, `#0891B2`, `#09B1EC`, `#38BDF8`, `#67E8F9`, `#A5F3FC`, `#CFFAFE`
- **Sky**: `#0C4A6E`, `#075985`, `#0369A1`, `#0284C7`, `#0EA5E9`, `#38BDF8`, `#7DD3FC`, `#BAE6FD`, `#E0F2FE`
- **Blue**: `#001D4D`, `#002E7A`, `#003FA8`, `#0051D5`, `#0062FF`, `#3B89FF`, `#73ACFF`, `#A6CAFF`, `#D1E4FF`
- **Indigo**: `#1E1B4B`, `#312E81`, `#3730A3`, `#4338CA`, `#6366F1`, `#818CF8`, `#A5B4FC`, `#C7D2FE`, `#E0E7FF`
- **Violet**: `#2E1065`, `#4C1D95`, `#5B21B6`, `#6D28D9`, `#5200FF`, `#8B5CF6`, `#A78BFA`, `#C4B5FD`, `#EDE9FE`
- **Pink**: `#831843`, `#9D174D`, `#BE185D`, `#DB2777`, `#EC4899`, `#F472B6`, `#F9A8D4`, `#FBCFE8`, `#FCE7F3`

---

## 3. 반응형 12컬럼 그리드, B-Contents & 8pt 간격 체계

### 3.1 B-Contents 레이아웃 & 그리드 규격
- **Max-Width**: `1360px`, 기본 그리드 거터(Gutter): **`16px`**, Flex 컨테이너(`Flex Direction: Row / Wrap`).
- **디바이스별 컬럼 분할**:
	- **Desktop (12 Cols)**: `span 4` (3등분 B-Contents 카드), `span 6` (2등분 Half Column 카드)
	- **Tablet (6 Cols)**: `span 6` (2열 배치)
	- **Mobile (4 Cols · 375px 기준)**: `span 12` (단일 컬럼 전체 폭 배치)

### 3.2 8pt 공간 간격 스케일 (Spatial System)
- `--sp-1` (**`4px`**): 아이콘-텍스트 최소 간격
- `--sp-2` (**`8px`**): 인접 칩/배지 그룹 간격
- `--sp-3` (**`12px`**): 폼 필드·리스트 간격
- `--sp-4` (**`16px`**): 기본 그리드 거터
- `--sp-6` (**`24px`**): 카드 및 모달 내부 표준 패딩
- `--sp-8` (**`32px`**): 컴포넌트 블록 간격 (`48px` 섹션 간 여백)

---

## 4. 엘리베이션(그림자) 5단계, 곡률 & 모션 이징

### 4.1 엘리베이션 5단계 (No Colored Glow)
1. **Level 1 (`--shadow-xs`)**: `0 1px 2px rgba(15, 23, 42, 0.04)` — 보조 버튼, 기본 셀
2. **Level 2 (`--shadow-sm`)**: `0 4px 20px -2px rgba(15, 23, 42, 0.05), 0 2px 6px -1px rgba(15, 23, 42, 0.03)` (Dark: `0 4px 12px rgba(0,0,0,0.35)`) — 표준 콘텐츠 카드
3. **Level 3 (`--shadow-md`)**: `0 10px 28px rgba(15, 23, 42, 0.08), 0 2px 6px rgba(15, 23, 42, 0.04)` (Dark: `0 12px 32px rgba(0,0,0,0.45)`) — 플로팅 툴바, 팝오버
4. **Level 4 (`--shadow-lg`)**: `0 20px 48px rgba(15, 23, 42, 0.12), 0 4px 12px rgba(15, 23, 42, 0.06)` (Dark: `0 24px 56px rgba(0,0,0,0.6)`) — 모달 다이얼로그, 토스트
5. **Primary Shadow (`--shadow-primary`)**: `0 1px 2px rgba(15, 23, 42, 0.04)` (글로우 없는 단색 경계 강조) + 포커스 링 `--focus-ring: 0 0 0 3.5px rgba(0, 98, 255, 0.18)`

### 4.2 곡률 체계 (Border Radius Scale)
- **`6px`** (`--r-xs`): 22px 체크박스, 스테퍼 증감 버튼, 스펙 태그, XS 버튼
- **`8px`** (`--r-sm`): SM 버튼, 플로팅 툴바 버튼
- **`10px`**: 표준 MD 버튼, 세그먼트 컨트롤
- **`12px`** (`--r-md`): 54px 인풋 필드, LG 버튼, 아코디언, 플로팅 툴바
- **`16px`** (`--r-lg`): 52×52px 스쿼클 앱 아이콘
- **`20px`** (`--r-xl`): 표준 콘텐츠 카드 (`375×375` 카드 등)
- **`24px`** (`--r-2xl`): 모달 다이얼로그 팝업, 히어로 배너
- **`9999px`** (`--r-full`): 커머스 배지, 28px 토글 스위치, 상세보기 필(Pill) 버튼

### 4.3 모션 이징 커브 (Motion Easing)
- **Standard Easing (`--ease-standard`)**: `cubic-bezier(0.4, 0, 0.2, 1)` — 기본 상태 전환 (`240ms`, 빠른 호버 `150ms`)
- **Out Expo (`--ease-out-expo`)**: `cubic-bezier(0.16, 1, 0.3, 1)` — 부드러운 감속 진입
- **Spring Overshoot (`--ease-spring`)**: `cubic-bezier(0.34, 1.56, 0.64, 1)` — 토글 스위치 썸 이동 및 인터랙티브 배지 탄성 전환 (`220ms`)

---

## 5. 버튼 위계, 수량 스테퍼(22px), 토글 스위치(28px) & 카테고리 탭

### 5.1 버튼 종류 (Button Variants)
- **Primary (`.btn-primary`)**: 배경 `#0062FF`, 텍스트 `#FCFDFE`, 호버 `#0051D5`, 액티브 `scale(0.98)`
- **Primary Focus (`.btn-primary.is-focus`)**: `box-shadow: 0 0 0 3.5px rgba(0, 98, 255, 0.18)`
- **Secondary (`.btn-secondary`)**: 배경 `#FCFDFE`, 보더 `1px solid #DCE0E8`, 텍스트 `#111318`, 호버 시 배경 `#F5F7FB` 및 보더 `#B0B7C6`
- **Soft Tint (`.btn-soft`)**: 배경 `#EBF3FF`, 텍스트 `#0062FF`
- **Tertiary Ghost (`.btn-ghost`)**: 투명 배경, 텍스트 `#434A5B`, 호버 시 `#F5F7FB`
- **Danger (`.btn-danger`)**: 배경 `#FF3B30`, 텍스트 `#FCFDFE`
- **Disabled (`:disabled`)**: 배경 `#EBEEF3`, 텍스트 `#9AA2B5`, 보더 `#DCE0E8`, `cursor: not-allowed`
- **Pill Secondary**: `border-radius: 9999px`, `padding: 0 16px` (`상세보기 →`)

### 5.2 버튼 5단계 크기 규격 (Button Size Scale)
- **Button XS (`.btn-xs`)**: 높이 **`30px`**, 좌우 패딩 `10px`, 폰트 `13px`, 곡률 `6px`
- **Button SM (`.btn-sm`)**: 높이 **`36px`**, 좌우 패딩 `14px`, 폰트 `14px`, 곡률 `8px`
- **Button MD (`.btn-md`, 표준)**: 높이 **`44px`**, 좌우 패딩 `18px`, 폰트 `15px`, 곡률 `10px` (최소 터치 타겟 `44×44px` 충족)
- **Button LG (`.btn-lg`)**: 높이 **`52px`**, 좌우 패딩 `24px`, 폰트 `16px`, 곡률 `12px`
- **Button XL (`.btn-xl`)**: 높이 **`60px`**, 좌우 패딩 `28px`, 폰트 `18px`, 곡률 `14px`

### 5.3 수량 스테퍼 (`22px` Quantity Stepper: `- 999 +`)
- 컨테이너(`.stepper-group`): `padding: 4px 8px`, `border-radius: 8px`, `1px solid #DCE0E8`, 배경 `#FCFDFE`.
- 증감 버튼(`.stepper-btn`): **`22×22px`**, `border-radius: 6px`, 배경 `#F5F7FB`, 호버 시 배경 `#0062FF` + 텍스트 `#FCFDFE`.
- 수량 텍스트(`.stepper-val`): `14px`, Weight `700`, `tabular-nums`, `min-width: 34px`, 가운데 정렬.

### 5.4 토글 스위치 (`28px` Toggle Switch)
- 트랙(`.toggle-track`): **`50×28px`**, `border-radius: 9999px`, OFF 배경 `#DCE0E8`, ON 배경 `#0062FF`, 내부 패딩 `3px`.
- 썸(`.toggle-thumb`): **`22×22px`**, 원형(`50%`), 배경 `#FCFDFE`, ON 상태에서 `transform: translateX(22px)`, 이징 `cubic-bezier(0.34, 1.56, 0.64, 1)` (`220ms`).

### 5.5 세그먼트 & 텍스트 카테고리 탭 (`JEWELRY / TRAVEL / MAN / WOMEN`)
- **Segmented Bar**: 컨테이너 배경 `#F5F7FB`, 패딩 `4px`, 곡률 `10px`, 활성 탭은 배경 `#FCFDFE` + `--shadow-xs` + 텍스트 `#111318`.
- **Text Tabs**: 하단 보더 `1px solid #DCE0E8`, 활성 탭은 텍스트 `#0062FF` + 하단 `2px solid #0062FF` 인디케이터, 영문 대문자 자간 `+0.05em`.

---

## 6. 54px 인풋 필드 상태 가이드 & 48px 접이식 아코디언

### 6.1 54px 플로팅/고정 라벨 인풋 (`.ref-input-box`)
- **치수 규격**: 높이 **`54px`**, 패딩 `7px 14px`, 곡률 **`12px`**, 상단 고정 라벨(`13px`, Weight `700`, 필수 `*` `#FF3B30`) + 하단 입력 컨트롤(`15px`, Weight `600`) 2단 배치.
- **클리어 버튼 (`.ref-input-clear`)**: 우측 상단 `20×20px` 원형 버튼 (`#DCE0E8` 배경, 호버 시 `#434A5B` 배경 + `#FCFDFE` 아이콘).
- **7대 상태 명세**:
	1. **DEFAULT (기본)**: 배경 `#FCFDFE`, 보더 `1.5px solid #DCE0E8`, 라벨 `#737C91`, 플레이스홀더 `#9AA2B5` (`아이디 또는 이메일`).
	2. **HOVER (마우스 오버)**: 배경 `#FCFDFE`, 보더 `1.5px solid #B0B7C6`.
	3. **TYPING (입력 중)**: 배경 `#FCFDFE`, 보더 `1.5px solid #0062FF`, 포커스 링 `0 0 0 3.5px rgba(0, 98, 255, 0.18)`, 우측 클리어(`X`) 버튼 노출.
	4. **FOCUSED (포커스)**: 배경 `#FCFDFE`, 보더 `1.5px solid #0062FF`, 포커스 링 유지, 상단 라벨 컬러 `#0062FF` 강조.
	5. **COMPLETED (입력 완료)**: 배경 `#FCFDFE`, 보더 `1.5px solid #434A5B`, 상태 태그 `#029352`(`COMPLETED`).
	6. **DISABLED (비활성화)**: 배경 `#F3F5F8`, 보더 `1.5px solid #E6EAF2`, 텍스트 `#9AA2B5`, `cursor: not-allowed`.
	7. **ERROR (에러)**: 배경 `#FFF1F0`, 보더 `1.5px solid #FF3B30`, 라벨 `#FF3B30`, 하단 에러 가이드 문구(`13px`, Weight `600`, `#FF3B30`: `"한글/영문/숫자 2~12자 이내로 다른 닉네임을 입력해 주세요."`) 동시 노출.

### 6.2 48px 접이식 아코디언 (`.accordion-item`)
- 헤더 높이 **`48px`**, 좌우 패딩 `18px`, 곡률 `12px`, 폰트 `15px` (Weight `600`).
- 펼침(`.open`) 상태에서 보더 `#0062FF`, 우측 화살표 아이콘 `rotate(180deg)` 및 `#0062FF` 컬러 전환, 본문 영역은 배경 `#F5F7FB`, 패딩 `14px 18px`, 폰트 `14px` 적용.

---

## 7. 22px 선택 컨트롤, 커머스 배지 7종 & 별점 레이팅

### 7.1 22×22px 체크박스 & 라디오 컨트롤
- **Checkbox (`.chk-box`)**: **`22×22px`**, 곡률 **`6px`**, 기본 보더 `2px solid #B0B7C6`, 배경 `#FCFDFE`.
	- Checked Active: 배경 `#0062FF`, 보더 `#0062FF`, 체크 아이콘 `#FCFDFE` (`13px`).
	- Disabled Checked: 배경 `#DCE0E8`, 보더 `#DCE0E8`, 체크 아이콘 `#737C91`.
- **Radio (`.rad-box`)**: **`22×22px`**, 원형(`50%`), 기본 보더 `2px solid #B0B7C6`, 배경 `#FCFDFE`.
	- Selected Active: 보더 `6.5px solid #0062FF`, 내부 코어 `#FCFDFE`.

### 7.2 커머스 배지 7종 (Outline & Solid Pill · 높이 `30px`)
- 공통 규격: 높이 **`30px`**, 좌우 패딩 `13px`, 곡률 `9999px`, 폰트 `13px` (Weight `700`), 호버 시 `translateY(-2px)`.

| 배지명 | Style 1: Soft Tint & Outline (배경 / 보더 / 텍스트) | Style 2: Solid Pill (배경 / 텍스트) |
| :--- | :--- | :--- |
| **셀링아이템** (Neutral) | `#FCFDFE` / `#B0B7C6` / `#434A5B` | `#616A7E` / `#FCFDFE` |
| **이벤트** (Event) | `#FFF5F5` / `#FCA5A5` / `#EF4444` | `#EF4444` / `#FCFDFE` |
| **베스트** (Best) | `#F5F7FB` / `#B0B7C6` / `#2C313D` | `#111318` / `#FCFDFE` |
| **재구매** (Repurchase) | `#EFF6FF` / `#93C5FD` / `#2563EB` | `#0062FF` / `#FCFDFE` |
| **한달사용기** (Monthly) | `#F5F3FF` / `#C4B5FD` / `#7C3AED` | `#6D28D9` / `#FCFDFE` |
| **사은품** (Gift) | `#ECFDF5` / `#6EE7B7` / `#059669` | `#16A34A` / `#FCFDFE` |
| **특가세일** (Sale) | `#FFF7ED` / `#FDBA74` / `#EA580C` | `#F97316` / `#FCFDFE` |

### 7.3 별점 레이팅 (Star Rating)
- 별 아이콘 크기 `22px`, 활성 별 컬러 `#F59E0B`(Gold), 비활성 별 컬러 `#DCE0E8`, 우측 평점 숫자는 `16px` (`tabular-nums`, 예: `4.0`).

---

## 8. 플로팅 에디터 툴바, 미디어 캐러셀 바 & 52×52px 퀵 메뉴 아이콘

1. **미디어 캐러셀 프로그레스 바 (`.media-carousel-bar`)**:
	- 슬라이드 카운터 필(`01 / 05 II`): 배경 `#111318`, 텍스트 `#FCFDFE`, 패딩 `4px 12px`, 곡률 `9999px`, `13px`.
	- 페이지네이션 도트(`.c-dot`): 기본 `8×8px` 원형(`#DCE0E8`), 활성 도트는 폭 **`22px`** 필(`#0062FF`).
	- 프로그레스 트랙: 높이 `4px`, 배경 `#DCE0E8`, 진행 바 `#0062FF`.
2. **플로팅 에디터 툴바 (`.floating-toolbar`)**:
	- 컨테이너: 배경 `#FCFDFE`, 보더 `1px solid #DCE0E8`, 곡률 `12px`, 패딩 `6px`, 그림자 `--shadow-md`.
	- 툴 버튼(`.tool-btn`): **`36×36px`**, 곡률 `8px`, 활성(`.active`) 시 배경 `#EBF3FF` + 텍스트 `#0062FF`, 구분선(`1px × 20px`).
3. **카테고리 퀵 메뉴 스쿼클 아이콘 (`52×52px`)**:
	- 스쿼클 박스(`.app-icon-squircle`): **`52×52px`**, 곡률 **`16px`**, 아이콘 `24px`, 하단 레이블 `13px` (Weight `600`).
	- 6대 단색 파스텔 조합:
		- 포인트: 배경 `#FEF3C7` / 아이콘 `#D97706`
		- 알림: 배경 `#FFEDD5` / 아이콘 `#EA580C`
		- 혜택: 배경 `#FFE4E6` / 아이콘 `#E11D48`
		- 글쓰기: 배경 `#E0E7FF` / 아이콘 `#4338CA`
		- 고객센터: 배경 `#DCFCE7` / 아이콘 `#15803D`
		- 보안인증: 배경 `#E0F2FE` / 아이콘 `#0284C7`

---

## 9. 모달 다이얼로그 & 375×375 정방형 콘텐츠 카드

1. **표준 모달 다이얼로그 (`.modal-preview-card`)**:
	- 최대 폭 **`360px`**, 곡률 **`24px`**, 내부 패딩 **`24px`**, 배경 `#FCFDFE`, 보더 `1px solid #DCE0E8`, 그림자 `--shadow-lg`.
	- 상단 아이콘 버블: `44×44px`, 곡률 `12px`, 배경 `#EBF3FF`, 아이콘 `#0062FF` (`22px`).
	- 타이틀 `18px~20px` (Weight `800`), 설명문 `15px` (`#434A5B`), 하단 액션 버튼 영역은 `2열 균등 분할`(`grid-template-columns: 1fr 1fr`, `gap: 10px`, `[취소]` + `[확인/참여하기]`).
2. **375×375 정방형 비율 콘텐츠 카드 (`.style-guide-card`)**:
	- 카드 곡률 **`20px`**, 배경 `#FCFDFE`, 보더 `1px solid #DCE0E8`, 호버 시 `translateY(-4px)` 및 `--shadow-md`.
	- 상단 1:1 정방형 썸네일 영역(`375×375` 비율, 높이 `210px` 프리뷰, 단색 다크 `#0F172A` 배경) + 하단 본문 패딩 `22px` + 타이틀(`18px`) + 보조 설명(`14px`) + 필 버튼(`상세보기 →`).

---

## 10. 웹/앱 접근성(WCAG 2.1) & 필수 체크리스트

1. **명도 대비 기준 (Contrast Ratio)**:
	- 일반 본문 텍스트: 최소 **`4.5 : 1`** 이상 (WCAG AA 통과, 예: `#FCFDFE` on `#0062FF` = **`5.08 : 1`** AA PASS).
	- 대형 텍스트(`18pt+` 또는 `14pt Bold+`) 및 UI 그래픽 보더: 최소 **`3.0 : 1`** 이상 (AA Large).
	- 최고 등급(AAA): **`7.0 : 1`** 이상.
2. **4대 필수 접근성 수칙**:
	- **최소 터치 타겟 (`44×44px`)**: 시각적 컨트롤이 `22px`(체크박스, 스테퍼)이더라도 클릭/터치 반응 영역은 최소 `44×44px` 이상 확보한다.
	- **비색상 상태 단서 병행**: 에러 상태는 빨간 보더(`#FF3B30`)뿐 아니라 상단 상태 태그(`ERROR`)와 하단 해결 안내 문구를 반드시 함께 제공한다.
	- **키보드 포커스 링 유지**: 키보드 탐색 사용자를 위해 `--focus-ring`(`0 0 0 3.5px rgba(0, 98, 255, 0.18)`)을 제거하지 않고 항상 표시한다.
	- **한글 어절 보호 및 자간 분리**: 국문은 `word-break: keep-all`과 음수 자간을 적용하되, 영문(`0em`)과 코드(`tabular-nums`, `0em`)는 자간을 분리한다.

---

## 11. UX 라이팅 & 컴포넌트 설계 Do / Don't 원칙

- **액션 버튼 레이블**:
	- **✓ DO**: 결과를 직관적으로 예측할 수 있는 동사 중심의 구체적 행동 명시 (예: **`[비밀번호 변경하기]`**, **`[내역 삭제하기]`**)
	- **✕ DON'T**: 파괴적 모달에서 `"정말 취소하시겠습니까? → [취소] / [확인]"`처럼 혼동을 주는 단답형·이중 부정 문구 사용 금지
- **입력 폼 라벨 설계**:
	- **✓ DO**: `54px` 인풋 상단에 고정 라벨(`닉네임 *`)을 상시 노출하여 타이핑 중이나 입력 완료 후에도 필드 역할을 즉시 식별하게 설계
	- **✕ DON'T**: Placeholder만 두고 Label을 생략하여 타이핑 시작과 동시에 입력 조건 안내가 사라지는 설계 금지

---

## 12. 디자인 토큰 익스포트 (CSS Custom Properties & W3C JSON)

### 12.1 CSS Variables (`tokens.css`)
```css
:root {
	/* Surface & Canvas (No Pure #FFFFFF) */
	--bg-app:     #F1F4F9;
	--bg-surface: #FCFDFE;
	--bg-subtle:  #F5F7FB;

	/* Solid Brand Colors */
	--color-primary-500: #0062FF;
	--color-violet-500:  #5200FF;
	--color-cyan-500:    #09B1EC;
	--color-emerald-500: #03B666;
	--color-danger-500:  #FF3B30;

	/* Typography Scale (Min Floor: 13px) */
	--fs-display:  40px;
	--fs-h1:       32px;
	--fs-h2:       28px;
	--fs-h3:       24px;
	--fs-title-lg: 20px;
	--fs-title-md: 18px;
	--fs-body-lg:  16px;
	--fs-body-md:  15px;
	--fs-label:    14px;
	--fs-caption:  13px;

	/* Script-Specific Letter-Spacing (KR vs EN vs Mono) */
	--ls-kr-display: -0.03em;
	--ls-kr-title:   -0.02em;
	--ls-kr-body:    -0.015em;
	--ls-kr-caption: -0.005em;
	--ls-en-title:   -0.01em;
	--ls-en-body:    0em;
	--ls-en-caps:    0.05em;
	--ls-mono:       0em;

	/* Component Sizing Specs */
	--size-control-sm: 22px; /* Checkbox, Radio, Stepper */
	--size-toggle-h:   28px; /* Toggle Switch Height */
	--size-button-md:  44px; /* Standard Button */
	--size-input-h:    54px; /* Floating Label Input */
}
```

### 12.2 W3C Design Tokens (`tokens.json`)
```json
{
	"surface": {
		"canvas":  { "$value": "#F1F4F9", "$type": "color" },
		"default": { "$value": "#FCFDFE", "$type": "color" },
		"subtle":  { "$value": "#F5F7FB", "$type": "color" }
	},
	"typography": {
		"sizeScale": {
			"display": "40px",
			"h1": "32px",
			"h2": "28px",
			"h3": "24px",
			"titleLg": "20px",
			"titleMd": "18px",
			"bodyLg": "16px",
			"bodyMd": "15px",
			"label": "14px",
			"captionMin": "13px"
		},
		"letterSpacing": {
			"krDisplay": "-0.03em",
			"krTitle": "-0.02em",
			"krBody": "-0.015em",
			"krCaption": "-0.005em",
			"enTitle": "-0.01em",
			"enBody": "0em",
			"enCaps": "0.05em",
			"mono": "0em"
		}
	},
	"componentSpec": {
		"checkboxSize": "22px",
		"toggleHeight": "28px",
		"inputHeight":  "54px",
		"cardSquare":   "375x375"
	}
}
```