# Windows Endpoint Management Portfolio

## Microsoft Intune | Windows 11 | Autopilot | Device Compliance | EUC Support

<p>
  <img src="https://img.shields.io/badge/Microsoft%20Intune-0078D4?style=for-the-badge&logo=microsoft&logoColor=white" alt="Microsoft Intune" />
  <img src="https://img.shields.io/badge/Windows%2011-0078D4?style=for-the-badge&logo=windows11&logoColor=white" alt="Windows 11" />
  <img src="https://img.shields.io/badge/Windows%20Autopilot-0078D4?style=for-the-badge&logo=microsoft&logoColor=white" alt="Windows Autopilot" />
  <img src="https://img.shields.io/badge/Microsoft%20Entra%20ID-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Microsoft Entra ID" />
  <img src="https://img.shields.io/badge/PowerShell-0078D4?style=for-the-badge&logo=powershell&logoColor=white" alt="PowerShell" />
  <img src="https://img.shields.io/badge/AB--900-0078D4?style=for-the-badge&logo=microsoft&logoColor=white" alt="AB-900" />
  <img src="https://img.shields.io/badge/MS--721-0078D4?style=for-the-badge&logo=microsoftteams&logoColor=white" alt="MS-721" />
  <img src="https://img.shields.io/badge/MS--900-0078D4?style=for-the-badge&logo=microsoft&logoColor=white" alt="MS-900" />
</p>

<hr>

Hi, I am **Tom**.

This portfolio demonstrates practical Windows endpoint management knowledge for an Associate EUC Engineer role.

The projects focus on setting up and documenting core endpoint management tasks in Microsoft Intune and related Microsoft services. This includes Windows 11 build preparation, Autopilot deployment configuration, Intune policy setup, Win32 application packaging configuration, compliance policy setup, Conditional Access planning, daily Intune support task awareness, and basic hardware support evidence.

This portfolio is designed to show configuration capability, technical understanding, and clear documentation. It does not claim full live deployment validation where no Intune-enrolled test devices are available.

My background includes Windows 11 device deployment support, user enrolment and setup guidance, BAU troubleshooting, PowerShell-based administration, DHCP/DNS readiness checks, and hardware installation exposure.

<hr>

## Certifications

| Certification | Exam / Code | Skills evidenced |
|---|---:|---|
| **Microsoft 365 Certified: Copilot and Agent Administration Fundamentals** | **AB-900** | Microsoft 365 core services, Copilot, agents, identity, access, security, data protection, governance, and basic administration. |
| **Microsoft 365 Certified: Collaboration Communications Systems Engineer Associate** | **MS-721** | Microsoft Teams Phone, Teams Rooms, meetings, certified devices, deployment, management, and troubleshooting. |
| **Microsoft 365 Certified: Fundamentals** | **MS-900** | Microsoft 365 services, cloud concepts, identity, security, compliance, licensing, and support fundamentals. |
| **MTA: Mobility and Device Fundamentals** | **98-368** | Windows devices, mobility concepts, device configuration, access control, cloud services, and basic endpoint support. |
| **MTA: Database Fundamentals** | **98-364** | Core database concepts, relational database structure, tables, queries, and basic database administration awareness. |
| **8x8 XCaaS: Build, Support and Deploy Certified** | **8x8-BU02 / 8x8-SU02 / 8x8-DE02** | 8x8 XCaaS build, support, deployment, configuration, troubleshooting, and operational support. |

<hr>

## Relevant Experience Alignment

| Experience area | Portfolio relevance |
|---|---|
| **Windows 11 device deployment** | Supports the Windows build, setup, and device preparation project. |
| **Device enrolment and setup guidance** | Aligns with Autopilot, OOBE, and Intune enrolment concepts. |
| **BAU troubleshooting** | Supports understanding of common endpoint issues and support processes. |
| **PowerShell and CSV administration** | Supports basic automation, data handling, and repeatable support tasks. |
| **DHCP and DNS readiness awareness** | Supports endpoint provisioning checks where connectivity affects enrolment and policy retrieval. |
| **Hardware installation exposure** | Supports the hardware replacement and post-repair validation project. |

<hr>

## Technical Skills

| Area | Technologies and tasks |
|---|---|
| Endpoint management | Microsoft Intune, device enrolment concepts, compliance policy setup, device lifecycle awareness |
| Device provisioning | Windows Autopilot, group tags, deployment profiles, Enrolment Status Page |
| Identity targeting | Microsoft Entra ID, assigned groups, dynamic device groups |
| Operating systems | Windows 11 installation media, OOBE, Windows Update, driver checks |
| Application deployment | Win32 apps, IntuneWinAppUtil, install commands, uninstall commands, detection rules |
| Compliance | Windows compliance policy configuration and expected device state planning |
| Conditional Access | Compliant device requirement planning and safe report-only configuration |
| Device health | BitLocker status checks, TPM checks, Secure Boot checks |
| Hardware support | RAM, SSD, battery, keyboard, Wi-Fi card, docking, display checks |
| Network basics | DHCP, DNS, connectivity checks |
| Scripting | Basic PowerShell checks, CSV import and export tasks |

<hr>

## Projects

### Project 00 - Windows 11 USB Media and Clean Build

**Location:** [projects/project-00-windows-11-clean-build](projects/project-00-windows-11-clean-build)

**Status:** Planned

Create Windows 11 installation media and complete a clean laptop rebuild.

**Skills**

- Create bootable Windows 11 media
- Rebuild a Windows laptop
- Confirm Windows setup completion
- Check drivers, Windows Update, and basic device health
- Prepare the device for future Intune or Autopilot enrolment

**Evidence**

- Media creation screenshots
- Boot menu or setup screenshots
- Windows 11 installation evidence
- Device Manager screenshot
- Windows Update screenshot
- Build notes

<hr>

### Project 01 - Windows Autopilot Deployment Configuration

**Location:** [projects/project-01-windows-autopilot-deployment](projects/project-01-windows-autopilot-deployment)

**Status:** Planned

Configure and document the core Windows Autopilot deployment components required to target and provision Windows 11 corporate devices.

**Skills**

- Define the Autopilot group tag: `WIN11-CORP-STANDARD`
- Create the dynamic device group: `GRP-DYN-WIN11-AP-STANDARD`
- Configure the dynamic membership rule for Autopilot group tag targeting
- Create the Autopilot deployment profile: `AP-WIN11-STANDARD`
- Configure user-driven deployment settings
- Create the Enrolment Status Page profile: `ESP-WIN11-STANDARD`
- Configure required application and device setup blocking settings
- Assign the Autopilot and ESP profiles to the appropriate device group
- Document how group tags, dynamic groups, profiles, and assignments work together
- Document the expected Windows Out-of-Box Experience and provisioning flow

**Evidence**

- Autopilot group tag and naming standard
- Dynamic device group configuration
- Dynamic membership rule screenshot
- Autopilot deployment profile screenshots
- Enrolment Status Page configuration screenshots
- Assignment screenshots or documented assignment plan
- Expected device membership behaviour
- Expected user provisioning experience
- Configuration and validation notes
- Limitation note explaining that no live Autopilot device deployment was completed

<hr>

### Project 02 - Windows Device Configuration Profile Setup

**Location:** [projects/project-02-device-configuration](projects/project-02-device-configuration)

**Status:** Planned

Set up basic Windows configuration profiles in Intune.

**Skills**

- Create configuration profile: `CFG-WIN11-DEVICE-BASELINE`
- Select appropriate Windows settings
- Assign the profile to the correct device group
- Document the expected endpoint behaviour

**Evidence**

- Configuration profile screenshots
- Settings selected
- Assignment screenshots
- Expected result notes
- Known limitations without a managed test endpoint

<hr>

### Project 03 - Device Security Baseline Setup

**Location:** [projects/project-03-device-security-baseline](projects/project-03-device-security-baseline)

**Status:** Planned

Set up basic endpoint security settings and document expected device checks.

**Skills**

- Configure disk encryption policy: `SEC-WIN11-DISK-ENCRYPTION`
- Understand BitLocker readiness
- Understand TPM and Secure Boot requirements
- Document expected security state

**Evidence**

- Security policy screenshots
- BitLocker setting notes
- TPM and Secure Boot check commands
- Expected result notes
- Known limitations without policy deployment to a managed device

<hr>

### Project 04 - Win32 Application Packaging Setup

**Location:** [projects/project-04-win32-application-packaging](projects/project-04-win32-application-packaging)

**Status:** Planned

Prepare a Win32 application package and document the Intune app configuration.

**Skills**

- Package an application with IntuneWinAppUtil
- Configure install command
- Configure uninstall command
- Configure detection rule
- Prepare app object: `APP-WIN32-7ZIP-REQ`
- Document expected deployment behaviour

**Evidence**

- Source folder structure
- IntuneWinAppUtil command used
- `.intunewin` package evidence
- Install and uninstall command notes
- Detection rule screenshot or documentation
- App configuration screenshots
- Limitation note where installation is not tested on an Intune-managed endpoint

<hr>

### Project 05 - Compliance and Conditional Access Setup

**Location:** [projects/project-05-compliance-conditional-access](projects/project-05-compliance-conditional-access)

**Status:** Planned

Configure Windows compliance and Conditional Access policies in a safe test state.

**Skills**

- Create compliance policy: `COMP-WIN11-STANDARD`
- Create Conditional Access policy: `CA-ALL-REQ-COMPLIANT-DEVICE`
- Use a test user group
- Use report-only mode where appropriate
- Document the expected access behaviour

**Evidence**

- Compliance policy screenshots
- Conditional Access screenshots
- Assignment screenshots
- Report-only configuration evidence
- Expected compliant and non-compliant outcomes
- Limitation note where no device compliance result is available

<hr>

### Project 06 - Daily Intune Operations Runbook

**Location:** [projects/project-06-daily-intune-operations-runbook](projects/project-06-daily-intune-operations-runbook)

**Status:** Planned

Document common Intune device support actions and where they are performed in the Intune admin centre.

This project is a written runbook. As no Intune-enrolled devices are available, it does not include real device data or live device action results.

**Skills**

- Understand where to search for Intune devices
- Understand where to view last check-in
- Understand where device sync is triggered
- Understand restart, rename, retire, wipe, and reset actions
- Understand where app and policy status are reviewed
- Understand where diagnostics collection is started
- Understand where BitLocker recovery keys are accessed

**Evidence**

- Written support runbook
- Screenshots of Intune admin centre menu locations where available
- Notes explaining when each action should be used
- Safety notes for destructive actions such as wipe, retire, and reset
- Limitation note confirming no real device action was performed

<hr>

### Project 07 - Hardware Component Replacement

**Location:** [projects/project-07-hardware-component-replacement](projects/project-07-hardware-component-replacement)

**Status:** Planned

Evidence a basic laptop component replacement and post-repair checks.

**Skills**

- Capture before, during, and after photos
- Replace a component such as RAM, SSD, battery, keyboard, or Wi-Fi card
- Confirm hardware detection in BIOS or Windows
- Check Device Manager
- Document BitLocker and device management considerations after repair

**Evidence**

- Redacted photos
- Component replacement notes
- BIOS or Windows detection evidence
- Device Manager screenshot
- Post-repair checklist
- BitLocker and Autopilot impact notes where relevant

<hr>

## Summary

This portfolio provides evidence of practical Windows endpoint management understanding for an Associate EUC Engineer role.

It focuses on setup, configuration, documentation, and support readiness across Windows 11, Autopilot deployment configuration, Intune configuration, application packaging, compliance planning, Conditional Access planning, daily Intune support actions, and hardware support.

Where live Intune-enrolled devices are not available, the portfolio records expected outcomes and limitations rather than claiming full deployment validation.
