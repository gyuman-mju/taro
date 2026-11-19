# 오늘의 타로 디자인 가이드

## 1. 디자인 방향

따뜻한 종이색, 와인색, 라일락으로 구성한 라이트 테마. 여백과 얇은 테두리로 화면의 위계를 만들고, 타로 그림에 가장 강한 시각적 대비를 준다. 첫 화면에는 카드 뒷면과 시작 버튼을, 결과에는 카드 앞면과 짧은 해석을 중심에 둔다. 화면당 가장 중요한 행동 하나에 와인색 버튼을 쓴다.

카드 22장은 동일한 테두리, 번호 위치, 명도 범위의 원본 일러스트로 제작하거나 사용 범위가 확인된 세트를 선택한다. 앞면은 모두 정방향이며, 뒷면의 별과 궤도 모티프는 시작 화면과 뒤집기 효과에 재사용한다. 카드 그림의 출처는 확정 후 기록한다.

## 2. 색상 토큰

| 역할 | CSS 변수 | 값 | 적용 |
|---|---|---|---|
| 화면 | `--background` | `#F2F0EB` | 공통 바탕 |
| 기본 글자 | `--foreground` | `#292827` | 제목, 본문, 아이콘 |
| 카드 | `--card` | `#FFFCF8` | 결과 카드, 입력 필드, 저장 미리보기 |
| 주요 행동 | `--primary` / `--primary-foreground` | `#421D24` / `#FFFFFF` | 시작, 뽑기, 이미지 저장 |
| 주요 행동 호버 | `--primary-hover` | `#572A33` | 마우스 호버 |
| 보조 행동 | `--secondary` / `--secondary-foreground` | `#D4C7FF` / `#292827` | 공유, 주제 선택 배경 |
| 강조·초점 | `--accent-foreground` / `--ring` | `#714CB6` | 링크, 선택 표시, 키보드 초점 |
| 보조 표면·글자 | `--muted` / `--muted-foreground` | `#EAE5DE` / `#625D58` | 개인정보 안내, 도움말, 비활성 버튼 |
| 구분선 | `--border` | `#DDD5CB` | 카드 외곽, 섹션 구분 |
| 입력 외곽선 | `--input` | `#8B817B` | 입력과 주제 선택의 조작 영역 구분 |
| 오류 | `--destructive` | `#A3263C` | 날짜 오류, 잘못된 필드 |
| 카드 뒷면 | `--illustration` | `#0C4243` | 타로 일러스트 전용 |

색상만으로 상태를 전달하지 않는다. 선택에는 체크 표시, 오류에는 구체적인 문구를 함께 제공한다. 일반 텍스트 대비는 4.5:1 이상, 큰 텍스트와 조작 요소의 필수 시각 경계는 3:1 이상을 목표로 실제 조합을 확인한다.

## 3. 글자 · 간격 · 레이아웃

| 용도 | 크기 / 줄 높이 | 굵기 | 적용 |
|---|---|---|---|
| 시작 제목 | 36 / 44px, 넓은 화면 48 / 56px | 500 | 오늘의 타로 |
| 화면 제목 | 28 / 36px | 500 | 나에 대해 알려 주세요 |
| 결과 카드 이름 | 24 / 32px | 600 | XIX 태양 |
| 본문·해석·입력 | 16 / 24px | 400 | 본문, 입력값, 해석 |
| 필드 라벨·버튼 | 16 / 24px | 600 | 입력 라벨, CTA |
| 개인정보·안내 | 14 / 20px | 400 | 오류, 오락용 안내, 도움말 |

- 한글은 Noto Sans KR, 영문은 Inter를 우선 사용한다. 폰트는 앱과 함께 제공하고, 누락 시 Malgun Gothic과 시스템 산세리프로 대체한다. 날짜와 로마 숫자에는 `tabular-nums`를 적용한다.
- 4px 단위 간격을 사용한다. 아이콘과 글자 8px, 라벨과 입력 8px, 필드 사이 16px, 안내와 CTA 사이 24px, 주요 섹션 사이 32px.
- 모바일 좌우 여백 16px, 640px 이상에서는 24px. 콘텐츠는 가운데 정렬하며 입력 화면 최대 480px, 시작과 결과 최대 560px. 화면 하단은 기기의 안전 영역을 포함해 여백을 둔다.
- 버튼, 입력, 주제 선택의 최소 조작 높이는 44px, 주요 CTA는 48px. 입력과 선택 타일의 모서리는 8px, 버튼은 12px, 결과 카드와 미리보기는 16px. 카드 그림은 2:3 비율을 유지한다.

## 4. shadcn/ui 컴포넌트 규칙

| 컴포넌트 | 스타일과 동작 |
|---|---|
| `Button` | `default`는 와인색 배경과 흰 글자. `secondary`는 라일락 배경과 짙은 글자. `outline`과 `ghost`는 다시 뽑기와 처음으로에 적용. 모두 2px 보라색 초점 링과 2px 간격을 사용한다. 비활성 버튼은 음영 표면과 보조 텍스트로 표시하고 실제 `disabled` 속성을 사용한다. |
| `Field` + `Input` | 라벨을 위에 고정하고 `id`와 연결한다. 이름은 닉네임을 허용하며 최대 10자. 생년월일은 기기 날짜 입력을 활용하고 실제 달력 날짜인지 검증한다. 전공 라벨에는 ‘선택’을 표시한다. 날짜 오류는 필드 아래에 표시하고 `aria-invalid`, `aria-describedby`로 연결한다. |
| `RadioGroup` + `RadioGroupItem` | 커리어 · 재물 · 연애 · 건강 · 학업 · 종합 순서. 타일 전체가 라벨 겸 터치 영역이다. 기본은 종이색과 입력 테두리, 선택은 라일락 바탕과 보라색 테두리·체크. 초기 선택은 비워 두고 방향키 탐색을 지원한다. 3열을 기본으로 하되 확대 시 2열로 줄인다. |
| `Card` | 카드 표면, 1px 테두리, 16px 모서리, 내부 여백 24px(좁은 화면 16px). 결과 제목, 그림, 카드 이름과 별자리, 해석, 오락용 안내, 서비스 이름을 순서대로 배치한다. 버튼과 개인정보 안내는 카드 바깥에 둔다. |
| `Alert` | 입력 및 결과의 개인정보 안내는 보조 표면에 자물쇠와 본문으로 표시한다. 읽는 순서에 맞춰 배치하며 정적인 안내는 라이브 알림으로 읽히지 않게 한다. |
| `Sonner` · `Dialog` | 저장·복사 성공은 비차단 알림으로 읽어 준다. 길게 누르기 대안은 제목이 있는 다이얼로그로 열고, 닫으면 실행한 버튼에 초점을 돌려준다. 텍스트 복사 대안은 선택 가능한 여러 줄 텍스트로 제공한다. |

## 5. 화면별 적용

### S-01 시작 · F-1

‘오늘의 타로’ → 카드 뒷면 → ‘내 정보를 넣고 카드 한 장으로 나만의 해석을 받아 봐요’ → **타로 시작** → ‘오락용 타로 · 정보는 저장 안 해요’. 시작 버튼은 모바일에서 콘텐츠 너비만큼 채운다.

### S-02 내 정보 · 주제 · F-2/F-3

상단에 뒤로 가기와 제목, 그 아래 이름·생년월일·전공 입력을 표시한다. 입력 묶음 직후 개인정보 안내를 두고, 주제 선택과 **카드 한 장 뽑기**를 이어 배치한다. 이름·유효한 생년월일·주제가 모두 입력되면 버튼을 활성화한다. 날짜 오류 문구는 ‘날짜를 다시 확인해 주세요’. 뽑는 동안 재실행을 막고 카드 뒤집기는 600ms를 기준으로 최대 1초 안에 끝낸다. 동작 줄이기 설정에서는 뒷면 회전 없이 결과를 바로 표시한다.

### S-03 맞춤 해석 결과 · F-4~F-7

카드 안에는 ‘{이름}님의 타로 · {주제}’, 카드 그림, 카드 이름·별자리, 기본 해석·별자리 문장·선택적 전공 문장, ‘※ 오락용 타로 해석입니다’, 서비스 이름 순으로 표시한다. 전공이 비었거나 계열을 찾지 못하면 전공 문장을 생략한다. 해석은 최대 세 문장, 전체 90자 이내로 작성하고 문장 단위로 줄을 나눈다. 화면 확대나 좁은 화면에서는 자연스럽게 줄바꿈하며 글을 자르지 않는다. 건강·재물은 행동을 돌아볼 관점으로 쓰고 예측을 단정하지 않는다.

카드 아래에 **이미지 저장**과 **결과 공유**, 다음 줄에 **다시 뽑기**와 **처음으로**를 둔다. 좁은 화면에서 버튼 문구가 잘리면 세로로 쌓는다. 저장·공유 버튼 옆에 ‘저장 이미지와 공유 글에 입력한 이름이 들어가요’를 표시한다. 다시 뽑으면 내 정보는 유지하고 주제를 다시 선택한다. 처음으로 돌아가면 입력과 결과를 지운다. 화면 전환 뒤 제목이나 주제 영역으로 초점을 이동한다.

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

shadcn/ui의 역할별 CSS 변수에 값을 정의하고 `@theme inline`으로 Tailwind 유틸리티에 연결한다. 버튼 상태와 크기는 공통 변형에서 설정하고, 화면별로 색상 값을 다시 지정하지 않는다.

```css
@import "tailwindcss";

:root {
  color-scheme: light;
  --background: #f2f0eb;
  --foreground: #292827;
  --card: #fffcf8;
  --card-foreground: var(--foreground);
  --popover: var(--card);
  --popover-foreground: var(--foreground);
  --primary: #421d24;
  --primary-foreground: #ffffff;
  --primary-hover: #572a33;
  --secondary: #d4c7ff;
  --secondary-foreground: var(--foreground);
  --accent: #ede6fc;
  --accent-foreground: #714cb6;
  --muted: #eae5de;
  --muted-foreground: #625d58;
  --border: #ddd5cb;
  --input: #8b817b;
  --ring: #714cb6;
  --destructive: #a3263c;
  --illustration: #0c4243;
  --radius: 0.75rem;
  --font-app: Inter, "Noto Sans KR", "Malgun Gothic", system-ui, sans-serif;
}

@theme inline {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-card-foreground: var(--card-foreground);
  --color-popover: var(--popover);
  --color-popover-foreground: var(--popover-foreground);
  --color-primary: var(--primary);
  --color-primary-foreground: var(--primary-foreground);
  --color-primary-hover: var(--primary-hover);
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
  --color-illustration: var(--illustration);
  --radius-field: calc(var(--radius) - 4px);
  --radius-action: var(--radius);
  --radius-card: calc(var(--radius) + 4px);
  --font-sans: var(--font-app);
}
```

- 주요 버튼 예시 `min-h-12 rounded-action bg-primary px-4 text-primary-foreground hover:bg-primary-hover focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:bg-muted disabled:text-muted-foreground`.
- 내용 카드 예시 `rounded-card border border-border bg-card p-4 text-card-foreground sm:p-6`.

## 8. 구현 인계 확인

- 320px 화면과 큰 글자 설정에서 입력 라벨, 주제 타일, 긴 이름·해석이 잘리지 않는다.
- 키보드만으로 입력, 주제 선택, 결과 확인과 대체 다이얼로그 닫기가 가능하다.
- 전공 미입력 결과, 카드 뒤집기 생략, 저장 미리보기, 공유 취소, 복사 실패를 각각 확인한다.
- PNG는 1080×1350이며 이름·오락용 안내가 읽힌다. PNG와 공유 글에 생년월일·전공 원문이 없고, 시작 링크에 입력값이 없다.
- 처음으로 돌아간 뒤 입력칸과 주제가 초기화된다.

## 근거 문서

- [PRD](./TARO_01_PRD.md) · [기능명세서](./TARO_02_기능명세서.md) · [유저플로우](./TARO_03_유저플로우.md) · [와이어프레임](./TARO_04_와이어프레임.md)
- [Tailwind CSS 테마 변수](https://tailwindcss.com/docs/theme) · [shadcn/ui Tailwind v4](https://ui.shadcn.com/docs/tailwind-v4) · [shadcn/ui Radio Group](https://ui.shadcn.com/docs/components/base/radio-group)
