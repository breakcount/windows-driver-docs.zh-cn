---
title: GUID_DEVICE_MEMORY
description: GUID_DEVICE_MEMORY
ms.assetid: 8351585d-6538-41aa-891a-b7c1e0b75cef
keywords:
- GUID_DEVICE_MEMORY 设备和驱动程序安装
topic_type:
- apiref
api_name:
- GUID_DEVICE_MEMORY
api_location:
- Poclass.h
api_type:
- HeaderDef
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: d445484ed6ee5bb0196b650ef10c02c0613674a0
ms.sourcegitcommit: 4db5f9874907c405c59aaad7bcc28c7ba8280150
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2020
ms.locfileid: "89096987"
---
# <a name="guid_device_memory"></a>GUID_DEVICE_MEMORY


GUID_DEVICE_MEMORY [设备接口类](./overview-of-device-interface-classes.md) 定义 (ACPI) 内存设备的高级配置和电源接口。

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
<td align="left"><p>GUID_DEVICE_MEMORY</p></td>
</tr>
<tr class="even">
<td align="left"><p>类 GUID</p></td>
<td align="left"><p>{3FD0F03D-92E0-45FB-B75C-5ED8FFB01021}</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

系统提供的 [ACPI 驱动程序](../kernel/acpi-driver.md) 将注册此设备接口类的实例，通知操作系统和应用程序是否存在 ACPI 内存设备。

有关为 ACPI 设备提供 WDM [函数驱动程序](../kernel/function-drivers.md) 的信息，请参阅 [支持 acpi 设备](../acpi/supporting-acpi-devices.md)。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>标头</p></td>
<td align="left">Poclass (包含 Poclass) </td>
</tr>
</tbody>
</table>

 

