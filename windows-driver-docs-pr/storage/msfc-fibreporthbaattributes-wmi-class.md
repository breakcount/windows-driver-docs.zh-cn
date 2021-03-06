---
title: MSFC \_ FIBREPORTHBAATTRIBUTES WMI 类
description: MSFC \_ FIBREPORTHBAATTRIBUTES WMI 类
ms.assetid: 028afadf-1a2d-4792-8b6c-d53359af64c1
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 3d7e93a436daa488fe0509eef178e6daca223915
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89184081"
---
# <a name="msfc_fibreporthbaattributes-wmi-class"></a>MSFC \_ FIBREPORTHBAATTRIBUTES WMI 类


## <span id="ddk_msfc_fibreporthbaattributes_wmi_class_kr"></span><span id="DDK_MSFC_FIBREPORTHBAATTRIBUTES_WMI_CLASS_KR"></span>


支持 FCbre 通道 HBA API 的 HBA 微型端口驱动程序使用 MSFC \_ FIBREPORTHBAATTRIBUTES WMI 类公开与光纤通道端口关联的属性信息。 每个端口都应有此类的一个实例。

MSFC \_ FibrePortHBAAttributes 类在 *Hbaapi*中定义如下：

```cpp
class MSFC_FibrePortHBAAttributes {
  [key] 
  string InstanceName;
  boolean Active;
  [Description ("Unique identifier for the port. "
    "This identifier must be unique among all "
    "ports on all adapters. The same value for "
    "in other classes that expose port information"
    "the identifier must be used for the same port") : amended,
    WmiRefClass("MSFC_FibrePort"),
    WmiRefProperty("UniquePortId"),
    WmiDataId(1)
    ] uint64 UniquePortId;
  [HBA_STATUS_QUALIFIERS, WmiDataId(2)] HBA_STATUS  HBAStatus;
  [HBAType("HBA_PORTATTRIBUTES"),WmiDataId(3)]
    MSFC_HBAPortAttributesResults Attributes;
};
```

由 WMI 工具套件编译时，此类定义生成以下数据结构：

[**MSFC \_ FibrePortHBAAttributes**](/windows-hardware/drivers/ddi/hbapiwmi/ns-hbapiwmi-_msfc_fibreporthbaattributes)

没有与此 WMI 类相关联的方法。

 

