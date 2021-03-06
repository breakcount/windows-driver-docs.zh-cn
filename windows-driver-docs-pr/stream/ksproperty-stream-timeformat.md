---
title: KSPROPERTY \_ 流 \_ TIMEFORMAT
description: KSPROPERTY \_ STREAM \_ TIMEFORMAT 属性用于检索特定 pin 连接上使用的时间格式。
ms.assetid: bf8c32b2-401f-4f89-bcca-97a07c50cc45
keywords:
- KSPROPERTY_STREAM_TIMEFORMAT 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_STREAM_TIMEFORMAT
api_location:
- ks.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: b349565f84e31096803e8a6a590cdb58e0a3cf49
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90106976"
---
# <a name="ksproperty_stream_timeformat"></a>KSPROPERTY \_ 流 \_ TIMEFORMAT


KSPROPERTY \_ STREAM \_ TIMEFORMAT 属性用于检索特定 pin 连接上使用的时间格式。

## <span id="ddk_ksproperty_stream_timeformat_ks"></span><span id="DDK_KSPROPERTY_STREAM_TIMEFORMAT_KS"></span>


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
<td><p>GUID</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

属性返回 GUID，该 GUID 指定连接中使用的时间格式，并指示呈现时间和范围的格式。 定义的时间格式对应于 DirectShow 定义的时间格式。

KSPROPERTY \_ STREAM \_ TIMEFORMAT 是一个可选属性，如果 pin 支持 "速率"、"表示时间/区" 或 "跳过降级属性" (应实现此属性，有关这些属性的详细信息，请参阅 [质量管理](./quality-management.md)) 。 这样一来，客户端就可以确定用于连接的时间格式，以及在速率、演示时间/范围和跳过降级操作中使用的时间戳信息的格式。

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
<td>Ks (包含 Ks .h) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[**KSPROPERTY**](/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)

