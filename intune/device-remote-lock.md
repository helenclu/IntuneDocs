---
# required metadata

title: Remotely lock managed devices with Intune 
titleSuffix: "Intune on Azure"
description: Learn how to use Intune to remotely lock devices you manage."
keywords:
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: ilwu
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure

---

# Remotely lock managed devices with Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

The **Remote lock** device locks the selected device. The device owner must use their passcode to unlock it. You can only remotely lock a device that has a PIN or password set.

1. Sign into the Azure portal.
2. Choose **More Services** > **Monitoring + Management** > **Intune**.
3. On the **Intune** blade, choose **Devices**.
4. On the **Devices and groups** blade, choose **All devices**.
5. From the list of devices you manage, choose a device, and then choose the **Remote lock** device remote action.

To see the status of the action you just took, on the **Devices and groups** blade, choose **Device Actions**.
