---
title: DSM \_ QUERYSUPPORTEDLBPOLICIES WMI 类
description: DSM \_ QUERYSUPPORTEDLBPOLICIES WMI 类
ms.assetid: fab4d9e6-68fb-42f8-89e5-a5f5b2580964
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: d83f68268f90e805f24085c34e95673ea26cb254
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89185227"
---
# <a name="dsm_querysupportedlbpolicies-wmi-class"></a>DSM \_ QUERYSUPPORTEDLBPOLICIES WMI 类


MPIO 发布 DSM \_ QuerySupportedLBPolicies \_ V2 WMI 类，但要求 DSM 注册 GUID 并处理其实现。 WMI 客户端使用 DSM \_ QuerySupportedLBPolicies \_ V2 WMI 类来查询 DSM 支持的所有负载平衡策略。

```cpp
class DSM_QuerySupportedLBPolicies
{

    [key, read]
    string InstanceName;

    [read]
    boolean Active;

    [WmiDataId(1),
     Description("Number of supported Load Balance policies") : amended
    ]
    uint32 SupportedLBPoliciesCount;

    [WmiDataId(2),
     Description("Reserved") : amended
    ]
    uint32 Reserved;

    [WmiDataId(3),
     WmiSizeIs("SupportedLBPoliciesCount"),
     Description("Supported Load Balance Policies array") : amended
    ]
    DSM_Load_Balance_Policy Supported_LB_Policies[];
};
```

当 WMI 工具套件编译此类定义时，此类定义生成 [**DSM \_ QuerySupportedLBPolicies**](/windows-hardware/drivers/ddi/mpiodisk/ns-mpiodisk-_dsm_querysupportedlbpolicies) 数据结构。 没有与此 WMI 类相关联的方法。

 

