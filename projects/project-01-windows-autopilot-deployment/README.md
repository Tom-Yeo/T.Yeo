# Project 01 - Windows Autopilot Deployment Configuration

## Project Overview

This project demonstrates the configuration of the core Microsoft Intune components required for a Windows Autopilot deployment.

The project covers:

* Autopilot group tag design
* Dynamic device group membership
* Windows Autopilot deployment profile configuration
* Enrolment Status Page configuration
* Profile assignment planning
* Expected Windows provisioning behaviour

No physical device is enrolled into Windows Autopilot as part of this project. The project therefore focuses on configuration, documentation, screenshots and expected deployment behaviour.

## Project Status

Planned

## Project Location

`projects/project-01-windows-autopilot-deployment`

## Objectives

The objectives of this project are to:

* Define a consistent Autopilot group tag
* Create a dynamic device group based on the group tag
* Configure a user-driven Windows Autopilot deployment profile
* Configure an Enrolment Status Page profile
* Assign the profiles to the correct device group
* Explain how the Autopilot components work together
* Document the expected device provisioning process
* Record any limitations caused by the absence of a physical Autopilot device

## Technologies Used

* Microsoft Intune
* Windows Autopilot
* Microsoft Entra ID
* Windows 11

## Configuration Summary

| Component                     | Name                        |
| ----------------------------- | --------------------------- |
| Autopilot group tag           | `WIN11-CORP-STANDARD`       |
| Dynamic device group          | `GRP-DYN-WIN11-AP-STANDARD` |
| Autopilot deployment profile  | `AP-WIN11-STANDARD`         |
| Enrolment Status Page profile | `ESP-WIN11-STANDARD`        |

## Autopilot Targeting Design

The Autopilot group tag is used to identify devices that should receive the standard Windows 11 corporate deployment configuration. 

The group tag used in this project is:

`WIN11-CORP-STANDARD`

Autopilot devices assigned this group tag should automatically become members of the following Microsoft Entra dynamic device group:

`GRP-DYN-WIN11-AP-STANDARD`

The dynamic group is then used to assign:

* The Windows Autopilot deployment profile
* The Enrolment Status Page profile
* Any future applications, configuration profiles or compliance policies required during deployment

This provides a repeatable method of targeting devices without manually adding each device to a group.

## Dynamic Device Group

### Group Name

`GRP-DYN-WIN11-AP-STANDARD`

### Group Type

* Security group: Yes
* Membership type: Dynamic Device

### Dynamic Membership Rule

```text
(device.devicePhysicalIds -any (_ -eq "[OrderID]:WIN11-CORP-STANDARD"))
```

### Expected Behaviour

When a Windows Autopilot device is registered with the group tag `WIN11-CORP-STANDARD`, the device should meet the dynamic membership rule and become a member of `GRP-DYN-WIN11-AP-STANDARD`.

Dynamic group membership processing may not be immediate. Microsoft Entra ID must evaluate the device attributes before the device appears in the group.

No physical Autopilot device is available in this project to confirm live group membership.

## Windows Autopilot Deployment Profile

### Profile Name

`AP-WIN11-STANDARD`

### Deployment Mode

User-driven

### Join Type

Microsoft Entra joined

### Intended Use

The profile represents a standard corporate Windows 11 deployment where the user completes authentication during the Out-of-Box Experience and the device joins Microsoft Entra ID.

### Profile Settings

| Setting                          | Configuration          |
| -------------------------------- | ---------------------- |
| Deployment mode                  | User-driven            |
| Join to Microsoft Entra ID as    | Microsoft Entra joined |
| Microsoft Software Licence Terms | Hide                   |
| Privacy settings                 | Hide                   |
| Hide change account options      | Hide                   |
| User account type                | Standard               |
| Language or region               | User select            |
|                                  |                        |
| Apply device name template       | STD%SERIAL%            |
| Allow pre-provisioned deployment | No                     |

### Assignment

The Autopilot deployment profile should be assigned to:

`GRP-DYN-WIN11-AP-STANDARD`

This assignment ensures that devices using the `WIN11-CORP-STANDARD` group tag receive the standard Autopilot deployment profile.

## Enrolment Status Page

### Profile Name

`ESP-WIN11-STANDARD`

### Purpose

The Enrolment Status Page controls what the user sees while Intune prepares the device.

It can prevent the user from reaching the Windows desktop until required device configuration and applications have been processed.

### ESP Settings

| Setting                                                                       | Configuration |
| ----------------------------------------------------------------------------- | ------------- |
| Show app and profile configuration progress                                   | Yes           |
| Show an error when installation takes longer than specified number of minutes | 60 minutes    |
| Show custom message when a time limit error occurs                            | Yes           |
| Turn on log collection and diagnostics page for end users                     | Yes           |
| Only show page to devices provisioned by Out-of-Box Experience                | Yes           |
| Install Windows updates (might restart the device)                            | No            |
| Block device use until all apps and profiles are installed                    | Yes           |
| Allow users to reset the device if an installation error occurs               | Yes           |
| Allow users to use the device if an installation error occurs                 | No            |
| Block device use until required apps are installed                            | Selected      |



### Required Applications

This project documents the ESP configuration but does not require live application deployment testing.

Note: Selected required apps has been chosen but no apps assigned. This is only because this is my lab environment and apps have not yet been created. Selected is chosen because assigning all in production is not best practice. Only required apps for core device configuration should be deployed at this stage. Having all apps assigned could lead to failures or timeouts. 
Also to note, Win32 Apps preferred for blocking only, if you block with a Store app such as company portal it can cause failure due to store apps timing / install process.

Any applications selected as blocking applications should be:

* Required for the device build
* Suitable for installation during Autopilot
* Tested for reliable unattended installation
* Assigned to the same device group
* Kept to the minimum required set

Adding too many blocking applications can increase deployment time and make troubleshooting more difficult.

### Assignment

The Enrolment Status Page profile assigned to:

`GRP-DYN-WIN11-AP-STANDARD`

## Configuration Process

### 1. Create the Dynamic Device Group

1. Open the Microsoft Intune admin centre.

2. Navigate to `Groups`.

3. Select `New group`.

4. Set the group type to `Security`.

5. Enter the group name:

   `GRP-DYN-WIN11-AP-STANDARD`

6. Set the membership type to `Dynamic Device`.

7. Open the dynamic membership rule editor.

8. Add the following rule:

```text
(device.devicePhysicalIds -any (_ -eq "[OrderID]:WIN11-CORP-STANDARD"))
```

9. Validate the rule syntax.
10. Create the group.

### 2. Create the Autopilot Deployment Profile

1. Open the Microsoft Intune admin centre.

2. Navigate to:

   `Devices > Windows > Windows enrolment > Deployment profiles`

3. Select `Create profile`.

4. Select `Windows PC`.

5. Enter the profile name:

   `AP-WIN11-STANDARD`

6. Select user-driven deployment.

7. Configure the required Out-of-Box Experience settings.

8. Set the user account type to `Standard`.

9. Assign the profile to:

   `GRP-DYN-WIN11-AP-STANDARD`

10. Review and create the profile.

### 3. Create the Enrolment Status Page Profile

1. Open the Microsoft Intune admin centre.

2. Navigate to:

   `Devices > Windows > Windows enrolment > Enrolment Status Page`

3. Select `Create`.

4. Enter the profile name:

   `ESP-WIN11-STANDARD`

5. Enable configuration progress.

6. Configure the deployment timeout.

7. Enable device blocking until required applications and profiles are processed.

8. Configure error handling and diagnostic options.

9. Assign the profile to:

   `GRP-DYN-WIN11-AP-STANDARD`

10. Review and create the profile.

## Expected Deployment Flow

The expected Windows Autopilot deployment process is:

1. A device is registered with Windows Autopilot.
2. The group tag `WIN11-CORP-STANDARD` is assigned to the device.
3. Microsoft Entra ID evaluates the device attributes.
4. The device becomes a member of `GRP-DYN-WIN11-AP-STANDARD`.
5. The Autopilot deployment profile is assigned to the device.
6. The Enrolment Status Page profile is assigned to the device.
7. The user starts the device and connects it to a network.
8. Windows identifies the device as an Autopilot-registered device.
9. The Autopilot deployment profile controls the Out-of-Box Experience.
10. The user signs in using their organisational account.
11. The device joins Microsoft Entra ID.
12. The device enrols into Microsoft Intune.
13. The Enrolment Status Page displays configuration progress.
14. Required policies and applications are processed.
15. The user reaches the Windows desktop after the required deployment stages complete.

## Validation

The following checks should be completed within the Intune and Microsoft Entra admin centres:

* Confirm that the dynamic group was created
* Confirm that the membership rule syntax is valid - (No physical devices in test to carry this out but in prod would be validated)
* Confirm that the Autopilot deployment profile was created
* Confirm that the profile is configured for user-driven deployment
* Confirm that the user account type is set to standard
* Confirm that the deployment profile is assigned to the dynamic device group
* Confirm that the Enrolment Status Page profile was created
* Confirm that ESP blocking settings are enabled
* Confirm that the ESP profile is assigned to the dynamic device group
* Confirm that there are no obvious assignment conflicts

Live validation of device membership, profile delivery and the Out-of-Box Experience cannot be completed without a registered Autopilot device.

## Evidence

Evidence saved in the `Evidence` folder.

Evidence includes:

* Screenshot of the dynamic device group overview
* Screenshot of the dynamic membership rule
* Screenshot of the Autopilot deployment profile properties
* Screenshot of the Autopilot Out-of-Box Experience settings
* Screenshot of the Autopilot profile assignment
* Screenshot of the Enrolment Status Page settings
* Screenshot of the ESP assignment

## Diagram

Diagram created for this project stored in the `Diagrams` folder.

## Limitations

This project does not include a physical device registered with Windows Autopilot.

The following activities cannot therefore be fully tested:

* Autopilot device registration
* Group tag application to a real device
* Dynamic group membership processing
* Deployment profile delivery
* Microsoft Entra join
* Automatic Intune enrolment
* Enrolment Status Page application processing
* Complete Out-of-Box Experience
* Required application installation
* End-user desktop access after provisioning

The project demonstrates configuration knowledge and the expected deployment process rather than a completed physical device deployment.

## Skills Demonstrated

* Windows Autopilot configuration
* Microsoft Intune administration
* Microsoft Entra dynamic group configuration
* Dynamic membership rule creation
* Device targeting using Autopilot group tags
* User-driven deployment profile configuration
* Enrolment Status Page configuration
* Profile assignment planning
* Windows provisioning process documentation
* Evidence collection and technical validation
