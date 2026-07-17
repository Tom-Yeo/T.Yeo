# Project 00 - Windows 11 USB Media and Clean Build

## Project Overview

This project demonstrates the preparation of bootable Windows 11 installation media and the completion of a clean Windows 11 build on a physical device.

The project covers:

* Pre-build planning and data protection
* Windows 11 installation media creation
* USB boot and UEFI configuration
* Clean Windows 11 installation
* Initial Windows setup
* Driver installation and validation
* Windows Update completion
* Windows activation checks
* Device health and security validation
* Build documentation and evidence collection
* Preparation for future Microsoft Intune or Windows Autopilot enrolment

This project establishes the physical device and operating system foundation required before later endpoint management projects are completed.

## Project Status

In Progress

## Project Location

`projects/project-00-windows-11-clean-build`

## Objectives

The objectives of this project are to:

* Confirm that the target device meets the Windows 11 hardware requirements
* Protect any existing data before rebuilding the device
* Create bootable Windows 11 installation media
* Configure the device to boot from USB media using UEFI
* Complete a clean installation of Windows 11
* Remove previous operating system partitions where appropriate
* Complete the Windows Out-of-Box Experience
* Install and validate the required hardware drivers
* Install all available Windows quality and security updates
* Confirm that Windows is activated
* Confirm that Device Manager contains no unresolved hardware issues
* Validate basic device health and Windows security readiness
* Document the build process and collect supporting evidence
* Prepare the device for future Microsoft Intune or Windows Autopilot enrolment

## Technologies Used

* Windows 11
* Microsoft Windows 11 Media Creation Tool
* Windows Setup
* Unified Extensible Firmware Interface
* Windows Update
* Device Manager
* Windows Security
* PowerShell
* Command Prompt

## Build Summary

| Component | Configuration |
| --- | --- |
| Operating system | Windows 11 |
| Installation type | Clean installation |
| Installation media | Bootable USB |
| Firmware mode | UEFI |
| Partition format | GPT |
| Secure Boot | Enabled where supported |
| Trusted Platform Module | TPM 2.0 where supported |
| Driver source | Windows Update and device manufacturer |
| Update source | Windows Update |
| Device state after build | Standalone Windows 11 device |
| Future management state | Ready for Intune or Autopilot preparation |

The exact Windows edition, version, operating system build, device model and firmware version should be recorded during the build.

## Build Design

The device is rebuilt from bootable USB installation media rather than upgraded from an existing Windows installation.

A clean installation is used to:

* Remove the previous Windows installation
* Eliminate inherited configuration problems
* Start from a known operating system state
* Validate the complete installation process
* Confirm that required hardware is detected correctly
* Create a suitable baseline for future endpoint management work

## Pre-Build Preparation

### Data Protection

A clean installation can remove the existing operating system, applications, settings and user data.

Before starting the rebuild:

* Confirm that the correct device has been selected
* Back up any required user data
* Confirm that the backup can be accessed
* Record any required application or licence information
* Record the current Windows edition where relevant
* Confirm that recovery keys or encrypted data are not required after the rebuild
* Disconnect unnecessary external storage devices
* Ensure that the device is connected to power

No confidential information, product keys, recovery keys, usernames, email addresses or device identifiers should be exposed in screenshots committed to the public repository.

### Hardware Readiness

The following hardware and firmware checks should be completed:

* Confirm that the processor is suitable for Windows 11
* Confirm that sufficient memory is installed
* Confirm that sufficient storage is available
* Confirm that UEFI firmware is available
* Confirm that Secure Boot is supported
* Confirm that TPM 2.0 is present and enabled
* Confirm that the device can boot from USB
* Confirm that the device battery and power supply are reliable
* Record the device manufacturer and model

Where the device does not meet a Windows 11 requirement, the limitation should be documented rather than bypassed without explanation.

## Windows 11 Installation Media

### Media Type

Bootable USB flash drive.

### Recommended Preparation

The USB drive should:

* Have sufficient capacity for the Windows 11 installation files
* Contain no required data
* Be connected directly to the build device where possible
* Be clearly identified to avoid selecting the wrong removable drive

Creating the installation media may erase the existing contents of the USB drive.

### Media Creation Method

The Microsoft Windows 11 Media Creation Tool is used to download the Windows installation files and prepare the bootable USB drive.

The installation media should be created from a trusted Windows device using the official Microsoft tool.

### Expected Result

After media creation:

* The tool reports that the USB drive is ready
* The USB drive contains the Windows installation files
* The device can detect the USB drive as a boot option
* Windows Setup starts when the device boots from the media

## UEFI and Boot Configuration

### Intended Firmware Configuration

| Setting | Intended configuration |
| --- | --- |
| Boot mode | UEFI |
| Legacy or Compatibility Support Module boot | Disabled where possible |
| Secure Boot | Enabled |
| TPM | Enabled |
| USB boot | Enabled |
| Internal storage mode | Manufacturer-supported default |
| Boot source | Windows 11 USB media |

Firmware settings vary between device manufacturers. Only settings required for the installation should be changed.

Any firmware change should be recorded in the build notes.

### Boot Selection

The preferred method is to use the device's temporary boot menu rather than permanently changing the firmware boot order.

The boot entry labelled as the UEFI USB device should be selected.

## Windows 11 Clean Installation

### Installation Type

Custom Windows installation.

The upgrade option is not used because the objective is to complete a clean operating system build.

### Disk and Partition Handling

Where the device is approved for a complete rebuild and all required data has been protected, the existing Windows partitions can be removed during Windows Setup.

Windows Setup can then install Windows into the unallocated space and create the required system partitions automatically.

Before deleting a partition:

* Confirm that the correct physical disk is selected
* Confirm that no required data remains on the disk
* Confirm that no secondary disk is being selected accidentally
* Record any unusual recovery or manufacturer partitions
* Confirm that the rebuild is authorised

Partition deletion is destructive and cannot be treated as a reversible troubleshooting step.

### Installation Outcome

The clean installation should result in:

* Windows installed to the internal system drive
* Windows Boot Manager configured
* Windows starting without the USB drive
* The Windows Out-of-Box Experience loading successfully
* No dependency on the previous Windows installation

## Windows Out-of-Box Experience

The Out-of-Box Experience is completed after Windows Setup finishes.

The exact screens presented can vary based on:

* Windows edition
* Windows version
* Network connectivity
* Device hardware
* Microsoft account or organisational account requirements
* Previous device registration state

During the project, the selected setup path should be documented accurately.

The device should not be joined to Microsoft Intune or Windows Autopilot as part of this project unless that activity is explicitly included in a later project.

## Post-Build Configuration

### Initial Checks

After reaching the Windows desktop:

* Confirm that Windows starts normally
* Confirm that the keyboard and pointing device work
* Confirm that the display resolution is appropriate
* Confirm that wired or wireless networking works
* Confirm that audio devices are detected
* Confirm that the internal storage is available
* Confirm that the system date, time and time zone are correct
* Confirm that the installed Windows edition is expected

### Device Naming

The device name used during this standalone build should be recorded.

A later Intune or Autopilot project may apply a different managed device naming standard.

### Driver Installation

Drivers should be installed using trusted sources in the following order:

1. Windows Update
2. Optional driver updates where justified
3. The device manufacturer's approved support application or support website
4. A specific manufacturer driver package where Windows Update does not resolve the device

Drivers should not be downloaded from unofficial third-party driver websites.

The following hardware areas should be checked:

* Chipset
* Storage controller
* Display adapter
* Network adapter
* Wireless adapter
* Bluetooth
* Audio
* Camera
* Touchpad
* Biometric devices
* Docking or USB controllers
* Firmware

### Device Manager Validation

Device Manager should be reviewed after driver installation.

The expected result is:

* No unknown devices
* No devices with warning icons
* No devices with error icons
* No disabled hardware unless intentionally disabled
* Correct hardware categories present

Any unresolved device should be documented with:

* Device name
* Hardware ID where required
* Device status or error code
* Driver source attempted
* Final resolution or limitation

## Windows Update

Windows Update should be run repeatedly until no further required quality, security, cumulative or servicing updates are offered.

The update process may require several restart and scan cycles.

The process should include:

1. Check for updates.
2. Install available required updates.
3. Restart the device when prompted.
4. Check for updates again.
5. Repeat until the device reports that it is up to date.
6. Review optional updates separately.
7. Install optional drivers only where they are appropriate and required.

The final Windows version and operating system build should be recorded using `winver` or the Windows Settings application.

## Windows Activation

Windows activation should be checked after the installation and after the device has internet access.

The validation should record:

* Installed Windows edition
* Activation status
* Whether activation completed automatically
* Any activation issue encountered

Product keys, digital licence information and partial product key details should not be exposed in public evidence.

## Security and Device Health Validation

### Windows Security

The following areas should be checked:

* Virus and threat protection
* Firewall and network protection
* Device security
* Secure Boot status
* Security processor status
* Core isolation status where supported
* Windows Security notification status

The purpose of this project is to validate the clean operating system baseline. It does not replace later Intune security policy configuration.

### TPM Validation

TPM status can be checked using:

```text
tpm.msc
```

The expected result is that the TPM is detected, ready for use and reports the appropriate specification version for the device.

### Secure Boot Validation

Secure Boot status can be checked using System Information or PowerShell.

Example PowerShell command:

```powershell
Confirm-SecureBootUEFI
```

On a supported UEFI device with Secure Boot enabled, the expected result is:

```text
True
```

### BitLocker Status

BitLocker status should be reviewed and documented.

Example command:

```powershell
Get-BitLockerVolume
```

BitLocker should not be enabled, disabled or reconfigured without understanding where the recovery key will be stored.

Later Intune security projects can define the managed BitLocker configuration.

### System Information

The following commands can support validation and evidence collection:

```powershell
Get-ComputerInfo
```

```text
winver
```

```text
msinfo32
```

```text
dxdiag
```

Only relevant, non-sensitive information should be captured for the repository.

## Build Process

### 1. Complete Pre-Build Checks

1. Identify the target device.
2. Confirm that the rebuild is authorised.
3. Back up any required data.
4. Confirm that the backup is accessible.
5. Record the device manufacturer and model.
6. Confirm Windows 11 hardware readiness.
7. Confirm that UEFI, Secure Boot and TPM are available.
8. Connect the device to power.
9. Disconnect unnecessary external storage.

### 2. Create the Windows 11 USB Media

1. Connect the USB drive to a trusted Windows device.
2. Download the official Windows 11 Media Creation Tool.
3. Run the tool with the required administrative permissions.
4. Accept the applicable licence terms.
5. Select the option to create installation media.
6. Confirm the required language and architecture.
7. Select `USB flash drive`.
8. Select the correct USB drive.
9. Allow the tool to download and prepare the media.
10. Confirm that the tool reports the USB drive is ready.
11. Safely remove the USB drive.

### 3. Boot from the USB Drive

1. Connect the Windows 11 USB drive to the target device.
2. Start or restart the device.
3. Open the temporary boot menu.
4. Select the UEFI entry for the USB drive.
5. Confirm that Windows Setup loads.
6. Review firmware settings only if the USB drive does not start.

### 4. Complete the Clean Installation

1. Select the required language, time and keyboard options.
2. Start the Windows installation.
3. Select or confirm the appropriate Windows edition where required.
4. Accept the applicable licence terms.
5. Select `Custom: Install Windows only`.
6. Identify the correct internal system disk.
7. Remove existing partitions only after confirming the disk and backup state.
8. Select the unallocated space.
9. Continue the installation.
10. Allow Windows Setup to copy files and restart the device.
11. Remove or stop booting from the USB drive when Windows Setup no longer requires it.

### 5. Complete Windows Setup

1. Complete the Windows Out-of-Box Experience.
2. Select the required region and keyboard layout.
3. Connect to the appropriate network where required.
4. Complete the selected account setup path.
5. Review privacy and diagnostic settings.
6. Allow Windows to complete initial configuration.
7. Confirm that the Windows desktop loads.

### 6. Install Drivers

1. Open Windows Update.
2. Install available updates.
3. Restart the device.
4. Review Device Manager.
5. Install manufacturer-provided drivers where devices remain unresolved.
6. Review optional driver updates where appropriate.
7. Restart the device after significant driver or firmware installation.
8. Confirm that Device Manager contains no unresolved devices.

### 7. Complete Windows Updates

1. Check for updates.
2. Install required updates.
3. Restart when prompted.
4. Repeat the update scan.
5. Continue until no further required updates are available.
6. Record the final Windows version and build.

### 8. Validate the Build

1. Confirm Windows activation.
2. Confirm Device Manager health.
3. Confirm network connectivity.
4. Confirm audio, display, camera and input device operation.
5. Confirm Secure Boot status.
6. Confirm TPM status.
7. Review Windows Security.
8. Review BitLocker status.
9. Confirm that the device starts correctly after a full shutdown.
10. Record the results in the build notes.

## Expected Build Flow

The expected Windows 11 clean-build process is:

1. The target device and rebuild scope are confirmed.
2. Required data is backed up.
3. Windows 11 hardware and firmware readiness is checked.
4. Official Windows 11 installation media is created.
5. The target device boots from the USB drive using UEFI.
6. Windows Setup starts.
7. The existing operating system partitions are removed where authorised.
8. Windows is installed into unallocated disk space.
9. Windows Setup creates the required system partitions.
10. The device restarts into the Windows Out-of-Box Experience.
11. Initial Windows setup is completed.
12. The Windows desktop loads.
13. Windows Update installs operating system and driver updates.
14. Manufacturer drivers are installed where required.
15. Device Manager is checked for unresolved hardware.
16. Windows activation is confirmed.
17. TPM, Secure Boot, Windows Security and BitLocker status are reviewed.
18. The final Windows version and build are recorded.
19. Evidence and build notes are saved.
20. The device is ready for later Microsoft Intune or Windows Autopilot work.

## Validation

The following checks should be completed after the build:

* Confirm that Windows starts without the USB drive
* Confirm that the correct Windows edition is installed
* Confirm that Windows is activated
* Confirm that the system disk uses the expected partition layout
* Confirm that the device is using UEFI
* Confirm that Secure Boot is enabled where supported
* Confirm that TPM is present and ready
* Confirm that Windows Update reports no outstanding required updates
* Confirm that Device Manager contains no unknown or failed devices
* Confirm that network connectivity works
* Confirm that audio works
* Confirm that the display adapter and resolution are correct
* Confirm that the keyboard, touchpad or mouse works
* Confirm that the camera and biometric devices work where present
* Confirm that Windows Security is operational
* Confirm that BitLocker status is understood and documented
* Confirm that the device restarts and shuts down normally
* Confirm that the final Windows version and build are recorded
* Confirm that no sensitive data is visible in the evidence

Any failed check should be recorded with the troubleshooting actions completed and the final outcome.

## Evidence

Evidence is saved in the `Evidence` folder.

Evidence should include:

* Screenshot of the Windows 11 Media Creation Tool
* Screenshot confirming that the USB media was created
* Photograph or screenshot of the temporary boot menu
* Photograph or screenshot of Windows Setup
* Photograph or screenshot of the installation disk selection
* Screenshot of the completed Windows desktop
* Screenshot of `winver`
* Screenshot of Windows activation status
* Screenshot of Windows Update showing the final update state
* Screenshot of Device Manager
* Screenshot of System Information
* Screenshot of TPM status
* Screenshot of Secure Boot status
* Screenshot of Windows Security
* Screenshot or command output showing BitLocker status
* Completed build notes
* Record of any issue and its resolution

Suggested evidence filenames:

```text
01-windows-media-creation-tool.png
02-usb-media-created.png
03-uefi-boot-menu.jpg
04-windows-setup.jpg
05-disk-partition-selection.jpg
06-windows-desktop.png
07-windows-version.png
08-windows-activation.png
09-windows-update-complete.png
10-device-manager.png
11-system-information.png
12-tpm-status.png
13-secure-boot-status.png
14-windows-security.png
15-bitlocker-status.png
build-notes.md
```

Evidence filenames can be adjusted to match the screenshots collected during the project.

## Diagram

A diagram for this project should be stored in the `Diagrams` folder.

The diagram should show the Windows 11 clean-build sequence from pre-build checks through to final validation and future Intune or Autopilot readiness.

## Scripts

Any PowerShell commands or reusable validation scripts created during the project should be stored in the `Scripts` folder.

Potential script outputs include:

* Windows version and build information
* Computer hardware information
* TPM status
* Secure Boot status
* BitLocker status
* Network adapter information
* Device driver error checks
* Windows activation status
* Windows Update history summary

Scripts must not export confidential information, licence keys, recovery keys or personal account information into the public repository.

## Troubleshooting Record

Any installation or validation issue should be documented using the following structure:

| Field | Details |
| --- | --- |
| Issue | Description of the problem |
| Stage | Media creation, boot, installation, setup, drivers, updates or validation |
| Symptoms | Error message or observed behaviour |
| Cause | Confirmed or likely cause |
| Resolution | Actions completed |
| Outcome | Resolved, workaround applied or unresolved |
| Evidence | Related screenshot or log file |

This demonstrates the ability to investigate and resolve endpoint build problems rather than only record a successful result.

## Limitations

The following limitations may apply to this project:

* The exact Windows Setup screens can vary between Windows versions and editions
* Firmware settings and boot menu keys vary between manufacturers
* Driver availability depends on the device model and manufacturer support
* Windows Update results can vary depending on when the build is completed
* Some security features depend on the device hardware
* Windows activation depends on the device licence and installed edition
* A standalone clean build does not demonstrate Intune enrolment or Autopilot provisioning
* Application deployment and corporate configuration are outside the scope of this project
* BitLocker management is reviewed but is not centrally enforced in this project
* The device may require later preparation before it can be registered with Windows Autopilot

Any limitation encountered during the physical build should be recorded in the build notes.

## Skills Demonstrated

* Windows 11 installation media creation
* Physical Windows device rebuilding
* UEFI boot configuration
* Windows Setup administration
* Disk and partition selection
* Windows Out-of-Box Experience completion
* Windows driver installation
* Windows Update administration
* Device Manager troubleshooting
* Windows activation validation
* TPM and Secure Boot validation
* Windows Security review
* BitLocker status review
* PowerShell validation
* Hardware and operating system troubleshooting
* Technical evidence collection
* Build documentation
* Data protection awareness
* Security-conscious handling of screenshots and logs
* Preparation of a Windows device for future endpoint management
