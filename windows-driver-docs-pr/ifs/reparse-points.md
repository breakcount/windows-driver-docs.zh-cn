---
title: 关于重新分析点
description: 描述文件系统筛选器驱动程序的重新分析点
ms.assetid: 50a4f124-024f-4b91-a51e-4f8c86e532ee
keywords:
- WDK 文件系统筛选器驱动程序，重新分析点
- 重新分析点 WDK 文件系统
ms.date: 09/10/2020
ms.localizationpriority: medium
ms.openlocfilehash: 30e3a3c1b50f1d73e53806647fa9995e06df935e
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90104638"
---
# <a name="about-reparse-points"></a>关于重新分析点

重新分析点是用于扩展文件系统属性的文件系统对象。 并非所有文件系统都支持重新分析点;例如，NTFS 和 ReFS 支持它们，但 FAT 文件系统不支持。 重新分析点包含：

- 用户定义的数据
- 唯一标识拥有重新分析点的文件系统筛选器驱动程序的 *重分析点标记* 。 所有重新分析点标记均由 Microsoft 分配，并在 *ntifs*中定义。 有些标记是为 Microsoft 保留的; [可以请求非 Microsoft 标记](reparse-point-tag-request.md)。

筛选器可以通过调用 [**FltTagFileEx**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-flttagfileex) 和 [**FltUntagFile**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltuntagfile)来设置或删除文件或目录中的重新分析点。

当文件系统使用重新分析点打开文件时，它会尝试查找与重新分析标记标识的数据格式相关联的文件系统筛选器。 如果存在，则关联的筛选器应按照重新分析数据的指示处理该文件。

有关重新分析点的详细信息，请参阅 [Windows SDK 文档](/windows/win32/fileio/reparse-points)。