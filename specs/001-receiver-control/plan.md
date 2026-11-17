# 001 수신기 조종 — 계획

## 구조

```
ui (Jetpack Compose)  ──  ViewModel (상태 한 벌)  ──  ReceiverRepository  ──  ReceiverApi (Retrofit + kotlinx.serialization)
                                   │                                              │
                              SessionStore (DataStore: 교실 자리표, 최근 허브)       └─ 1초 폴링 (Flow), 끊김 감지
```

- **언어·틀**: Kotlin, Jetpack Compose, 단일 Activity, Navigation-Compose. 최소 SDK 26 (ARCore 조건과 같음).
- **통신**: 허브 주소는 고정(`http://192.168.4.1`, Wi-Fi 이름 `DeteCam-RX`). Retrofit + OkHttp(타임아웃 3초). 상태는 1초 폴링 Flow 하나로 모으고 화면은 그것만 본다.
- **주소 계약**: `net/ReceiverApi.kt` 의 형(type)은 [주소 계약](../../docs/주소%20계약.md)의 표를 그대로 옮긴다. 계약 시험은 가짜 허브에 실제로 부른다.
- **흐름**: 화면이 다음 단계를 정하지 않는다. 허브의 `status.prompt`, `top.next` 를 그대로 읽어 한 줄 안내로 보여 준다 (판단은 허브 한 곳에만).

## 화면

| 화면 | 내용 |
|---|---|
| 연결 | 허브 Wi-Fi 안내, 연결 상태 |
| 패널 | 패널마다 연결·배터리·자리 등록, '자리 등록'(002) |
| 찾기 | 큰 단추 하나(찾기 시작), 단계 표시(엿듣기 → 확인 → 자리 찾기), 한 줄 안내, 멈춤 |
| 기기 | 의심 점수 순 목록, 까닭 한 줄, 내 기기 표시, '이 기기 자리 찾기' |
| 교실 설정 | 줄·칸, 첫 자리·끝 자리 찍기(002), 저장한 교실 |
| 결과 | 2D 평면도(자리 후보 셋과 확률) + 'AR 로 보기' ([002](../002-ar-zone-display/spec.md)) |

## 검증

- 단위: ViewModel 상태 전이 (가짜 Repository).
- 계약: 가짜 허브에 대고 모든 주소를 한 번씩.
- 손 시험: 시나리오 1·2 를 실제 수신기로 ([데모 환경](https://github.com/DeteCam/receiver/blob/main/docs/%EB%8D%B0%EB%AA%A8%20%ED%99%98%EA%B2%BD.md)).

## 위험

- 폰이 허브 Wi-Fi(인터넷 없음)에 붙으면 안드로이드가 모바일 데이터로 돌려 버린다 → `ConnectivityManager.requestNetwork` 로 그 Wi-Fi 에 소켓을 묶는다.
