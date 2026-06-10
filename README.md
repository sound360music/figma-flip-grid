# figma-flip-grid

6×6 타일 그리드에 이미지를 랜덤으로 배치하고, 다양한 전환 애니메이션으로 교체하면서 전체 그리드가 무한히 위로 흐르는 웹 위젯입니다.  
Figma Sites, Notion, 웹페이지 등 iframe/embed가 가능한 모든 환경에서 사용할 수 있습니다.

---

## 미리보기

- 6열 × 6행 이미지 그리드
- 2~5초마다 랜덤으로 1~3개 타일이 교체
- 전환 방식: Y축 플립, X축 플립, 상하좌우 슬라이드, 블러 디졸브 중 랜덤
- 전체 그리드가 72초 주기로 천천히 위로 무한 스크롤
- 투명 배경, corner radius 2px

---

## 파일 구조

```
figma-flip-grid/
├─ index.html        ← 메인 위젯 파일
└─ images/
   ├─ 01.jpg
   ├─ 02.png
   ├─ 03.jpeg
   └─ ...            ← 01~99 숫자 이름으로 자유롭게 추가
```

---

## 이미지 규칙

| 항목 | 규칙 |
|------|------|
| 파일명 | `01` ~ `99` (두 자리 숫자) |
| 확장자 | `jpg`, `jpeg`, `png`, `gif` 지원 |
| 대소문자 | 소문자 권장 (GitHub Pages는 대소문자 구분) |
| 비율 | 1:1 권장 (자동으로 cover 처리됨) |
| 최소 장수 | 36장 이상 권장 (비중복 배치 기준) |

---

## 주요 설정값 (index.html 내 CONFIG)

```js
const CONFIG = {
  tilesPerBoard: 36,        // 한 판당 타일 수 (6×6)
  boardCount: 3,            // 세로로 이어 붙일 판 수
  minRefreshDelay: 2000,    // 교체 최소 간격 (ms)
  maxRefreshDelay: 5000,    // 교체 최대 간격 (ms)
  minTilesPerRefresh: 1,    // 한 번에 교체 최소 타일 수
  maxTilesPerRefresh: 3,    // 한 번에 교체 최대 타일 수
  minAnimDuration: 300,     // 전환 애니메이션 최소 시간 (ms)
  maxAnimDuration: 600,     // 전환 애니메이션 최대 시간 (ms)
};
```

스크롤 속도는 CSS에서 조정합니다.

```css
.strip {
  animation-duration: 72s; /* 한 판(6행)이 완전히 올라가는 시간 */
}
```

---

## 전환 애니메이션 종류

| 클래스 | 설명 |
|--------|------|
| `anim-flip-y` | Y축 기준 카드 플립 |
| `anim-flip-x` | X축 기준 카드 플립 |
| `anim-slide-up` | 위로 밀어내기 |
| `anim-slide-down` | 아래로 밀어내기 |
| `anim-slide-left` | 왼쪽으로 밀어내기 |
| `anim-slide-right` | 오른쪽으로 밀어내기 |
| `anim-dissolve` | 블러 디졸브 |

타일마다, 교체마다 완전 랜덤으로 선택됩니다.

---

## Figma Sites 적용 방법

1. 이 저장소를 GitHub Pages로 배포합니다.  
   - Settings → Pages → Source: main 브랜치, /(root) 선택 → Save
2. 배포 URL 확인합니다.  
   - 형태: `https://사용자이름.github.io/figma-flip-grid/`
3. Figma Sites 편집 화면에서 Embed 블록을 추가합니다.
4. 배포 URL을 Embed 블록에 붙여 넣습니다.
5. 크기를 730×730px로 맞춥니다.

---

## 이미지 추가 방법

1. 이미지를 1:1 비율로 준비합니다.
2. 파일명을 `01.jpg`, `02.png` 형식으로 지정합니다.
3. `images/` 폴더에 업로드합니다.
4. GitHub에 커밋 후 자동 반영됩니다.
5. 코드 수정 불필요.

---

## 라이선스

MIT
