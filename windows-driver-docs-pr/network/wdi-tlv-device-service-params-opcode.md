---
title: WDI_TLV_DEVICE_SERVICE_PARAMS_OPCODE
description: WDI_TLV_DEVICE_SERVICE_PARAMS_OPCODE 是一种 TLV，其中包含特定于设备服务的操作码。
ms.assetid: A0C9E728-E0E5-47C1-AEB8-E001057FA35A
ms.date: 06/15/2018
keywords:
- 从 Windows Vista 开始 WDI_TLV_DEVICE_SERVICE_PARAMS_OPCODE 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 1c8a4ee4799d1ddcde2e41908afc28fa94541fea
ms.sourcegitcommit: ca5045a739eefd6ed14b9dbd9249b335e090c4e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2020
ms.locfileid: "85968192"
---
# <a name="wdi_tlv_device_service_params_opcode"></a>WDI_TLV_DEVICE_SERVICE_PARAMS_OPCODE

WDI_TLV_DEVICE_SERVICE_PARAMS_OPCODE 是一种 TLV，其中包含特定于设备服务的操作码。 此 TLV 用于[NDIS_STATUS_WDI_INDICATION_DEVICE_SERVICE_EVENT](ndis-status-wdi-indication-device-service-event.md)状态指示。

## <a name="tlv-type"></a>TLV 类型

0x13F

## <a name="length"></a>长度

UINT8 的大小（以字节为单位）。

## <a name="values"></a>值

| 类型 | 说明 |
| --- | --- |
| TLV\<UINT8\> | 特定于设备服务的操作码。 |

## <a name="requirements"></a>要求

**支持的最低客户端**： Windows 10，版本1809

**支持的最低服务器**： Windows server 2016

**标头**： Wditypes. hpp

