---
title: 报告、启用和禁用 NIC 分析 UDP ESP 数据包的能力
description: 报告、启用和禁用 NIC 分析 UDP ESP 数据包的能力
ms.assetid: 3a75c5b2-2d94-428e-9b2a-d760e14df552
keywords:
- UDP 封装的 ESP 数据包 WDK IPsec 卸载，分析功能
- 分析功能 WDK IPsec 卸载
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 990150de9225e497916f24da6fa00df78fd4cd2a
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89206249"
---
# <a name="reporting-enabling-and-disabling-a-nics-ability-to-parse-udp-esp-packets"></a>报告、启用和禁用 NIC 分析 UDP ESP 数据包的能力

\[IPsec 任务卸载功能已弃用，不应使用。\]




微型端口驱动程序在 [**NDIS \_ IPsec \_ 卸载 \_ V1**](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_ipsec_offload_v1) 结构中指定 NIC 的 Internet 协议安全 (IPsec) 功能。 有关详细信息，请参阅 [报告 NIC 的 IPsec 功能](reporting-a-nic-s-ipsec-capabilities.md)。

微型端口通过在 **支持** 的中设置一个或多个标志来报告 NIC 分析传入的 UDP 封装的 ESP 包的能力。 **Reserved** NDIS \_ IPSEC \_ 卸载 V1 结构的保留成员 \_ 。 微型端口驱动程序可以指定 [udp-Esp 封装类型](udp-esp-encapsulation-types.md)中描述的四个 udp esp 封装子类型中的任何一个或全部。

有关启用和 disableing UDP ESP 分析功能的信息，请参阅 [启用和禁用 Tcp/ip 卸载服务](enabling-and-disabling-task-offload-services.md)。

 

