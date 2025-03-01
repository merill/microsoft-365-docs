---
title: What's new in Microsoft Defender for Endpoint on Mac
description: Learn about the major changes for previous versions of Microsoft Defender for Endpoint on Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: 
  - m365-security-compliance
ms.topic: reference
ms.technology: mde
---

# What's new in Microsoft Defender for Endpoint on Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## 101.61.69 (20.122022.16169.0)

- Bug fixes

## 101.60.91 (20.122021.16091.0)

- This version contains a security update for [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

## 101.59.50 (20.122021.15950.0)

- This version adds support for macOS 12.3. Starting with macOS 12.3, [Apple is removing Python 2.7](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). There will be no Python version preinstalled on macOS by default. **ACTION NEEDED**: 
  - Users must update Microsoft Defender for Endpoint for Mac to version 101.59.50 (or newer) prior to updating their devices to macOS Monterey 12.3 (or newer). This minimal version 101.59.50 is a prerequisite to eliminating Python-related issues with Microsoft Defender for Endpoint for Mac on macOS Monterey.
  - For remote deployments, existing MDM setups must be updated to Microsoft Defender for Endpoint for Mac version 101.59.50 (or newer). Pushing via MDM an older Microsoft Defender for Endpoint for Mac version to macOS Monterey 12.3 (or newer) will result in an installation failure.

## 101.59.10 (20.122012.15910.0)

- The command-line tool now supports restoring quarantined files to a location other than the one where the file was originally detected. This can be done through `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Extended device control to handle devices connected over Thunderbolt 3
- Improved the handling of device control policies containing invalid vendor IDs and product IDs. Prior to this version, if the policy contained one or more invalid IDs, the entire policy was ignored. Starting from this version, only the invalid portions of the policy are ignored. Issues with the policy are surfaced through `mdatp device-control removable-media policy list`.
- Bug fixes

## 101.56.62 (20.121122.15662.0)

- Bug fixes

## 101.56.35 (20.121121.15635.0)

- The application has been renamed from "Microsoft Defender ATP" to "Microsoft Defender". End users will observe the following changes:
  - The application installation path has been changed from `/Application/Microsoft Defender ATP.app` to `/Applications/Microsoft Defender.app`.
  - Within the user experience, occurrences of "Microsoft Defender ATP" have been replaced with "Microsoft Defender"
- Resolved an issue where some VPN applications could not connect due to the network content filter that is distributed with Microsoft Defender for Endpoint for Mac
- Addressed an issue discovered in macOS 12.2 beta 2 where the installation package could not be opened due to a change in the operating system (OS) that prevents installation of packages with certain characteristics. While it appears that this OS change is not included in the final release of macOS 12.2, it is likely that it will be reintroduced in a future macOS version. As such, we encourage all enterprise administrators to refresh the Microsoft Defender for Endpoint package in their management console to this product version (or a newer version).
- Addressed an issue seen on some M1 devices where the product was stuck with invalid antimalware definitions and could not successfully update to a working set of definitions.
- `mdatp health` output has been extended with an additional attribute called `full_disk_access_enabled` that can be used to determine whether Full Disk Access has been granted to all components of Microsoft Defender for Endpoint for Mac.
- Performance improvements & bug fixes

## 101.54.16 (20.121111.15416.0)

- macOS 10.14 (Mojave) is no longer supported
- After a product setting stops being managed by the administrator through MDM, it now reverts to the value it had before it was managed (the value configured locally by the end user or, if no such local value was explicitly provided, the default value used by the product). Prior to this change, after a setting stopped being managed, its managed value persisted and was still used by the product.
- Performance improvements & bug fixes

## 101.49.25 (20.121092.14925.0)

- Added a new switch to the command-line tool to control whether archives are scanned during on-demand scans. This can be configured through `mdatp config scan-archives --value [enabled/disabled]`. By default, this is set to `enabled`.
- Bug fixes

## 101.47.27 (20.121082.14727.0)

- Fix for a system freeze occurring on shutdown on macOS Mojave and macOS Catalina

## 101.43.84 (20.121082.14384.0)

- Candidate build for macOS 12 (Monterey)
- Bug fixes

## 101.41.10 (20.121072.14110.0)

- Added new switches to the command-line tool:
  - Control degree of parallelism for on-demand scans. This can be configured through `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. By default, a degree of parallelism of `2` is used.
  - Control whether scans after security intelligence updates are enabled or disabled. This can be configured through `mdatp config scan-after-definition-update --value [enabled/disabled]`. By default, this is set to `enabled`.
- Changing the product log level now requires elevation
- Performance improvements & bug fixes

## 101.40.84 (20.121071.14084.0)

- M1 chip native support
- Performance improvements & bug fixes

## 101.37.97 (20.121062.13797.0)

- Performance improvements & bug fixes

## 101.34.28 (20.121061.13428.0)

- Bug fixes

## 101.34.27 (20.121052.13427.0)

- Bug fixes

## 101.34.20 (20.121051.13420.0)

- [Device control for macOS](mac-device-control-overview.md) is now in general availability
- Addressed an issue where a quick scan could not be started from the status menu on macOS 11 (Big Sur)
- Other bug fixes

## 101.32.69 (20.121042.13269.0)

- Addressed an issue where concurrent access to the keychain from Microsoft Defender for Endpoint and other applications can lead to keychain corruption.

## 101.29.64 (20.121042.12964.0)

- Starting with this version, threats detected during on-demand antivirus scans triggered through the command-line client are automatically remediated. Threats detected during scans triggered through the user interface still require manual action.
- `mdatp diagnostic real-time-protection-statistics` now supports two additional switches:
  - `--sort`: sorts the output descending by total number of files scanned
  - `--top N`: displays the top N results (only works if `--sort` is also specified)
- Performance improvements (specifically for when YARN is used) & bug fixes

## 101.27.50 (20.121022.12750.0)

- Fix to accommodate for Apple certificate expiration for macOS Catalina and earlier. This fix restores Threat & Vulnerability Management (TVM) functionality.

## 101.25.69 (20.121022.12569.0)

- Microsoft Defender for Endpoint on macOS is now available in preview for US Government customers. For more information, see [Microsoft Defender for Endpoint for US Government customers](gov.md).
- Performance improvements (specifically for the situation when the XCode Simulator app is used) & bug fixes.

## 101.23.64 (20.121021.12364.0)

- Added a new option to the command-line tool to view information about the last on-demand scan. To view information about the last on-demand scan, run `mdatp health --details antivirus`
- Performance improvements & bug fixes

## 101.22.79 (20.121012.12279.0)

- Performance improvements & bug fixes

## 101.19.88 (20.121011.11988.0)

- Performance improvements & bug fixes

## 101.19.48 (20.120121.11948.0)

> [!NOTE]
> The old command-line tool syntax has been deprecated with this release. For information on the new syntax, see [Resources](mac-resources.md#configuring-from-the-command-line).

- Added a new command-line switch to disable the network extension: `mdatp system-extension network-filter disable`. This command can be useful to troubleshoot networking issues that could be related to Microsoft Defender for Endpoint on Mac
- Performance improvements & bug fixes

## 101.19.21 (20.120101.11921.0)

- Bug fixes

## 101.15.26 (20.120102.11526.0)

- Improved the reliability of the agent when running on macOS 11 Big Sur
- Added a new command-line switch (`--ignore-exclusions`) to ignore AV exclusions during custom scans (`mdatp scan custom`)
- Performance improvements & bug fixes

## 101.13.75 (20.120101.11375.0)

- Removed conditions when Microsoft Defender for Endpoint was triggering a macOS 11 (Big Sur) bug that manifests into a kernel panic
- Fixed a memory leak in the Endpoint Security system extension when running on mac 11 (Big Sur)
- Bug fixes

## 101.10.72

- Bug fixes

## 101.09.61

- Added a new managed preference for [disabling the option to send feedback](mac-preferences.md#show--hide-option-to-send-feedback)
- Status menu icon now shows a healthy state when the product settings are managed. Previously, the status menu icon was displaying a warning or error state, even though the product settings were managed by the administrator
- Performance improvements & bug fixes

## 101.09.50

- This product version has been validated on macOS Big Sur 11 beta 9

- The new syntax for the `mdatp` command-line tool is now the default one. For more information on the new syntax, see [Resources for Microsoft Defender for Endpoint on macOS](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > The old command-line tool syntax will be removed from the product on **January 1st, 2021**.

- Extended `mdatp diagnostic create` with a new parameter (`--path [directory]`) that allows the diagnostic logs to be saved to a different directory
- Performance improvements & bug fixes

## 101.09.49

- User interface improvements to differentiate exclusions that are managed by the IT administrator versus exclusions defined by the local user
- Improved CPU utilization during on-demand scans
- Performance improvements & bug fixes

## 101.07.23

- Added new fields to the output of `mdatp --health` for checking the status of passive mode and the EDR group ID

  > [!NOTE]
  > `mdatp --health` will be replaced with `mdatp health` in a future product update.

- Fixed a bug where automatic sample submission was not marked as managed in the user interface
- Added new settings for controlling the retention of items in the antivirus scan history. You can now [specify the number of days to retain items in the scan history](mac-preferences.md#antivirus-scan-history-retention-in-days) and [specify the maximum number of items in the scan history](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Bug fixes

## 101.06.63

- Addressed a performance regression introduced in version `101.05.17`. The regression was introduced with the fix to eliminate the kernel panics some customers have observed when accessing SMB shares. We have reverted this code change and are investigating alternative ways to eliminate the kernel panics.

## 101.05.17

> [!IMPORTANT]
> We are working on a new and enhanced syntax for the `mdatp` command-line tool. The new syntax is currently the default in the Insider Fast and Insider Slow update channels. We encourage you to famliliarize yourself with this new syntax.
>
> We will continue supporting the old syntax in parallel with the new syntax and will provide more communication around the deprecation plan for the old syntax in the upcoming months.

- Addressed a kernel panic that occurred sometimes when accessing SMB file shares
- Performance improvements & bug fixes

## 101.05.16

- Improvements to quick scan logic to significantly reduce the number of scanned files
- Added [autocompletion support](mac-resources.md#how-to-enable-autocompletion) for the command-line tool
- Bug fixes

## 101.03.12

- Performance improvements & bug fixes

## 101.01.54

- Improvements around compatibility with Time Machine
- Accessibility improvements
- Performance improvements & bug fixes

## 101.00.31

- Improved [product onboarding experience for Intune users](/mem/intune/apps/apps-advanced-threat-protection-macos)
- Antivirus [exclusions now support wildcards](mac-exclusions.md#supported-exclusion-types)
- Added the ability to trigger antivirus scans from the macOS contextual menu. You can now right-click a file or a folder in Finder and select **Scan with Microsoft Defender for Endpoint**
- In-place product downgrades are now explicitly disallowed by the installer. If you need to downgrade, first uninstall the existing version and reconfigure your device
- Other performance improvements & bug fixes

## 100.90.27

- You can now [set an update channel](mac-updates.md#set-the-channel-name) for Microsoft Defender for Endpoint on macOS that is different from the system-wide update channel
- New product icon
- Other user experience improvements
- Bug fixes

## 100.86.92

- Improvements around compatibility with Time Machine
- Addressed an issue where the product was sometimes not cleaning all files under `/Library/Application Support/Microsoft/Defender` during uninstallation
- Reduced the CPU utilization of the product when Microsoft products are updated through Microsoft AutoUpdate
- Other performance improvements & bug fixes

## 100.86.91

> [!CAUTION]
> To ensure the most complete protection for your macOS devices and in alignment with Apple stopping delivery of macOS native security updates to OS versions older than [current - 2], MDATP for Mac deployment and updates will no longer be supported on macOS Sierra [10.12]. MDATP for Mac updates and enhancements will be delivered to devices running versions Catalina [10.15], Mojave [10.14], and High Sierra [10.13].
>
> If you already have MDATP for Mac deployed to your Sierra [10.12] devices, please upgrade to the latest macOS version to eliminate risks of losing protection.

- Performance improvements & bug fixes

## 100.83.73

- Added more controls for IT administrators around [management of exclusions](mac-preferences.md#exclusion-merge-policy), [management of threat type settings](mac-preferences.md#threat-type-settings-merge-policy), and [disallowed threat actions](mac-preferences.md#disallowed-threat-actions)
- When Full Disk Access is not enabled on the device, a warning is now displayed in the status menu
- Performance improvements & bug fixes

## 100.82.60

- Addressed an issue where the product fails to start following a definition update.

## 100.80.42

- Bug fixes

## 100.79.42

- Fixed an issue where Microsoft Defender for Endpoint on Mac was sometimes interfering with Time Machine
- Added a new switch to the command-line utility for testing the connectivity with the backend service

  ```bash
  mdatp connectivity test
  ```

- Added ability to view the full threat history in the user interface (can be accessed from the **Protection history** view)
- Performance improvements & bug fixes

## 100.72.15

- Bug fixes

## 100.70.99

- Addressed an issue that impacts the ability of some users to upgrade to macOS Catalina when real-time protection is enabled. This sporadic issue was caused by Microsoft Defender for Endpoint locking files within Catalina upgrade package while scanning them for threats, which led to failures in the upgrade sequence.

## 100.68.99

- Added the ability to configure the antivirus functionality to run in [passive mode](mac-preferences.md#enforcement-level-for-antivirus-engine)
- Performance improvements & bug fixes

## 100.65.28

- Added support for macOS Catalina

  > [!CAUTION]
  > macOS 10.15 (Catalina) contains new security and privacy enhancements. Beginning with this version, by default, applications are not able to access certain locations on disk (such as Documents, Downloads, Desktop, etc.) without explicit consent. In the absence of this consent, Microsoft Defender for Endpoint is not able to fully protect your device.
  >
  > The mechanism for granting this consent depends on how you deployed Microsoft Defender for Endpoint:
  >
  > - For manual deployments, see the updated instructions in the [Manual deployment](mac-install-manually.md#how-to-allow-full-disk-access) topic.
  > - For managed deployments, see the updated instructions in the [JAMF-based deployment](mac-install-with-jamf.md) and [Microsoft Intune-based deployment](mac-install-with-intune.md#create-system-configuration-profiles) topics.

- Performance improvements & bug fixes
