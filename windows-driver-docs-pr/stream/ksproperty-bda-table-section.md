---
title: KSPROPERTY \_ BDA \_ 表 \_ 部分
description: '\_ \_ \_ 当在节点的输出上传递数据时，客户端使用 KSPROPERTY BDA 表部分来通知节点要使用的表部分。'
ms.assetid: 58e6cc37-b6f1-49d6-a832-46f1edabf740
keywords:
- KSPROPERTY_BDA_TABLE_SECTION 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_BDA_TABLE_SECTION
api_location:
- Bdamedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: dfd33893a97b1c51ac670140a0cc9236b19a4d82
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89192395"
---
# <a name="ksproperty_bda_table_section"></a>KSPROPERTY \_ BDA \_ 表 \_ 部分


\_ \_ \_ 当在节点的输出上传递数据时，客户端使用 KSPROPERTY BDA 表部分来通知节点要使用的表部分。

## <span id="ddk_ksproperty_bda_table_section_ks"></span><span id="DDK_KSPROPERTY_BDA_TABLE_SECTION_KS"></span>


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
<td><p>BDA_TABLE_SECTION</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>注解
-------

KSP **NodeId**节点的节点成员 \_ 指定了 LNB 放大器节点。

"BDA \_ 表" \_ 部分结构描述了表部分。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Header</p></td>
<td>Bdamedia (包含 Bdamedia) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**BDA \_ 表 \_ 部分**](/windows-hardware/drivers/ddi/bdatypes/ns-bdatypes-_bda_table_section)

[**KSP \_ 节点**](/windows-hardware/drivers/ddi/ks/ns-ks-ksp_node)

 

