---
title: GUID_NDIS_STATUS_PACKET_FILTER
description: 本主题描述了 NDIS WMI 接口的 GUID_NDIS_STATUS_PACKET_FILTER GUID。
ms.assetid: d842862b-5b9f-46bf-aaa9-4542b3a3e047
keywords:
- GUID_NDIS_STATUS_PACKET_FILTER，WDK GUID_NDIS_STATUS_PACKET_FILTER 网络驱动程序
ms.date: 11/22/2017
ms.localizationpriority: medium
ms.openlocfilehash: bd081804080534b4fe8328b4ef87db7a81a4eda0
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89209739"
---
# <a name="guid_ndis_status_packet_filter"></a>GUID_NDIS_STATUS_PACKET_FILTER

GUID_NDIS_STATUS_PACKET_FILTER 事件 GUID 指示微型端口适配器的数据包筛选器发生了更改。 在 NDIS 6.0 和更高版本中支持此 WMI GUID。

NDIS 生成 NDIS_STATUS_PACKET_FILTER 状态指示，通知过量驱动程序可能存在对数据包筛选器配置的更改。

NDIS 将状态指示转换为 WMI 客户端的 WMI GUID_NDIS_STATUS_PACKET_FILTER 事件。

具有 GUID 的 NDIS 提供的数据缓冲区包含后跟 ULONG 值的 [NDIS_WMI_EVENT_HEADER](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_wmi_event_header) 结构。 有关数据包筛选器状态和可能值的详细信息，请参阅 [OID_GEN_CURRENT_PACKET_FILTER](oid-gen-current-packet-filter.md)。