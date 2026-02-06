# specific_reader
유저가 페이지를 읽는 속도와 도달 비율에 따라 유저를 3단계로 분류합니다.
1. reader - 페이지를 기준 비율_(기본 80%)_까지 300px/s로 읽은 유저
2. skimmer - 페이지를 기준 비율_(기본 80%)_까지 읽었으나, 300px/s보다 빠르게 읽은 유저
3. bouncer - 페이지를 기준 비율_(기본 80%)_에 도달하지 못하고 이탈한 유저

## 적용 방법
### dataLayer 생성

1. Google Tag Manager에서 태그를 생성합니다.
2. 맞춤 HTML 태그에 하기 코드를 추가합니다.

```JavaScript
<script>
window.ReaderTrackerConfig = {
    thresholdDepth: 0.8,  // 스크롤 깊이 (기본: 0.8)
    speedStandard: 300,   // 속도 기준 px/s (기본: 300)
    debug: false           // 디버그 모드 (기본: false)
};
</script>

<script src="https://cdn.jsdelivr.net/gh/lud0914/specific_reader_gtm/reader-tracker.js">
```

3. 트리거는 가급적 'DOM 사용 가능' 으로 적용하시길 권장드립니다.


### 트리거 구성
1. 트리거는 가급적 DOM 사용 가능으로 넣습니다.
2. 메인페이지 등이 포함되는 경우, Bouncer가 높게 나타나 데이터 신뢰성을 낮출 수 있으니 가급적 Blog 등 아티클 위주로 사용을 권장합니다.

#### 매개변수 구성

1. Google Tag Manager 내 변수에 접속 후 변수 생성을 진행합니다.
2. 변수를 데이터 영역 변수로 잡고 "reader_type"을 입력합니다.
3. 해당 변수를 매개변수로 구성하면 됩니다.

### 태그 구성
1. 태그 구성 시 유의 사항은 트리거로 사용하는 '맞춤 이벤트'에 'specific_reader' 를 입력해야 합니다.
2. 트리거의 작동은 가급적 blog 등 아티클 위주로 사용하는 것을 권장합니다. 랜딩페이지도 적용 시, bouncer가 증가하여 데이터 정재 과정이 발생할 수 있습니다.

**매개변수 구성 시, 활용에 따라 유저 속성/이벤트 속성을 나눠서 진행합니다.**
- 콘텐츠별 유저의 읽기가 궁금하다면, 이벤트 속성
- 전환 등 다른 액션을 한 유저의 최근 타입이 궁금하다면 사용자 속성

## 완료된 태그 구성 예시

### 전체 태그
<img width="400" height="100%" alt="image" src="https://github.com/user-attachments/assets/fa9d86a8-d952-4d6c-9351-bcd08ec70c81" />

### 데이터 레이어
<img width="400" height="100%" alt="image" src="https://github.com/user-attachments/assets/d07104e2-d55f-4fb3-9bd2-06022aeb00a2" />

### 매개변수 구성
<img width="400" height="100%" alt="image" src="https://github.com/user-attachments/assets/b50d877b-9dc4-4f58-baf5-964f006b1230" />

### 트리거 구성
<img width="400" height="100%" alt="image" src="https://github.com/user-attachments/assets/ee3016c8-bf26-4cff-ba12-3d4881364f7b" />




