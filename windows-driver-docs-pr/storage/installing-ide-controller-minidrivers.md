---
title: 安装 IDE 控制器微型驱动程序
description: 安装 IDE 控制器微型驱动程序
ms.assetid: c1b41f89-150d-47e9-9bed-04f5796f69bd
keywords:
- IDE 控制器微型驱动程序 WDK 存储，安装
- 存储 IDE 控制器微型驱动程序 WDK，安装
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 3ddbb4bc95a6ab90b2045199f57d824351bb61ba
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89192663"
---
# <a name="installing-ide-controller-minidrivers"></a>安装 IDE 控制器微型驱动程序


## <span id="ddk_installing_ide_controller_minidrivers_kg"></span><span id="DDK_INSTALLING_IDE_CONTROLLER_MINIDRIVERS_KG"></span>


本部分提供了特定于 Microsoft Windows 2000 和更高版本操作系统中 IDE 控制器驱动程序和控制器微型驱动程序的安装信息。

提供自己的控制器微型驱动程序的供应商应该使该驱动程序成为硬盘控制器的成员， (在驱动程序的 INF 文件的 [**Inf 版本部分**](../install/inf-version-section.md) 中) 安装程序类。 例如：

```cpp
[version]
Signature="$WINDOWS NT$"
Class=hdc
ClassGuid={4D36E96A-E325-11CE-BFC1-08002BE10318}
```

除了安装 IDE 控制器微型驱动程序，没有其他特殊要求。

有关更多安装信息，包括在 Windows 2000 和更高版本的操作系统中受支持的控制器硬件列表，请参阅系统提供的硬盘控制器 INF 文件 *mshdc*。

有关在 Windows 2000 和更高版本的操作系统中安装设备的常规信息，请参阅 [供应商提供的 IDE 控制器微型驱动程序](requirements-for-vendor-supplied-ide-controller-minidrivers.md) 和 [设备安装概述](../install/overview-of-device-and-driver-installation.md)的要求。

 

