---
title: KSPROPERTY \_ TVAUDIO \_ CAP
description: KSPROPERTY \_ TVAUDIO \_ cap 属性检索 TV 音频设备的功能。 必须实现此属性。
ms.assetid: a5b7348e-0f85-430c-acf0-c35e289ef338
keywords:
- KSPROPERTY_TVAUDIO_CAPS 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_TVAUDIO_CAPS
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 07bf0b0d6357d2df2b6309c0abcf2f0eb480503e
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90105974"
---
# <a name="ksproperty_tvaudio_caps"></a>KSPROPERTY \_ TVAUDIO \_ CAP


KSPROPERTY \_ TVAUDIO \_ cap 属性检索 TV 音频设备的功能。 必须实现此属性。

## <span id="ddk_ksproperty_tvaudio_caps_ks"></span><span id="DDK_KSPROPERTY_TVAUDIO_CAPS_KS"></span>


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
<td><p><a href="/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_tvaudio_caps_s" data-raw-source="[&lt;strong&gt;KSPROPERTY_TVAUDIO_CAPS_S&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_tvaudio_caps_s)"><strong>KSPROPERTY_TVAUDIO_CAPS_S</strong></a></p></td>
<td><p>ULONG</p></td>
</tr>
</tbody>
</table>

 

 (操作数据) 的属性值是一个 ULONG，它指定 TV 音频设备的功能，例如立体声与 mono 音频支持和多种语言功能。

<a name="remarks"></a>备注
-------

KSPROPERTY **Capabilities** \_ TVAUDIO \_ Cap S 结构的功能成员 \_ 指定 TV 音频设备的功能。

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

[**KSPROPERTY \_ TVAUDIO \_ CAP \_ S**](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksproperty_tvaudio_caps_s)

