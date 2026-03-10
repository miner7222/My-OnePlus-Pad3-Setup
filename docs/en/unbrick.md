# Unbrick / Cross-Flash Guide (EDL Method)

⚠️ **MUST READ** This method is no longer available starting from OxygenOS 16.0.3.500 due to the introduction of Anti-Rollback (ARB). It remains functional on ColorOS 16.0.3.501, as ARB has not yet been implemented in that version.

This guide explains how to unbrick your device or convert between OnePlus Pad 2 Pro and OnePlus Pad 3 (Cross-flashing) using the EDL (Emergency Download) mode.

---

## **Prerequisites**
* **OplusEdlTool:** Download the latest version from [here](https://static-tcdn.anteasy.com/xasdun/upload-log/oet-upload.html).
* **Firehose files:** Download `oppo_oneplus_realme_Files.rar` from [here](https://xdaforums.com/t/oppo-oneplus-realme-qualcomm-files-share.4769736/).
* **EDL package:** The target firmware you wish to flash.
    * [OnePlus Pad 3 (OPD2415)](https://dfs-serverauto-in.allawnofs.com/dfs/25/05/12/ec3fb9a938c3462abe962c37a179d92b.zip)
    * [OnePlus Pad 2 Pro (OPD2413)](https://dfs-serverauto-in.allawnofs.com/dfs/25/08/05/5c568cdb9436442796dac8f2d0eae4ac.zip)
* **ocdt.img (Optional):** Required if converting between Pad 2 Pro and Pad 3 to fix stylus compatibility. Download it from [here](https://drive.google.com/file/d/1SR0xg_MQtoSDGPM2XUGgo9vw3TpaVwUo/view?usp=sharing).

---

## **Instructions**

### **1. Setup the Tool**
Extract `OplusEdlTool` and the `oppo_oneplus_realme_Files.rar`.
Run `OplusEdlTool.exe` from the extracted folder.

**Configure the file paths in the tool:**
* **Device Programmer:** Select `OPPO_SM8750_V1.0.05.melf` located in `oppo_oneplus_realme_Files\SM8750_8E`.
* **Digest:** Select `OPPO_SM8750_Digest.elf`.
* **Sig:** Select `OPPO_SM8750_Sign.bin`.

![Image: OplusEdlTool Configuration Interface](../edl.png)

### **2. Enter EDL Mode**
Reboot your device into EDL mode.
* If the device is hard-bricked (no boot logo), you may need a special cable like the "Hydra Pro v2 EDL cable".

### **3. Port Detection & Registry Fix**
Open **Device Manager** on Windows and check for `Qualcomm HS-USB QDLoader 9008 (COM)`.

> **⚠️ Important Bug Fix**
> The tool has a bug where it fails to detect the port if there is no space between `9008` and the parenthesis `(COM)`.
> * **Bad:** `Qualcomm HS-USB QDLoader 9008(COM3)`
> * **Good:** `Qualcomm HS-USB QDLoader 9008 (COM3)`

**How to fix:**
1.  Open Registry Editor (`Win + R`, type `regedit`).
2.  Navigate to: `Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USB\VID_05C6&PID_9008`.
3.  Go into the subfolder and modify the `FriendlyName` value.
4.  Add a space before the `(COM...)` part.
5.  Disconnect and reconnect the cable. The tool should now detect the port.

![Image: Registry Editor FriendlyName Fix](../edl2.png)

### **4. Connect to Firehose**
Once the port is detected in the top right of the tool:
1.  Click the **[Enter Firehose]** button.
2.  Check the log. Once it says "Firehose mode success", the device will stay in EDL mode securely.

### **5. Backup Critical Partitions**
**Do not skip this step.**
1.  Click **[Read Partitions]**, then click **[Auto]** to list the device partitions.
2.  Select important partitions such as `modemst1`, `modemst2`, `ocdt`, `persist`, `frp`, `param`, `secdata`, etc.
3.  Click **[Read Selected]** to extract and save them.

### **6. Select ROM and Flashing**
1.  Select the folder containing your uncompressed EDL package in the tool.
2.  Click **[All]**, then click **[Load]**.
3.  The partition list on the right will update. Generally, you do not need to touch this unless you know what you are doing.

**For Cross-Flashing (Pad 2 Pro <-> Pad 3):**
If you are converting the device, you must flash the specific `ocdt` image to prevent stylus issues.
1.  Download appropriate image:
    * **Installing OxygenOS (Global) on Pad 2 Pro:** Select `ocdt_opd2415_global.img`.
    * **Installing ColorOS (CN) on Pad 3:** Select `ocdt_opd2413_cn.img`.
2.  In the partition list, find `ocdt` and double-click it to select the image.
3.  Ensure the checkmark for `ocdt` is selected.

### **7. Start Flash**
1.  Ensure you have backed up important partitions (Step 5).
2.  Check **[Auto reboot after flash]**.
3.  Click the **[Start Flash]** button.

The device will reboot automatically once flashing is complete.

### **8. Troubleshooting**
If the device hangs at the boot logo after flashing, boot into Recovery Mode manually and perform a data wipe (Factory Reset).

Note that this method can be performed without unlocking the bootloader, but access to the bootloader (fastboot) will be blocked afterwards. To fix this, **do not install any OTA updates** and follow the method below:

https://xdaforums.com/t/cn-to-glo-permanantly-fixing-stylus-without-module-and-keep-fastboot.4780607/