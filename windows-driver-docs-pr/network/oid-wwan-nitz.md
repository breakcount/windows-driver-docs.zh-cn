---
title: OID_WWAN_NITZ
description: OID_WWAN_NITZ 用于使用网络标识和时区 (NITZ) 查询当前网络时间。
ms.assetid: 5AC5842E-CBD1-47E0-88D2-D3F58CC6F142
ms.date: 04/11/2019
keywords:
- 从 Windows Vista 开始 OID_WWAN_NITZ 网络驱动程序
ms.localizationpriority: medium
ms.custom: 19H1
ms.openlocfilehash: 018e11bb956b36f749dd94ded031efd38cee3f49
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89216140"
---
# <a name="oid_wwan_nitz"></a>OID_WWAN_NITZ

OID_WWAN_NITZ 用于使用网络标识和时区 (NITZ) 查询当前网络时间。

微型端口驱动程序必须异步处理查询请求，最初将 NDIS_STATUS_INDICATION_REQUIRED 返回到原始请求，然后再发送 [NDIS_STATUS_WWAN_NITZ_INFO](ndis-status-wwan-nitz-info.md) 状态通知，其中包含描述当前网络时间和时区的 [**NDIS_WWAN_NITZ_INFO**](/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_nitz_info) 结构。

设置请求不适用。

## <a name="remarks"></a>备注

有关此 OID 的用法的详细信息，请参阅 [MB NITZ 支持](mb-nitz-support.md)。

## <a name="requirements"></a>要求

**版本**： Windows 10，版本 1903 **头**： Ntddndis (包括 Ndis .h) 

## <a name="see-also"></a>另请参阅

[MB NITZ 支持](mb-nitz-support.md)

[NDIS_STATUS_WWAN_NITZ_INFO](ndis-status-wwan-nitz-info.md)

[**NDIS_WWAN_NITZ_INFO**](/windows-hardware/drivers/ddi/ndiswwan/ns-ndiswwan-_ndis_wwan_nitz_info)