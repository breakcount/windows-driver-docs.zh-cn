---
title: 压力测试
description: 压力测试
ms.assetid: 14d20ce2-7d98-4fa3-b639-a4e9b7b07a72
keywords:
- 压力测试 WDK 打印机
- 总线压力测试 WDK 打印机
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 7e5e380e119a3ef842dd65870b55d292fffa2c1b
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63329893"
---
# <a name="stress-testing"></a>压力测试


应为其运行打印机通过压力测试通过发送大 (超过 100 MB) 长 （超过 150 台页面），并占用大量图形资源的打印作业。 对于图形密集型作业，不同类型的图形图像尽可能多地与不同大小的组合。

### <a name="specialized-bus-stress"></a>专用的总线压力

当创建压力情况下时，考虑到专用总线可能出现的考虑因素压力因素。 多个设备可以共享相同的总线，因此请确保测试你的设备与相同的总线-的相同类型或模型中，设备或用户通常具有附加到系统的常见设备上的其他设备正常共存。 例如，无法插入您的打印机所附加到同一个 USB 集线器同时插入多个设备。

建议使用以下测试：

1.  验证该插入几个其他设备中心或系统不会干扰你的设备。

2.  链接多个中心和设备在一起，并验证你的设备继续正常工作。

3.  验证可以同时处理相同的总线上的所有设备。

4.  验证你的设备正常卸载时附加的中心是从系统中拔出。

对于已启用蓝牙的打印机，压力测试上运行的打印作业，如下所示：

1.  移入和移出最大范围的蓝牙无线打印机通常 30 到 90 英尺 （10 到 30 米），具体取决于广播。

2.  将作业发送到打印机的蓝牙无线范围内。

3.  将作业发送到超出最大范围的蓝牙无线打印机。 等待出现，错误状态，然后移动回在范围内以验证它能够顺利地恢复打印机。

 

 




