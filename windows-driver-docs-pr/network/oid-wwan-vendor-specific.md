---
title: OID_WWAN_VENDOR_SPECIFIC
description: OID_WWAN_VENDOR_SPECIFIC 允许微型端口驱动程序实现特定于供应商的对象。
ms.assetid: 7c1843bc-3d60-437c-a24d-6da82262a468
ms.date: 08/08/2017
keywords: -从 Windows Vista 开始 OID_WWAN_VENDOR_SPECIFIC 的网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 42b9919ec090487e757aa5d5b07200cff2cd36b4
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89216982"
---
# <a name="oid_wwan_vendor_specific"></a>OID \_ WWAN \_ 供应商 \_ 特定


OID \_ WWAN \_ 供应商 \_ 特定允许微型端口驱动程序实现特定于供应商的对象。

不支持查询请求。

微型端口驱动程序必须异步处理设置请求，最初 \_ 返回 \_ \_ 原始请求所需的 ndis 状态指示，稍后发送 [**ndis \_ 状态 " \_ WWAN \_ 供应商 \_ 特定**](ndis-status-wwan-vendor-specific.md) 状态通知"，其中包含一个供应商定义的结构，以在完成该事务时实现专用对象。

<a name="remarks"></a>备注
-------

有关使用此 OID 的详细信息，请参阅 [WWAN 供应商特定操作](./mb-vendor-specific-operations.md)。

如果微型端口驱动程序 \_ 不 \_ \_ 支持特定于供应商的操作，则它应返回不受支持的 NDIS 状态。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>版本</p></td>
<td><p>在 windows 7 和更高版本的 Windows 中可用。</p></td>
</tr>
<tr class="even">
<td><p>标头</p></td>
<td>Ntddndis (包含 Ndis .h) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[WWAN 供应商特定操作](./mb-vendor-specific-operations.md)

[**NDIS \_ 状态 \_ WWAN \_ 供应商 \_ 特定**](ndis-status-wwan-vendor-specific.md)

 

