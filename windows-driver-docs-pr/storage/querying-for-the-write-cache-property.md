---
title: 查询写缓存属性
description: 查询写缓存属性
ms.assetid: 80b7c366-3b54-4dae-8ac7-63caaa1767f9
keywords:
- 存储驱动程序 WDK，写入缓存
- 写入缓存 WDK 存储
- 写回 WDK 存储
- 通过 WDK 存储写入
- 同步缓存支持 WDK 存储
- 电池备份 WDK 存储
- 缓存 WDK 存储
- 查询写入缓存
- 写入请求 WDK 存储
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 102b08d75535511f6014a2196cbec21a3e89dfda
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89185099"
---
# <a name="querying-for-the-write-cache-property"></a>查询写缓存属性


存储设备通常会在写入缓存中缓冲数据，然后再将数据写入非易失性介质（如磁盘盘片）。 这种类型的缓冲区可以提高设备性能，但也会降低数据完整性。 如果写入缓存没有电池备份，则电源故障可能会导致缓存数据丢失。

解决数据丢失问题的一项措施是使用 SCSI 设备) 上的 SCSI SYNCHRONIZE 缓存命令刷新写入缓存 (。 但是，刷新写入缓存是一种开销高昂的操作，如果频繁完成，则会显著降低性能。 许多存储设备允许 *写入* 请求，而不是刷新写入缓存。 直写请求会绕过写入缓存并直接将数据发送到媒体。

例如，数据库应用程序可以使用写请求来确保事务日志到达媒体，而文件系统驱动程序可以使用写请求来确保文件系统元数据到达媒体。

但是，并不是所有具有写入缓存的存储设备都支持写入请求或同步缓存;某些设备不需要将缓存的数据作为一种预防措施，因为它们具有电池备份系统，可防止在电源故障期间发生数据损坏。 应用程序和驱动程序必须具有有关设备的写缓存属性的信息，才能有效地使用它。

在 Windows Vista 中，可以使用具有**StorageDeviceWriteCacheProperty**属性标识符的[**IOCTL \_ 存储 \_ 查询 \_ 属性**](/windows-hardware/drivers/ddi/ntddstor/ni-ntddstor-ioctl_storage_query_property)请求来查询用于指定设备写入缓存特性的写入缓存属性的存储类驱动程序。 写入缓存属性包含有关设备的缓存功能的下列信息：

-   *存在写入缓存*。 写入缓存属性指定设备是否具有写入缓存。

-   *写入缓存的类型*。 写入缓存有两种主要类型： *写回* 和 *写入*。 使用回写缓存，在绝对必要的情况下，设备不会将缓存数据复制到非易失性介质。 此操作改善了写入操作的性能。 使用写入缓存，设备将数据并行写入缓存和媒体。 这不会提高写入性能，但可以更快地执行后续读取操作。

    不要将写入 *缓存* 与写入 *请求*混淆。 如果设备支持写入请求，则可以将写入请求用于任何类型的缓存，包括回写缓存。 例如，假设目标是带有回写缓存的 SCSI 设备。 如果设备支持写入请求，则发起程序可以绕过写入缓存，方法是在命令描述符块中设置 (FUA) 位，并 (CDB) 写入命令。

-   *同步缓存支持*。 写入缓存属性指示设备是否支持 SCSI 同步缓存命令，或其他总线上的等效命令。

-   *备用电池*。 写入缓存属性指示设备是否具有在电源故障期间保护缓存数据完整性的电池备份。

有关写入缓存属性报告的信息的完整说明，请参阅 [**存储 \_ 写入 \_ 缓存 \_ 属性**](/windows-hardware/drivers/ddi/ntddstor/ns-ntddstor-_storage_write_cache_property)。

如果没有写入缓存属性机制 (也就是说，使用 IOCTL \_ 存储 \_ 查询 \_ 属性请求和 **StorageDeviceWriteCacheProperty** 属性标识符) ，应用程序和驱动程序必须使用不同的命令序列为每个总线查询设备的写缓存特性。 例如，如果目标设备连接到 IEEE 1394 总线并使用简化的块命令 (红细胞) 协议，则发起方必须检索设备模式数据的第6页，以确定是否启用了写入缓存。 但如果目标设备符合 SCSI 标准，则发起方必须检索模式数据的第8页。 写缓存属性机制将从发起方中隐藏这些操作的详细信息，并提供一种方法来查询不同总线上的存储设备写入缓存的特征。

 (RAID 设备不支持写入缓存属性机制，因为) 或闪存设备中没有用于查询这些设备的标准技术。

Windows 的64位版本支持写入缓存属性。

 

