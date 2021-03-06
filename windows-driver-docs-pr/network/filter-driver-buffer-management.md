---
title: 筛选器驱动程序缓冲区管理
description: 筛选器驱动程序缓冲区管理
ms.assetid: 92b38710-056d-4853-b266-ca86cee298b6
keywords:
- 筛选器驱动程序 WDK 网络，缓冲区
- NDIS 筛选器驱动程序 WDK，缓冲区
- 缓冲区管理 WDK NDIS 筛选器
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 8fff94f453fa96750da135d1d90be51a429120bc
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89217066"
---
# <a name="filter-driver-buffer-management"></a>筛选器驱动程序缓冲区管理





筛选器驱动程序创建缓冲区以复制从其他驱动程序获取的网络数据，或用于启动发送或接收操作。

如果筛选器驱动程序不创建缓冲区，则驱动程序不会管理缓冲池。 此类驱动程序只需将其从其他驱动程序接收的缓冲区传递到该驱动程序。

用于创建支持发送或接收操作的缓冲区的筛选器驱动程序必须管理 [**网络 \_ 缓冲区 \_ 列表**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer_list) 结构池和 [**网络 \_ 缓冲区**](/windows-hardware/drivers/ddi/ndis/ns-ndis-_net_buffer) 结构池。

若要创建这些池，驱动程序将调用以下函数：

[**NdisAllocateNetBufferListPool**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlistpool)

[**NdisAllocateNetBufferPool**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferpool)

筛选器驱动程序可以使用以下函数从池中分配结构：

[**NdisAllocateNetBufferAndNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferandnetbufferlist)

[**NdisAllocateNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbufferlist)

[**NdisAllocateNetBuffer**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisallocatenetbuffer)

调用 **NdisAllocateNetBufferAndNetBufferList** 比调用 **NdisAllocateNetBufferList** 后跟 **NdisAllocateNetBuffer**更有效。 但是， **NdisAllocateNetBufferAndNetBufferList** 只 \_ 在网络 \_ 缓冲区列表结构上创建了一个网络缓冲区结构 \_ 。 若要**使用 NdisAllocateNetBufferAndNetBufferList**，则在调用**NdisAllocateNetBufferListPool**时，驱动程序必须将*AllocateNetBuffer*参数设置为**TRUE** 。

发起发送请求的筛选器驱动程序应该确定基础驱动程序的上下文和回填空间要求。 筛选器驱动程序使用重新启动属性来确定底层驱动程序的回填要求。 筛选器驱动程序应该确定 *重启* 状态中的回填和环境要求。 驱动程序应为整个堆栈分配足够的回填和上下文空间。 如有必要，筛选器驱动程序可以释放池，并在 *重新启动* 状态下重新分配池。

筛选器驱动程序使用以下函数来释放池：

[**NdisFreeNetBufferListPool**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlistpool)

[**NdisFreeNetBufferPool**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferpool)

筛选器驱动程序使用以下函数来释放从池中分配的结构：

[**NdisFreeNetBufferList**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbufferlist)

[**NdisFreeNetBuffer**](/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisfreenetbuffer)

\_在释放关联的**NdisAllocateNetBuffer**网络 \_ 缓冲区列表结构之前，驱动程序应释放用 NdisAllocateNetBuffer 分配的网络缓冲区结构 \_ 。 \_当驱动程序为关联**NdisAllocateNetBufferAndNetBufferList**的**NdisFreeNetBufferList**网络 \_ 缓冲区列表结构调用 NdisFreeNetBufferList 时，将释放用 NdisAllocateNetBufferAndNetBufferList 分配的网络缓冲区结构 \_ 。

 

