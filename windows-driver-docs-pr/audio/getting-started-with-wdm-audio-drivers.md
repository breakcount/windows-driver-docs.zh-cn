---
title: WDM 音频驱动程序概述
description: Windows 驱动模型 (WDM) 音频驱动程序使用内核流式处理 (KS) 组件，这些组件在内核模式下运行，并且是操作系统的一部分。
ms.assetid: 573a9b6d-6c50-40a6-9241-470ab418eb66
keywords:
- WDM 音频驱动程序 WDK
- 音频驱动程序 WDK，关于音频驱动程序
- WDM 音频驱动程序 WDK，关于 WDM 音频驱动程序
- 供应商提供的驱动程序 WDK 音频
- 自定义音频驱动程序 WDK
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: a8fc55f232dd8be892a7a823fcf75b7b449cc4ce
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89209219"
---
# <a name="wdm-audio-drivers-overview"></a>WDM 音频驱动程序概述


[Windows 驱动模型](https://docs.microsoft.com/windows-hardware/drivers/kernel/windows-driver-model) (WDM) 音频驱动程序使用 [内核流式处理](../stream/kernel-streaming.md) (KS) 组件，这些组件在内核模式下运行，并且是操作系统的一部分。

硬件供应商应该在开始开发基于 Windows 的音频硬件设备之前做出多种设计决策。

第一决定是设计需要供应商提供的自定义驱动程序的音频设备。 Windows 包含适用于 PCI、USB 和 IEEE 1394 设备的操作系统支持，这些设备符合 Microsoft [通用音频体系结构](universal-audio-architecture.md) (UAA) 指导原则。 供应商无需为 UAA 兼容音频设备提供自定义驱动程序。

但是，如果需要供应商提供的自定义音频驱动程序，则供应商必须选择是否应将驱动程序设计为与 PortCls 系统驱动程序结合使用 ( # A0) 或 AVStream 类系统驱动程序 ( # A1) 。 PortCls 和 AVStream 都是 Windows 操作系统的一部分。 对于大多数音频适配器，PortCls 是正确的选择。 有关 PortCls 的详细信息，请参阅 [Port Class 简介](introduction-to-port-class.md)。 有关 AVStream 的详细信息，请参阅 [AVStream 概述](../stream/avstream-overview.md)。

设计使用 PortCls 的自定义适配器驱动程序时，可以使用 WaveRT 的应用程序将音频适配器上的设备提供给应用程序。 有关详细信息，请参阅 [WaveRT 端口驱动程序简介](introducing-the-wavert-port-driver.md)。

另外两个决策涉及如何显示适配器拓扑，以及如何将数据范围固定到音频应用程序。 拓扑是适配器电路中数据路径和控制节点的逻辑映射。 数据范围指定设备在其波形和 MIDI 流中可以支持的数据格式。 这两个决策都会影响音频适配器上的设备对应用程序的显示方式。

在做出所有前面提到的决策之后，硬件供应商必须根据实现它们的成本来权衡性能增强的价值。 另一个考虑因素是是否可以使用特定解决方案来处理 Windows 系列中的多种产品。 本部分概述了这些问题，并介绍了有关特定主题的更详细文档。

本节包括下列主题：

[通用音频体系结构](universal-audio-architecture.md)

[音频信号处理模式](audio-signal-processing-modes.md)

[自定义音频驱动程序](custom-audio-drivers.md)

[指定拓扑](specifying-the-topology.md)

[指定引脚数据范围](specifying-pin-data-ranges.md)

 

