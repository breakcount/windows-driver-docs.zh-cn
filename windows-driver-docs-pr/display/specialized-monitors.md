---
title: 打印头和专用监视器
description: 打印头和专用监视器
keywords:
- 显示设备 WDK
- 监视驱动程序 WDK
- 显示驱动程序 WDK，监视驱动程序
- monitors
- HMD
- 虚拟现实
ms.date: 11/30/2018
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.localizationpriority: medium
ms.openlocfilehash: a7ab45724cae973993235e3085232d3a80c6b188
ms.sourcegitcommit: e6247811ff9a07070547af3d89705dae33a2f465
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91026430"
---
# <a name="head-mounted-and-specialized-monitors"></a>打印头和专用监视器

Windows 内置了对 head 装载的支持 (HMDs) 和其他类型的 "专用" 显示方案。 这些显示只能由自定义排序器来寻址，因为标准 Windows 系统组合器 (DWM) 忽略这些显示。 此外，Windows 提供了 HMDs 和专用化的显示的下列属性：

* 由于系统组合器会忽略它们 (DWM) ，因此无法将 Windows shell 扩展到这些显示 (如墙纸、桌面图标、任务栏) 。
* 当 PC 正在使用时，操作系统不会自动打开它们。
* 它们不会接收触摸或鼠标输入。
* 它们可由应用进行控制，以便进行专用控制和演示，并受访问模型的限制。

Windows Mixed Reality 耳机是自定义组合器控制的 HMDs 的一个示例。 类似的解决方案可由第三方使用本文档生成。

## <a name="topics"></a>主题

[用于 head 装载和专用监视器的 EDID 扩展](specialized-monitors-edid-extension.md)

[为 HMDs 和专用显示器生成自定义排序器](specialized-monitors-compositor.md)

## <a name="version-history"></a>版本历史记录

### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10 版本 1709 (秋季创建者更新) 

* Windows Mixed Reality 附带了对虚拟现实设备的支持。 Windows Mixed Reality 设备必须符合适用于 HMDs 版本1的 Microsoft EDID 扩展。

### <a name="windows-10-version-1809"></a>Windows 10 版本 1809

* 添加了对使用 Api 系列构建第三方 HMD 排序器的支持 `Windows.Devices.Display.Core` 。 支持的设备必须符合 Microsoft EDID extension for HMDs 版本2。

### <a name="windows-10-version-2004"></a>Windows 10 版本 2004

* * * 增加了对 "专用" 的支持，其中包含适用于 HMDs 和专用显示器的 Microsoft EDID extension 版本3。
* * * 增加了对用户的支持，可通过设置将任何监视器指定为 "专用" 显示。

* * 适用于 Windows 10 企业版、Windows 10 专业版工作站和 Windows 10 IoT 企业版