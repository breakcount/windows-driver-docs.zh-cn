---
title: 分区单元的热更换
description: 分区单元的热更换
ms.assetid: 6d50dc7d-6c3b-41e5-b6eb-aead9833dd1e
keywords:
- 动态硬件分区 WDK，热替换
- 硬件分区 WDK 动态、热替换
- 将 WDK 动态硬件分区、热替换
- 热替换 WDK 动态硬件分区
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: 08f6e6aa61712675aac3d0e9dddc7dc627152cad
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89193229"
---
# <a name="hot-replace-of-partition-units"></a>分区单元的热更换


在动态分区的服务器上，随时可以动态替换硬件分区中的分区单位。 这称为热替换操作。 在更换分区单元时，操作系统会将硬件分区置于伪 S4 睡眠状态。 为了使硬件分区进入此特殊睡眠状态，操作系统会将一个 S4 设备 *电源* 管理请求发送到系统中的所有设备驱动程序。 但是，与典型的 S4 电源状态不同的是，操作系统不会将系统状态写出到休眠文件。

设备驱动程序必须通过正确地处理 *查询功能* 和 *设置电源* 管理请求，来支持此伪 S4 睡眠状态。 设备驱动程序不得拒绝 *查询电源* 请求。 当设备驱动程序收到 S4 *电源* 管理请求时，它必须将其设备转换为 D3 设备电源状态并停止所有 i/o 操作。 这包括 (DMA) 当前正在进行的任何直接内存访问。 通过将驱动程序的设备置于低功耗状态，禁用中断，并停止正在进行的所有 i/o 操作，replace 操作可以继续，而不会影响设备驱动程序。

如果设备驱动程序的设备处于 D3 电源状态，则设备驱动程序应该对它收到的任何新的 i/o 请求进行排队。 设备驱动程序应将 i/o 超时期限用于其处理的 i/o 请求。 此超时期限必须足够长，以便在更换分区单元时，i/o 请求停止或排队，使其不会超时。 当操作系统从伪 S4 睡眠状态恢复时，设备驱动程序可以继续处理任何已停止或排队的 i/o 请求。

有关如何对设备驱动程序中的电源管理实现支持的详细信息，请参阅 [电源管理](./introduction-to-power-management.md)。

设备驱动程序不得将自身绑定到系统硬件的唯一可识别实例，如特定处理器。 否则，如果在硬件分区中替换了包含该硬件的分区单元，驱动程序可能会失败。

 

