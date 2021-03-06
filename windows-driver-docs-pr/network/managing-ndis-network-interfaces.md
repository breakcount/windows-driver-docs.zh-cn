---
title: 管理 NDIS 网络接口
description: 管理 NDIS 网络接口
ms.assetid: b4c61b8a-a3ef-449d-9bce-853d91911dc4
keywords:
- NDIS 网络接口 WDK，管理
- 网络接口 WDK，管理
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: aae2cb572a3504cd3d605093b94115dc249d84f3
ms.sourcegitcommit: b84d760d4b45795be12e625db1d5a4167dc2c9ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90715740"
---
# <a name="managing-ndis-network-interfaces"></a>管理 NDIS 网络接口





NDIS 网络接口提供程序向 NDIS 注册网络接口。 在注册接口之前，接口提供程序会获取该接口的 [**NET \_ LUID**](/windows/win32/api/ifdef/ns-ifdef-net_luid_lh) 值。 当注册时，NDIS 会将 ( 在 RFC 2863) 的 *IfIndex* 中的接口索引分配给接口。

NDIS 还提供了一些服务，驱动程序可以使用这些服务来管理 (RFC 2863) 中的接口堆栈 *表中的* 条目。

本节包括：

[NET \_ LUID 值](net-luid-value.md)

[使用 NET \_ LUID 索引](using-a-net-luid-index.md)

[注册网络接口](registering-a-network-interface.md)

[取消注册网络接口](deregistering-a-network-interface.md)

[将 NET \_ LUID 值映射到接口索引](mapping-a-net-luid-value-to-an-interface-index.md)

[\_微型端口适配器和筛选器模块的 NET LUID 值](net-luid-values-for-miniport-adapters-and-filter-modules.md)

[维护网络接口堆栈](maintaining-a-network-interface-stack.md)

 

