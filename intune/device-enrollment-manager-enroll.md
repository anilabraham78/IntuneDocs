---
# required metadata

title: Enroll devices using a device enrollment manager account
titleSuffix: Microsoft Intune
description: Use the device enrollment manager account to enroll devices in Intune.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.custom: seodec18
ms.collection: M365-identity-device-management
---

# Enroll devices in Intune by using a device enrollment manager account

You can enroll up to 1,000 mobile devices with a single Azure Active Directory account by using a device enrollment manager (DEM) account. DEM is an Intune permission that can be applied to an AAD user account and lets the user enroll up to 1,000 devices. A DEM account is useful for scenarios where devices are enrolled and prepared before handing them out to the users of the devices.

## Limitations of devices that are enrolled with a DEM account

DEM user accounts and devices that are enrolled with a DEM user account have the following limitations:

  - A DEM account user must be assigned an Intune license.
  - Wipe can't be done from the Company Portal. Wiping a device enrolled by a DEM user account can be done from the Intune in Azure portal.
  - Only the local device appears in the Company Portal app or website.
  - DEM user accounts can’t use Apple Volume Purchase Program (VPP) apps with Apple VPP user licenses because of per-user Apple ID requirements for app management.
  - Devices can install VPP apps if they have Apple VPP device licenses.
  - Devices are blocked for Conditional Access with the exception of Windows 10 1803+
  - Every device enrolled with DEM accounts needs to be properly licensed to be managed by Intune. The license could be an Intune user license or an Intune device license.



## Add a device enrollment manager

1. In [Intune in the Azure portal](https://aka.ms/intuneportal), choose **Device enrollment** > **Device enrollment managers**.

2. Select **Add**.

3. On the **Add User** blade, enter a user principal name for the DEM user, and select **Add**. The DEM user is added to the list of DEM users.

## Permissions for DEM

Global Administrator or Intune Service Administrator Azure AD roles are required to
- assign DEM permission to an Azure AD user account
- see all DEM users

If a user doesn't have the Global Administrator or Intune Service Administrator role assigned to them, but has read permissions enabled for the Device Enrollment Managers role assigned to them, they can see only the DEM users they've created.


## Remove device enrollment manager permissions

Removing a device enrollment manager doesn't affect enrolled devices.

**To remove a device enrollment manager**

1. In [Intune in the Azure portal](https://aka.ms/intuneportal), choose **Device enrollment**, and then choose **Device enrollment managers**.
2. On the **Device enrollment managers** blade, select the DEM user, and select **Delete**.

