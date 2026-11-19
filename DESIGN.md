# 오늘의 타로 디자인 가이드

## 1. 디자인 방향

명지대학교 타로 디자인 팩의 연회색 화면, 흰색 라운드 카드, 초록 강조색을 적용한다. 375px 모바일 화면과 상태별 Figma 시안은 [오늘의 타로 · 모바일 375](https://www.figma.com/design/3pCL6EZIfjPhBr3wc2psnl)에서 확인한다.

카드는 정방향 메이저 아르카나 22장을 사용한다. 팩의 앞면 이미지는 500×836px이며 Rider–Waite–Smith 계열로 표기되어 있다. 시안에 사용하며 서비스 배포 전 원본 출처, 해당 디지털 이미지의 사용 범위, 필요한 출처 표시를 확인한다. 뒷면은 120×200px의 흰색 카드에 초록 외곽선과 별을 사용한다. 앞면의 비율은 유지한다.

## 2. 색상 토큰

| 역할 | 토큰 | 값 |
|---|---|---|
| 화면 · 카드 · 보조 표면 | Background / Surface / Surface Sub | `#F3F3F5` / `#FFFFFF` / `#F6F6F8` |
| 기본 · 보조 · 장식 글자 | Text Primary / Secondary / Tertiary | `#000000` / `#4D4D4E` / `#979F9B` |
| 기본 테두리 | Border | `#DCDCDD` |
| 강조 · 선택 배경 · 스와이프 그림 | Accent / Accent Soft / Accent Illustration | `#00D959` / `#E6FAEF` / `#00DE00` |
| 비활성 · 오류 테두리 · 토스트 | Disabled / Danger / Inverse | `#D7D7D7` / `#E5484D` / `#232427` |
| 읽을 수 있는 강조 · 포커스 · 오류 글자 · 입력 경계 | Accent Ink / Focus / Danger Ink / Input Border | `#006B37` / `#006B37` / `#A5262D` / `#858588` |

초록 Primary에는 사용자가 확정한 검은 글자를 쓴다. 결과의 카드 이름과 선택 표시는 진한 초록을 사용한다. 필수 안내와 플레이스홀더는 보조 글자색을 사용한다. 일반 텍스트 대비 4.5:1, 필수 조작 경계와 초점 표시는 3:1을 목표로 한다. 선택은 체크, 오류는 구체적인 문구를 함께 표시한다.

## 3. 글자 · 간격 · 레이아웃

Noto Sans KR, 자간 −2%. 날짜와 로마 숫자에 고정폭 숫자를 적용한다.

| 스타일 | 굵기 | 크기 / 줄 높이 | 용도 |
|---|---|---|---|
| Display | Bold | 28 / 38px | 시작 제목 |
| Title | Bold | 22 / 32px | 화면 질문 |
| Headline | Bold | 18 / 26px | 앱 바 · 카드 이름 |
| Body | Regular | 16 / 26px | 본문 · 해석 · 입력값 |
| Body Bold | Bold | 16 / 24px | L 버튼 |
| Label | Medium | 15 / 22px | M 버튼 · 주제 칩 · 토스트 |
| Caption | Regular | 13 / 19px | 보조 문구 · 오류 · 개인정보 |
| Caption Bold | Bold | 13 / 19px | 입력 라벨 |

375px 화면의 좌우 여백은 20px이며 콘텐츠는 335px이다. 앱 바는 높이 56px, 좌우 패딩 16px을 사용한다. 입력 간격은 16px, 라벨과 필드 사이 8px, 칩 사이 10px, 결과 버튼 열 간격 11px을 기준으로 한다. 시작의 주요 요소 간격은 24px, 결과 카드 안쪽은 가로 24px·세로 28px, 항목 간격 16px을 기준으로 한다. 하단 안전 영역을 확보하고, 확대나 좁은 화면에서는 칩과 버튼을 줄바꿈한다.

## 4. 컴포넌트 규칙

| 컴포넌트 | 규격과 상태 |
|---|---|
| Button | L 335×56px · 모서리 16px, M 162×48px · 모서리 14px. Primary는 초록 바탕과 검은 글자, Secondary는 흰 바탕과 회색 테두리, Disabled는 회색 바탕과 실제 비활성 처리. 아이콘 20px · 글자와 6px 간격. 화면의 주요 행동 하나를 Primary로 표시한다. |
| Input | 필드 335×52px, 반경 12px, 좌우 패딩 16px. Default · Filled · Focused · Error 상태. 이름 최대 10자, 전공은 선택. 날짜 오류는 필드 아래 구체적인 문구와 접근성 연결을 제공한다. |
| Topic Chip | 105×44px · 반경 22px, 3열 단일 선택. 기본은 흰색, 선택은 연초록 배경·진한 초록 경계와 체크. 커리어 · 재물 · 연애 · 건강 · 학업 · 종합 순서. 방향키 입력을 지원한다. |
| Privacy Notice | 보조 표면 · 반경 12px, 패딩 세로 14px·가로 16px. 자물쇠와 문구 간격 10px. 본문이 늘면 높이도 늘린다. |
| Result Card | 폭 335px · 흰 표면 · 반경 24px. 앞면 160×268px, 해석은 16/26px 가운데 정렬. 전공 문장은 조건부 표시. |
| Toast · Dialog | 토스트는 역상 배경과 흰 글자, 반경 12px, 세로 14px·가로 20px 패딩. 다이얼로그에는 제목과 닫기 동작을 제공하며 닫은 뒤 실행 버튼으로 초점을 돌린다. |

## 5. 화면별 적용

### S-01 시작 · F-1

‘오늘의 타로’ → 카드 부채꼴 → ‘내 정보를 넣고 카드 한 장으로 나만의 해석을 받아 봐요’ → **타로 시작** → ‘오락용 타로 · 정보는 저장 안 해요’. 시작 버튼은 모바일에서 콘텐츠 너비만큼 채운다.

### S-02 내 정보 · 주제 · F-2/F-3

상단에 뒤로 가기와 제목, 그 아래 이름·생년월일·전공 입력을 표시한다. 입력 묶음 직후 개인정보 안내를 두고, 주제 선택과 **카드 한 장 뽑기**를 이어 배치한다. 이름·유효한 생년월일·주제가 모두 입력되면 버튼을 활성화한다. 날짜 오류 문구는 ‘날짜를 다시 확인해 주세요’. 버튼을 누르면 카드 선택 화면으로 이동한다. 선택 화면에서 주제와 함께 카드를 고르는 방법을 안내한다. 22장 뒷면을 반지름 430px, 8° 간격으로 펼친다. 좌우 스와이프 또는 키보드·이전/다음 버튼으로 카드를 탐색하고, 탭 또는 Enter로 선택한다. 선택 후 중복 입력을 막고, 카드 이동 0.4초와 뒤집기 0.6초를 합쳐 1초 안에 정방향 앞면을 공개한다. 동작 줄이기에서는 이동·회전을 생략하고 결과를 즉시 표시한다.

### S-03 맞춤 해석 결과 · F-4~F-7

카드 안에는 ‘{이름}님의 타로 · {주제}’, 카드 그림, 카드 이름·별자리, 기본 해석·별자리 문장·선택적 전공 문장, ‘※ 오락용 타로 해석입니다’, 서비스 이름 순으로 표시한다. 전공이 비었거나 계열을 찾지 못하면 전공 문장을 생략한다. 해석은 최대 세 문장, 전체 90자 이내로 작성하고 문장 단위로 줄을 나눈다. 화면 확대나 좁은 화면에서는 자연스럽게 줄바꿈하며 글을 자르지 않는다. 건강·재물은 행동을 돌아볼 관점으로 쓰고 예측을 단정하지 않는다.

카드 아래에 **이미지 저장**(Secondary)과 **결과 공유**(Primary), 다음 줄에 **다시 뽑기**와 **처음으로**를 둔다. 좁은 화면에서 버튼 문구가 잘리면 세로로 쌓는다. 저장·공유 버튼 옆에 ‘저장 이미지와 공유 글에 입력한 이름이 들어가요’를 표시한다. 다시 뽑으면 내 정보는 유지하고 주제를 다시 선택한다. 처음으로 돌아가면 입력과 결과를 지운다. 화면 전환 뒤 제목이나 주제 영역으로 초점을 이동한다.

입력·결과 공통 안내

> 입력한 이름 · 생년월일 · 전공은 해석을 만드는 데만 쓰고, 서버로 보내거나 저장하지 않아요. 창을 닫거나 [처음으로]를 누르면 바로 지워져요.

## 6. 이미지 저장과 공유

- 결과 카드 콘텐츠로 1080×1350 PNG를 생성한다. 바깥 여백은 72px, 카드 그림은 찌그러뜨리지 않고, 내보내기 전 글꼴과 이미지 로딩을 마친다. 이름·주제·그림·카드 이름·별자리·해석·오락용 안내·서비스 이름을 포함한다. 생년월일과 전공 원문은 이미지와 공유 글에서 제외한다.
- 공유는 기기 메뉴에서 이미지와 글을 함께 전달한다. 해당 공유 방식을 사용할 수 없으면 글 자동 복사를 시도한다. 사용자가 기기 공유를 취소하면 결과 화면으로 돌아오며 자동 복사는 실행하지 않는다.
- 시작 링크에는 개인정보와 결과를 담지 않는다. 해석, 이미지 생성과 폴백용 데이터는 화면 메모리에서 처리한다. 새로 고침, 창 닫기, 처음으로에서 앱 상태를 초기화한다.

| 상황 | 문구·처리 |
|---|---|
| 직접 내려받기 시작 | 이미지를 저장했어요 · 브라우저에 다운로드를 넘긴 직후 표시 |
| 직접 내려받기 미지원·실패 | 이미지를 길게 눌러 저장해 주세요 · PNG 미리보기 표시 |
| 자동 복사 성공 | 결과를 복사했어요. 원하는 앱에 붙여 넣어 주세요 |
| 복사 실패 | 아래 글을 길게 눌러 복사해 주세요 · 메시지 표시 |

공유 글 예시

```text
🔮 {이름}님의 타로 · {주제}
{카드 이름} · {별자리}
{해석}
※ 오락용 타로 해석입니다
나도 한 장 뽑기 → {시작 링크}
```

## 7. Tailwind CSS v4 적용 예시

Tailwind CSS v4의 `@theme inline`에서 역할 토큰을 유틸리티로 연결한다. shadcn/ui의 `Button`, `Input`, `RadioGroup`, `Card`, `Alert`, `Sonner`, `Dialog`에 같은 토큰을 적용한다.

```css
@import "tailwindcss";

:root {
  color-scheme: light;
  --background: #f3f3f5;
  --foreground: #000;
  --card: #fff;
  --primary: #00d959;
  --primary-foreground: #000;
  --secondary: #fff;
  --secondary-foreground: #000;
  --accent: #e6faef;
  --accent-foreground: #006b37;
  --muted: #f6f6f8;
  --muted-foreground: #4d4d4e;
  --border: #dcdcdd;
  --input: #858588;
  --ring: #006b37;
  --destructive: #a5262d;
  --danger-border: #e5484d;
  --disabled: #d7d7d7;
  --inverse: #232427;
  --illustration: #00de00;
}

@theme inline {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-primary: var(--primary);
  --color-primary-foreground: var(--primary-foreground);
  --color-secondary: var(--secondary);
  --color-secondary-foreground: var(--secondary-foreground);
  --color-accent: var(--accent);
  --color-accent-foreground: var(--accent-foreground);
  --color-muted: var(--muted);
  --color-muted-foreground: var(--muted-foreground);
  --color-border: var(--border);
  --color-input: var(--input);
  --color-ring: var(--ring);
  --color-destructive: var(--destructive);
  --color-danger-border: var(--danger-border);
  --color-disabled: var(--disabled);
  --color-inverse: var(--inverse);
  --color-illustration: var(--illustration);
  --radius-field: 12px;
  --radius-button-m: 14px;
  --radius-button-l: 16px;
  --radius-chip: 22px;
  --radius-result: 24px;
  --font-sans: "Noto Sans KR", "Malgun Gothic", system-ui, sans-serif;
}
```

## 8. 구현 인계 확인

- 320px 화면과 큰 글자 설정에서 입력 라벨, 주제 타일, 긴 이름·해석이 잘리지 않는다.
- 키보드만으로 입력, 주제 선택, 결과 확인과 대체 다이얼로그 닫기가 가능하다.
- 전공 미입력 결과, 카드 뒤집기 생략, 저장 미리보기, 공유 취소, 복사 실패를 각각 확인한다.
- PNG는 1080×1350이며 이름·오락용 안내가 읽힌다. PNG와 공유 글에 생년월일·전공 원문이 없고, 시작 링크에 입력값이 없다.
- 처음으로 돌아간 뒤 입력칸과 주제가 초기화된다.

## 근거 문서

- [PRD](./TARO_01_PRD.md) · [기능명세서](./TARO_02_기능명세서.md) · [유저플로우](./TARO_03_유저플로우.md) · [와이어프레임](./TARO_04_와이어프레임.md)
- [Tailwind CSS 테마 변수](https://tailwindcss.com/docs/theme) · [shadcn/ui Tailwind v4](https://ui.shadcn.com/docs/tailwind-v4) · [shadcn/ui Radio Group](https://ui.shadcn.com/docs/components/base/radio-group)
