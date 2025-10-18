# ⚡ Ultimate Guide to Optimizing Windows 11

Turn any low-end PC into a fast, lightweight machine by **debloating Windows, disabling unnecessary services, and applying tweaks**.  

<br>

> ⚠️ **Warning:** Advanced modifications. Backup all important data before proceeding.

<br>

## 📑 Table of Contents

| Section | Description |
|---------|-------------|
| **1️⃣ Required Files & Tools** | Tools needed before starting. |
| **2️⃣ Prepare Bootable USB** | Create Windows 11 USB with unattended XML. |
| **3️⃣ BIOS & Installation** | Install Windows 11 cleanly. |
| **4️⃣ Atlas OS Optimization** | Strip useless services & processes. |
| **5️⃣ Chris Titus Tweaks** | Standard & advanced Windows optimizations. |
| **6️⃣ Disable Useless Services** | Stop unnecessary background services. |
| **7️⃣ RAM Registry Optimization** | Reduce process count via registry tweaks. |
| **8️⃣ Optional: Disable Windows Updates Completely** | Prevent Windows from reinstalling drivers/updates (advanced users only). |
| **9️⃣ Final Cleanup** | Disable startup apps and finalize system. |

<br>

## 1️⃣ Required Files & Tools

- **Rufus** → [Download Rufus](https://rufus.ie/)  
- **Windows 11 24H2 ISO** → [Download ISO](https://windows-11.en.uptodown.com/windows/download/1029251675)  
- **Unattended XML** → [autounattend.xml](https://github.com/memstechtips/UnattendedWinstall/blob/main/autounattend.xml)  
- **Atlas OS** (AME Wizard + Playbook `.apbx`)  [Download Atlas OS](https://atlason.net)
> 💡 **Note**: Download all the folders above in the repository 

<br>

## 2️⃣ Prepare Bootable USB

1. Install **Rufus**.  
2. Load your **Windows 11 ISO** in Rufus and extract to USB.  
3. Copy `autounattend.xml` **directly to the root of the USB**.  

> This ensures Windows installation automatically removes bloatware via PowerShell scripts.

<br>

## 3️⃣ BIOS & Windows Installation

1. Restart PC → Enter BIOS (`F2` or `DEL`).  
2. Set USB as the first boot device.  
3. Install Windows 11:
   - Select language, region, keyboard layout.
   - Create a **local account**.
   - Set security questions.

✅ After installation:
- Wait 2–3 minutes for scripts to run.  
- Click popup to **restart**.

<br>

## 4️⃣ Atlas OS Optimization 🛠️

1. Open Atlas OS folder:
   - Run `AME Wizard Beta.exe`.
   - Drag `AtlasPlaybook_v0.4.1.apbx` into the top-left.  
2. Configure:
   - **Microsoft Defender:** Optional to disable (frees up resources).  
   - **Windows Updates:** Disable recommended.  
   - **Windows Mitigations:** Disable on older CPUs. Kepp recommended for newer CPUs.  
   - **Power settings:** Leave default.  
   - **Edge / Browser:** Highly recommened to remove Edge. Brave is recommended for privacy and performance, but you can choose any browser you prefer.
   
3. Click `Next` → Wait for installation to finish.  

### Post-Installation:
- Customize wallpaper, taskbar, lock screen.  
- Delete Atlas logo in `Customize Windows > User Account Pictures` folder if desired.  
- Edit system info via `Edit System Information.ps1`.
  
<br>

> 💡 **Note:**  
> If you’re on a **laptop** and your **main screen appears black or low resolution** after installing Atlas OS, don’t panic — it’s completely normal.  
> This happens because Windows hasn’t installed your **graphics drivers** yet.  
> 
> Simply connect to Wi-Fi (if needed) and manually install your GPU drivers:
> - 🟩 **NVIDIA laptops:** [NVIDIA Drivers](https://www.nvidia.com/Download/index.aspx)  
> - 🔵 **AMD laptops:** [AMD Drivers](https://www.amd.com/en/support)  
> - ⚪ **Intel laptops:** [Intel Drivers](https://www.intel.com/content/www/us/en/download-center/home.html)  
> 
> After installing and restarting, your display should return to normal with proper resolution and performance.

<br>

## 5️⃣ Chris Titus Tweaks ⚡

1. Go to the `Optimize Windows` folder located on your desktop.  
2. Right-click on the **Chris Titus Tool** PowerShell script and select **Run with PowerShell**.  
3. Once the tool launches, follow these steps carefully:  

   - **Install Required Apps:**  
     Choose any apps you may need for daily use (e.g., 7zip, Notepad++, etc.).  
     Only install what’s essential — this step ensures a lightweight setup.  

   - **Standard Tweaks:**  
     Click on the **Standard** button.  
     This will automatically disable several unnecessary background services, telemetry, and other performance-killing features.  

   - **Advanced Tweaks:**  
     After applying the Standard tweaks, open the **Advanced** section.  
     Enable the options **onl** from *“Disable Teredo”* down to *“Set Display for Performance”*.  
     Then, enable the **last four tweaks** and click on **Run Tweaks**.  
     Wait patiently until all scripts complete — this may take a few minutes.  

> 💡 These tweaks dramatically reduce background tasks, improve boot times, and enhance overall system responsiveness.

<br>

## 6️⃣ Disable Useless Services

- Run `Disable Useless Services.ps1`.  
- ⚠️ **Note:** `Spooler` service is for printing — re-enable in Services app if needed.

<br>

## 7️⃣ RAM Registry Optimization 🖥️

1. Run `Edit RAM Value - Registry.ps1`.  
2. Modify `SvcHostSplitThresholdInKB` based on RAM:

| RAM | Value |
|-----|-------|
| 4GB  | 400000 |
| 6GB  | 600000 |
| 8GB  | 800000 |
| 12GB | C00000 |
| 16GB | 1000000 |
| 24GB | 1800000 |
| 32GB | 2000000 |
| 64GB | 4000000 |

> Reduces process count and optimizes memory usage.

<br>

## 8️⃣ Optional: Disable Windows Updates Completely 

> ⚠️ **Advanced and Risky — Proceed with Caution**

Windows has multiple fallback update systems that often **override** user settings and re-enable updates over time.  
Even after using Atlas OS, Windows may **revert** your optimization changes by reinstalling bloatware, telemetry, background drivers, and third-party software (like Tobii Eye Tracker, Intel Services, or Thunderbolt utilities).  
These services run silently in the background and can **severely impact performance**.  

<br>

### 🔧 Why Disable Updates
Disabling Windows Updates ensures that:
- Atlas OS and your performance tweaks **remain intact**.  
- Windows won’t automatically install **unwanted drivers or background services**.  
- You maintain **full control** over what’s running on your PC.  

<br>

### 🪜 Step-by-Step Instructions

1. **Run O&O ShutUp from Chris Titus Tool**:
   - Run the Chris Titus tool with powershell from `Optimize Windows` Folder
   - Open the **Tweaks → Advanced** section at the bottom of CTT.  
   - Launch **O&O ShutUp**.  
   - Go to the **Local Machine** section.  
   - **Disable everything** in the **Windows Update section**, making sure **all buttons turn green** *(indicating “disabled”)*.  

2. Open the folder named `Stop Windows Update`.  
3. Inside, you’ll see several shortcuts — each points to a protected Windows folder that controls update services.  
4. Start with the **Servicing** folder:
   - Double-click to open it, then go up one directory by clicking on the **Windows** breadcrumb path at the top.  
   - Right-click the **Servicing** folder → **Take Ownership**.  
   - Right-click again → **Properties → Security → Advanced**.  
   - In the permission entries box, select any entry that says **SYSTEM**, then click **Disable Inheritance**.  
   - Choose **Convert inherited permissions into explicit permissions**, then remove all **SYSTEM** entries one by one.  
5. Repeat the exact same steps for every shortcut inside the `Stop Windows Update` folder, **except** the one leading to `System32`.  

6. Open the `System32` shortcut folder:
   - Use the search bar (top right) to find these files:
     - `wuauclt.exe`
     - `usoclient.exe`
     - `dosvc.exe`
   - For each file:
     - Right-click → **Take Ownership**.  
     - Right-click again → **Properties → Security → Advanced**.  
     - Disable inheritance, convert permissions, and remove all **SYSTEM** entries.  

7. Once finished, run the file:
   - `Disable Updates and Driver Installation.bat`  
   - Right-click → **Run as Administrator**.  

8. When the script completes, **restart your PC**.

> 💡 **Note**: If you see a `ctfmon.exe` error popup, run the `Suppress Windows Errors.reg` in `Stop Windows Update` folder to make it stop.

   <br>
   
### ✅ Results
- Windows Update will now be **completely disabled** (including fallback services).  
- Your system will remain stable and lightweight, with **no background driver or telemetry reinstalls**.  
- Task Manager should now show **around 50–70 processes total** (depending on your setup).  

> 💡 **Tip**: You can still manually update apps or drivers later if needed — just be careful not to re-enable Windows Update accidentally.

<br>

## 9️⃣ Final Cleanup 🧹

- Disable all startup apps: `Settings > Apps > Startup`.  
- Verify unnecessary processes are gone.  
- Enjoy your **fast, lightweight, and optimized Windows 11** system.  
