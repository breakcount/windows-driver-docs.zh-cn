---
title: 处理 NDIS 端口状态指示
description: 处理 NDIS 端口状态指示
ms.assetid: ba3794de-b17e-4878-a65e-6c9f5f8ebbbc
keywords:
- 端口 WDK NDIS，状态指示
- NDIS 端口 WDK，状态指示
- 状态指示 WDK 网络，NDIS 端口
- 端口状态 WDK NDIS
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 46e23370f3025d071a0f6dc01e0442fa14356a59
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89218412"
---
# <a name="handling-ndis-ports-status-indications"></a>处理 NDIS 端口状态指示





如果 NDIS 端口是状态指示的源，则微型端口驱动程序应使用[**NDIS \_ 状态 \_ 指示**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_status_indication)结构中的**PortNumber**成员来指定源端口。 微型端口驱动程序从不指示非活动端口的状态。

小型端口驱动程序应使用 [**ndis \_ 状态 \_ 端口 \_ 状态**](./ndis-status-port-state.md) 指示来指示 ndis 端口状态的更改。 对于此状态指示，微型端口驱动程序必须在[**NDIS \_ 状态 \_ 指示**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_status_indication)结构的**PortNumber**成员中设置端口号。 NDIS **StatusBuffer** \_ 状态指示结构的 StatusBuffer 成员 \_ 包含指向[**ndis \_ 端口 \_ 状态**](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_port_state)结构的指针。

 

