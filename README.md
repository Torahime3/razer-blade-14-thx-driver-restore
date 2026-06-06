# Razer Blade 14 (2022) THX Realtek Audio Driver Restore

This repository provides a clean backup/mirror of the original factory Realtek and THX Spatial Audio drivers extracted directly from a fully functional **Razer Blade 14 (2022)** running Windows 11.

> [!WARNING]
> **DISCLAIMER / INTELLECTUAL PROPERTY:**
> I do not own these drivers. All rights, software, copyrights, and trade names belong exclusively to **Razer Inc.**, **Realtek Semiconductor Corp.**, and **THX Ltd**. This repository is strictly intended as a non-commercial, community-driven hardware archive to help legitimate laptop owners restore functionalities omitted during OS transitions. If any rights holder wishes this archive to be removed, please open an issue and it will be taken down immediately.

## Why this exists
My personal Razer Blade 14 (2022) shipped with Windows 10 and featured perfectly tuned THX Spatial Audio processing. However, after performing a clean upgrade to **Windows 11**, the dedicated THX processing stack completely broke. While general audio was still coming out of the speakers, the spatial enhancement was gone, resulting in a flat, muddy, and significantly lower sound quality experience.

Because Razer does not separate or easily distribute these factory-embedded THX processing layers on their support site, finding a fix online was nearly impossible. Fortunately, I managed to get access to an identical twin laptop (Razer Blade 14 2022) that ran Windows 11 natively with the factory THX drivers intact. I successfully extracted the entire original driver catalog and force-injected it back onto my upgraded machine, fully restoring the premium sound stage. This repository is a share-back to the community to save you from the same headache.

> [!CAUTION]
> **HARDWARE COMPATIBILITY WARNING:**
> These drivers were extracted from a specific **Razer Blade 14 (2022)** model. Due to the extremely high level of hardware-to-driver binding (especially regarding Realtek's Audio Processing Objects / APO), **I cannot guarantee this will work on different laptop models or other Razer generations**. Use at your own risk.

## How to Install
Standard Windows Driver Update might refuse these files claiming *"The best drivers for your device are already installed"*. To bypass this and restore all secondary THX software components at once, follow these steps:

1. Download this repository as a ZIP archive and extract it anywhere on your machine (e.g., `C:\RazerDrivers`).
2. Open the Windows Start Menu, type **CMD**, right-click on *Command Prompt*, and select **Run as Administrator**.
3. Run the following command (make sure to replace the path with the exact folder where you extracted the files):

```cmd
pnputil /add-driver "C:\Path\To\Repository\drivers\*.inf" /subdirs /install
```

4. Let the prompt register and force-install all 90+ inf components (including `thxhdaudio.inf`, `hdx_razerext_thx`, and `thxrtapo.inf`).
5. Restart your computer.
6. Once the PC has rebooted, you will most likely need to manually reinstall the control interface from the Microsoft Store. You can download it directly via this official link: [THX Spatial Audio on the Microsoft Store](https://apps.microsoft.com/detail/9NC521C2JHDK?hl=neutral&gl=FR&ocid=pdpshare).

## Security
Since this repository involves installing system drivers via command line, it is perfectly normal to be cautious. You can easily verify the absolute integrity and authenticity of these files yourself before installing anything.

**Check the Digital Signatures (WHQL):**
I have not compiled, altered, or modified any of these files. They are strictly the original OEM binaries extracted from the system. Windows strictly enforces driver signing, and you can verify this manually:

1. Open any of the extracted driver folders.
2. Right-click on any `.sys` (System File), `.dll` (Application Extension), or `.cat` (Security Catalog) file.
3. Select **Properties**.
4. Go to the **Digital Signatures** tab.
5. You will see that all files are officially cryptographically signed by **Microsoft Windows Hardware Compatibility Publisher**, **Realtek Semiconductor Corp.**, or **Razer Inc.**
