---
title: '视频微型端口驱动程序中的镜像驱动程序支持 (XDDM) '
description: 视频微型端口驱动程序中的镜像驱动程序支持（Windows 2000 模型）
ms.assetid: ca91e0a6-d619-432a-829e-49012951f27c
keywords:
- 视频微型端口驱动程序 WDK Windows 2000，镜像驱动程序
- 镜像驱动程序 WDK Windows 2000 显示
ms.date: 12/06/2018
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 119c65f70d7f09077d559cc26e2c8fe15591ea9f
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89066490"
---
# <a name="mirror-driver-support-in-video-miniport-drivers-windows-2000-model"></a>视频微型端口驱动程序中的镜像驱动程序支持（Windows 2000 模型）

> [!NOTE]
>
> 从 Windows 8 开始，镜像驱动程序将不会安装在系统上。 有关详细信息，请参阅 [镜像驱动程序](mirror-drivers.md)。


Windows 2000 和更高版本提供了对视频微型端口驱动程序的*镜像驱动程序*支持，因此小型端口驱动程序不能有任何特殊代码来尝试此类支持。 有关镜像系统中显示驱动程序的详细信息，请参阅 [镜像驱动程序](mirror-drivers.md) 。

镜像驱动程序微型端口驱动程序的要求很小。 唯一必须实现的函数是 [**DriverEntry**](./driverentry-of-video-miniport-driver.md)，它是由微型端口驱动程序导出的，以及以下内容：

[*HwVidFindAdapter*](/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_find_adapter)

[*HwVidInitialize*](/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_initialize)

[*HwVidStartIO*](/windows-hardware/drivers/ddi/video/nc-video-pvideo_hw_start_io)

由于不存在与镜像图面关联的物理显示设备，因此前面列表中显示的三个功能都可以是始终返回 success 的空实现。