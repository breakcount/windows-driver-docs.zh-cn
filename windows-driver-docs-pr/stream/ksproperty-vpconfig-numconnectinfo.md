---
title: KSPROPERTY \_ VPCONFIG \_ NUMCONNECTINFO
description: KSPROPERTY \_ VPCONFIG \_ NUMCONNECTINFO 属性获取电源连接配置的最大数目。
ms.assetid: 8ffab85d-cf0d-44d7-ba37-692c3adfa1e5
keywords:
- KSPROPERTY_VPCONFIG_NUMCONNECTINFO 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_VPCONFIG_NUMCONNECTINFO
api_location:
- ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: a26c81e3e3568af58d8b2441b797bbb69c2234d3
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90105924"
---
# <a name="ksproperty_vpconfig_numconnectinfo"></a>KSPROPERTY \_ VPCONFIG \_ NUMCONNECTINFO


KSPROPERTY \_ VPCONFIG \_ NUMCONNECTINFO 属性获取电源连接配置的最大数目。

## <span id="ddk_ksproperty_vpconfig_numconnectinfo_ks"></span><span id="DDK_KSPROPERTY_VPCONFIG_NUMCONNECTINFO_KS"></span>


### <a name="usage-summary-table"></a>使用情况摘要表

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>获取</th>
<th>设置</th>
<th>目标</th>
<th>属性描述符类型</th>
<th>属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>是</p></td>
<td><p>否</p></td>
<td><p>Pin</p></td>
<td><p><a href="/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier" data-raw-source="[&lt;strong&gt;KSPROPERTY&lt;/strong&gt;](/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)"><strong>KSPROPERTY</strong></a></p></td>
<td><p>DWORD</p></td>
</tr>
</tbody>
</table>

 

 (操作数据) 的属性值是一个 DWORD 值，用于描述视频端口配置的最大数目。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>标头</p></td>
<td>Ksmedia (包含 Ksmedia) </td>
</tr>
</tbody>
</table>

