# 루팅

## 사전 요구사항
- [부트로더 잠금 해제](./unlock.md)

---

### **LKM 모드**

1.  ROM 아카이브에서 현재 ColorOS/OxygenOS 버전에 맞는 전체 OTA zip 파일을 다운로드합니다.

2.  [otaripper](https://github.com/syedinsaf/otaripper/releases)를 사용하여 `ota.zip`에서 `init_boot.img` 파일을 추출합니다.
    ```
    otaripper ota.zip --partitions init_boot
    ```

3.  추출한 `init_boot.img`를 기기의 내부 저장소로 복사합니다.

4.  최신 [ReSukiSU 매니저](https://nightly.link/ReSukiSU/ReSukiSU/workflows/build-manager/main/Spoofed-Manager-release)를 다운로드하여 설치합니다.

5.  ReSukiSU 앱을 열고 우측 상단의 **설치** 버튼을 누른 뒤, `init_boot.img`를 선택하여 패치를 시작합니다.

6.  `Downloads` 폴더에 `kernelsu_next_patched_{date}_{time}.img`라는 이름의 패치된 파일이 생성됩니다. 이 파일을 다시 PC로 복사합니다.

7.  기기를 Fastboot 모드로 부팅하고 PC에 연결합니다.

8.  터미널에서 다음 명령어를 실행하여 패치된 이미지를 플래싱합니다:

    ```
    fastboot flash init_boot kernelsu_patched_{date}_{time}.img
    ```

9.  플래싱이 성공하면 기기를 재부팅합니다:

    ```
    fastboot continue
    ```

---

### **GKI 모드**

1.  [OnePlus_KernelSU_SUSFS](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS)에서 `AK3_OP-PAD-2-PRO*.zip` 또는 `AK3_OP-PAD-3*.zip`을 다운로드합니다.
2.  해당 저장소에 있는 **설치 가이드(Installation Instructions)**를 따라 설치를 진행합니다.

---

### **루팅 유지하며 OTA 업데이트**

OTA 또는 로컬 업데이트가 설치된 후, **절대로 재부팅하지 마세요.**

#### **LKM 모드의 경우**
ReSukiSU 앱을 엽니다. 우측 상단의 **설치** 버튼을 누른 후, **설치 -> 비활성 슬롯에 설치**를 선택합니다. 완료되면 기기를 재부팅합니다.

#### **GKI 모드의 경우**
[Kernel Flasher](https://github.com/fatalcoder524/KernelFlasher)를 사용하여 AK3 zip 파일을 **비활성 슬롯**에 설치합니다.

업데이트가 적용되고 루팅 권한도 유지됩니다.