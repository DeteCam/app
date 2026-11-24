# DeteCam 6.0 (`Nano-2 AI`) — AR-OPA-2 최적 배치 & 3D 가상 거울·AR 탐지 앱

> 스마트폰 1대로 **단 2기 포켓 수신기(`9.6 cm`)**의 벽면 부착 위치·15° 클릭 각도를 15초 만에 안내하고,
> `CamGuard-Net` + 5초 `CamLoPA` 인과 판별 결과와 `MA-PINN` 가상 거울 앵커·`RAPS 90%` AR 신뢰 구역을 실시간 오버레이합니다.

## 1. 앱 핵심 기능 (DeteCam 6.0 `Nano-2 AI`)
1. **5초 AR 스캔 → `AR-OPA-2` 단 2기 벽면 최적 배치**: 방 네 모서리·장애물(L자 코너·기둥·거울·철제 사물함·칠판)을 스캔해 직선 LoS + 1차 가상 거울 가시성을 동시 최적화한 **2개 AR 가이드 박스 + Pan/Tilt 클릭 각도**를 0.1초 표시.
2. **3초 상호 교정 (`Auto-Verify`)**: 2기 노드 간 테스트 패킷으로 벽 속 숨은 철근·배관 반사를 탐지하고, 이상 시 *"옆으로 40 cm 이동"* 안내.
3. **5초 `CamLoPA` 인과 자극 마법사**: *"조명을 5초간 껐다 켜주세요 / 방 안에서 손을 흔들어 주세요"* 버튼 1회로 `CamGuard-Net` F1 `98.88%` 카메라 확정.
4. **선택적 0원 5초 보행 정밀 모드 (프라이빗 룸)**: 스마트폰을 들고 방 안을 3걸음 걸으면 ARCore 궤적+RSSI 경사를 자동 융합해 2.45/5.22 GHz P90 `0.50~0.65 m` (`≤1m 96.4~98.2%`) 달성.
5. **`RAPS 90%` Conformal AR + 가상 거울 경로 시각화**: L자 코너 뒤 사각지대 카메라도 거울 반사선과 90% 신뢰 구역으로 직관 표시.

## 2. 문서 및 사양
- [`docs/주소 계약.md`](docs/주소%20계약.md) — 앱 ↔ `Nano-2` 2기 노드 REST/WebSocket API 계약
- [`specs/001-receiver-control/spec.md`](specs/001-receiver-control/spec.md) — 2기 `NanoPi R5C` 제어·동기화·`Auto-Verify` 사양
- [`specs/002-ar-opa-and-display/spec.md`](specs/002-ar-opa-and-display/spec.md) — `AR-OPA-2` + 0원 보행 융합 + `RAPS 90%` AR 표시 사양
