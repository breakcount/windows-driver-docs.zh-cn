---
title: usbkd _ehciep
description: _Ehciep usbkd 命令显示 usbehci _ENDPOINT_DATA 结构中的信息。 使用此命令显示 (的异步终结点的相关信息，) 控制和批量终结点。
ms.assetid: 0DA42FDD-41D6-4234-9D9C-36872F0CE0C1
keywords:
- usbkd _ehciep Windows 调试
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- usbkd._ehciep
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 100e5a10ed3be099030fd55b0a4887a1e6937b72
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89210877"
---
# <a name="usbkd_ehciep"></a>！ usbkd。 \_ehciep


**！ Usbkd。 \_ehciep**命令显示 usbehci 中的信息 **！ \_终结点 \_ 数据**结构。 使用此命令显示 (的异步终结点的相关信息，) 控制和批量终结点。

```dbgcmd
!usbkd._ehciep StructAddr
```

## <a name="span-idddk__devobj_dbgspanspan-idddk__devobj_dbgspanparameters"></a><span id="ddk__devobj_dbg"></span><span id="DDK__DEVOBJ_DBG"></span>参数


<span id="_______StructAddr______"></span><span id="_______structaddr______"></span><span id="_______STRUCTADDR______"></span>*StructAddr*   
Usbehci 的地址 **！ \_终结点 \_ 数据** 结构。 查找 usbehci 的地址 **！ \_终结点 \_ 数据** 结构，请使用 [**！ usbhcdext**](-usbkd-usbhcdext.md) 和 [**！ usblist**](-usbkd-usblist.md)。

## <a name="span-iddllspanspan-iddllspandll"></a><span id="DLL"></span><span id="dll"></span>.DLL


Usbkd.dll

<a name="examples"></a>示例
--------

此示例展示了获取 usbehci 地址的一种方法 **！ \_终结点 \_ 数据** 结构。 从 [**！ usb2tree**](-usbkd-usb2tree.md) 命令开始。

```dbgcmd
0: kd> !usbkd.usb2tree
...
2)!ehci_info ffffe0000206e1a0 !devobj ffffe0000206e050 PCI: VendorId 8086 DeviceId 293c RevisionId 0002 
    RootHub !hub2_info ffffe000024a61a0 !devstack ffffe000024a6050
        Port 1: !port2_info ffffe000026dd000 
        Port 2: !port2_info ffffe000026ddb40 
        Port 3: !port2_info ffffe000026de680 !devstack ffffe00001ec3060
            !device2_info ffffe00001ec31b0 (USB Mass Storage Device: Xxx Corporation)
        Port 4: !port2_info ffffe000026df1c0 
```

在上面的输出中，FDO 的设备扩展的地址显示为 [DML](debugger-markup-language-commands.md) 命令 **！ ehci \_ info ffffe0000206e1a0**的参数。 单击 DML 命令或将设备扩展的地址传递给 [**！ usbhcdext**](-usbkd-usbhcdext.md)。

```dbgcmd
0: kd> !usbkd.usbhcdext ffffe0000206e1a0
...
DeviceHandleList: !usblist ffffe0000206f3b8, DL 
DeviceHandleDeletedList: !usblist ffffe0000206f3c8, DL [Empty]
GlobalEndpointList: !usblist ffffe0000206f388, EP 
...
```

前面的输出显示了命令 **！ usblist ffffe0000206f388，EP**。 使用此命令可以显示终结点的列表。

```dbgcmd
0: kd> !usblist ffffe0000206f388, EP 
list: ffffe0000206f388 EP
...
dt usbport!_HCD_ENDPOINT ffffe000026dc970  !usbep ffffe000026dc970
common buffer bytes 0x00003000 (12288) @ va 0000000021e6e000 pa 00000000d83c9000
Device Address: 0x01, ep 0x81 Bulk In Flags: 00000041 dt _USB_ENDPOINT_FLAGS ffffe000026dc990
... usbehci!_ENDPOINT_DATA ffffe000026dcc38
...
```

在上面的输出中， `ffffe000026dcc38` 是 usbehci 的地址 **！ \_终结点 \_ 数据** 结构。 将此地址传递给 **！ \_ehciep**。

```dbgcmd
0: kd> !usbkd._ehciep ffffe000026dcc38
*USBEHCI
dt usbehci!_ENDPOINT_DATA ffffe000026dcc38
Flags: 0x00000000
dt usbehci!_HCD_QUEUEHEAD_DESCRIPTOR ffffd00021e6e080
*HwQH ffffd00021e6e080
HwQH
     HwQH.HLink dea2e002
     HwQH.EpChars 02002101
         DeviceAddress: 0x1
         IBit: 0x0
         EndpointNumber: 0x1
         EndpointSpeed: 0x2 HcEPCHAR_HighSpeed
         DataToggleControl: 0x0
         HeadOfReclimationList: 0x0
         MaximumPacketLength: 0x200 - 512
   ...
current slot 0000000000000000
slot[0] dt usbehci!_ENDPOINT_SLOT ffffe000026dcdb8 - slot_NotBusy
----
     ffffd00021e6e100
     dt usbehci!_HCD_TRANSFER_DESCRIPTOR ffffd00021e6e100
    tdphys: d83c9100'200 txlen 00000000 tx ffffd00000000041 flags 6d4e695d  _BUSY _SLOT_RESET
    Next_qTD: d83c9200'd83c9180 AltNext_qTD 77423c00'41 
    NextTD: ffffd00021e6e200 AltNextTD ffffd00021e6e180 SlotNextTd ffffd00021e6e200 tok 00000c00  Xbytes x0 (0)
.
     ffffd00021e6e200
     dt usbehci!_HCD_TRANSFER_DESCRIPTOR ffffd00021e6e200
    tdphys: d83c9200'5000 txlen 00000000 tx ffffd00000000041 flags 6d4e695d  _BUSY _SLOT_RESET
    Next_qTD: d83c9280'd83c9180 AltNext_qTD 77423c00'41 
    NextTD: ffffd00021e6e280 AltNextTD ffffd00021e6e180 SlotNextTd ffffd00021e6e280 tok 00000c00  Xbytes x0 (0)
...
```

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另请参阅


[USB 2.0 调试器扩展](usb-2-0-extensions.md)

[ (USB) 驱动程序的通用串行总线](../usbcon/index.md)

 

