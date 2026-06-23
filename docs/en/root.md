# Root

## Prerequisites
- [Unlock Bootloader](./unlock.md)

---

### **LKM Mode**

1.  Download the Full OTA zip corresponding to your current ColorOS/OxygenOS version from the ROM Archive.

2.  Use [otaripper](https://github.com/syedinsaf/otaripper/releases) to extract the `init_boot.img` files from the `ota.zip`.
    ```
    otaripper ota.zip --partitions init_boot
    ```

3.  Copy the extracted `init_boot.img` to your device's internal storage.

4.  Download and install the latest [ReSukiSU manager](https://nightly.link/ReSukiSU/ReSukiSU/workflows/build-manager/main/Spoofed-Manager-release).

5.  Open ReSukiSU app, tap **Install** button in the top right, and select the `init_boot.img` to begin patching.

6.  A patched file named `kernelsu_next_patched_{date}_{time}.img` will be created in your device's `Downloads` folder. Copy this file back to your PC.

7.  Boot your device into Fastboot mode and connect it to your PC.

8.  In your terminal, run the following commands to flash the patched image:

    ```
    fastboot flash init_boot kernelsu_patched_{date}_{time}.img
    ```

9.  If the flashing is successful, reboot your device:

    ```
    fastboot continue
    ```

---

### **GKI Mode**

1.  Download `AK3_OP-PAD-2-PRO*.zip` or `AK3_OP-PAD-3*.zip` from [OnePlus_KernelSU_SUSFS](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS).
2.  Follow the **Installation Instructions** provided in the repository to install it.

---

### **How to Install OTA while Maintaining Root**

After an OTA or local update is installed, **do not reboot**.

#### **For LKM Mode**
Open the ReSukiSU app. Tap the **Install** button in the top right, then go to **Install** -> **Install to Inactive Slot**. After it finishes, reboot the device.

#### **For GKI Mode**
Use [Kernel Flasher](https://github.com/fatalcoder524/KernelFlasher) to install the AK3 zip file to the **Inactive Slot**.

The update will be applied, and root access will be maintained.
