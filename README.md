# DeteCam app — 스마트폰 앱

수신기를 무선으로 조종하고, 폰 AR로 방 지도를 만들며, 카메라 방향과 의심 구역을 AR 화면에 보여 주는 앱입니다.

> 상태(2026-11-24): **명세 단계.** 수신기 설계가 스위치 고리로 바뀌어 주소 계약과 스펙을 새로 썼습니다. 이전(v6)의 2기 벽 부착 배치 추천, 폰 들고 걷기 보정은 뺐습니다. 작업 기준은 [docs/AGENTS.md](https://github.com/DeteCam/docs/blob/main/AGENTS.md)입니다.

## 기능

1. **방 지도**: ARCore로 바닥 · 벽 · 천장 평면을 잡아 방 크기를 얻고, 수신기를 둔 위치와 방향을 표시받는다.
2. **수신기 조종**: 의심 기기 목록 보기, 측정 시작 · 중지, 자극 안내(조명 끄기 등), 현장 보정 진행.
3. **AR 표시**: 수신기에서 나가는 방향 부채꼴, 두 자리 이상을 합친 의심 구역, 믿을 만한 정도를 함께 보여 준다. 결과는 "의심"으로 표시한다.

사용자는 측정 중 돌아다니지 않는다. 폰은 방 지도를 만들 때와 결과를 볼 때 쓴다.

## 문서
- [`docs/주소 계약.md`](docs/주소%20계약.md) — 앱 ↔ 수신기 주소(API)
- [`specs/001-receiver-control/spec.md`](specs/001-receiver-control/spec.md) — 수신기 조종
- [`specs/002-ar-opa-and-display/spec.md`](specs/002-ar-opa-and-display/spec.md) — 방 지도와 AR 표시
