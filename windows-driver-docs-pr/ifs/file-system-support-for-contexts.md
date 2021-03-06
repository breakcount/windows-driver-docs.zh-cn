---
title: 用于上下文的文件系统支持
description: 用于上下文的文件系统支持
ms.assetid: 661ee3ff-3171-4d1e-a8fe-8d1852c5e990
keywords:
- 上下文 WDK 文件系统微筛选器，文件系统支持
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: e24ff6ce9d0a7e392c74217d7619677daf58e25d
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89063650"
---
# <a name="file-system-support-for-contexts"></a>用于上下文的文件系统支持

若要支持文件上下文 (如果适用的) 、流上下文和文件对象 (流句柄) 上下文，则文件系统必须使用 [**FSRTL \_ ADVANCED \_ FCB \_ 标头**](/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_fsrtl_advanced_fcb_header) 结构。 所有 Microsoft Windows 文件系统都使用此结构，并且强烈建议所有第三方文件系统开发人员也这样做。 有关详细信息，请参阅 [**FsRtlSetupAdvancedHeader**](/previous-versions/ff547257(v=vs.85)) and **FSRTL \_ ADVANCED \_ FCB \_ HEADER**。

NTFS 和 FAT 文件系统不支持页面文件、预创建或关闭后路径或 [**IRP \_ MJ \_ 网络 \_ 查询 \_ 打开**](./flt-parameters-for-irp-mj-network-query-open.md) 操作上的文件、流或文件对象上下文。

微筛选器驱动程序可以通过分别调用 [**FltSupportsStreamContexts**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltsupportsstreamcontexts) 和 [**FltSupportsStreamHandleContexts**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltsupportsstreamhandlecontexts)，来确定文件系统是否支持给定文件对象的流上下文和文件对象上下文。

文件上下文在 Windows Vista 和更高版本上可用。

对于文件系统 (例如 FAT) ，每个文件仅支持一个数据流，文件上下文等效于流上下文。 此类文件系统通常支持流上下文，但不支持文件上下文。 相反，筛选器管理器将使用文件系统对流上下文的现有支持来提供此支持。 对于附加到这些文件系统的微筛选器驱动程序实例， [**FltSupportsFileContexts**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltsupportsfilecontexts)将返回**FALSE**，而当) 为*实例*参数传递了有效的非**NULL**值时， [**FltSupportsFileContextsEx**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltsupportsfilecontextsex)将返回**TRUE** (。

如果文件不支持上下文类型，则微筛选器无法将该类型的上下文附加到该文件。

为了支持文件上下文，文件系统必须：

* 在其文件上下文结构中嵌入 PVOID 类型的 **FileContextSupportPointer** 成员，通常 (FCB) 的文件上下文块。 文件系统必须将此成员初始化为 **NULL**。

* 使用 **FsRtlSetupAdvancedHeaderEx** (而不是 [**FsRtlSetupAdvancedHeader**](/previous-versions/ff547257(v=vs.85))) 来初始化其流上下文结构，并将有效指针传递到 **FileContextSupportPointer** 成员， (嵌入到 *FileContextSupportPointer* 参数的对应文件上下文结构) 中。 有关详细信息，请参阅 **FsRtlSetupAdvancedHeaderEx** and [**FSRTL \_ ADVANCED \_ FCB \_ HEADER**](/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_fsrtl_advanced_fcb_header)。

* 调用 **FsRtlTeardownPerFileContexts** ，以在文件系统删除文件的文件上下文结构时，释放筛选器和微筛选器驱动程序与文件相关联的所有文件上下文结构。