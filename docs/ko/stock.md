# ColorOS/OxygenOS 팁

## **게임 어시스턴트가 어디에 있나요?**

OnePlus Pad 3에는 게임 어시스턴트 앱이 사전 설치되어 있지 않습니다.

OnePlus Pad 2 Pro에는 사전 설치되어 있지만, 중국어 콘텐츠가 과도하게 포함되어 있습니다. 핵심 기능은 유지하면서 Google Play 스토어에서 업데이트하는 것이 훨씬 좋습니다.

1. Google Play 스토어에서 [Games by HeyTap](https://play.google.com/store/apps/details?id=com.oplus.games)을 설치/업데이트하세요.

---

## **램 확장 비활성화**
16GB RAM 모델을 사용하는 경우 (사용 패턴에 따라 12GB 모델도 포함), 더 나은 성능을 위해 램 확장 기능을 끄는 것이 권장됩니다.

끄는 방법: `설정 > 기기 정보 > RAM > 램 확장`

---

## ~~**권한 모니터링 비활성화**~~
~~COS/OOS에는 순정 안드로이드보다 훨씬 제한적이고 공격적인 자체 권한 모니터링 시스템이 포함되어 있습니다.~~

~~보안을 위한 기능이지만, 고급 도구(예: Shizuku)나 특정 ADB 명령어 같은 파워 유저 기능을 사용할 때 과도한 제약으로 작용하여 방해가 되곤 합니다.~~

~~개발자 옵션에서 '권한 모니터링 비활성화'를 켜면 이러한 과도한 제어를 우회할 수 있습니다. 이를 통해 불편함을 해소하고 시스템 커스터마이징이나 고급 애플리케이션 사용에 더 큰 자유를 얻을 수 있습니다.~~

이 옵션을 활성화하지 말거나 이미 그렇게 했다면 비활성화하세요. v16.0.5.xxx부터는 이 옵션을 활성화하면 디스플레이 설정이 올바르게 표시되지 않습니다.

---

## **Google Discover 비활성화**
이 팁은 COS/OOS 16에서만 유효합니다.

위의 '권한 모니터링 비활성화'를 진행하고, USB 디버깅을 켠 뒤 PC에 연결하세요.

ADB가 있는 경로에서 명령 프롬프트(CMD)를 열고 다음 명령어를 입력하세요:

```
adb shell settings put secure assistant_screen_type 0
adb shell settings put secure assistant_screen_type_left_enable 0
```
