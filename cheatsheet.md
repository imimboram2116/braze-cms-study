# 시험 직전 체크

> 이론 탭에서 시험에 바로 쓰이는 것만 뽑았다. 출처는 이론 탭과 같다. "(미확인)"은 강의에서만 나왔고 Braze AI 확인을 못 받은 것.

## 1. 시험 형식

- 90분, 객관식 50문항, 합격 69%, 과락 없음 [슬라이드 2] [강의5 00:28]
- "2개 고르기"처럼 고를 개수가 문제에 적혀 있으니 꼭 확인 [강의1 01:07~01:08]
- 문제 은행에서 랜덤 출제. 예전 문제도 나옴. 그래서 예전 정답(예상문제 정답)이 그대로 나올 수 있음 [강의1 00:53]
- 신분증 없으면 응시 불가 [강의3 00:57]
- 한국어 응시 가능하고 시험 중 한영 전환 가능. 번역이 어색하면 영어 원문으로 판단 [강의1 00:00] [강의3 00:31] (강의5는 다르게 말해 확실하지 않음)

## 2. 숫자 한 장

| 숫자 | 뭐의 값 | 출처 |
|---|---|---|
| **25개** | 세그먼트 애널리틱스 추적, 워크스페이스당 | [Braze AI 확인 11/20] [예상 Q9] |
| **50개** | 세그먼트 익스텐션 활성 (CDI 익스텐션은 안 셈) | [Braze AI 확인 11/20] [대시보드 화면 11/20] |
| **10개** | 게재빈도 제한 규칙, 워크스페이스당 | [Braze AI 확인 11/20] [예상 Q10] |
| **10% 이하 / 15%** | 글로벌 컨트롤 그룹 권장 / 설정 최대. 대상 1만 명 미만이면 15%까지 | [Braze AI 확인 11/20] |
| **730일(2년)** | 세그먼트 익스텐션 최대 조회 기간 | [강의1 00:22] [사용자 제공 설명] |
| **최근 2일** | Incremental refresh가 갱신 때 다시 처리하는 기간 | [대시보드 화면 11/20] |
| **매일 자정** | Incremental refresh 자동 재생성 (회사 시간대, 최대 1시간 지연) | [Braze AI 확인 11/20] |
| **12시간마다** | Intelligent Selection이 성과를 다시 보고 배분을 조정 | [Braze AI 확인 11/20] |
| **99.999%** | 세그먼트 도달 사용자 계산 정확도 | [강의1 00:24] |
| **6개월 / 1년** | Email Insights 조회 기간 / Email Performance 조회 기간 | [Braze AI 확인 11/20] |
| 30일 | 일반 세그먼트 필터의 기본 평가 기간 (미확인) | [강의1 00:16] |
| 8개 | Action Path 분기 수, Everyone Else 포함 (미확인) | [강의4 00:05] |

- **[시험 팁]** "숫자 모르면 25"는 강사의 찍기 요령일 뿐. 무엇의 한도를 묻는지 먼저 볼 것 [강의5 00:10]

## 3. 헷갈리는 짝

### 세그먼트

| A | B |
|---|---|
| **AND**: 조건을 모두 만족 | **OR**: 하나라도 만족 |
| 필터 그룹 안의 필터는 전부 같은 연산자로만 연결 | 그룹끼리는 따로 AND/OR로 묶음 |
| **Segment Analytics**: 세그먼트 규모, 매출 추이를 시간에 따라 봄 (토글 켠 뒤 데이터만) | **Segment Extensions**: 최대 2년 과거 행동, 이벤트 속성으로 대상 만들기 |

- 필터 연산자: Exactly 일치, Does not equal 불일치, Is any of 하나라도 일치, less than 미만, more than 초과 [슬라이드 9]
- 익스텐션 4가지: Simple(SQL 안 씀, 이벤트 1개) / Template(Catalog Segments) / Incremental refresh(최근 2일) / Full refresh(전체 재계산, CDI는 필수 아님) [대시보드 화면 11/20] [Braze AI 확인 11/20]
- 세그먼트별 매출 보기: Analytics Tracking 켜기 + Revenue Report에서 Break Down by Segment [예상 Q13]

### 개인화 (Liquid)

| 쓰는 곳 | 구문 |
|---|---|
| API 트리거 캠페인 | `api_trigger_properties` |
| 캔버스 진입 속성 | `canvas_entry_properties` |
| 이벤트 기반 | `event_properties` |
| 값이 없을 때 대체값 | `default` |
| 첫 글자 대문자 | `capitalize` |

- `$`는 Braze 데이터에서 온 객체 표시. `{% assign %}`으로 만든 변수에는 안 붙임 [슬라이드 22]
- Liquid는 모든 채널 작성기, HTML 편집기, 드래그 앤 드롭 편집기에서 씀. 프로필 업데이트나 API 검색 도구가 아님 [예상 Q14]
- 저장 안 된 외부 API 데이터를 바로 쓰기: **Connected Content** / Braze에 저장된 비사용자 데이터: Catalog [예상 Q21]
- Liquid 코드 만들어 주는 도구: 개인화 도구(+ 아이콘), Liquid AI Assistant [예상 Q15]

### 테스트와 실험

| 기능 | 무엇을 하나 | 지금 |
|---|---|---|
| **Winning Variant** | 일부에게 테스트 후 이긴 배리언트를 나머지에게 | 사용 가능 |
| **Intelligent Selection** (Optimize with BrazeAI) | 테스트 도중 성과 좋은 쪽에 점점 더 배정. 캠페인과 캔버스 둘 다 | 사용 가능 |
| **Personalized Variant** | 사용자마다 맞는 배리언트 | 새 캠페인에서는 선택 불가 |
| **Intelligent Timing** | 사용자별 참여 가능성 높은 시점에 발송. 시간에 민감하지 않은 반복 캠페인에 | |
| **Intelligent Channel** | 사용자가 가장 많이 참여하는 채널로 거르는 필터 | |

- 반복 캠페인에서 우승 배리언트로 보내는 사용자 극대화(2개): Winning Variant 최적화, Intelligent Selection [예상 Q39]
- 대조군 = 메시지를 받지 않는 기준 집단 [예상 Q33]

### 캔버스 (비중 20%)

| 컴포넌트 | 나누는 기준 |
|---|---|
| **Action Path** | 정해진 기간 동안 한 **행동**. 안 하면 Everyone Else |
| **Audience Path** | 사용자 **속성**, 세그먼트 조건 |
| **Decision Split** | 도착한 **순간**의 조건. 스스로 기다리지 않음 |
| **Experiment Path** | 정한 비율로 **무작위** (A/B 테스트) |

| 기능 | 무엇을 하나 |
|---|---|
| **Winning Path** | Experiment Paths 안에서만. 실험 뒤 이긴 경로로 모두 보냄 |
| **Personalized Path** | 사용자마다 맞는 경로. 새 단계에서는 선택 불가 |
| **Intelligent Selection** | Canvas 전체 배리언트 사이에서 성과 좋은 쪽에 점점 더 배정 |
| **Global Exit Criteria** | 지정 행동을 하면 캔버스에서 나감, 이후 메시지 모두 중단 |
| **Delivery Validation** | 메시지 보낼 때마다 조건 재확인. 설정에 따라 이번 것만 건너뛸 수도 |

- **[시험 팁]** "경로"나 "path"가 보이면 캔버스 [강의4 00:21~00:23]
- **[시험 팁]** 24시간 기다렸다가 업그레이드 여부로 나누기 = Action Path. 모두 24시간 붙잡으려면 Advance users based on ranked order 켜기 [Braze AI 확인 11/20] [예상 Q54]
- 캔버스 중간 메시지 A/B 테스트 = 실험 경로(Experiment Paths) [예상 Q35]
- 채널 참여도에 따라 분기 = Audience Path + Intelligent Channel 필터 [예상 Q37]
- 인앱 선호도 설문에 필요한 것: 커스텀 속성, 커스텀 이벤트, Braze SDK [예상 Q51]
- Winning, Personalized Path 결과 보는 곳: Canvas analytics [예상 Q53]

### 채널

| 채널 | 구독 상태 |
|---|---|
| 푸시 | Opted-in(명시 동의), Subscribed(기본), Unsubscribed |
| 이메일 | Opted-in, Subscribed(수신 거부도 명시 동의도 안 한 기본 상태), Unsubscribed |
| SMS | Subscribed(명시적으로 받겠다고 확인), Unsubscribed. 구독 그룹별로 관리 |

- 동의한 채널로만 보내기 = Subscription Status. GCG는 효과 비교용 대조군 [예상 Q50]
- 이메일 구독 그룹 만드는 곳 = Audience > Subscription Group Management [대시보드 화면 11/20] [슬라이드 31]
- "수신 거부자 포함 모든 사용자"에게 보낼 수 있는 것 = 거래 메시지, 정책 변경 안내 [슬라이드 33]
- 푸시 프라이머 가장 좋은 때 = 사용자가 가치 높은 행동을 마친 뒤. 시스템 프롬프트 전에 인앱으로 가치 설명 [슬라이드 34] [예상 Q44]
- 하드 바운스율이 높을 때 = 더블 옵트인 도입, 선셋 정책 적용 [슬라이드 27]
- 피드에 계속 떠 있는 세일 정보 = Content Card [슬라이드 15]
- **인앱 메시지와 Content Card는 게재빈도 제한을 안 받고**, 다른 메시지 횟수에도 안 셈 [Braze AI 확인 11/20]

### 리포팅

| 기여 방식 | 전환으로 세는 때 |
|---|---|
| Upon Receipt | 받기만 해도 |
| **Upon Open** | 열었을 때. **Machine Open은 뺌** |
| Upon Click | 클릭했을 때 (참여 증거가 가장 강함) |
| Last Touch | 마지막 접점에 모든 공로 |

- **Machine Open** = MPP를 켠 사용자의 열기. Apple Mail로 연 것이 다 해당되는 건 아님. 실제 사람이 연 것도 섞임. "사람이 안 연 수"로 보면 틀림 [Braze AI 확인 11/20]
- Unique Opens에는 Machine Open이 들어감 [Braze AI 확인 11/20]
- SMS 성과 지표 = 통신사 거절, 총 클릭 수. 반송, 고유 열람은 이메일 지표 [예상 Q57]
- **[시험 팁]** "over the past year"(지난 1년) 반송과 전달 비교 = Overview (추정, 확신 80%) [강의5 00:00] [예상 Q58]

## 4. 원본도 정답이 확실하지 않았던 예상문제

| 문항 | 고를 답 |
|---|---|
| Q11 CSV 내보내기 | ③은 확실. 두 번째는 ① 또는 ④ |
| Q26 테스트 변수 | ③ 제목란, ④ 딥링크 (잠정) |
| Q34 GCG | ④ 10% 이하 (이제 확정) |
| Q55 Delay Group | ② (예전 문제 기준. 지금 문서는 Winning Path와 함께 설명) |
| Q58 지난 1년 이메일 | ④ Overview (추정, 확신 80%) |
| Q59 Machine Opens | ③ (가장 가까운 보기. 정의는 MPP 기준) |
