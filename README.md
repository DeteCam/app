<div align="center">

# 📱 DeteCam 앱

**수신기를 조종하고, 카메라가 있을 만한 자리를 AR 로 보여 주는 안드로이드 앱**

![Android](https://img.shields.io/badge/Android-8.0+-3DDC84?style=flat-square&logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![Compose](https://img.shields.io/badge/Jetpack_Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white)
![ARCore](https://img.shields.io/badge/ARCore-FF6F00?style=flat-square&logo=google&logoColor=white)
![상태](https://img.shields.io/badge/상태-스펙-19C2B0?style=flat-square)

</div>

## 하는 일

| | |
|---|---|
| 🎛️ **조종** | 수신기(허브)의 Wi-Fi 에 붙어 찾기를 시키고, 의심 기기와 그 까닭을 보여 준다. 다음 할 일을 한 줄로 알려 준다 |
| 🧭 **패널 자리 등록** | 패널 앞덮개의 AR 마커를 비춰, 패널이 방 어디에 어느 쪽을 보고 걸렸는지 알아낸다 |
| 🗺️ **자리표 · 방 훑기** | 교실은 첫 자리와 끝 자리를 찍어 자리표를 만들고, 방은 벽과 천장을 훑어 겉면을 잡는다 |
| 🫧 **AR 표시** | 의심 자리 세 곳을 확률과 함께 폰 화면 속 방 위에 겹쳐 그린다. 교실은 책상 위에, 방은 벽·천장의 점에 |

![시스템 구성도](https://raw.githubusercontent.com/DeteCam/receiver/main/docs/images/%EC%84%A4%EA%B3%84%EB%8F%84_%EC%8B%9C%EC%8A%A4%ED%85%9C_%EA%B5%AC%EC%84%B1.png)

## 지금 상태

스펙 단계다. 코드는 아직 없다. 수신기와 주고받는 주소는 [주소 계약](docs/주소%20계약.md)에 정했고, 허브 쪽은 receiver 스펙 006 에서 이 표에 맞춘다.

범위(2026-11-18): AR 표시는 시험장과 숙소 모두에서 쓴다. 사진을 간간이 보내는 카메라와 영상을 실시간으로 보내는 카메라를 모두 다룬다. AR 화면은 녹화하지 않는다. 휴대폰 송신 경보는 권장이다 ([작품 범위](https://github.com/DeteCam/receiver/blob/main/docs/%EC%9E%91%ED%92%88%20%EB%B2%94%EC%9C%84.md)).데모에서 무엇을 보일지는 receiver 의 [데모 환경](https://github.com/DeteCam/receiver/blob/main/docs/%EB%8D%B0%EB%AA%A8%20%ED%99%98%EA%B2%BD.md)에 있다.

## 폴더

```
specs/     스펙: 001 수신기 조종, 002 AR 표시
docs/      앱 문서 (주소 계약)
app/       안드로이드 프로젝트 (구현 단계에서 추가)
```

## 관련

- 일하는 규칙: [CONTRIBUTING](https://github.com/DeteCam/.github/blob/main/CONTRIBUTING.md)
- 시스템 전체: [docs](https://github.com/DeteCam/docs) · 수신기의 설계도: [receiver](https://github.com/DeteCam/receiver/blob/main/docs/%EC%84%A4%EA%B3%84%EB%8F%84.md)
