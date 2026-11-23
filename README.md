# Universal OBD-II Dashboard PWA

## 실행
1. 파일을 HTTPS를 지원하는 정적 호스팅(GitHub Pages, Cloudflare Pages 등)에 업로드합니다.
2. Android의 Web Bluetooth 지원 브라우저에서 접속합니다.
3. 브라우저 메뉴에서 홈 화면에 추가/앱 설치를 선택합니다.
4. CONNECT OBD-II를 눌러 BLE 장치를 직접 선택합니다.

## 현재 범위와 제한
- 반응형 모바일 대시보드, PWA manifest, Service Worker 오프라인 캐시 포함.
- Web Bluetooth 기반 BLE 장치 검색은 acceptAllDevices 방식으로 제조사 이름을 제한하지 않습니다.
- 알려진 ELM BLE GATT 프로파일(FFF0/FFE0/Nordic UART/일부 18F0 계열)을 우선 탐색합니다.
- 모든 BLE 어댑터가 동일한 GATT 서비스/특성을 쓰는 것은 아니므로, 알 수 없는 BLE 프로파일은 연결되지 않을 수 있습니다.
- Bluetooth Classic SPP와 Wi-Fi OBD 어댑터는 브라우저 Web Bluetooth로 직접 연결할 수 없습니다.
- ELM327 호환 AT 명령과 표준 OBD-II PID 중심입니다. 제조사 확장 PID는 아직 구현하지 않았습니다.
- 지원 PID 응답을 실제로 받지 못하면 해당 값은 대시보드에서 대시(—)로 표시됩니다.
- Boost는 MAP(흡기 매니폴드 절대압) - BARO(대기압)로 계산합니다. MAP/BARO 미지원 시 계산할 수 없습니다.
- 오일 온도 PID 0x5C는 차량 ECU가 지원할 때만 표시됩니다.

## 안전 및 검증
- 주행 중 연결/조작하지 마십시오.
- 최초 테스트는 정차 상태에서 시행하십시오.
- 응답시간과 PID 지원 여부는 차량/어댑터/ECU에 따라 달라집니다.
- 현재는 실험용 첫 PWA 버전이며, 여러 제조사 어댑터와 차량에서 검증이 필요합니다.
