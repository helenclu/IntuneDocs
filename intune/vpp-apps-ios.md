---
# required metadata

title: Manage iOS volume-purchased apps 
titleSuffix: "Intune on Azure"
description: Learn about how you can sync apps you purchased in volume from the iOS store into Intune and then manage and track their usage."
keywords:
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# How to manage iOS apps you purchased through a volume-purchase program with Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

The iOS app store lets you purchase multiple licenses for an app that you want to run in your company. Purchasing multiple copies of an app helps you reduce the administrative overhead of tracking multiple purchased copies of apps.

Microsoft Intune helps you manage apps that you purchased through this program by:

- Importing the license information from the app store
- Tracking how many of the licenses you have used
- Preventing you from installing more copies of the app than you own

Additionally, you can synchronize, manage, and assign books you purchased from the Apple volume-purchase program store with Intune. Use the **Books** workload in the Intune portal to manage books. The procedures to manage books are the same as you use for managing apps.
You must have uploaded an Apple Volume Purchase Program token before you start. Currently, you can only assign books as a **Required** install.
When you assign a book to a device, that device must have the built-in iBooks app installed. If it is not, the end user must reinstall the app in order to read the book. You cannot currently use Intune to restore removed built-in apps.


## Manage volume-purchased apps for iOS devices
Purchase multiple licenses for iOS apps through the [Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) or the [Apple Volume Purchase Program for Education](http://volume.itunes.apple.com/us/store). This process involves setting up an Apple VPP account from the Apple website and uploading the Apple VPP token to Intune.  You can then synchronize your volume purchase information with Intune and track your volume-purchased app use.

## Before you start
Before you start, you need to get a VPP token from Apple and upload it to your Intune account. Additionally, you should understand the following criteria:

* You can associate multiple volume-purchase program tokens with your Intune account.
* If you previously used a VPP token with a different product, you must generate a new one to use with Intune.
* Each token is valid for one year.
* By default, Intune syncs with the Apple VPP service twice a day. You can start a manual sync at any time.
* After you have imported the VPP token to Intune, do not import the same token to any other device management solution. Doing so might result in the loss of license assignment and user records.
* Before you start to use iOS VPP with Intune, remove any existing VPP user accounts created with other mobile device management (MDM) vendors. Intune does not synchronize those user accounts into Intune as a security measure. Intune only synchronizes data from the Apple VPP service that Intune created.
* Intune supports adding up to 256 VPP tokens.
* If you assign a volume-purchased app for a device enrolled through a Device Enrollment Profile or Apple Configurator, only apps that are targeted to devices work. You cannot target volume-purchased apps to users of a DEP device, which does not have any user affinity.
* A VPP token is only supported for use on one Intune account at a time. Do not reuse the same VPP token for multiple Intune tenants.
* When you assign VPP apps using the user licensing model to users or devices (with user affinity), each Intune user needs to be associated with a unique Apple ID or an email address when they accept the Apple terms and conditions on their device.
Ensure that when you set up a device for a new Intune user, you configure it with that users unique Apple ID or email address. The Apple ID or email address and Intune user form a unique pair and can used on up to 5 devices.


## To get and upload an Apple VPP token

1. Sign into the Azure portal.
2. Choose **More Services** > **Monitoring + Management** > **Intune**.
3. On the **Intune** blade, choose **Mobile apps**.
1.  In the **Mobile Apps** workload, choose **Setup** > **iOS VPP Tokens**.
2.  On the list of VPP tokens blade, click **Add**.
3.  On the **New VPP Token** blade, specify the following information:
	- **VPP token file** - If you haven't already, sign up for the Volume Purchase Program for Business or the program for Education. After you sign up, download the Apple VPP token for your account and select it here.
	- **Apple ID** - Enter the Apple ID of the account associated with the volume-purchase program.
	- **Type of VPP account** - Choose from **Business** or **Education**.
4. When you are done, click **Upload**.

The token is displayed in the list of tokens blade.


You can synchronize the data held by Apple with Intune at any time by choosing **Sync now**.

> [!NOTE]
> Microsoft Intune only syncs information of Apps, which are publicly available through the iTunes Store. **Custom B2B Apps for iOS** are not yet supported. If your scenario targets such apps, the app information is not synchronized.

## To assign a volume-purchased app

1. In the **Mobile Apps** workload, choose **Manage** > **Licensed Apps**.
2. On the list of apps blade, choose the app you want to assign, and then choose '**...**' > **Assign Groups**.
3. On the <*app name*> - **Groups Assigned** blade, choose **Manage** > **Groups Assigned**.
4. Choose **Assign Groups** then, on the **Select groups** blade, choose the Azure AD user or device groups to which you want to assign the app.
You must choose an assignment action of **Required**. Additionally, assignments to device groups are available to new tenants created after January 2017. If your tenant was created before this date, and you do not have the option to assign VPP apps to device groups, contact Intune support.
5. Once you are done, choose **Save**.

>[!NOTE]
>The list of apps displayed is associated with a token. If you have an app that is associated with multiple VPP tokens, you see the same app being displayed multiple times; once for each token.

See [How to monitor apps](apps-monitor.md) for information to help you monitor app assignments.

## Further information

When you assign the app as a **Required** installation, each user who installs the app uses a license.

To reclaim a license, you must change the assignment action to **Uninstall**. The license will be reclaimed after the app is uninstalled.

When a user with an eligible device first tries to install a VPP app, they are asked to join the Apple Volume Purchase program. They must join before the app installation proceeds. The invitation to join the Apple Volume Purchase program requires that the user can use the iTunes app on the iOS device. If you have set a policy to disable the iTunes Store app, user-based licensing for VPP apps does not work. The solution is to either allow the iTunes app by removing the policy, or use device-based licensing.

When you assign a VPP app as Available, the app content and license are assigned directly from the app store.
