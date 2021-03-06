---
title: KSPROPERTY \_ BDA \_ PIDFILTER \_ 列表 \_ PID
description: 客户端使用 KSPROPERTY \_ BDA \_ PIDFILTER \_ LIST \_ pid 从 PID 筛选器节点检索它的 pid 列表，该节点标识节点从输入流传递到输出流的数据包组。
ms.assetid: fc7dc0af-af74-4bd1-b99c-f06de25aae3c
keywords:
- KSPROPERTY_BDA_PIDFILTER_LIST_PIDS 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_BDA_PIDFILTER_LIST_PIDS
api_location:
- Bdamedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 182a9121e4b3803bd4d931af96985b0f880dd28e
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89183821"
---
# <a name="ksproperty_bda_pidfilter_list_pids"></a>KSPROPERTY \_ BDA \_ PIDFILTER \_ 列表 \_ PID


客户端使用 KSPROPERTY \_ BDA \_ PIDFILTER \_ LIST \_ pid 从 PID 筛选器节点检索它的 pid 列表，该节点标识节点从输入流传递到输出流的数据包组。

## <span id="ddk_ksproperty_bda_pidfilter_list_pids_ks"></span><span id="DDK_KSPROPERTY_BDA_PIDFILTER_LIST_PIDS_KS"></span>


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
<td><p>是</p></td>
<td><p>筛选器</p></td>
<td><p>KSP_NODE</p></td>
<td><p>Pid 列表</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

KSP **NodeId** \_ 节点的节点标识号指定 PID 筛选器节点的标识符。

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
<td>Bdamedia (包含 Bdamedia) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[**KSP \_ 节点**](/windows-hardware/drivers/ddi/ks/ns-ks-ksp_node)

 

