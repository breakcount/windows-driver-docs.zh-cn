---
title: GUID_DEVINTERFACE_WPD
description: GUID_DEVINTERFACE_WPD
ms.assetid: 611d1866-2530-4acb-8c83-77c29bdd128c
keywords:
- GUID_DEVINTERFACE_WPD 设备和驱动程序安装
topic_type:
- apiref
api_name:
- GUID_DEVINTERFACE_WPD
api_location:
- Portabledevice.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: d7d58d1faa80e4e4641ac3030cdb8d6952baf8cc
ms.sourcegitcommit: 4db5f9874907c405c59aaad7bcc28c7ba8280150
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2020
ms.locfileid: "89096871"
---
# <a name="guid_devinterface_wpd"></a>GUID_DEVINTERFACE_WPD


GUID_DEVINTERFACE_WPD [设备接口类](./overview-of-device-interface-classes.md) 是 (WPD) 的 [Windows 便携设备](https://go.microsoft.com/fwlink/p/?linkid=106527) 定义的。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Attribute</th>
<th align="left">设置</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>标识符</p></td>
<td align="left"><p>GUID_DEVINTERFACE_WPD</p></td>
</tr>
<tr class="even">
<td align="left"><p>类 GUID</p></td>
<td align="left"><p>{6AC27878-A6FA-4155-BA85-F98F491D4F33}</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

适用于设备的驱动程序，这些设备支持 WPD 设备驱动程序接口 (DDI) 注册 GUID_DEVINTERFACE_WPD 的实例，通知操作系统和 WPD 设备存在的应用程序。

WPD 类扩展组件为使用 WPD 类扩展的 WPD 驱动程序注册此设备接口的实例。

使用 WPD 设备的客户端应注册，通知此设备接口类的实例到达。

客户端可以通过调用 Windows SDK) 中记录的 **IPortableDeviceManager：： GetDevices** (来枚举注册此接口的 WPD 设备。

有关专用 WPD 设备的设备接口类的信息，请参阅 [**GUID_DEVINTERFACE_WPD_PRIVATE**](guid-devinterface-wpd-private.md)。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>版本</p></td>
<td align="left"><p>在 windows Vista、Windows XP 和更高版本的 Windows 中可用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>标头</p></td>
<td align="left">Portabledevice (包含 Portabledevice) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[**GUID_DEVINTERFACE_WPD_PRIVATE**](guid-devinterface-wpd-private.md)

 

