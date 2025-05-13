# How to Disable VBS



https://www.tomshardware.com/how-to/disable-vbs-windows-11

## How to Check if VBS is Enabled in Windows 11 or 10

Before you start thinking about turning off VBS, you need to find out if it's on in the first place. 

1. **Open system information**. The easiest way to do that is by searching for "system information" in Windows search and clicking the top result.
   <img src="./How.to.Disable.VBS.assets/image-20240510012754529.png" alt="image-20240510012754529" style="zoom: 50%;" />

(Image credit: Future)

2. **Scroll down to find the "Virtualization-based security" row.** If it says "running," VBS is enabled. But if it says "not enabled," then you're done.
   <img src="./How.to.Disable.VBS.assets/image-20240510012822153.png" alt="image-20240510012822153" style="zoom:50%;" />





## How to Disable VBS / HVCI in Windows 11 or 10

1. **Search for Core Isolation** in Windows search and **click the top result**.
   <img src="./How.to.Disable.VBS.assets/image-20240510012856801.png" alt="image-20240510012856801" style="zoom:50%;" />

(Image credit: Future)

**2. Toggle Memory Integrity to off**, if it was on. If it is not on, skip ahead to step 6.
<img src="./How.to.Disable.VBS.assets/image-20240510012918600.png" alt="image-20240510012918600" style="zoom:50%;" />

(Image credit: Future)

3. **Reboot your PC** as prompted.

![reboot](./How.to.Disable.VBS.assets/CL8QLZCF2hkHBpRBSK6ZP6-320-80.png)

(Image credit: Future)

4. **Check system info** again to see if virtualization-based security is listed as "not enabled." If so, you are done. If not, go to step 6 where you'll disable VBS in the registry.
   <img src="./How.to.Disable.VBS.assets/image-20240510012822153.png" alt="image-20240510012822153" style="zoom:50%;" />

(Image credit: Future)

5. **Open regedit**. The easiest way is by hitting Windows + R, entering regedit in the text box and click Ok.
   <img src="./How.to.Disable.VBS.assets/image-20240510013031251.png" alt="image-20240510013031251" style="zoom:33%;" />

(Image credit: Future)

6. **Navigate to HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\DeviceGuard.**
   <img src="./How.to.Disable.VBS.assets/image-20240510013053069.png" alt="image-20240510013053069" style="zoom: 50%;" />

(Image credit: Future)

7. **Open EnableVirtualizationBasedSecurity** and **set it to 0.** 
   <img src="./How.to.Disable.VBS.assets/image-20240510013113892.png" alt="image-20240510013113892" style="zoom: 50%;" />

(Image credit: Future)

**If the entry does not exist, create a new one** with the key **EnableVirtualizationBasedSecurity**, value (DWORD 32-bit) 0.

<img src="./How.to.Disable.VBS.assets/image-20240510012638425.png" alt="image-20240510012638425" style="zoom: 50%;" />

8. Reset **WindowsHello**.
   ![win-hello](./How.to.Disable.VBS.assets/win-hello.webp) 
9. **Close regedit** and **reboot your PC**.
10. **Check system information again** to see if Virtualization Based Security is listed as  "not enabled." 
   <img src="./How.to.Disable.VBS.assets/image-20240510013201871.png" alt="image-20240510013201871" style="zoom:33%;" />

(Image credit: Future)

If VBS is still enabled try the method of disabling it below.

## How to Disable Windows VBS By Uninstalling Virtual Machine

If you still see that VBS is running, you can get rid of it by uninstalling the "Virtual Machine" feature in Windows. Note, however, that if this is the feature that's enabling VBS for you, losing it may cost you the ability to run Windows Subsystem for Linux. Here's how you do it.

1. **Open Turn Windows Features on or Off** by searching for it.
   <img src="./How.to.Disable.VBS.assets/image-20240510013225007.png" alt="image-20240510013225007" style="zoom: 33%;" />

(Image credit: Future)

2. **Uncheck Hyper-V, Virtual Machine Platform and Windows Hypervisor Platform** and **click Ok**.
   
   ![A screenshot of a computer  Description automatically generated](./How.to.Disable.VBS.assets/clip_image001.png)
    You **may or may not have Hyper-V** feature depending on your PC vendor’s customized installation of Windows.
   <img src="./How.to.Disable.VBS.assets/image-20240510012415520.png" alt="image-20240510012415520" style="zoom:50%;" />

(Image credit: Future)

3. **Reboot** your PC.
4. Download and unzip Device Guard and Credential Guard hardware readiness tool from https://www.microsoft.com/en-us/download/details.aspx?id=53337
5. Start PowerShell as an Administrator. `Set-ExecutionPolicy RemoteSigned` answer `Y`
6. Enter the folder that contains unzipped Device Guard and Credential Guard hardware readiness tool, then run `.\DG_Readiness_Tool_v3.6.ps1 -Disable`
7. **Check system information** again to make sure virtualization based security is listed as "not enabled."
8. **If your PC vendor is Lenovo, you may see VBS status is “Enabled but not running”. This is also acceptable.**
9. **If your PC vendor is Lenovo, after trying ALL the steps mentioned above and VBS is still enabled, you may need to perform a clean installation of Windows.**
