---
title: KSPROPERTY \_ BDA \_ 引脚 \_ 类型
description: 客户端使用 KSPROPERTY \_ BDA \_ pin \_ 类型来检索 PIN 类型的列表。
ms.assetid: de11ab3c-a787-4831-aad4-e97f46432032
keywords:
- KSPROPERTY_BDA_PIN_TYPES 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_BDA_PIN_TYPES
api_location:
- Bdamedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: cb3208d967b9a5df393ec582e9780b4f2509118c
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89192403"
---
# <a name="ksproperty_bda_pin_types"></a>KSPROPERTY \_ BDA \_ 引脚 \_ 类型


客户端使用 KSPROPERTY \_ BDA \_ pin \_ 类型来检索 PIN 类型的列表。

## <span id="ddk_ksproperty_bda_pin_types_ks"></span><span id="DDK_KSPROPERTY_BDA_PIN_TYPES_KS"></span>


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
<td><p>筛选器</p></td>
<td><p>KSPROPERTY</p></td>
<td><p>KSPIN_DESCRIPTOR_EXs 列表</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

在模板拓扑中，每个 pin 类型只能出现一次，但它可以在实际拓扑中出现多次。 此引脚类型列表是 KSPIN \_ 描述符 EX 结构的数组 \_ 。

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


[**BdaPropertyPinTypes**](/windows-hardware/drivers/ddi/bdasup/nf-bdasup-bdapropertypintypes)

[**KSPIN \_ 描述符 \_ EX**](/windows-hardware/drivers/ddi/ks/ns-ks-_kspin_descriptor_ex)

[**KSPROPERTY**](/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)

 

