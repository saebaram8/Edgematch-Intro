# edgemat.ch 웹사이트 컬러 전략 (v1 · 2026-11-11)

기존 작업 검토(`edgematch/pipeline/ui`, `edgematch-intro/index.html`)를 바탕으로 정한 것. 값은 `tokens/tokens.json`·`tokens.css`가 정본.

## 0. 검토에서 발견한 것
| 항목 | 기존 | 문제 | 결정 |
|---|---|---|---|
| 앱 테마 | 다크(배경 #212830, 패널 #29323c), 청록 액센트 #8dd6d0 | 청록은 브랜드 색이 아니며 시안 계열이라 차가움. 브랜드(차콜·앰버·스파크)와 따로 놂 | 다크 테마 유지하되 **청록 → 앰버**로 교체, 배경을 차콜 계열로 이동 |
| 소개 사이트 | 라이트, 청록 액센트 #0f6f63, 텍스트 로고 | 로고 없음, 브랜드와 불일치 | 라이트 기본, 브랜드 토큰 적용, 아레나 로고 조합 |
| ISO 513 색 | `dictionary-viz.js`에 P #356ea7 · M #c99618 · K #bd5149 · N #2e8b68 · S #b36b39 · H #697584 | 적록색약(deutan)에서 **K/N 대비 1.05 → 구분 불가**. 색만으로 의미 전달 | 라이트·다크 두 벌로 재정의, 글자 동반 필수 |
| A/B 비교색(칩맵) | A 청록 #00877d, B 파랑 #5577c2 | B 파랑이 ISO **P(파랑)와 충돌** | A 앰버 실선, B 무채색 점선 |
| 서체 | Segoe UI / 맑은 고딕 / Consolas | 1·l·I, 0·O 구분 안 됨, 한·영 굵기 불균형 | **Pretendard GOV**(cdnjs dynamic subset), 숫자 열 tabular-nums |
| 로고 | 텍스트 "Edge**Match**" | 마크 없음 | 아레나 조합(헤더), small(내비 ≤47px), micro(파비콘). 밝은 배경 = Y3, 어두운 배경 = 레드(흰 날) |

## 1. 두 영역 원칙 (변하지 않는 규칙)
- **데이터 영역**(표·칩·바·그래프·칩맵): ISO 6색 + 무채색 + A/B 비교색만.
- **크롬 영역**(헤더·사이드바·푸터·버튼·로고): 브랜드 3색(차콜·앰버·스파크) + 무채색.
- 둘이 한 컴포넌트 안에 같이 있지 않는다. Spark(빨강)와 K, Amber와 M이 한 화면에 있어도 **자리와 모양**으로 구분된다.
- ISO 색은 항상 글자(P/M/K/N/S/H)와 함께. 바는 P→M→K→N→S→H 고정 순서.

## 2. 테마
| 토큰 | 라이트 (소개 사이트·문서·인쇄 기본) | 다크 (앱 기본) |
|---|---|---|
| bg | #FAFAF8 | #1E2023 |
| panel | #FFFFFF | #2B2D31 |
| ink / muted / hint | #161616 / #555555 / #8A8A8A | #EDEDEA / #A9ABB0 / #7E8187 |
| line | #E4E2DD | #3E4148 |
| chrome (헤더·사이드바) | #2B2D31 위 흰 글자 | #17181B 위 #EDEDEA |
| accent (링크·선택·하이라이트) | #F2B01E | #F2B01E |
| action (주요 버튼·MATCH) | #E8392B 위 흰 글자 | #E8392B 위 흰 글자 |
| focus ring | #E8392B | #F2B01E |

앱이 다크인 이유는 유지한다(현장·야간·기존 사용자). 대신 배경의 푸른 기를 빼고 차콜 계열로 옮겨 로고의 링과 같은 재질이 되게 한다. 라이트 테마는 `data-theme` 토글로 제공하되 기본은 다크.

## 3. ISO 513 데이터 색 (두 벌)
| 군 | 라이트 fill / tint | 다크 fill / tint | 글자 |
|---|---|---|---|
| P | #1F5FC4 / #DCE6F7 | #5B8FE0 / #2A3A52 | 라이트 흰 · 다크 검정 |
| M | #FFD100 / #FFF4BF | #FFD54A / #4A4120 | 검정 |
| K | #B5121B / #F6D6D8 | #E0514F / #4A2B2B | 라이트 흰 · 다크 검정 |
| N | #3FBF7F / #DCF3E7 | #5FD49A / #23412F | 검정 |
| S | #DD7118 / #FBE4D0 | #E2781A / #4A3220 | 검정 |
| H | #7A8089 / #E6E8EB | #9AA0A8 / #383B40 | 라이트 흰 · 다크 검정 |

검증(Machado 2009): 라이트 K/N deutan 2.31 · protan 4.47, 다크 K/N deutan 1.70 · protan 2.95(기존 1.05). 모든 fill은 자기 배경 대비 3:1 이상.

## 4. 비교·상태 색
- **A/B 비교**(칩맵·Feed–Ap): A = 앰버 실선 + 16% 채움, B = 무채색(라이트 #161616 / 다크 #EDEDEA) 점선. 겹침 = 앰버 16%. 색상(hue)이 ISO 6색과 겹치지 않는다.
- **매치 성사**: Spark 배경 버튼/배지("MATCH"). 데이터 셀 안에서는 쓰지 않고 행 끝 액션 칸에서만.
- **오류/경고**: 빨간 면 금지(K와 혼동). 아이콘 + 굵은 글자 + 얇은 Spark 밑줄. **성공**: 초록 금지(N과 혼동). 체크 아이콘 + 글자.
- **단종·미확인**: 무채색 해칭/점선, 글자로 상태 명시.

## 5. 로고 적용
| 자리 | 파일 | 크기 |
|---|---|---|
| 사이트 헤더(소개) | `02-lockup/edgematch-lockup-horizontal-small.svg` | 배지 32px (small 변형이라 20~47px 안전) |
| 앱 사이드바(다크) | `02-lockup/edgematch-lockup-horizontal-small-dark.svg` (레드 아레나) | 배지 36px |
| 파비콘 | `04-png/favicon.ico` + `01-arena/edgematch-arena-micro.svg` | 16/32/48 |
| 터치 아이콘 | `04-png/appicon-180.png` | 180 |
| 문서·제안서 표지 | `02-lockup/edgematch-lockup-horizontal.svg` | 배지 ≥64px |
| 굿즈 | `01-arena/edgematch-arena-red.svg` | 서비스 UI에는 쓰지 않음 |

## 6. 서체
`<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/pretendard-gov/1.3.9/static/pretendard-gov-dynamic-subset.min.css">`
`font-family: 'Pretendard GOV', Pretendard, system-ui, 'Segoe UI', 'Malgun Gothic', sans-serif;` 숫자 열 `font-variant-numeric: tabular-nums`. 품번·코드는 고정폭(ui-monospace/Consolas) 유지.

## 7. 적용 순서
1. `tokens/tokens.css`를 모든 페이지의 첫 스타일시트로.
2. 하드코딩 hex를 토큰으로 치환(청록 → `--t-accent`, 배경·패널·선·글자 → `--t-*`).
3. `dictionary-viz.js`의 ISO 맵을 테마별 토큰으로, 칩맵 A/B 색을 `--cmp-*`로.
4. 로고·파비콘·서체 교체.
5. 라이트 테마 토글(선택).
