Here is the complete, start-to-finish master guide to permanently fix and lock in the internal speaker audio on a Lenovo ThinkPad X390 Yoga running Windows 11 LTSC.

---

### Step 1: Install the Intel Serial IO / Chipset Driver (Foundation)

_Without this prerequisite driver, Windows cannot communicate with the audio chip via the system bus, causing internal speakers to disappear completely._

1. Open your web browser and navigate to `[https://pcsupport.lenovo.com](https://pcsupport.lenovo.com)`.
2. Search for **ThinkPad X390 Yoga**.
3. Go to **Drivers & Software** $\rightarrow$ **Manual Update** $\rightarrow$ **Motherboard Devices (Backplanes, core chipset, onboard video, PCIe switches)**.
4. Download the **Intel Serial IO Driver** package (`1.34 MB`, Version `30.100.1947.3`).
5. Open the downloaded `.exe` file, click **Next** through the setup wizard, and complete the installation.
6. **Restart your laptop.**

_Verification:_ Open **Device Manager** (`Win + X` $\rightarrow$ **Device Manager**). Any missing hardware under **Other devices** (like _PCI Data Acquisition..._) will be cleared.

---

### Step 2: Download and Install the Official Realtek Audio Driver

_This installs the exact Lenovo driver package tailored for the X390 Yoga's hardware components._

1. Return to the Lenovo Support page for the **ThinkPad X390 Yoga**.
2. Navigate to **Drivers & Software** $\rightarrow$ **Manual Update** $\rightarrow$ **Audio**.
3. Download the **Realtek Audio Driver for Windows 11 / 10** (`238.36 MB`, Version `6.0.9430.1`).
4. Open the downloaded installer file (`.exe`), follow the setup prompts (Click **Next** $\rightarrow$ **Accept** $\rightarrow$ **Install**).
5. **Restart your laptop** when prompted by the setup wizard.

_Verification:_ Open **Device Manager** $\rightarrow$ expand **Sound, video and game controllers**. You will see **Realtek(R) Audio** listed.

---

### Step 3: Force Assign the Lenovo Driver in Device Manager

_If Windows caches a generic driver or grays out the device, force Windows to attach to the official Lenovo driver files._

1. Press `Win + X` and select **Device Manager**.
2. Click **View** on the top menu bar $\rightarrow$ select **Show hidden devices**.
3. Expand **Sound, video and game controllers**.
4. Right-click **Realtek(R) Audio** (or _High Definition Audio Device_) and select **Update driver**.
5. Select **Browse my computer for drivers**.
6. Click **Let me pick from a list of available drivers on my computer**.
7. Ensure **Show compatible hardware** is checked.
8. Highlight **Realtek(R) Audio** (Version `6.0.9430.1`) and click **Next**.
9. Once Windows displays **"Successfully updated your drivers,"** close the window.

_Verification:_ The device icon will change to solid color (no longer grayed out).

---

### Step 4: Configure Sound Control Panel & Set Speaker Default

_Ensure Windows routes audio output through the built-in speakers._

1. Press `Win + R`, type `mmsys.cpl`, and press **Enter**.
2. Under the **Playback** tab, right-click on any empty space inside the box and check both **Show Disabled Devices** and **Show Disconnected Devices**.
3. Locate **Speakers (Realtek(R) Audio)**.
4. If disabled, right-click **Speakers** $\rightarrow$ select **Enable**.
5. Check for a green checkmark next to **Speakers**. If it displays a telephone icon, right-click **Speakers** $\rightarrow$ select **Set as Default Device**.
6. Right-click **Speakers** $\rightarrow$ select **Test**.

_Verification:_ You will hear test chime tones directly through your laptop's built-in speakers.

---

### Step 5: Stop Windows Update from Overwriting/Deactivating the Driver

_Prevents Windows Update from silently replacing your working Lenovo driver with generic Microsoft drivers during background system updates._

1. Press `Win + R`, type `sysdm.cpl`, and press **Enter**.
2. Go to the **Hardware** tab and click **Device Installation Settings**.
3. Select **No (your device might not work as expected)**.
4. Click **Save Changes**, then click **Apply** and **OK**.

_Verification:_ Windows Update will no longer automatically replace or deactivate your manually installed Realtek audio driver.

---

### Step 6: Prevent Audio Service Crash Disconnections

_Ensures Windows automatically restarts the audio engine if the driver drops out after sleep or idle states._

1. Press `Win + R`, type `services.msc`, and press **Enter**.
2. Scroll down and locate **Windows Audio**.
3. Right-click **Windows Audio** $\rightarrow$ select **Properties**.
4. Go to the **Recovery** tab.
5. Set **First failure**, **Second failure**, and **Subsequent failures** to **Restart the Service**.
6. Click **Apply** and **OK**.
7. Repeat the exact same steps for **Windows Audio Endpoint Builder**.

_Verification:_ If an audio service crashes or becomes idle, Windows will instantly restore speaker functionality without requiring a reboot or driver update.

F!iSc*RnMx$uR^xGC*63
(F!iSc*RnMx$uR^xGC*63)

rather penalty trip neither rule inquiry
hill tower million bean model aisle
