<div align="center">

# 📱 DeteCam 앱

**수신기를 조종하고, 카메라가 있을 만한 곳을 AR 로 보여 주는 안드로이드 앱**

![Android](https://img.shields.io/badge/Android-8.0+-3DDC84?style=flat-square&logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![Compose](https://img.shields.io/badge/Jetpack_Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white)
![ARCore](https://img.shields.io/badge/ARCore-FF6F00?style=flat-square&logo=google&logoColor=white)
![상태](https://img.shields.io/badge/상태-스펙_작성-19C2B0?style=flat-square)

</div>

## 하는 일

| | |
|---|---|
| 🎛️ **조종** | 수신기의 Wi-Fi 에 붙어 탐지 → 확인 → 위치 측정을 시키고, 다음 할 일을 한 줄로 알려 준다 |
| 🧭 **자리 등록** | 수신기 등판의 마커를 비춰, 수신기가 방 어디에 어느 쪽을 보고 놓였는지 알아낸다 |
| 🫧 **AR 표시** | 카메라가 있을 만한 구역(시험장에서는 자리 후보 3곳)을 폰 화면 속 방 위에 겹쳐 그린다 |

## 지금 상태

스펙을 쓰는 단계다. 코드는 아직 없다. 수신기 쪽 주소(API)는 정해져 있고 가짜 수신기로 돌려 볼 수 있다 ([receiver](https://github.com/DeteCam/receiver)).

## 폴더

```
specs/     스펙: 001 수신기 조종, 002 AR 의심 구역 표시
docs/      앱 문서 (화면 설계, 주소 계약)
app/       안드로이드 프로젝트 (구현 단계에서 추가)
```

## 관련

- 일하는 규칙: [CONTRIBUTING](https://github.com/DeteCam/.github/blob/main/CONTRIBUTING.md)
- 시스템 전체: [docs](https://github.com/DeteCam/docs)
