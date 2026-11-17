# 001 수신기 조종 — 계획

## 구조

```
ui (Jetpack Compose)  ──  ViewModel (상태 한 벌)  ──  ReceiverRepository  ──  ReceiverApi (Retrofit + kotlinx.serialization)
                                   │                                              │
                              SessionStore (DataStore: 교실 배치, 최근 수신기)        └─ 1초 폴링 (Flow), 끊김 감지
```

- **언어·틀**: Kotlin, Jetpack Compose, 단일 Activity, Navigation-Compose. 최소 SDK 26 (ARCore 조건과 같음).
- **통신**: 수신기 주소는 고정(`http://192.168.4.1`, Wi-Fi 이름 `DeteCam-RX`). Retrofit + OkHttp(타임아웃 3초). 상태는 1초 폴링 Flow 하나로 모으고 화면은 그것만 본다. 수신기가 한 번에 한 가지 일만 하므로(다른 일은 409) 앱도 'busy 면 단추 잠금' 한 가지 규칙으로 간다.
- **주소 계약**: `net/ReceiverApi.kt` 의 형(type)은 receiver 의 `docs/혼자 동작.md` 5절 표를 그대로 옮긴다. 계약 시험은 가짜 수신기(`firmware/host`)에 실제로 부른다.
- **흐름**: 화면이 다음 단계를 정하지 않는다. 수신기의 `status.prompt`, `zone.next`, `exam.next` 를 그대로 읽어 한 줄 안내로 보여 준다 (판단은 수신기 한 곳에만).

## 화면

| 화면 | 내용 |
|---|---|
| 연결 | 수신기 Wi-Fi 안내, 연결 상태 |
| 찾기 | 큰 단추 하나(찾기 시작), 단계 표시(탐지 → 확인 → 측정), 한 줄 안내, 멈춤 |
| 기기 | 의심 점수 순 목록, 근거 한 줄 |
| 시험장 설정 | 좌석 줄·칸·간격, 놓을 수 있는 곳 고르기, 저장한 교실 |
| 결과 | 2D 평면도(구역 또는 자리 후보 3개) + 'AR 로 보기' ([002](../002-ar-zone-display/spec.md)) |
| 정비 | 관절 움직이기, 원점, 판 0°, 끄기 |

## 검증

- 단위: ViewModel 상태 전이 (가짜 Repository).
- 계약: 가짜 수신기에 대고 모든 주소를 한 번씩.
- 손 시험: 시나리오 1·2 를 실제 수신기로.

## 위험

- 폰이 수신기 Wi-Fi(인터넷 없음)에 붙으면 안드로이드가 모바일 데이터로 돌려 버린다 → `ConnectivityManager.requestNetwork` 로 그 Wi-Fi 에 소켓을 묶는다.
