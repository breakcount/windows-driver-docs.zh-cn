---
title: KSPROPERTY \_ 音频 \_ 宽度
description: KSPROPERTY \_ AUDIO \_ 宽度属性指定立体声图像的宽度 (明显宽度) 。
ms.assetid: 56b18337-c29b-437f-b52f-8d804d857729
keywords:
- KSPROPERTY_AUDIO_WIDENESS 音频设备
topic_type:
- apiref
api_name:
- KSPROPERTY_AUDIO_WIDENESS
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 71f50e8fab3f1a7945585457a55356f74a2958df
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90102030"
---
# <a name="ksproperty_audio_wideness"></a>KSPROPERTY \_ 音频 \_ 宽度


KSPROPERTY \_ AUDIO \_ 宽度属性指定立体声图像的宽度 (明显宽度) 。

## <span id="ddk_ksproperty_audio_wideness_ks"></span><span id="DDK_KSPROPERTY_AUDIO_WIDENESS_KS"></span>


### <a name="span-idusage_summary_tablespanspan-idusage_summary_tablespanspan-idusage_summary_tablespanusage-summary-table"></a><span id="Usage_Summary_Table"></span><span id="usage_summary_table"></span><span id="USAGE_SUMMARY_TABLE"></span>使用情况摘要表

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
<th align="left">获取</th>
<th align="left">设置</th>
<th align="left">目标</th>
<th align="left">属性描述符类型</th>
<th align="left">属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>筛选器</p></td>
<td align="left"><a href="/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksnodeproperty" data-raw-source="[&lt;strong&gt;KSNODEPROPERTY&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksnodeproperty)"><strong>KSNODEPROPERTY</strong></a></td>
<td align="left"><p>ULONG</p></td>
</tr>
</tbody>
</table>

 

操作数据) 的属性值 (为 ULONG 类型，并指定宽度。 宽度表示为带有16位小数的无符号固定点值。 宽度值跟随从零到0xFFFFFFFF 的线性范围：

-   值0x00010000 表示 unity (100%) ，这表示立体声图像的宽度应该与左右扬声器所分帧的区域一致。

-   对于比 unity 大的值，立体声图像应显示在左侧和右侧扬声器所括的区域之外。

-   对于小于 unity 的值，立体声图像的 "感知宽度" 应小于左右扬声器之间的空间。

-   如果值为零，则表示声音应显示为源自左右扬声器的位置。

在宽度值中，立体声图像的外观宽度应该线性增加。

### <a name="span-idreturn_valuespanspan-idreturn_valuespanspan-idreturn_valuespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值

KSPROPERTY \_ 音频 \_ 宽度属性请求返回状态 " \_ 成功" 以指示它已成功完成。 否则，请求将返回相应的错误状态代码。

<a name="remarks"></a>备注
-------

这是宽度节点的属性， ([**KSNODETYPE \_ 立体声 \_ 范围**](ksnodetype-stereo-wide.md)) 。 宽度节点可以将 spaciousness 添加到现有立体声 (两通道) 流。 若要实现此效果，该节点将处理该流，使某些声音看起来就像由左右扬声器括起来的区域之外的位置。

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
<td align="left">Ksmedia (包含 Ksmedia) </td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另请参阅


[**KSNODEPROPERTY**](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksnodeproperty)

[**KSNODETYPE \_ 立体声 \_**](ksnodetype-stereo-wide.md)

