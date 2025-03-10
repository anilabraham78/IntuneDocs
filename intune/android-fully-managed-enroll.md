---
# required metadata

title: Setup Intune enrollment for Android Enterprise fully managed devices
titleSuffix: Microsoft Intune
description: Learn how to enroll Android Enterprise fully managed devices in Intune.
keywords:
author: ErikjeMS 
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology:
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure
ms.custom: seodec18
ms.collection: M365-identity-device-management
---

# Set up Intune enrollment of Android Enterprise fully managed devices (Preview)

Android Enterprise fully managed devices are corporate-owned devices associated with a single user and used exclusively for work and not personal use. Admins can manage the entire device and enforce policy controls unavailable to work profiles, such as:
- allow app installation only from Managed Google Play
- block uninstallation of managed apps
- prevent users from factory resetting devices, and so on.

Intune helps you deploy apps and settings to Android Enterprise devices, including Android Enterprise fully managed devices. For specific details about Android Enterprise, see [Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## Technical requirements

You must have an Intune standalone tenant to manage Android Enterprise fully managed devices. Fully managed device management isn't available in either hybrid (Configuration Manager-connected) mode or in the legacy Silverlight management console.

Devices must meet these requirements to be managed as an Android Enterprise fully managed device:

- Android OS version 5.1 and above.
- Devices must run a build of Android that has Google Mobile Services (GMS) connectivity. Devices must have GMS available and must be able to connect to GMS.

There is no restriction on device manufacturer/OEM if the above requirements are met.

## Set up Android Enterprise fully managed device management

To set up Android Enterprise fully managed device management, follow these steps:

1. To prepare to manage mobile devices, you must [set the mobile device management (MDM) authority to **Microsoft Intune**](mdm-authority-set.md). You set this item only once, when you're first setting up Intune for mobile device management.
2. [Connect your Intune tenant account to your Android Enterprise account](connect-intune-android-enterprise.md).
3. [Enable corporate-owned user devices](#enable-corporate-owned-user-devices)
4. [Enroll the fully managed devices](#enroll-the-fully-managed-devices).

### Enable corporate owned user devices

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) and choose **Device enrollment** > **Android enrollment** > **Corporate-owned, fully managed user devices (Preview)**.
2. Under **Allow users to enroll corporate-owned user devices**, choose **Yes**.

> [!NOTE]
> If you have an Azure AD Conditional Access policy defined that uses the *require a device to be marked as compliant* control and  applies to **All Cloud apps**, **Android** and **Browsers** - you must exclude the **Microsoft Intune** cloud app from this policy. This is because the Android setup processes uses a Chrome tab to authenticate your users during enrolment. For more information, see [Azure AD Conditional Access Documentation](https://docs.microsoft.com/azure/active-directory/conditional-access/).

When this setting is set to **Yes**, it provides you with an enrollment token (a random string) and a QR code for your Intune tenant. This single enrollment token is valid for all your users and won't expire. Depending on the Android OS and version of the device, you can use either the token or QR code to enroll the kiosk device.

## Enroll the fully managed devices
You can now [enroll your fully managed devices](android-dedicated-devices-fully-managed-enroll.md).

## Considerations for this preview feature
This public preview includes a core set of features for the Android Enterprise fully managed solution set. We want to hear about your experience using the preview features using any of your current communication channels to the team (like [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853)).

This preview supports the following features for Android Enterprise fully managed devices:
- Device enrollment using NFC, token entry, QR code and Zero Touch
- Device configuration for user groups
- App distribution and configuration for user groups


When using these preview features, keep the following in mind:
- Features in preview aren't recommended for mission-critical or production deployments. 
- Preview features are implemented to Microsoft Intune production standards. However, not all Intune features are available for use with Android Enterprise fully managed user devices. Preview features are clearly labeled with “(preview)” in the Intune console. 
- The preview features are fully supported through the usual Intune support channels.
- Enrolling Android Enterprise fully managed devices using Samsung Knox Mobile Enrollment isn't supported in preview. 
- Use of the Intune Company Portal app isn't supported on Android Enterprise fully managed devices. 
- Intune features like Conditional Access, app protection policies, and certificate deployment aren't supported in preview. 
- Device group targeting of any profile or app isn't supported in preview. Only user group targeting is supported. 
- There is no first-class UI for configuring email, WiFi, or VPN. Use app configuration policies to configure supported app configuration settings.

## Next steps
- [Add Android Enterprise fully managed device configuration policies](device-restrictions-android-for-work.md#device-owner-only)
- [Configure app configuration policies for Android Enterprise fully managed devices](app-configuration-policies-use-android.md)

