---
title: KSPROPERTY \_ 横线 \_ PININFO
description: KSPROPERTY \_ 纵横制 \_ PININFO 属性检索由 pin 表示的物理连接类型，包括诸如数据流方向、中等 GUID () 和 pin 类型等设置。
ms.assetid: d025b401-bc75-40d6-a367-1b98e065a48d
keywords:
- KSPROPERTY_CROSSBAR_PININFO 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_CROSSBAR_PININFO
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 6d04e5f649fee1d275a436fee233fc352fe95784
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90102732"
---
# <a name="ksproperty_crossbar_pininfo"></a>KSPROPERTY \_ 横线 \_ PININFO


KSPROPERTY \_ 纵横制 \_ PININFO 属性检索由 pin 表示的物理连接类型，包括诸如数据流方向、中等 GUID () 和 pin 类型等设置。 对于视频 pin，此属性还指示是否存在与特定视频 pin 关联的音频 pin。 必须实现此属性。

## <span id="ddk_ksproperty_crossbar_pininfo_ks"></span><span id="DDK_KSPROPERTY_CROSSBAR_PININFO_KS"></span>


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
<td><p><a href="/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_crossbar_pininfo_s" data-raw-source="[&lt;strong&gt;KSPROPERTY_CROSSBAR_PININFO_S&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_crossbar_pininfo_s)"><strong>KSPROPERTY_CROSSBAR_PININFO_S</strong></a></p></td>
<td><p><a href="/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_crossbar_pininfo_s" data-raw-source="[&lt;strong&gt;KSPROPERTY_CROSSBAR_PININFO_S&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_crossbar_pininfo_s)"><strong>KSPROPERTY_CROSSBAR_PININFO_S</strong></a></p></td>
</tr>
</tbody>
</table>

 

) 操作数据 (的属性值是 KSPROPERTY \_ 纵横制 \_ PININFO \_ S 结构。

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

## <a name="see-also"></a>另请参阅


[**KSPROPERTY**](/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)

[**KSPROPERTY \_ 横线 \_ PININFO \_ S**](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_crossbar_pininfo_s)

