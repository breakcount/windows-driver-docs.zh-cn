---
title: SCSI \_ 地址 WMI 类
description: SCSI \_ 地址 WMI 类
ms.assetid: 720cf803-b004-4c63-8884-66b0e07d82c0
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: dc634fa7f62a98b53dba5276b21fc467b1f14362
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89184927"
---
# <a name="scsi_addr-wmi-class"></a>SCSI \_ 地址 WMI 类


MPIO 驱动程序使用 SCSI \_ 地址 WMI 类识别 MPIO 磁盘的 SCSI 地址。

```cpp
class SCSI_ADDR
{
    //
    // ScsiAddress: Port, Bus, Target, Lun
    //
    [WmiDataId(1)] uint8 PortNumber;
    [WmiDataId(2)] uint8 ScsiPathId;
    [WmiDataId(3)] uint8 TargetId;
    [WmiDataId(4)] uint8 Lun;
};
```

当 WMI 工具套件编译此类定义时，它将生成 [**SCSI \_ 地址**](/windows-hardware/drivers/ddi/mpiowmi/ns-mpiowmi-_scsi_addr) 数据结构。 没有与此 WMI 类相关联的方法。

 

