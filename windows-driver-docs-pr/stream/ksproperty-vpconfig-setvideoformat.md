---
title: KSPROPERTY \_ VPCONFIG \_ SETVIDEOFORMAT
description: KSPROPERTY \_ VPCONFIG \_ SETVIDEOFORMAT 属性设置视频格式。 格式必须与之前 KSPROPERTY \_ VPCONFIG \_ GETVIDEOFORMAT Get 请求返回的格式匹配。
ms.assetid: f701ad32-ba85-4766-ac6b-11744af8fc0d
keywords:
- KSPROPERTY_VPCONFIG_SETVIDEOFORMAT 流媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_VPCONFIG_SETVIDEOFORMAT
api_location:
- ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: b39f5b54b80592568a9f70e1989d1b7c50197079
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90102232"
---
# <a name="ksproperty_vpconfig_setvideoformat"></a>KSPROPERTY \_ VPCONFIG \_ SETVIDEOFORMAT


KSPROPERTY \_ VPCONFIG \_ SETVIDEOFORMAT 属性设置视频格式。 格式必须与之前 KSPROPERTY \_ VPCONFIG \_ GETVIDEOFORMAT **Get** 请求返回的格式匹配。

## <span id="ddk_ksproperty_vpconfig_setvideoformat_ks"></span><span id="DDK_KSPROPERTY_VPCONFIG_SETVIDEOFORMAT_KS"></span>


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
<td><p>否</p></td>
<td><p>是</p></td>
<td><p>Pin</p></td>
<td><p><a href="/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier" data-raw-source="[&lt;strong&gt;KSPROPERTY&lt;/strong&gt;](/windows-hardware/drivers/ddi/ks/ns-ks-ksidentifier)"><strong>KSPROPERTY</strong></a></p></td>
<td><p><a href="/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-_ddpixelformat" data-raw-source="[&lt;strong&gt;DDPIXELFORMAT&lt;/strong&gt;](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-_ddpixelformat)"><strong>DDPIXELFORMAT</strong></a></p></td>
</tr>
</tbody>
</table>

 

 (操作数据) 的属性值是一个 DDPIXELFORMAT 结构，它指定要使用的视频格式。

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

[**DDPIXELFORMAT**](/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-_ddpixelformat)

